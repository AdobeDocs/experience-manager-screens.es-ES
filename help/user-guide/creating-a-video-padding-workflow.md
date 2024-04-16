---
title: Creación de un flujo de trabajo de relleno de vídeo
description: Obtenga más información sobre la creación de un relleno de vídeo en el flujo de trabajo para sus recursos.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Creación de un flujo de trabajo de relleno de vídeo {#creating-a-video-padding-workflow}

Esta sección trata los siguientes temas:

* **Información general**
* **Requisitos previos**
* **Creación de un flujo de trabajo de relleno de vídeo**
   * **Creación de un flujo de trabajo**
   * **Uso del flujo de trabajo en el proyecto de AEM Screens**

* **Validación de la salida para el flujo de trabajo**

## Información general {#overview}

El siguiente caso de uso implica colocar un vídeo (por ejemplo: 1280 x 720) en un canal en el que la visualización es de 1920 x 1080 y colocar el vídeo en 0x0 (parte superior izquierda). El vídeo no se debe estirar ni modificar de ninguna manera y no utilice **Cubierta** en el componente de vídeo.

El vídeo se muestra como un objeto desde el píxel 1 al píxel 1280 de ancho y desde el píxel 1 al píxel 720 de abajo y el resto del canal es el color predeterminado.

## Requisitos previos {#prerequisites}

Antes de crear un flujo de trabajo para vídeo, complete los siguientes requisitos previos:

1. Cargar un vídeo en **Assets** AEM carpeta en la instancia de la
1. Cree un proyecto de AEM Screens (por ejemplo, **TestVideoRendition**) y un canal denominado (**VideoRendering**), como se muestra en la figura siguiente:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Creación de un flujo de trabajo de relleno de vídeo {#creating-a-video-padding-workflow-1}

Para crear un flujo de trabajo de relleno de vídeo, cree un flujo de trabajo para el vídeo y, a continuación, utilice el mismo en el canal del proyecto de AEM Screens.

Siga los pasos a continuación para crear y utilizar el flujo de trabajo:

1. Creación de un flujo de trabajo
1. Uso del flujo de trabajo en un proyecto de AEM Screens

### Creación de un flujo de trabajo {#creating-a-workflow}

Siga los pasos a continuación para crear un flujo de trabajo para el vídeo:

1. AEM Vaya a la instancia de la.
1. Haga clic en herramientas en el carril lateral.
1. Clic **Flujo de trabajo** > **Modelos** para que pueda crear un modelo.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Clic **Modelos** > **Crear** > **Crear modelo**. Introduzca el **Título** (como **VideoRendition**) y **Nombre** en el **Agregar modelo de flujo de trabajo**. Clic **Listo** para agregar el modelo de flujo de trabajo.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Después de crear el modelo de flujo de trabajo, haga clic en el modelo (**VideoRendition**) y haga clic en **Editar** de la barra de acciones.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Arrastre y suelte el **`Command Line`** al flujo de trabajo.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Haga clic en **`Command Line`** y abra el cuadro de diálogo de propiedades.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Haga clic en **Argumentos** pestaña.
1. En el **Línea de comandos - Propiedades de la etapa** , introduzca el formato en la **Tipos MIME** (como ***video/mp4***) y el comando como (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***). Este comando inicia el flujo de trabajo en **Comandos** field.

   Consulte los detalles sobre **Tipos MIME** y **Comandos** en la nota siguiente.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Haga clic en el flujo de trabajo (**VideoRenditions**).
1. Clic **Iniciar flujo de trabajo** de la barra de acciones.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. En el **Ejecutar flujo de trabajo** , haga clic en la ruta del recurso en el **Carga útil** (como ***/content/dam/huseinpeyda-cross-roads01_512kb 2.mp4***) e introduzca la **Título** as ***RunVideo*** y haga clic en **Ejecutar**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Uso del flujo de trabajo en un proyecto de AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Siga los pasos a continuación para utilizar el flujo de trabajo en su proyecto de AEM Screens:

1. Vaya a un proyecto de AEM Screens (**TestVideoRendition** > **Canales** >**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Clic **Editar** de la barra de acciones. Arrastre y suelte el vídeo que cargó inicialmente en **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Cuando haya cargado el vídeo, haga clic en **Previsualizar** para ver el resultado.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validación de la salida para el flujo de trabajo {#validating-the-output-for-the-workflow}

Para validar el resultado, haga lo siguiente:

* Compruebe la previsualización del vídeo en el canal
* Vaya a ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** en CRXDE Lite, como se muestra en la figura siguiente:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
