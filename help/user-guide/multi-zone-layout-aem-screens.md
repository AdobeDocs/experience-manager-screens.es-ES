---
title: Diseño de varias zonas
seo-title: Diseño de varias zonas
description: El diseño de varias zonas permite crear contenido de varias zonas y utilizar una gran variedad de recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Siga esta página para obtener más información.
seo-description: El diseño de varias zonas permite crear contenido de varias zonas y utilizar una gran variedad de recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Siga esta página para obtener más información.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: a246671ddf7fee333d01c09ca61daee91df737e4
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 4%

---


# Diseño de varias zonas {#multi-zone-layout}

La página siguiente describe el uso del diseño de varias zonas y abarca los siguientes temas:

* Información general
* Creación de un diseño de varias zonas
* Requisitos previos
* Uso de recursos únicos en una o varias zonas
* Uso de contenido secuencial en una o varias zonas

## Información general {#overview}

***El diseño*** de varias zonas permite crear contenido de varias zonas y utilizar una gran variedad de recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Puede obtener imágenes, vídeos y texto que le permitan combinarse y crear una experiencia digital intuitiva.

Según los requisitos del proyecto, a veces se necesitan varias zonas en un canal, así como poder editarlas como una sola unidad completa. Por ejemplo, una secuencia de productos con una fuente de medios sociales relacionada que se ejecuta en tres zonas distintas en un solo canal.


### Requisitos previos {#prerequisites}

Antes de inicio de implementar esta funcionalidad, asegúrese de tener conocimientos conceptuales sobre:

