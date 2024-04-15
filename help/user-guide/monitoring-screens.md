---
title: Centro de control de dispositivos de solución de problemas
description: Obtenga información sobre cómo monitorizar y solucionar problemas de rendimiento de la actividad del reproductor de AEM Screens y del dispositivo mediante el panel de dispositivos.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Solución de problemas del Centro de control de dispositivos {#troubleshooting-device-control-center}

Puede monitorizar y solucionar problemas de rendimiento de la actividad del reproductor AEM Screens y del dispositivo mediante el panel de dispositivos. Esta página proporciona información sobre cómo monitorizar y solucionar problemas de rendimiento percibidos para el reproductor Screens y los dispositivos asignados.

## Supervisión y solución de problemas desde el Centro de control de dispositivos {#monitor-and-troubleshoot-from-device-control-center}

Puede monitor el actividad y, por lo tanto, solucionar problemas de su reproductor de AEM Screens utilizando el panel de control del dispositivo.

### Tablero de dispositivo {#device-dashboard}

Siga los pasos que se indican a continuación para desplazarse al dispositivos panel:

1. Navegue hasta la dispositivos panel del proyecto, por ejemplo, ***Probar proyecto*** > ***dispositivos***.

   Seleccione **Dispositivos** y **Administrador** de dispositivos en la barra de acciones.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. La lista muestra los dispositivos asignados y no asignados, como se muestra en la figura siguiente.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Seleccione el dispositivo (**NewTestDevice**) y seleccione **Tablero** de la barra de acciones.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La página muestra la información del dispositivo, la actividad y los detalles del dispositivo que le permiten supervisar sus actividades y funciones.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorizar actividad del dispositivo {#monitor-device-activity}

El **Actividad** el panel muestra el último ping del reproductor de AEM Screens con la marca de tiempo. El último ping corresponde a la última vez que el dispositivo contactó con el servidor.

![chlimage_1](assets/chlimage_1.png)

Además, seleccione **Recopilar registros** en la esquina superior derecha del **panel de actividades** para vista los registros de su reproductor.

### Actualizar los detalles del dispositivo {#update-device-details}

Compruebe la **Detalles del dispositivo** para que pueda ver la IP del dispositivo, el uso del almacenamiento, la versión del firmware y el tiempo de actividad del reproductor del dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Además, seleccione **Borrar caché** y **Actualizar** para borrar la caché de su dispositivo y actualizar el [firmware](screens-glossary.md) versión respectivamente de este panel.

Además, seleccione **...** desde la esquina superior derecha de la **Detalles del dispositivo** panel para reiniciar o actualizar el estado del reproductor.

![chlimage_1-2](assets/chlimage_1-2.png)

### Actualizar la información del dispositivo {#update-device-information}

Compruebe el panel INFORMACIÓN **DEL** DISPOSITIVO. Aquí puede vista la actualización de configuración, dispositivos modelo, dispositivos sistema operativo y la información del shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Asimismo, seleccione (**...**) en la esquina superior derecha del panel Información del dispositivo para vista propiedades o actualizar el dispositivos.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Seleccionar **Propiedades** para que pueda ver la **Propiedades del dispositivo** Cuadro de diálogo. Puede editar el título del dispositivo o elegir la opción para las actualizaciones de configuración como **Manual** o **Automático**.

>[!NOTE]
>
>Para obtener más información acerca de los eventos asociados con las actualizaciones automáticas o manuales del dispositivo, consulte la sección ***Actualizaciones automáticas y manuales desde el panel de dispositivos*** in [Administración de canales](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Ver captura de pantalla del reproductor {#view-player-screenshot}

Puede ver la captura de pantalla del reproductor desde el dispositivo desde el **CAPTURA DE PANTALLA DEL REPRODUCTOR** panel.

Seleccionar (**...**) en la esquina superior derecha del panel Captura de pantalla del reproductor y seleccione **Actualizar captura de pantalla** para ver la instantánea del reproductor en ejecución.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Administrar preferencias {#manage-preferences}

El **PREFERENCIAS** El panel permite al usuario cambiar las preferencias de **IU de administración**, **Conmutador de canales**, y **Depuración remota** para el dispositivo.

>[!NOTE]
>Para obtener más información sobre estas opciones, consulte [AEM Screens reproductor](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Además, seleccione **Configuración** desde la esquina superior derecha para actualizar las preferencias del dispositivo. Puede actualizar las siguientes preferencias:

* **URL del servidor**
* **Resolución**
* **Reiniciar programa**
* **Número máximo. de archivos de registro que se van a conservar**
* **Nivel de registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Puede seleccionar cualquiera de los siguientes niveles de registro:
>* **Disable**
>* **Depurar**
>* **Información**
>* **Advertencia**
>* **Error**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Solución de problemas de OSGi Configuración {#troubleshoot-osgi-settings}

Active el remitente del reenvío vacío para que el dispositivos pueda entrada datos al servidor. Por ejemplo, si la propiedad referrer vacía está deshabilitada, el dispositivo no podrá devolver una captura de pantalla.

Actualmente, algunas de estas funciones solo están disponibles si la variable *Filtro de referente de Apache Sling permitir vacío* está habilitado en la configuración de OSGi. Es posible que el tablero muestre una advertencia indicando que la configuración de seguridad puede impedir que funcionen algunas de estas características.

Siga los pasos a continuación para habilitar el Filtro de referente de Apache Sling Permitir vacío

1. Desplácese hasta **Adobe Experience Manager configuración** de la consola web, es decir, `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Marque la **opción allow.empty** .
1. Seleccione **Guardar**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recomendaciones {#recommendations}

La siguiente sección recomienda supervisar los vínculos de red, los servidores y los reproductores para comprender el estado y reaccionar ante los problemas.

AEM proporciona una monitorización integrada para:

* *Heartbeat* cada 5 segundos para indicar que el Reproductor de AEM Screens está en funcionamiento.
* *Captura de pantalla* del reproductor que muestra lo que se muestra en el reproductor.
* El *Firmware del reproductor AEM Screens* versión instalada en el reproductor.
* *Espacio de almacenamiento gratuito* en el reproductor.

Recommendations para monitorado remoto con software de terceros:

* Uso de CPU en reproductores.
* Compruebe si el proceso del Reproductor de AEM Screens se está ejecutando.
* Reinicio o reinicio remoto del Reproductor.
* Notificaciones en tiempo real.

Se recomienda implementar el hardware y el sistema operativo del Reproductor de forma que permita el inicio de sesión remoto para diagnosticar problemas y reiniciar el Reproductor.

#### Otros recursos {#additional-resources}

Consulte [Vídeo Configuración de reproducción y solución de problemas](troubleshoot-videos.md) si desea depurar y solucionar problemas de los vídeos que se reproducen en su canal.
