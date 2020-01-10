---
title: Duración de reproducción de imágenes
seo-title: Duración de reproducción de imágenes
description: Siga esta página para conocer la duración de la reproducción de imágenes.
seo-description: Siga esta página para conocer la duración de la reproducción de imágenes.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49

---


# Duración de reproducción de imágenes {#image-playback-duration}

## Información general {#overview}

Una vez creado un canal de secuencia y agregado imágenes, de forma predeterminada, todas las imágenes asumirán la duración de reproducción definida en la configuración de nivel de canal. Cualquier imagen individual puede omitir el valor predeterminado y tener una duración de reproducción diferente; esto se logra editando la duración de reproducción del componente de imagen específico.

### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de haber configurado un proyecto como requisito previo para comenzar a implementarlo. Por ejemplo,

1. Creación de un proyecto de AEM Screens (en este ejemplo, **ChannelLevelPlayback**)

1. Creación de un canal de secuencia como **PlaybackChannel** en la carpeta **Canales**

1. Agregar contenido a **PlaybackChannel**

## Edición de la asignación de duración de reproducción de imágenes de nivel de canal {#editing-channel-level-image-playback-duration-assignment}

En la sección siguiente se explica cómo editar la duración de la reproducción de contenido en un canal de AEM Screens.

### Actualización de la duración de reproducción de imágenes en un canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga los pasos a continuación para obtener información sobre cómo actualizar la asignación de duración de la reproducción de imágenes en el nivel de canal:

1. Vaya al canal de secuencia **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Agregue dos o más imágenes en el editor de canales, como se muestra en la figura siguiente.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Seleccione todas las imágenes del canal y haga clic en el icono de la llave inglesa en la parte superior izquierda (como se muestra en la figura siguiente) para abrir el cuadro de diálogo Configurar nivel de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Se abre el cuadro de diálogo Página** .

   >[!NOTE]
   >
   >De forma predeterminada, las imágenes de un canal se establecen en una duración de reproducción de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite la **duración** de 8000 (ms) a 3000 (ms), es decir, 3 segundos. Haga clic en la marca de verificación en la parte superior derecha del cuadro de diálogo **Página** para guardar los cambios.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualización del resultado {#viewing-the-result}

Una vez que haya actualizado la duración de la reproducción del canal (en este ejemplo, las tres imágenes), notará que las imágenes se reproducirán durante 3 segundos en lugar de 8 segundos (valor predeterminado).

![channel_preview](assets/channel_preview.gif)

