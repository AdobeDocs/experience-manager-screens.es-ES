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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

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

## Creación de un diseño de varias zonas {#creating-multi-zone-layout}

Al crear un canal, puede utilizar distintas plantillas para crear zonas en el canal. Puede agregar una sola imagen, vídeo o un canal incrustado que permita mostrar varios recursos en una secuencia.

### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de tener un proyecto listo como requisito previo para empezar a implementar el diseño de varias zonas. Por ejemplo,

* Creación de un proyecto de AEM Screens titulado como **zonas**
* Creación de una visualización en **Ubicaciones** tituladas **MultiZoneDisplay**

Cree un canal titulado como proyecto **MultiZone** in **Zones** . Siga los pasos a continuación:

**Creación del canal**

1. Seleccione el vínculo de Adobe Experience Manager (superior izquierda) y, a continuación, **Screens**. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. Vaya a la carpeta **Canales** y haga clic en **Crear** en la barra de acciones.

1. Seleccione Canal **dividido de pantalla de barra L** izquierda en el asistente **Crear** .

1. Haga clic en **Siguiente** e introduzca el **título** como **MultiZone**.

1. Haga clic en **Crear** para completar la creación del canal.

![screen_shot_2018-12-07at120026pm](assets/screen_shot_2018-12-07at120026pm.png)

### Uso de recursos únicos en una o varias zonas {#using-single-assets-in-one-or-more-zones}

Puede utilizar recursos únicos como una imagen o un vídeo en las tres zonas diferentes. Siga los pasos a continuación para la implementación:

1. **Adición de contenido al canal**

   1. Vaya a **Zonas** —&gt; **Canales**—&gt;**MultiZone**.
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.
   ![screen_shot_2018-12-07at14917pm](assets/screen_shot_2018-12-07at14917pm.png)

1. **Adición de imágenes al canal**

   Para reproducir una sola imagen o un vídeo en las tres zonas, simplemente arrastre y suelte la imagen en el editor de canales, como se muestra a continuación.

   ![new1-1](assets/new1-1.gif)

### Uso de contenido secuencial en una o varias zonas {#using-sequenced-content-in-one-or-more-zones}

Si desea que las zonas muestren la secuencia de imágenes o contenido y una imagen estática en tres zonas diferentes, siga los pasos a continuación para obtener más información.

1. **Creación de una carpeta de canal**

   1. Vaya a **Zonas** —&gt; **MultiZone** —&gt; **Canales** y haga clic en **Crear** en la barra de acciones.
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adición de dos canales más a la carpeta de canal**

   1. Vaya a **Zonas** —&gt; **Canales** —&gt; Canales **incrustados** y haga clic en **Crear** en la barra de acciones.
   1. Seleccione Canal **** de secuencia en el asistente **Crear** para crear un canal denominado** Zone1**.
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. Arrastre y suelte algunas imágenes en este canal.
   Del mismo modo, cree otro canal de secuencia denominado **Zone2** en la carpeta **EmbeddedChannels** .

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

1. **Adición de secuencias o componentes incrustados al canal principal (MultiZone)**

   1. Vaya a **Zonas** —&gt; **Canales** —&gt; **MultiZone**.
   1. Haga clic en **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte el componente Secuencia **** incrustada en dos de las zonas, como se muestra en la figura siguiente.
   ![nuevo](assets/new.gif)

1. **Agregar contenido a las tres zonas**

   1. Vaya a **Zonas** —&gt; **Canales** —&gt; **MultiZone**.
   1. Seleccione la secuencia incrustada en una de las zonas.
   1. Haga clic en el icono **Configurar** (llave inglesa) en una de las secuencias incrustadas en el editor.
   1. Seleccione la ruta del canal como **Zonas** —&gt; **Canales** —&gt; **Canales** incrustados —&gt; **Zona1**, como se muestra en la figura siguiente.
   Del mismo modo, agregue **Zone2** a otro componente de secuencia incrustada en el editor. Además, agregue una imagen a la tercera zona de la parte inferior, como se muestra a continuación.

   ![new2-1](assets/new2-1.gif)

#### Visualización del resultado {#viewing-the-result}

Una vez implementados los diseños de varias zonas mediante los pasos anteriores, se muestra el siguiente resultado, como se muestra en la figura siguiente.

La siguiente salida de Screens Player muestra el contenido en tres zonas diferentes. Las zonas izquierda y derecha (ambas utilizan la secuencia incrustada como componente) muestran una secuencia de imágenes y la zona siguiente muestra una imagen estática.

![new2-2](assets/new2-2.gif)
