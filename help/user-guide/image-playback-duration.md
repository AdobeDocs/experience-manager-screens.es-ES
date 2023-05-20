---
title: Duración de reproducción de imagen
seo-title: Image Playback Duration
description: Siga esta página para obtener más información sobre la duración de la reproducción de la imagen.
seo-description: Follow this page to learn about image playback duration.
contentOwner: jsyal
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# Duración de reproducción de imagen {#image-playback-duration}

## Información general {#overview}

Una vez que cree un canal de secuencia y le añada imágenes, de forma predeterminada, todas las imágenes asumirán la duración de reproducción definida en la configuración de nivel de canal. Cualquier imagen individual puede seguir anulando el valor predeterminado y tener una duración de reproducción diferente; esto se consigue editando la duración de reproducción del componente de imagen específico.

### Requisitos previos {#prerequisites}

Antes de comenzar a implementar esta funcionalidad, asegúrese de haber configurado un proyecto como requisito previo para comenzar a implementarlo. Por ejemplo,

1. Cree un proyecto de AEM Screens (en este ejemplo, **ChannelLevelPlayback**)

1. Crear un canal de secuencia como **CanalDeReproducción** bajo **Canales** carpeta

1. Añadir contenido a **CanalDeReproducción**

## Edición de asignación de duración de reproducción de imagen a nivel de canal {#editing-channel-level-image-playback-duration-assignment}

En la sección siguiente se explica cómo editar la duración de reproducción del contenido en un canal de AEM Screens.

### Actualización de la duración de reproducción de las imágenes de un canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga los pasos a continuación para aprender a actualizar la asignación de duración de reproducción de imagen a nivel de canal:

1. Vaya al canal de secuencia **CanalDeReproducción**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Clic **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Añada dos o más imágenes en el editor de canales, como se muestra en la figura siguiente.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Seleccione todas las imágenes del canal y haga clic en el icono de la llave inglesa en la parte superior izquierda (como se muestra en la figura siguiente) para abrir el cuadro de diálogo Configurar nivel de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Página** se abre el cuadro de diálogo.

   >[!NOTE]
   >
   >De forma predeterminada, las imágenes de un canal se establecen en una duración de reproducción de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite el **Duración** de 8000 (ms) a 3000 (ms), es decir, 3 segundos. Haga clic en la marca de verificación situada en la parte superior derecha del **Página** para guardar los cambios.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualización del resultado {#viewing-the-result}

Una vez que haya actualizado la duración de reproducción del canal (en este ejemplo, las tres imágenes), verá que las imágenes se reproducirán durante 3 segundos en lugar de 8 segundos (valor predeterminado).

![channel_preview](assets/channel_preview.gif)

