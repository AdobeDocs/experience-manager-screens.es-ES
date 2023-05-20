---
title: Implementación del reproductor Android
seo-title: Implementation of Android Player
description: Siga esta página para conocer la implementación de Android Watchdog, una solución para recuperar al reproductor de bloqueos.
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# Implementación del reproductor Android {#implementing-android-player}

En esta sección se describe la configuración del reproductor Android. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre los ajustes que se deben utilizar para el desarrollo y las pruebas.

Además, **Vigilante** es una solución para recuperar el reproductor de los bloqueos. Una aplicación debe registrarse a sí misma en el servicio de vigilancia y luego enviar periódicamente mensajes al servicio de que está activa. Si el servicio de vigilancia no recibe un mensaje de conexión persistente en un plazo estipulado, el servicio intenta reiniciar el dispositivo para una recuperación limpia (si tiene los privilegios suficientes) o reiniciar la aplicación.

## Instalación del reproductor Android {#installing-android-player}

Para implementar el reproductor Android para AEM Screens, instale el reproductor Android para AEM Screens.

Visite la [**AEM Descargas del reproductor de 6.5 en**](https://download.macromedia.com/screens/) página.

### Configuración del entorno para el paquete de servicio de AEM Screens 6.5.5 {#fp-environment-setup}

>[!NOTE]
>Debe configurar un entorno para el reproductor Android si utiliza el paquete de servicio de AEM Screens 6.5.5.

Configure las variables **Atributo SameSite para las cookies de token de inicio de sesión** de **Laxo** hasta **Ninguno** de **Configuración de la consola web Adobe Experience Manager** AEM en todas las instancias de autor y publicación de la.

Complete los siguientes pasos:

1. Vaya a **Configuración de la consola web Adobe Experience Manager** usando `http://localhost:4502/system/console/configMgr`.

1. Buscar por *Controlador de autenticación de token de Granite de Adobe*.

1. Configure las variables **Atributo SameSite para las cookies de token de inicio de sesión** de **Laxo** hasta **Ninguno**.
   ![imagen](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.


### Método ad hoc {#ad-hoc-method}

El método ad hoc permite instalar el último reproductor de Android (*.exe*). Visita [**AEM Descargas del reproductor de 6.5 en**](https://download.macromedia.com/screens/) página.

Una vez que descargue la aplicación, siga los pasos del reproductor para completar la instalación ad-hoc:

1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuración** AEM en el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de a la que desea conectarse y haga clic en **Guardar**.

1. Vaya a **Dispositivo** **Registro** Vínculo del menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si la variable **Estado** es **REGISTRADO**, verá el **ID de dispositivo** Este campo se rellenará.
>
>Si la variable **Estado** es **NO REGISTRADO**, puede utilizar el **Token** para registrar el dispositivo.

## Implementación de Android Watchdog {#implementing-android-watchdog}

Debido a la arquitectura de Android, para reiniciar el dispositivo es necesario que la aplicación tenga privilegios del sistema. Para ello, es necesario firmar el apk utilizando las claves de firma del fabricante, de lo contrario watchdog reiniciará la aplicación de reproducción y no reiniciará el dispositivo.

### Señalización de los apks de Android usando las claves del fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acceder a algunas de las API privilegiadas de Android, como *PowerManager* o *HDMIControlServices* Además, debe firmar el apk de android usando las claves del fabricante.

>[!CAUTION]
>
>Requisitos previos:
>
>Debe tener instalado el SDK para Android antes de realizar los siguientes pasos.

Siga los pasos a continuación para firmar el apk de Android con las claves del fabricante:

1. Descargue el apk desde Google Play o desde [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/) página
1. Obtenga las claves de plataforma del fabricante para obtener una *pk8* y una *pem* archivo

1. Busque la herramienta apksigner en el SDK de android mediante find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Busque la ruta a la herramienta zip align en el SDK de Android.
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Instalar ***aemscreensalign.apk*** usar la instalación de adb en el dispositivo

## Explicación de los servicios de Android Watchdog {#android-watchdog-services}

El servicio de vigilancia entre Android se implementa como complemento de Cordova mediante *AlarmManager*.

El diagrama siguiente muestra la implementación del servicio de vigilancia:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialización** En el momento de la inicialización del complemento cordova, se comprueban los permisos para ver si tenemos privilegios del sistema y, por lo tanto, el permiso de reinicio. Si se cumplen estos dos criterios, se crea un objeto Intent pendiente para reiniciar; de lo contrario, se crea un objeto Intent pendiente para reiniciar la aplicación (según su actividad de inicio).

**2. Temporizador de mantenimiento activo** Se utiliza un temporizador de mantenimiento de conexión para almacenar en déclencheur un evento cada 15 segundos. En ese caso, debe cancelar la intención pendiente existente (para reiniciar la aplicación) y registrar una nueva intención pendiente durante los mismos 60 segundos en el futuro (básicamente posponiendo el reinicio).

>[!NOTE]
>
>En Android, la variable *AlarmManager* se utiliza para registrar el *pendingIntents* que se puede ejecutar incluso si la aplicación se ha estrellado y su entrega de alarma es inexacta desde la API 19 (Kitkat). Mantenga cierto espacio entre el intervalo del temporizador y el *De AlarmManager* *pendingIntent* alarma.

**3. Bloqueo de aplicación** En caso de bloqueo, pendingIntent for Reboot registrado con AlarmManager ya no se restablece y, por lo tanto, ejecuta un reinicio o reinicio de la aplicación (según los permisos disponibles en el momento de la inicialización del complemento Cordova).

## Aprovisionamiento masivo del reproductor Android {#bulk-provision-android-player}

AEM Al desplegar el reproductor de Android por lotes, es necesario aprovisionar el reproductor para que apunte a una instancia de, así como configurar otras propiedades sin introducirlas manualmente en la IU de administración.

>[!NOTE]
>Esta función está disponible en el reproductor Android 42.0.372.

Siga los pasos a continuación para permitir el aprovisionamiento masivo en el reproductor Android:

1. Cree un archivo JSON de configuración con el nombre `player-config.default.json`.
Consulte una [Ejemplo de directiva JSON](#example-json) así como una tabla que describe el uso de los distintos [Atributos de política](#policy-attributes).

1. Utilice un explorador de archivos MDM, ADB o Android Studio para soltar este archivo JSON de directiva en *sdcard* en el dispositivo Android.

1. Una vez implementado el archivo, utilice el MDM para instalar la aplicación de reproducción.

1. AEM Cuando se inicia la aplicación de reproducción, leerá este archivo de configuración y señalará al servidor de reproducción aplicable donde se puede registrar y controlar posteriormente.

   >[!NOTE]
   >Este archivo es *solo lectura* la primera vez que se inicia la aplicación y no se puede utilizar para configuraciones posteriores. Si el reproductor se inicia antes de que se descarte el archivo de configuración, simplemente desinstale y vuelva a instalar la aplicación en el dispositivo.

### Atributos de política {#policy-attributes}

La siguiente tabla resume los atributos de la política con un ejemplo de JSON de política para referencia:

| **Nombre de política** | **Función** |
|---|---|
| *servidor* | La URL del servidor de Adobe Experience Manager. |
| *resolución* | La resolución del dispositivo. |
| *rebootSchedule* | La programación para reiniciar se aplica a todas las plataformas. |
| *enableAdminUI* | Habilite la IU de administración para configurar el dispositivo en el sitio. Configure como. *false* una vez que esté completamente configurado y en producción. |
| *enableOSD* | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de configurar en *false* una vez que esté completamente configurado y en producción. |
| *enableActivityUI* | Habilite para mostrar el progreso de las actividades como descarga y sincronización. Habilite para la resolución de problemas y deshabilite una vez que esté completamente configurado y en producción. |
| *enableNativeVideo* | Habilitar para utilizar la aceleración de hardware nativa para la reproducción de vídeo (solo Android). |

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
>Todos los dispositivos Android tienen un *sdcard* carpeta si es real *sdcard* se ha insertado o no. Este archivo cuando se implementa, se encuentra en el mismo nivel que la carpeta Descargas. Algunos MDM, como Samsung Knox, pueden hacer referencia a esto *sdcard* ubicación de la carpeta como *Almacenamiento interno*.

## Aprovisionamiento masivo del reproductor Android mediante Enterprise Mobility Management {#bulk-provisioning}

AEM Al implementar el reproductor de Android de forma masiva, resulta tedioso registrar manualmente todos los reproductores con la opción de configuración de la aplicación de forma. Se recomienda encarecidamente utilizar una solución EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron o Samsung Knox para aprovisionar y administrar de forma remota su implementación. El reproductor AEM Screens Android es compatible con el estándar del sector EMM AppConfig para permitir el aprovisionamiento remoto.

## Nombrar el reproductor Android {#name-android}

Puede asignar un nombre de dispositivo descriptivo al reproductor de Android y, de este modo, enviar el nombre de dispositivo asignado a Adobe Experience Manager AEM (). Esta capacidad no solo le permite asignar un nombre al reproductor de Android, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Solo puede elegir el nombre del reproductor antes del registro. Una vez registrado el reproductor, el nombre del reproductor ya no se puede cambiar.

Siga los pasos a continuación para configurar el nombre en el reproductor Android:

1. Vaya a **configuración** —> **Acerca del dispositivo**
1. Edite y establezca el nombre del dispositivo para el reproductor de Android

### Implementación del aprovisionamiento masivo del reproductor Android mediante Enterprise Mobility Management {#implementation}

Siga los pasos a continuación para permitir el aprovisionamiento masivo en el reproductor Android:

1. Asegúrese de que el dispositivo Android sea compatible con los servicios de Google Play.
1. Registre sus dispositivos de reproducción de Android con su solución EMM favorita que admita AppConfig.
1. Inicie sesión en la consola de EMM y extraiga la aplicación del Reproductor de AEM Screens de Google Play.
1. Seleccione la configuración administrada o la opción relacionada.
1. Ahora debería ver una lista de opciones de reproductor que se pueden configurar, como servidor y código de registro en bloque.
1. Configure estos parámetros, guarde e implemente la directiva en los dispositivos.

   >[!NOTE]
   >AEM Los dispositivos deben recibir la aplicación junto con la configuración y apuntar al servidor de correcto con la configuración seleccionada. AEM Si elige configurar el código de registro en bloque y lo mantiene igual que en la configuración de, el reproductor debe poder registrarse automáticamente en el mismo. Si ha configurado una pantalla predeterminada, también puede descargar y mostrar contenido predeterminado (que luego puede cambiar según le convenga).

Además, debe consultar al proveedor de EMM sobre la compatibilidad con AppConfig. Los más populares, como [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Hierro móvil](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) y [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) entre otros, apoyan este estándar industrial.

### Uso del control remoto de Screens {#using-remote-control}

AEM Screens proporciona la funcionalidad Control remoto. Obtenga más información acerca de esta función aquí: [Control remoto de Screens](implementing-remote-control.md)
