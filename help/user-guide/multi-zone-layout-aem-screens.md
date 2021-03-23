---
title: Diseño de varias zonas
seo-title: Diseño de varias zonas
description: El diseño de varias zonas le permite crear contenido de varias zonas y utilizar una gran variedad de recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Siga esta página para obtener más información.
seo-description: El diseño de varias zonas le permite crear contenido de varias zonas y utilizar una gran variedad de recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Siga esta página para obtener más información.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Creación en Screens
role: Administrador, Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 4%

---


# Diseño de varias zonas {#multi-zone-layout}

La siguiente página describe el uso del diseño de varias zonas y abarca los siguientes temas:

* Información general
* Creación de diseños de varias zonas
* Requisitos previos
* Uso de recursos únicos en una o varias zonas
* Uso de contenido secuencial en una o varias zonas

## Información general {#overview}

***El*** diseño de varias zonas le permite crear contenido de varias zonas y usar una variedad de recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Puede incorporar imágenes, vídeos y texto que le permitan combinarse y crear una experiencia digital intuitiva.

Según los requisitos del proyecto, a veces se necesitan varias zonas en un canal, así como poder editarlas como una sola unidad completa. Por ejemplo, una secuencia de productos con una fuente de medios sociales relacionada que se ejecuta en tres zonas independientes en un solo canal.


### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de que tiene conocimientos conceptuales sobre:

