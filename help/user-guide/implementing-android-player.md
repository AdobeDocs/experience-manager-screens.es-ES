---
title: Implementación de Android Player
seo-title: Implementación de Android Player
description: Siga esta página para conocer la implementación de Android Watchdog, una solución para recuperar el reproductor de los bloqueos.
seo-description: Siga esta página para conocer la implementación de Android Watchdog, una solución para recuperar el reproductor de los bloqueos.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: e2096260d06cc2db17d690ecbc39e8dc4f1b5aa7
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# Implementación de Android Player {#implementing-android-player}

En esta sección se describe cómo configurar el reproductor de Android. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre las opciones que se utilizarán para el desarrollo y la prueba.

Además, **Watchdog** es una solución para recuperar el reproductor de los bloqueos. Una aplicación debe registrarse en el servicio de vigilancia y luego enviar periódicamente mensajes al servicio de que está viva. En caso de que el servicio de vigilancia no reciba un mensaje de mantenimiento en el plazo estipulado, el servicio intentará reiniciar el dispositivo para una recuperación limpia (si tiene los privilegios suficientes) o reiniciar la aplicación.

## Instalación de Android Player {#installing-android-player}

Para implementar el Reproductor de Android para AEM Screens, instale el Reproductor de Android para AEM Screens.

