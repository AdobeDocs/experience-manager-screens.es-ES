---
title: Implementación del reproductor Android
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
feature: Administración de Screens, Reproductor de Android
role: Administrator
level: Intermediate
source-git-commit: 7fa4207be0d89a6c7d0d9d9a04722cd40d035634
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 0%

---


# Implementación del reproductor Android {#implementing-android-player}

En esta sección se describe la configuración del reproductor Android. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre qué configuración utilizar para el desarrollo y las pruebas.

Además, **Watchdog** es una solución para recuperar el reproductor de los bloqueos. Una aplicación necesita registrarse a sí misma con el servicio de vigilancia y luego enviar periódicamente mensajes al servicio de que está vivo. En caso de que el servicio de vigilancia no reciba un mensaje de mantenimiento en el plazo estipulado, el servicio intenta reiniciar el dispositivo para una recuperación limpia (si tiene los privilegios suficientes) o reiniciar la aplicación.

## Instalación de Android Player {#installing-android-player}

Para implementar el Reproductor de Android para AEM Screens, instale el Reproductor de Android para AEM Screens.

Visite la página [**AEM 6.5 Descargas del reproductor**](https://download.macromedia.com/screens/).

### Configuración del entorno para AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Debe configurar un entorno para el reproductor Android si utiliza AEM Screens 6.5.5 Service Pack.

Establezca el atributo **SameSite para las cookies de token de inicio de sesión** de **Lax** a **None** de **Configuración de la consola web de Adobe Experience Manager** en todas las instancias de autor y publicación de AEM.

Complete los siguientes pasos:

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante `http://localhost:4502/system/console/configMgr`.

1. Busque *Controlador de autenticación de token de Granite de Adobe*.

1. Establezca el atributo **SameSite para las cookies de token de inicio de sesión** de **Lax** a **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.


### Método ad hoc {#ad-hoc-method}

El método ad-hoc le permite instalar la última versión de Android Player (*.exe*). Visite la página [**AEM 6.5 Descargas del reproductor**](https://download.macromedia.com/screens/).

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad hoc:

1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuration** en el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de AEM a la que desea conectarse y haga clic en **Save**.

1. Vaya al enlace **Device** **Registration** del menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si **State** es **REGISTER**, verá que se rellenará el campo **Device id**.
>
>Si **State** es **UNREGISTER**, puede utilizar el **Token** para registrar el dispositivo.

## Implementación de Android Watchdog {#implementing-android-watchdog}

Debido a la arquitectura de Android, el reinicio del dispositivo requiere que la aplicación tenga privilegios del sistema. Para ello, debe firmar el apk utilizando las claves de firma del fabricante; de lo contrario, watchdog reiniciará la aplicación del reproductor y no reiniciará el dispositivo.

### Señal de apks de Android que utilizan claves de fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acceder a algunas de las API privilegiadas de Android, como *PowerManager* o *HDMIControlServices*, debe firmar el apk de android con las claves del fabricante.

>[!CAUTION]
>
>Requisitos previos:
>
>Debe tener instalado el SDK de android antes de realizar los siguientes pasos.

Siga los pasos a continuación para firmar el paquete de android con las claves del fabricante:

1. Descargue el paquete desde Google Play o desde la página [Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/)
1. Obtenga las claves de plataforma del fabricante para obtener un *pk8* y un archivo *pem*

1. Busque la herramienta apksigner en el sdk de android usando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Busque la ruta de acceso a la herramienta de alineación zip en el sdk de android
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Instale ***aemscreensalign.apk*** mediante la instalación de adb en el dispositivo

## Explicación de los servicios de vigilancia de Android {#android-watchdog-services}

El servicio de vigilancia entre Android se implementa como un complemento de Cordova utilizando *AlarmManager*.

El diagrama siguiente muestra la implementación del servicio de vigilancia:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialización** En el momento de la inicialización del complemento de cordova, se comprueban los permisos para ver si tenemos privilegios del sistema y, por lo tanto, el permiso de reinicio. Si se cumplen estos dos criterios, se crea un objeto Intent for Reboot pendiente; de lo contrario, se crea un objeto Intent pendiente para reiniciar la aplicación (en función de su actividad de Launch).

**2. Mantener activo el temporizador** Se utiliza un temporizador de mantenimiento activo para almacenar en déclencheur un evento cada 15 segundos. En ese caso, debe cancelar la intención pendiente existente (para reiniciar o reiniciar la aplicación) y registrar una nueva intención pendiente durante los mismos 60 segundos en el futuro (básicamente posponiendo el reinicio).

>[!NOTE]
>
>En Android, el *AlarmManager* se utiliza para registrar el *pendingIntents* que se puede ejecutar incluso si la aplicación se ha bloqueado y su envío de alarma es inexacto de la API 19 (Kitkat). Mantenga cierto espaciado entre el intervalo del temporizador y la alarma *AlarmManager&#39;s* *pendingIntent&#39;s*.

**3. Bloqueo de la aplicación** En caso de bloqueo, pendingIntent for Reboot registrado con AlarmManager ya no se restablece y, por lo tanto, ejecuta un reinicio o reinicio de la aplicación (dependiendo de los permisos disponibles en el momento de la inicialización del complemento cordova).

## Aprovisionamiento masivo de Android Player {#bulk-provision-android-player}

Al desplegar el reproductor Android de forma masiva, es necesario aprovisionar el reproductor para que apunte a una instancia de AEM, así como configurar otras propiedades sin introducirlas manualmente en la interfaz de usuario de administración.

>[!NOTE]
>Esta función está disponible en el reproductor Android 42.0.372.

Siga los pasos a continuación para permitir el aprovisionamiento masivo en el reproductor Android:

1. Cree un archivo JSON de configuración con el nombre `player-config.default.json`.
Consulte [Ejemplo de política JSON](#example-json), así como una tabla que describe el uso de los distintos [Atributos de política](#policy-attributes).

1. Utilice un explorador de archivos MDM, ADB o Android Studio para soltar este archivo JSON de directiva en la carpeta *sdcard* del dispositivo Android.

1. Una vez implementado el archivo, utilice el MDM para instalar la aplicación del reproductor.

1. Cuando se inicie la aplicación del reproductor, leerá este archivo de configuración y señalará al servidor de AEM correspondiente, donde se podrá registrar y posteriormente controlar.

   >[!NOTE]
   >Este archivo es *de solo lectura* la primera vez que se inicia la aplicación y no se puede usar para configuraciones posteriores. Si el reproductor se inicia antes de que se descargue el archivo de configuración, simplemente desinstale y vuelva a instalar la aplicación en el dispositivo.

### Atributos de política {#policy-attributes}

La siguiente tabla resume los atributos de política con un JSON de política de ejemplo para referencia:

| **Nombre de la directiva** | **Función** |
|---|---|
| *server* | Dirección URL del servidor de Adobe Experience Manager. |
| *resolución* | Resolución del dispositivo. |
| *restartSchedule* | La programación para reiniciar se aplica a todas las plataformas. |
| *enableAdminUI* | Active la IU de administración para configurar el dispositivo en el sitio. Configúrelo en *false* una vez que esté completamente configurado y en producción. |
| *enableOSD* | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de establecer en *false* una vez que esté completamente configurado y en producción. |
| *enableActivityUI* | Habilita para mostrar el progreso de actividades como descarga y sincronización. Habilite para solucionar problemas y deshabilite una vez que esté completamente configurado y en producción. |
| *enableNativeVideo* | Habilite para utilizar la aceleración de hardware nativa para la reproducción de vídeo (solo Android). |

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
>Todos los dispositivos Android tienen una carpeta *sdcard* tanto si se ha insertado una *sdcard* como si no. Cuando se implementa, este archivo se encuentra en el mismo nivel que la carpeta Descargas . Algunos MDM, como Samsung Knox, pueden hacer referencia a esta ubicación de carpeta *sdcard* como *Internal storage*.

## Aprovisionamiento masivo de Android Player mediante Enterprise Mobility Management {#bulk-provisioning}

Al implementar el reproductor de Android de forma masiva, resulta tedioso registrar manualmente todos los reproductores con AEM. Es muy recomendable utilizar una solución EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron o Samsung Knox para aprovisionar y administrar su implementación de forma remota. El reproductor AEM Screens Android es compatible con el estándar del sector EMM AppConfig para permitir el aprovisionamiento remoto.

## Asignación de nombre al reproductor Android {#name-android}

Puede asignar un nombre de dispositivo fácil de usar al reproductor Android, enviando así el nombre de dispositivo asignado a Adobe Experience Manager (AEM). Esta capacidad no solo le permite nombrar su reproductor de Android, sino que también le permite asignar fácilmente el contenido adecuado.

Siga los pasos a continuación para configurar el nombre en el reproductor Android:

1. Vaya a **settings** —> **Acerca del dispositivo**
1. Edite y configure el nombre del dispositivo para que asigne un nombre al reproductor Android.

### Implementación del aprovisionamiento masivo de Reproductor de Android mediante la administración de movilidad empresarial {#implementation}

Siga los pasos a continuación para permitir el aprovisionamiento masivo en Android Player:

1. Asegúrese de que su dispositivo Android sea compatible con los servicios de Google Play.
1. Inscríbase sus dispositivos de reproductor Android con su solución EMM favorita que admita AppConfig.
1. Inicie sesión en la consola de EMM y extraiga la aplicación AEM Screens Player de Google Play.
1. Seleccione la configuración administrada o la opción relacionada.
1. Ahora debería ver una lista de las opciones del reproductor que se pueden configurar, como servidor y código de registro masivo.
1. Configure estos parámetros, guarde e implemente la directiva en los dispositivos.

   >[!NOTE]
   >Los dispositivos deben recibir la aplicación junto con la configuración y apuntar al servidor de AEM correcto con la configuración seleccionada. Si elige configurar el código de registro masivo y lo mantiene igual que configurado en AEM, el reproductor debería poder registrarse automáticamente. Si ha configurado una visualización predeterminada, también puede descargar y mostrar algún contenido predeterminado (que se puede cambiar posteriormente según sea conveniente).

Además, debe consultar al proveedor de EMM acerca de la compatibilidad con AppConfig . Los más populares, como [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) y [Samsung Knox&lt;a> 11/> entre otros, admiten este estándar del sector.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)
