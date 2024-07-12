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
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Creación de un flujo de trabajo de relleno de vídeo {#creating-a-video-padding-workflow}

Esta sección trata los siguientes temas:

* **Información general**
* **Requisitos previos**
* **Creando un flujo de trabajo de relleno de vídeo**
   * **Creando un flujo de trabajo**
   * **Uso del flujo de trabajo en el proyecto de AEM Screens**

* **Validando la salida del flujo de trabajo**

## Información general {#overview}

El siguiente caso de uso implica colocar un vídeo (por ejemplo: 1280 x 720) en un canal en el que la visualización es de 1920 x 1080 y colocar el vídeo en 0x0 (parte superior izquierda). El vídeo no se debe estirar ni modificar de ninguna manera y no uses **Cover** en el componente de vídeo.

El vídeo se muestra como un objeto desde el píxel 1 al píxel 1280 de ancho y desde el píxel 1 al píxel 720 de abajo. El resto del canal es el color predeterminado.

## Requisitos previos {#prerequisites}

Antes de crear un flujo de trabajo para vídeo, complete los siguientes requisitos previos:

1. Cargue un vídeo en la carpeta **Assets AEM** de su instancia de la cuenta de usuario de la cuenta de usuario de la instancia de
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
1. Haga clic en las herramientas desde el carril lateral.
1. Haga clic en **Flujo de trabajo** > **Modelos** para poder crear un modelo.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Haga clic en **Modelos** > **Crear** > **Crear modelo**. Escriba **Title** (como **VideoRendition**) y **Name** en **Agregar modelo de flujo de trabajo**. Haga clic en **Listo** para agregar el modelo de flujo de trabajo.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Después de crear el modelo de flujo de trabajo, haga clic en el modelo (**VideoRendition**) y, a continuación, haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Arrastre y suelte el componente **`Command Line`** en el flujo de trabajo.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Haga clic en el componente **`Command Line`** y abra el cuadro de diálogo de propiedades.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Haga clic en la ficha **Argumentos**.
1. En el cuadro de diálogo **Línea de comandos - Propiedades del paso**, escriba el formato en **Tipos MIME** (como ***video/mp4***) y el comando como (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***). Este comando inicia el flujo de trabajo en el campo **Commands**.

   Vea los detalles de **Tipos MIME** y **Comandos** en la nota siguiente.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Haga clic en el flujo de trabajo (**VideoRenditions**).
1. Haga clic en **Iniciar flujo de trabajo** en la barra de acciones.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. En el cuadro de diálogo **Ejecutar flujo de trabajo**, haga clic en la ruta del recurso en la **carga útil** (como ***/content/dam/huseinpeyda-cross01_512kb 2.mp4***), escriba el **Título** como ***RunVideo*** y haga clic en **Ejecutar**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Uso del flujo de trabajo en un proyecto de AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Siga los pasos a continuación para utilizar el flujo de trabajo en su proyecto de AEM Screens:

1. Vaya a un proyecto de AEM Screens (**TestVideoRendition** > **Canales** >**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Haga clic en **Editar** en la barra de acciones. Arrastre y suelte el vídeo que subió inicialmente a **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Cuando haya subido el vídeo, haga clic en **Vista previa** para ver el resultado.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validación de la salida para el flujo de trabajo {#validating-the-output-for-the-workflow}

Para validar el resultado, haga lo siguiente:

* Compruebe una previsualización del vídeo en el canal
* Vaya a ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** en el CRXDE Lite, como se muestra en la figura siguiente:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