Visite la página [**Descargas del reproductor de AEM 6.5**](https://download.macromedia.com/screens/).

### Configuración de Entorno para AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Debe configurar un entorno para el reproductor de Android si utiliza AEM Screens 6.5.5 Service Pack.

Establezca el atributo **SameSite para las cookies de inicio de sesión-token** de **Lax** a **None** de **Adobe Experience Manager Web Console Configuration** en todas las instancias de publicación y creación de AEM.

Complete los siguientes pasos:

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante `http://localhost:4502/system/console/configMgr`.

1. Busque *Controlador de autenticación de token granito de Adobe*.

1. Establezca el atributo **SameSite para las cookies de inicio de sesión-token** de **Lax** a **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.


### Método ad-hoc {#ad-hoc-method}

El método Ad-Hoc le permite instalar el último reproductor de Android (*.exe*). Visite la página [**Descargas del reproductor de AEM 6.5**](https://download.macromedia.com/screens/).

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad-hoc:

1. Presione largo tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuration** desde el menú de acción de la izquierda e introduzca la ubicación (dirección) de la instancia de AEM con la que desea conectarse y haga clic en **Save**.

1. Vaya al vínculo **Device** **Registro** del menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si el **estado** es **REGISTRADO**, verá que se rellenará el campo **ID del dispositivo**.
>
>Si **State** es **UNREGISTERED**, puede utilizar el **Token** para registrar el dispositivo.

## Implementación de Android Watchdog {#implementing-android-watchdog}

Debido a la arquitectura de Android, el reinicio del dispositivo requiere que la aplicación tenga privilegios de sistema. Para ello, debe firmar el apk con las claves de firma del fabricante; de lo contrario, Watchdog reiniciará la aplicación del reproductor y no reiniciará el dispositivo.

### Señalización de los apks de Android mediante claves de fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acceder a algunas de las API privilegiadas de Android, como *PowerManager* o *HDMIControlServices*, debe firmar el apk androide con las claves del fabricante.

>[!CAUTION]
>
>Requisitos previos:
>
>Debe tener instalado el SDK de android antes de realizar los siguientes pasos.

Siga los pasos a continuación para firmar el apk androide con las claves del fabricante:

1. Descargue el paquete de Google Play o de la página [Descargas de AEM Screens Player](https://download.macromedia.com/screens/)
1. Obtenga las claves de plataforma del fabricante para obtener un *archivo pk8* y un *archivo pem*

1. Localice la herramienta apksigner en el sdk android usando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner Signo —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Busque la ruta a la herramienta de alineación de código postal en el sdk android
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Instale ***aemscreensalign.apk*** mediante la instalación de adb en el dispositivo

## Implementación de Android Watchdog {#android-watchdog-implementation}

El servicio de vigilancia de Android cruzado se implementa como un complemento de Cordova mediante *AlarmManager*.

El siguiente diagrama muestra la implementación del servicio de vigilancia:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialización** En el momento de la inicialización del complemento de cordova, se comprueban los permisos para ver si tenemos privilegios del sistema y, por lo tanto, el permiso de reinicio. Si se cumplen estos dos criterios, se crea una intención de reinicio pendiente; de lo contrario, se crea una intención pendiente de reiniciar la aplicación (según su Actividad de inicio).

**2. Mantener activo temporizador** Se utiliza un temporizador de mantenimiento para el déclencheur de un evento cada 15 segundos. En ese evento, debe cancelar la intención pendiente existente (para reiniciar o reiniciar la aplicación) y registrar una nueva intención pendiente durante los mismos 60 segundos en el futuro (principalmente posponiendo el reinicio).

>[!NOTE]
>
>En Android, el *AlarmManager* se utiliza para registrar los *pendingIntents* que se pueden ejecutar aunque la aplicación se haya bloqueado y su envío de alarma no sea exacto de la API 19 (Kitkat). Mantenga cierto espacio entre el intervalo del temporizador y la *alarma de AlarmManager* *pendingIntent&#39;s*.

**3. Bloqueo de la aplicación** En caso de que se produzca un bloqueo, el parámetro pendingIntent para el reinicio registrado con AlarmManager ya no se restablece y, por tanto, ejecuta un reinicio o reinicio de la aplicación (según los permisos disponibles en el momento de la inicialización del complemento de Cordova).

## Aprovisionamiento masivo de Android Player {#bulk-provision-android-player}

Al desplegar el reproductor de Android de forma masiva, es necesario aprovisionar el reproductor para que apunte a una instancia de AEM, así como configurar otras propiedades sin introducir manualmente las de la interfaz de usuario del administrador.

>[!NOTE]
>Esta función está disponible en el reproductor de Android 42.0.372.

Siga los pasos a continuación para permitir el aprovisionamiento masivo en el reproductor de Android:

1. Cree un archivo JSON de configuración con el nombre `player-config.default.json`.
Consulte una [Política JSON de ejemplo](#example-json), así como una tabla que describe el uso de los distintos [Atributos de política](#policy-attributes).

1. Use un explorador de archivos MDM, ADB o Android Studio para colocar este archivo JSON de directiva en la carpeta *sdcard* del dispositivo Android.

1. Una vez implementado el archivo, utilice MDM para instalar la aplicación del reproductor.

1. Cuando se inicie la aplicación del reproductor, leerá este archivo de configuración y señalará al servidor de AEM correspondiente, donde se podrá registrar y controlar posteriormente.

   >[!NOTE]
   >Este archivo es *de sólo lectura* la primera vez que se inicia la aplicación y no se puede utilizar para configuraciones posteriores. Si el reproductor se inicia antes de que se descargue el archivo de configuración, simplemente desinstale y vuelva a instalar la aplicación en el dispositivo.

### Atributos de directiva {#policy-attributes}

La siguiente tabla resume los atributos de política con un JSON de política de ejemplo para referencia:

| **Nombre de directiva** | **Función** |
|---|---|
| *server* | Dirección URL del servidor de Adobe Experience Manager. |
| *resolución* | La resolución del dispositivo. |
| *RestartSchedule* | La programación para reiniciar se aplica a todas las plataformas. |
| *enableAdminUI* | Habilite la interfaz de usuario del administrador para configurar el dispositivo en el sitio. Establezca *false* una vez que esté completamente configurado y en producción. |
| *enableOSD* | Habilite la interfaz de usuario del conmutador de canal para que los usuarios puedan cambiar de canal en el dispositivo. Considere la opción *false* una vez que esté completamente configurado y en producción. |
| *enableActivityUI* | Active esta opción para mostrar el progreso de actividades como la descarga y la sincronización. Habilite la solución de problemas y deshabilite una vez que esté completamente configurado y en producción. |
| *enableNativeVideo* | Active esta opción para utilizar la aceleración de hardware nativa para la reproducción de vídeo (solo Android). |

### Ejemplo de directiva JSON {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>Todos los dispositivos Android tienen una carpeta *sdcard* tanto si se inserta un *sdcard* como si no. Cuando se implementa, este archivo se encuentra en el mismo nivel que la carpeta de descargas. Algunos MDM, como Samsung Knox, pueden hacer referencia a esta *ubicación de carpeta sdcard* como *almacenamiento interno*.