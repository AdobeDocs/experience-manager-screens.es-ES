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
source-git-commit: 319a80a7fe3d68cbc16108eb302def390b445838
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---


# Implementación de Android Player {#implementing-android-player}

En esta sección se describe cómo configurar el reproductor de Android. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre las opciones que se utilizarán para el desarrollo y la prueba.

Además, **Watchdog** es una solución para recuperar al jugador de los bloqueos. Una aplicación debe registrarse en el servicio de vigilancia y luego enviar periódicamente mensajes al servicio de que está viva. En caso de que el servicio de vigilancia no reciba un mensaje de mantenimiento en el plazo estipulado, el servicio intentará reiniciar el dispositivo para una recuperación limpia (si tiene los privilegios suficientes) o reiniciar la aplicación.

## Instalación de Android Player {#installing-android-player}

Para implementar el Reproductor de Android para AEM Screens, instale el Reproductor de Android para AEM Screens.

Visite la página de descargas [**del reproductor**](https://download.macromedia.com/screens/) AEM 6.5.

### Configuración de Entorno para AEM Screens 6.5.5 Feature Pack y posterior {#fp-environment-setup}

Debe configurar un entorno para el reproductor de Android si utiliza AEM Screens 6.5.5 Feature Pack.

Complete los siguientes pasos:

1. Vaya a **Adobe Experience Manager Web ConsoleConfiguration** mediante `http://localhost:4502/system/console/configMgr`.

1. Busque el controlador de autenticación *Adobe Granite Token*.

1. Establezca el atributo **SameSite para las cookies** de inicio de sesión de **Lax** a **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.


### Método ad-hoc {#ad-hoc-method}

El método Ad-Hoc permite instalar el último reproductor de Android (*.exe*). Visite [**AEM página de descargas**](https://download.macromedia.com/screens/) del reproductor 6.5.

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad-hoc:

1. Presione largo tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuración** desde el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de AEM con la que desea conectarse y haga clic en **Guardar**.

1. Vaya al vínculo **Registro del** dispositivo **** desde el menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si el **estado** está **REGISTRADO**, verá que se rellenará el campo ID **del** dispositivo.
>
>Si el **estado** es **NO REGISTRADO**, puede utilizar el **testigo** para registrar el dispositivo.

## Implementación de Android Watchdog {#implementing-android-watchdog}

Debido a la arquitectura de Android, el reinicio del dispositivo requiere que la aplicación tenga privilegios de sistema. Para ello, debe firmar el apk con las claves de firma del fabricante; de lo contrario, Watchdog reiniciará la aplicación del reproductor y no reiniciará el dispositivo.

### Señalización de los apks de Android mediante claves de fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acceder a algunas de las API privilegiadas de Android como *PowerManager* o *HDMIControlServices*, debe firmar apk android con las claves del fabricante.

>[!CAUTION]
>
>Requisitos previos:
>
>Debe tener instalado el SDK de android antes de realizar los siguientes pasos.

Siga los pasos a continuación para firmar el apk androide con las claves del fabricante:

1. Descargue el paquete desde Google Play o desde la página de descargas [de](https://download.macromedia.com/screens/) AEM Screens Player
1. Obtenga las claves de plataforma del fabricante para obtener un *pk8* y un archivo *pem*

1. Localice la herramienta apksigner en el sdk android usando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Busque la ruta a la herramienta de alineación de código postal en el sdk android
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Instalar ***aemscreensalign.apk*** mediante la instalación de adb en el dispositivo

## Implementación de Android Watchdog {#android-watchdog-implementation}

El servicio de vigilancia de Android cruzado se implementa como un complemento de Cordova mediante *AlarmManager*.

El siguiente diagrama muestra la implementación del servicio de vigilancia:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialización** En el momento de la inicialización del complemento de cordova, se comprueban los permisos para ver si tenemos privilegios del sistema y, por lo tanto, el permiso de reinicio. Si se cumplen estos dos criterios, se crea una intención de reinicio pendiente; de lo contrario, se crea una intención pendiente de reiniciar la aplicación (según su Actividad de inicio).

**2. Mantener activo Temporizador** Se utiliza un temporizador de mantenimiento para activar un evento cada 15 segundos. En ese evento, debe cancelar la intención pendiente existente (para reiniciar o reiniciar la aplicación) y registrar una nueva intención pendiente durante los mismos 60 segundos en el futuro (principalmente posponiendo el reinicio).

>[!NOTE]
>
>En Android, *AlarmManager* se utiliza para registrar las *intenciones* pendientes que se pueden ejecutar aunque la aplicación se haya bloqueado y el envío de alarma no sea exacto de la API 19 (Kitkat). Mantenga cierto espacio entre el intervalo del temporizador y la alarma del *AlarmManager* *pendingIntent* .

**3. Bloqueo** de la aplicación En caso de bloqueo, el parámetro pendingIntent para el reinicio registrado con AlarmManager ya no se restablece y, por tanto, ejecuta un reinicio o reinicio de la aplicación (según los permisos disponibles en el momento de la inicialización del complemento de Cordova).
