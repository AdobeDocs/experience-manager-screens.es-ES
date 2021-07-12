---
title: Duración de la reproducción masiva de imágenes en el nivel de canal
seo-title: Duración de la reproducción masiva de imágenes en el nivel de canal
description: En esta página se describe cómo editar la duración de la reproducción de un componente de imagen específico.
seo-description: En esta página se describe cómo editar la duración de la reproducción de un componente de imagen específico.
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
feature: Creación en Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 4%

---

# Duración de la reproducción masiva de imágenes en el nivel de canal {#channel-level-bulk-image-playback-duration}

## Información general {#overview}

Una vez creado un canal de secuencia y agregado imágenes a él, de forma predeterminada, todas las imágenes asumirán la duración de reproducción definida en la configuración de nivel de canal. Cualquier imagen individual aún puede anular el valor predeterminado y tener una duración de reproducción diferente, esto se logra editando la duración de reproducción del componente de imagen específico.

### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de que ha configurado un proyecto como requisito previo para comenzar a implementar esta funcionalidad. Por ejemplo,

1. Cree un ejemplo de proyecto de AEM Screens, **ChannelLevelPlayback**.

1. Cree un canal de secuencia como **PlaybackChannel** en la carpeta **Channels**.

1. Añada contenido a **PlaybackChannel**.

## Edición de la asignación de la duración de la reproducción de imagen en el nivel de canal {#editing-channel-level-image-playback-duration-assignment}

En la sección siguiente se explica cómo editar la duración de la reproducción del contenido en un canal de AEM Screens.

### Actualización de la duración de reproducción de imágenes en un canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga los pasos a continuación para aprender a actualizar la asignación de duración de la reproducción de imagen a nivel de canal:

1. Vaya al canal de secuencia **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Añada dos o más imágenes en el editor de canales, como se muestra en la figura siguiente.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Seleccione todas las imágenes del canal y haga clic en el icono de la llave inglesa en la parte superior izquierda (como se muestra en la figura siguiente) para abrir el cuadro de diálogo Configurar nivel de canal .

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **** Se abre el cuadro de diálogo Pagedialog.

   >[!NOTE]
   >De forma predeterminada, las imágenes de un canal se establecen en una duración de reproducción de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite la **Duración** de 8000 (ms) a 3000 (ms), es decir, 3 segundos. Haga clic en la marca de verificación en la parte superior derecha del cuadro de diálogo **Página** para guardar los cambios.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualización del resultado {#viewing-the-result}

Una vez que haya actualizado la duración de reproducción del canal (en este ejemplo, las tres imágenes), verá que las imágenes ahora se reproducirán durante 3 segundos en lugar de 8 segundos (valor predeterminado).

![channel_preview](assets/channel_preview.gif)
