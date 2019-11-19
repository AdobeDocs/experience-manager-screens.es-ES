---
title: Resolución de problemas del centro de control de dispositivos
seo-title: Monitoreo de pantallas
description: Siga esta página para supervisar y solucionar problemas de rendimiento en la actividad del reproductor de pantallas y el dispositivo mediante el panel Dispositivo.
seo-description: Siga esta página para supervisar y solucionar problemas de rendimiento en la actividad del reproductor de pantallas y el dispositivo mediante el panel Dispositivo.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Resolución de problemas del centro de control de dispositivos {#troubleshooting-device-control-center}

Puede supervisar y solucionar problemas de rendimiento para la actividad y el dispositivo del reproductor de pantallas mediante el panel de control del dispositivo. Esta página proporciona información sobre cómo supervisar y solucionar problemas de rendimiento percibidos para el reproductor de pantallas y los dispositivos asignados.

## Monitorear y solucionar problemas desde el Centro de control de dispositivos {#monitor-and-troubleshoot-from-device-control-center}

Puede supervisar la actividad y, por lo tanto, solucionar los problemas del reproductor de pantallas mediante el panel de dispositivos.

### Tablero de dispositivos {#device-dashboard}

Siga los pasos a continuación para navegar al tablero del dispositivo:

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. La lista muestra los dispositivos asignados y no asignados, como se muestra en la figura siguiente.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Seleccione el dispositivo (**NewTestDevice**) y haga clic en **Tablero** en la barra de acciones.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La página muestra la información, la actividad y los detalles del dispositivo que le permiten supervisar las actividades y funciones del dispositivo.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorear la actividad del dispositivo {#monitor-device-activity}

El panel **Actividad** muestra el último ping del reproductor de pantallas con la marca de tiempo. El último ping corresponde a la última vez que el dispositivo se puso en contacto con el servidor.

![chlimage_1](assets/chlimage_1.png)

Además, haga clic en **Recopilar registros** en la esquina superior derecha del panel **Actividad** para ver los registros del reproductor.

### Actualizar detalles del dispositivo {#update-device-details}

Consulte el panel Detalles **del** dispositivo para ver la IP del dispositivo, el uso del almacenamiento, la versión del firmware y el tiempo de actividad del reproductor del dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Además, haga clic en **Borrar caché** y **Actualizar** para borrar la caché del dispositivo y actualizar la versión del [firmware](screens-glossary.md) , respectivamente, desde este panel.

**Además, haga clic en el**... en la esquina superior derecha del panel Detalles **del** dispositivo para reiniciar o actualizar el estado del reproductor.

![chlimage_1-2](assets/chlimage_1-2.png)

### Actualizar información del dispositivo {#update-device-information}

Consulte el panel **INFORMACIÓN** DEL DISPOSITIVO para ver la actualización de configuración, el modelo de dispositivo, el sistema operativo del dispositivo y la información del shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Además, haga clic en (**...**) en la esquina superior derecha del panel Información del dispositivo para ver las propiedades o actualizar el dispositivo.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Haga clic en **Propiedades** para ver el cuadro de diálogo Propiedades **del dispositivo** . Puede editar el título del dispositivo o elegir la opción para las actualizaciones de configuración como **Manual** o **Automático**.

>[!NOTE]
>
>Para obtener más información acerca de los eventos asociados con las actualizaciones automáticas o manuales del dispositivo, consulte la sección Actualizaciones ***automáticas contra manuales del panel*** del dispositivo en [Administración de canales](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Ver captura de pantalla del reproductor {#view-player-screenshot}

Puede ver la captura de pantalla del reproductor desde el dispositivo desde el panel **PLAYER SCREENSHOT **.

Haga clic (**...**) en la esquina superior derecha del panel Captura de pantalla del reproductor y seleccione **Actualizar captura de pantalla **para ver la instantánea del reproductor en ejecución.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Administrar preferencias {#manage-preferences}

El panel **PREFERENCIAS** permite al usuario cambiar las preferencias para la interfaz de usuario **del** administrador, el conmutador **de** canal y la depuración **remota** para el dispositivo.

>[!NOTE]
>
>Para obtener más información sobre estas opciones, consulte [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Además, haga clic en **Configuración** en la esquina superior derecha para actualizar las preferencias del dispositivo. Puede actualizar las siguientes preferencias:

* **URL del servidor**
* **Resolución**
* **Reiniciar programa**
* **Nº máximo de archivos de registro que se deben mantener**
* **Nivel de registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>
>Puede seleccionar cualquiera de los siguientes niveles de registro:
>
>* **Desactivar**
>* **Depurar**
>* **Información**
>* **Advertencia**
>* **Error**
>



![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Resolución de problemas de configuración de OSGI {#troubleshoot-osgi-settings}

Debe habilitar el referente vacío para permitir que el dispositivo publique datos en el servidor. Por ejemplo, si la propiedad referrer vacía está deshabilitada, el dispositivo no puede publicar una captura de pantalla de vuelta.

Actualmente, algunas de estas funciones solo están disponibles si el filtro *Apache Sling Referrer Allow Empty* está habilitado en la configuración OSGI. El tablero puede mostrar una advertencia de que la configuración de seguridad puede impedir que algunas de estas funciones funcionen.

Siga los pasos a continuación para habilitar el filtro de referente de Sling de Apache para permitir que esté vacío

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager, es decir, `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Active la opción **allow.empty **.
1. Haga clic en **Guardar**.

![climage_1-3](assets/chlimage_1-3.png)

### Recomendaciones {#recommendations}

En la siguiente sección se recomienda supervisar los vínculos de red, el servidor y los reproductores para comprender el estado y reaccionar a los problemas.

AEM proporciona supervisión integrada para:

* *Heartbeat* cada 5 segundos para indicar que AEM Screens Player está en funcionamiento.
* *Captura de pantalla* del Reproductor que muestra lo que se muestra actualmente en el Reproductor.
* La versión de firmware *del reproductor de* AEM Screens instalada en el reproductor.
* *Espacio* de almacenamiento gratuito en el reproductor.

Recomendaciones para la supervisión remota con software de terceros:

* Uso de CPU en Reproductores.
* Compruebe si se está ejecutando el proceso de AEM Screens Player.
* Reinicio/reinicio remoto del reproductor.
* Notificaciones en tiempo real.

Se recomienda implementar el hardware y el sistema operativo del reproductor de forma que permita el inicio de sesión remoto para diagnosticar problemas y reiniciar el reproductor.

#### Additional Resources {#additional-resources}

Consulte Configuración y solución de problemas [de reproducción de](troubleshoot-videos.md) vídeo para depurar y solucionar problemas de los vídeos que se reproducen en el canal.