* [Creación de un proyecto de AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Creación de una visualización](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Asignación de un Canal a una pantalla](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## Creación de un diseño de varias zonas {#creating-multi-zone-layout}

Al crear un canal, puede utilizar distintas plantillas para crear zonas en el canal. Puede agregar una sola imagen, vídeo o un canal incrustado que permita mostrar varios recursos en una secuencia.

**Creación del Canal**

1. Seleccione el vínculo de Adobe Experience Manager (superior izquierda) y, a continuación, **Screens**. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. Vaya a la carpeta **Canales** y haga clic en **Crear** en la barra de acciones.

1. Seleccione **1x2 Canal** de pantalla dividida en el asistente **Crear** .

1. Haga clic en **Siguiente** e introduzca el **título** como **MultiZone**.

1. Haga clic en **Crear** para completar la creación del canal.

### Uso de recursos únicos en una o varias zonas {#using-single-assets-in-one-or-more-zones}

Puede utilizar recursos únicos como una imagen o un vídeo en todas las zonas individuales. Siga los pasos a continuación para la implementación:

1. **Añadir contenido al Canal**

   1. Vaya a **Zones** —> **Canales**—> **MultiZone**.
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.

1. **Añadir imágenes al Canal**

   Para reproducir una sola imagen o un vídeo en dos zonas, simplemente arrastre y suelte una imagen en cada zona del editor de canal, como se muestra en la figura siguiente:

   ![image](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de contenido secuencial en una o varias zonas {#using-sequenced-content-in-one-or-more-zones}

Si desea que las zonas muestren la secuencia de imágenes y un vídeo en las distintas zonas, siga los pasos a continuación para obtener más información.

1. **Creación de una carpeta de Canal**

   1. Vaya a **Zonas** —> **MultiZone** —> **Canales** y haga clic en **Crear** en la barra de acciones.
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Añadir dos canales más a la carpeta Canal**

   1. Vaya a **Zonas** —> **Canales** —> Canales **incrustados** y haga clic en **Crear** en la barra de acciones.
   1. Seleccione **Secuencia Canal** en el asistente **Crear** para crear un canal denominado **Zona1**.
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. Arrastre y suelte algunas imágenes en este canal.
   1. Del mismo modo, cree otro canal de secuencia denominado **Zone2** en la carpeta **EmbeddedChannels** .
   1. Arrastre y suelte un vídeo en este canal.
   La siguiente figura muestra los canales **Zone1** y **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Las imágenes agregadas al editor del canal de secuencia de **Zone1** se muestran a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   El vídeo agregado al editor del canal de secuencia de **Zone2** se muestra a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Añadir secuencias incrustadas (componente) al canal principal (MultiZone)**

   1. Vaya a **Zones** —> **Canales** —> **MultiZone**.
   1. Haga clic en **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte el componente Secuencia **** incrustada en ambas zonas.
   1. Seleccione la secuencia incrustada en una de las zonas.
   1. Haga clic en el icono **Configurar** (llave inglesa) en una de las secuencias incrustadas en el editor.
   1. Seleccione la ruta de canal como **Zonas** —> **Canales** —> **Canales** incrustados —> **Zona1**, como se muestra en la figura siguiente.
   1. Del mismo modo, agregue **Zone2** a otro componente de secuencia incrustada en el editor.

      ![image](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creación de una ubicación y una visualización {#creating-location}

Debe crear una ubicación y una pantalla para la vista del contenido en el reproductor de pantallas. Siga los pasos a continuación para crear una ubicación y una visualización.

1. **Creación de una ubicación** 

   1. Vaya a la carpeta **Zones** —> **Ubicaciones** .
   1. Seleccione la carpeta **Ubicaciones** y haga clic en **Crear** en la barra de acciones.
   1. Select **Location** from the **Create** wizard and click **Next**.
   1. Enter the **Title** as **SanJose** and click **Create**.

1. **Creación de una visualización**

   1. Vaya a la carpeta **Zones** —> **Ubicaciones** .
   1. Seleccione la ubicación de **SanJosé** y haga clic en **Crear** en la barra de acciones.
   1. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter the **Title** as **Lobby** and click **Create**.

### Asignación de Canales a la visualización {#channel-channel}

Debe asignar los canales a la pantalla para la vista del contenido. Siga los pasos a continuación para asignar el canal a la pantalla.

1. **Asignación de Canales a la visualización**

   1. Vaya a **Zonas** —> **Ubicaciones** —> **SanJosé**—> **Punto de encuentro**.
   1. Seleccione la pantalla **Punto de encuentro** y haga clic en **Asignar Canal** en la barra de acciones.
   1. Introduzca la ruta de acceso al canal **MultiZone** en Ruta **de** Canal.
   1. Defina los Eventos **** admitidos como Carga **** inicial, **Pantalla** inactiva y **Temporizador**.
   1. Haga clic en **Guardar**.

      ![image](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Del mismo modo, debe asignar los otros dos canales incrustados (**Zone1** y **Zone2**) a esta pantalla.
   1. Una vez que asigne los tres canales a la pantalla **Punto de encuentro** , deberá poder realizar la vista de los canales asignados desde el panel de visualización.

      ![image](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!Iimportante]
      > Una vez asignado el canal principal (en este caso, **MultiZone**) a la pantalla, es obligatorio asignar los otros dos canales incrustados **Zone1** y **Zone2** también a la misma pantalla.

### Registro del dispositivo {#registering-device}

Una vez que haya configurado una ubicación y una pantalla, siga los pasos a continuación para registrar el dispositivo y asignar la visualización al dispositivo.

1. **Registro del dispositivo**

   1. Vaya a la carpeta **Zones** —> **Dispositivos** .
   1. Select the **Devices** folder and click **Device Manager** from the action bar.
   1. Haga clic en Registro **del** dispositivo y seleccione el dispositivo pendiente en la lista.
      >[!NOTE]
      > El título del dispositivo debe coincidir con el token del dispositivo (campo **Token** ) que se muestra en la ficha Registro **del** dispositivo.
   1. Si el título coincide con el autentificador del dispositivo, seleccione el dispositivo y haga clic en **Registrar dispositivo** en la barra de acciones.
   1. Si el código de registro coincide con el código de la ficha Registro **del** dispositivo del reproductor de pantallas, haga clic en **Validar** en la barra de acciones.
      ![image](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Enter the **Title** as **Chrome-Device1** and click **Register**.
   1. Seleccione **Asignar visualización** y seleccione la ruta de acceso a la configuración del dispositivo.
   >[!NOTE]
   >Si está intentando vista del contenido en el reproductor de pantallas, asegúrese de hacer clic en **Actualizar contenido** sin conexión en el panel de canal para cada uno de los canales asignados a la pantalla.

### Visualización del resultado {#viewing-the-result}

Una vez implementados los diseños de varias zonas mediante los pasos anteriores, se muestra el siguiente resultado.

Compruebe el reproductor de pantallas para vista de la salida que muestra el contenido en dos zonas diferentes. Las zonas izquierda y derecha (ambas utilizan la secuencia incrustada como componente).

La zona izquierda es un canal de secuencia y la zona derecha incluye un vídeo.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


