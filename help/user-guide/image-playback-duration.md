---
title: Duración de reproducción de imagen
description: Obtenga información acerca de la duración de la reproducción de imágenes en AEM Screens.
contentOwner: jsyal
source-git-commit: 8a914d4b0237c327b7954c936c84a2c1aa719603
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 1%

---


# Duración de reproducción de imagen {#image-playback-duration}

## Información general {#overview}

Después de crear un canal de secuencia y agregarle imágenes, de forma predeterminada, todas las imágenes asumen la duración de reproducción definida en la configuración de nivel de canal. Cualquier imagen individual puede seguir anulando el valor predeterminado y tener una duración de reproducción diferente. Esta capacidad se logra editando la duración de reproducción del componente de imagen específico.

### Requisitos previos {#prerequisites}

Antes de implementar esta funcionalidad, asegúrese de haber configurado un proyecto como requisito previo para comenzar a implementarlo. Por ejemplo,

1. Cree un proyecto de AEM Screens (en este ejemplo, **ChannelLevelPlayback**)
1. Cree un canal de secuencia como **PlaybackChannel** en la carpeta **Channels**
1. Agregar contenido a **PlaybackChannel**

## Edición de asignación de duración de reproducción de imagen a nivel de canal {#editing-channel-level-image-playback-duration-assignment}

En la sección siguiente se explica cómo editar la duración de reproducción del contenido en un canal de AEM Screens.

### Actualización de la duración de reproducción de las imágenes de un canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga los pasos a continuación para aprender a actualizar la asignación de duración de reproducción de imagen a nivel de canal:

1. Vaya al canal de secuencia **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Añada dos o más imágenes en el editor de canales, como se muestra en la figura siguiente.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Haga clic en todas las imágenes del canal y haga clic en el icono de la llave inglesa en la parte superior izquierda (como se muestra en la figura siguiente). Se abre el cuadro de diálogo Configurar nivel de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. Se abre el cuadro de diálogo **Página**.

   >[!NOTE]
   >
   >De forma predeterminada, las imágenes de un canal se establecen en una duración de reproducción de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite la **duración** de 8000 (milisegundos) a 3000 (milisegundos), es decir, 3 segundos. Haga clic en la marca de verificación situada en la parte superior derecha del cuadro de diálogo **Página** para guardar los cambios.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualización del resultado {#viewing-the-result}

Cuando haya actualizado la duración de reproducción del canal (en este ejemplo, las tres imágenes), observe que las imágenes ahora se reproducen durante 3 segundos en lugar de 8 segundos (el valor predeterminado).

![vista previa_de_canal](assets/channel_preview.gif)

