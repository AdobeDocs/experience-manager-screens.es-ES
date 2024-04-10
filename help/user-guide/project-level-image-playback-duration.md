---
title: Duración de reproducción de imagen de nivel de proyecto
description: Aprenda a definir la duración de la reproducción de la imagen en el nivel de proyecto.
contentOwner: jsyal
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 1%

---


# Duración de reproducción de imagen de nivel de proyecto {#project-level-image-playback}

## Información general {#overview}

Esta función permite definir la duración de la reproducción de la imagen en el nivel de proyecto. Todas las imágenes heredan esta duración de reproducción de forma predeterminada. Si no se define ninguna duración en el nivel de proyecto, la reproducción predeterminada de 8 segundos continuará.

### Requisitos previos {#prerequisites}

Antes de utilizar esta función, asegúrese de configurar un proyecto como requisito previo para comenzar a implementar esta funcionalidad. Por ejemplo,

1. Cree un proyecto de AEM Screens (en este ejemplo, **ProjectLevelPlayback**)

1. Crear un canal de secuencia como **PlayBackChannel** bajo **Canales** carpeta

1. Añadir contenido a **PlayBackChannel**

   ![activos](assets/image_playback1.png)

   Por ejemplo, la siguiente imagen muestra las imágenes agregadas al **PlayBackChannel** editor:

   ![activos](assets/image_playback2.png)

## Edición de asignación de duración de reproducción de imagen a nivel de proyecto {#editing-project-level-image-playback-duration-assignment}

En la sección siguiente se explica cómo editar la duración de reproducción del contenido en un proyecto de AEM Screens.

### Actualización de la duración de reproducción de imágenes en el nivel de proyecto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Si desea actualizar una duración de reproducción a nivel de imagen o de canal, consulte [Duración de reproducción de imagen a nivel de canal](channel-level-image-playback.md).

Siga los pasos a continuación para aprender a actualizar la duración de reproducción de imagen a nivel de proyecto:

1. Navegar al proyecto **ProjectLevelPlayback** y haga clic en **Propiedades** de la barra de acciones.
   ![activos](assets/image_playback3.png)

1. Seleccione todas las imágenes del canal y haga clic en el icono de la llave inglesa en la parte superior izquierda (como se muestra en la figura siguiente) para abrir el cuadro de diálogo Configurar nivel de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Página** se abre el cuadro de diálogo.

   >[!NOTE]
   >
   >De forma predeterminada, las imágenes de un canal se establecen en una duración de reproducción de 8 segundos y los vídeos se reproducen con la duración predeterminada.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite el **Duración** de 8000 (ms) a 3000 (ms), es decir, 3 segundos. Haga clic en la marca de verificación situada en la parte superior derecha del **Página** para guardar los cambios.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualización del resultado {#viewing-the-result}

Una vez que haya actualizado la duración de reproducción del canal (en este ejemplo, las tres imágenes), verá que las imágenes se reproducirán durante 3 segundos en lugar de 8 segundos (valor predeterminado).

![channel_preview](assets/channel_preview.gif)