* [Creación de un proyecto de AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Creación de una visualización](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Asignación de un canal a una pantalla](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## Creación de diseños de varias zonas {#creating-multi-zone-layout}

Al crear un canal, puede utilizar diferentes plantillas para crear zonas en el canal. Puede agregar una sola imagen, vídeo o canal incrustado que permita mostrar varios recursos en una secuencia.

**Crear un canal** 

1. Seleccione el vínculo de Adobe Experience Manager (superior izquierda) y, a continuación, **Screens**. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.
1. Vaya a la carpeta **Channels** y haga clic en **Create** en la barra de acciones.

1. Seleccione **1x2 Split Screen Channel** en el asistente **Create**.

1. Haga clic en **Siguiente** e introduzca el **título** como **MultiZone**.

1. Haga clic en **Create** para completar la creación del canal.

### Uso de recursos únicos en una o varias zonas {#using-single-assets-in-one-or-more-zones}

Puede utilizar recursos únicos, como una imagen o un vídeo, en todas las zonas individuales. Siga los pasos a continuación para la implementación:

1. **Adición de contenido al canal**

   1. Vaya a **Zones** —> **Canales**—> **MultiZone**.
   1. Seleccione el canal **MultiZone** y haga clic en **Editar** en la barra de acciones para abrir el editor.

1. **Adición de imágenes al canal**

   Para reproducir una sola imagen o un vídeo en dos zonas, simplemente arrastre y suelte una imagen en cada zona del editor de canales, como se muestra en la figura siguiente:

   ![image](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de contenido secuencial en una o más zonas {#using-sequenced-content-in-one-or-more-zones}

Si desea que las zonas muestren la secuencia de imágenes y un vídeo en las diferentes zonas, siga los pasos a continuación para obtener más información.

1. **Creación de una carpeta de canales**

   1. Vaya a **Zones** —> **MultiZone** —> **Canales** y haga clic en **Crear** en la barra de acciones.
   1. Seleccione **Carpeta de canales** en el asistente **Crear** y haga clic en **Siguiente**.
   1. Introduzca el título como **EmbeddedChannels** y haga clic en **Create**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adición de dos canales más a la carpeta de canales**

   1. Vaya a **Zones** —> **Canales** —> **Canales incrustados** y haga clic en **Crear** en la barra de acciones.
   1. Seleccione **Canal de secuencia** en el asistente **Crear** para crear un canal denominado **Zone1**.
   1. Seleccione **Zone1** y haga clic en **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte algunas imágenes en este canal.
   1. Del mismo modo, cree otro canal de secuencia denominado **Zone2** en la carpeta **EmbeddedChannels**.
   1. Arrastre y suelte un vídeo en este canal.

   La siguiente figura muestra los canales **Zone1** y **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Las imágenes agregadas al editor del canal de secuencia **Zone1** se muestran a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   El vídeo añadido al editor del canal de secuencia **Zone2** se muestra a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adición de secuencias incrustadas (componente) al canal principal (MultiZone)**

   1. Vaya a **Zones** —> **Canales** —> **MultiZone**.
   1. Haga clic en **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte el componente **Secuencia integrada** en ambas zonas.
   1. Seleccione la secuencia integrada en una de las zonas.
   1. Haga clic en el icono **Configure** (llave inglesa) para seleccionar una de las secuencias incrustadas en el editor.
   1. Seleccione la ruta del canal como **Zones** —> **Canales** —> **EmbeddedChannels** —> **Zona1**, como se muestra en la figura siguiente.
   1. Del mismo modo, añada **Zone2** a otro componente de secuencia integrada en el editor.

      ![image](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creación de una ubicación y una visualización {#creating-location}

Debe crear una ubicación y una visualización para ver el contenido en el reproductor Screens. Siga los pasos a continuación para crear una ubicación y una visualización.

1. **Creación de una ubicación** 

   1. Vaya a la carpeta **Zones** —> **Ubicaciones**.
   1. Seleccione la carpeta **Locations** y haga clic en **Create** en la barra de acciones.
   1. Seleccione **Ubicación** en el asistente **Crear** y haga clic en **Siguiente**.
   1. Introduzca el **Título** como **SanJosé** y haga clic en **Crear**.

1. **Creación de una visualización**

   1. Vaya a la carpeta **Zones** —> **Ubicaciones**.
   1. Seleccione la ubicación **SanJosé** y haga clic en **Crear** en la barra de acciones.
   1. Seleccione **Display** en el asistente **Create** y haga clic en **Next**.
   1. Introduzca el **Título** como **Lobby** y haga clic en **Crear**.

### Asignación de canales a la pantalla {#channel-channel}

Debe asignar los canales a la pantalla para ver el contenido. Siga los pasos a continuación para asignar el canal a la pantalla.

1. **Asignación de canales a la pantalla**

   1. Vaya a **Zones** —> **Ubicaciones** —> **San José**—> **Vestíbulo**.
   1. Seleccione la pantalla **Lobby** y haga clic en **Asignar canal** en la barra de acciones.
   1. Introduzca la ruta al canal **MultiZone** en **Channel Path**.
   1. Configure los **Eventos admitidos** como **Carga inicial**, **Pantalla inactiva** y **Temporizador**.
   1. Haga clic en **Guardar**.

      ![image](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Del mismo modo, debe asignar los otros dos canales incrustados (**Zone1** y **Zone2**) a esta pantalla.
   1. Una vez que asigne los tres canales a la pantalla **Lobby**, debería poder ver los canales asignados desde el panel de visualización.

      ![image](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Una vez asignado el canal principal (en este caso, **MultiZone**) a la pantalla, es obligatorio asignar los otros dos canales integrados **Zone1** y **Zone2** también a la misma pantalla.

### Registro del dispositivo {#registering-device}

Una vez que haya configurado una ubicación y una pantalla, siga los pasos a continuación para registrar el dispositivo y asignar la visualización al dispositivo.

1. **Registro del dispositivo**

   1. Vaya a la carpeta **Zones** —> **Dispositivos**.
   1. Seleccione la carpeta **Devices** y haga clic en **Device Manager** en la barra de acciones.
   1. Haga clic en **Device Registration** y seleccione el dispositivo pendiente en la lista.

      >[!NOTE]
      > El título del dispositivo debe coincidir con el token del dispositivo (campo **Token**) mostrado en la pestaña **Registro del dispositivo**.
   1. Si el título coincide con el token del dispositivo, seleccione el dispositivo y haga clic en **Registrar dispositivo** en la barra de acciones.
   1. Si el código de registro coincide con el código de la pestaña **Device Registration** del reproductor Screens, haga clic en **Validate** en la barra de acciones.
      ![image](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Introduzca **Title** como **Chrome-Device1** y haga clic en **Register**.
   1. Seleccione **Asignar pantalla** y seleccione la ruta de acceso a la configuración del dispositivo.

   >[!NOTE]
   >Si está intentando ver el contenido en el reproductor Screens, asegúrese de hacer clic en **Actualizar contenido sin conexión** en el panel del canal para cada uno de los canales asignados a la pantalla.

### Visualización del resultado {#viewing-the-result}

Una vez implementados los diseños de varias zonas siguiendo los pasos anteriores, se muestra el siguiente resultado.

Compruebe el reproductor Screens para ver la salida que muestra el contenido en dos zonas diferentes. Las zonas izquierda y derecha (ambas utilizan la secuencia incrustada como componente).

La zona izquierda es un canal de secuencia y la zona derecha incluye un vídeo.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


