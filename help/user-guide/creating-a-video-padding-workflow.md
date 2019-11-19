---
title: Creación de un flujo de trabajo de relleno de vídeo
seo-title: Creación de un flujo de trabajo de relleno de vídeo
description: Siga esta página para conocer la creación de un relleno de vídeo en el flujo de trabajo de los recursos.
seo-description: Siga esta página para conocer la creación de un relleno de vídeo en el flujo de trabajo de los recursos.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Creación de un flujo de trabajo de relleno de vídeo {#creating-a-video-padding-workflow}

Esta sección abarca los siguientes temas:

* **Información general**
* **Requisitos previos**
* **Creación de un flujo de trabajo de relleno de vídeo**
   * **Creación de un flujo de trabajo**
   * **Uso del flujo de trabajo en el proyecto de AEM Screens**

* **Validación de la salida para el flujo de trabajo**

## Información general {#overview}

El siguiente caso de uso implica colocar un vídeo (ejemplo: 1280 x 720) en un canal en el que la pantalla es de 1920 x 1080 y el vídeo se coloca en 0 x 0 (esquina superior izquierda). El vídeo no debe estirarse ni modificarse de ningún modo y no debe utilizarse **Portada** en el componente de vídeo.

El vídeo se mostrará como un objeto desde el píxel 1 hasta el píxel 1280, a lo largo y desde el píxel 1 hasta el píxel 720, y el resto del canal será el color predeterminado.

## Requisitos previos {#prerequisites}

Antes de crear un flujo de trabajo para vídeo, complete los siguientes requisitos previos:

1. Cargar un vídeo en la carpeta **Recursos** de la instancia de AEM
1. Cree un proyecto de AEM Screens (por ejemplo, **TestVideoRendition**) y un canal denominado (**VideoRendering**), como se muestra en la ilustración siguiente:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Creación de un flujo de trabajo de relleno de vídeo {#creating-a-video-padding-workflow-1}

Para crear un flujo de trabajo de relleno de vídeo, debe crear un flujo de trabajo para el vídeo y, a continuación, utilizarlo en el canal del proyecto de AEM Screens.

Siga los pasos a continuación para crear y utilizar el flujo de trabajo:

1. Creación de un flujo de trabajo
1. Uso del flujo de trabajo en un proyecto de AEM Screens

### Creación de un flujo de trabajo {#creating-a-workflow}

Siga los pasos a continuación para crear un flujo de trabajo para el vídeo:

1. Vaya a la instancia de AEM y haga clic en las herramientas desde el carril lateral. Seleccione **Flujo de trabajo** —&gt; **Modelos** para crear un nuevo modelo.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Haga clic en **Modelos** —&gt; **Crear** —&gt; **Crear modelo**. Introduzca el **Título** (como **VideoRendition**) y el **Nombre** en el Modelo **de flujo de trabajo** Agregar. Haga clic en **Finalizado** para agregar el modelo de flujo de trabajo.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Una vez creado el modelo de flujo de trabajo, seleccione el modelo (**VideoRendition**) y haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Arrastre y suelte el componente **Línea de comandos **al en el flujo de trabajo.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Seleccione el componente Línea de **comandos** y abra el cuadro de diálogo de propiedades.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Seleccione la ficha **Argumentos** para introducir los campos en el cuadro de diálogo Línea de **comandos - Propiedades** del paso.

   Introduzca el formato en los **tipos** de MIME (como ***vídeo/mp4***) y el comando como (**/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=negro" cq5dam.video.fullhd-hp .mp4***) para iniciar el flujo de trabajo en el campo **Comandos** .

   Consulte los detalles sobre los tipos **** de MIME y **los comandos** en la nota siguiente.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Seleccione el flujo de trabajo (**Representaciones** de vídeo) y haga clic en **Iniciar flujo de trabajo** en la barra de acciones para abrir el cuadro de diálogo **Ejecutar flujo de trabajo** .

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Seleccione la ruta del recurso en la **carga útil** (como ***/content/dam/huseinpeyda-cross01_512kb 2.mp4***) e introduzca el **Título ** (como ***RunVideo***) y haga clic en **Ejecutar**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Uso del flujo de trabajo en un proyecto de AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Siga los pasos a continuación para utilizar el flujo de trabajo en su proyecto de AEM Screens:

1. Vaya a un proyecto de AEM Screens (**TestVideoRendition** —&gt; **Channels** —&gt;**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. Arrastre y suelte el vídeo que cargó inicialmente en **Recursos**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Una vez cargado el vídeo, haga clic en **Vista previa** para ver el resultado.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validación de la salida para el flujo de trabajo {#validating-the-output-for-the-workflow}

Puede validar el resultado mediante:

* Compruebe la vista previa del vídeo en el canal
* Vaya a ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** en CRXDE Lite, como se muestra en la figura siguiente:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

