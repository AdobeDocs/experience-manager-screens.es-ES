---
title: Representaciones de vídeo
description: Obtenga información acerca de la generación de representaciones Full HD para su proyecto de AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Representaciones de vídeo {#video-renditions}

Puede generar representaciones full HD manuales y automáticas. En la siguiente sección se describe el flujo de trabajo para agregar representaciones a los recursos.

## Generar automáticamente representaciones Full HD {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Si las representaciones de vídeo de AEM Screens no se reproducen de forma óptima en el dispositivo, póngase en contacto con el proveedor de hardware para obtener las especificaciones del vídeo. Al hacerlo, obtendrá el mejor rendimiento en el dispositivo. Le ayuda a crear su propio perfil de vídeo personalizado donde proporciona los parámetros adecuados para que FFMPEG genere su representación. A continuación, siga los pasos a continuación para agregar su perfil de vídeo personalizado a la lista de perfiles.
>
>Vea también [Vídeos de resolución de problemas](troubleshoot-videos.md) para depurar y solucionar problemas de reproducción de vídeo en su canal.

Siga los pasos a continuación para generar representaciones en HD completas automáticamente:

1. Haga clic en el vínculo Adobe Experience Manager (parte superior izquierda) y luego en el icono de martillo para poder hacer clic en **Flujo de trabajo**.

   Haga clic en **Modelos**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. En la administración del modelo de flujo de trabajo, haga clic en el modelo **DAM Update Asset** y luego haga clic en **Editar** en la barra de acciones.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. En la ventana **Recurso de actualización DAM**, haga doble clic en el paso **Transcodificación FFmpeg**.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Haga clic en la ficha **Proceso**.
1. Escriba los perfiles HD completos en la lista de **Argumentos** de la siguiente manera:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Haga clic en **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Haga clic en **Guardar** en la parte superior izquierda de la pantalla de **Recurso de actualización DAM**.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Vaya a **Assets** y cargue un nuevo vídeo. Haga clic en el vídeo y abra el carril lateral Representaciones. Observe los dos vídeos en HD completa.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Abra **representaciones** desde el carril lateral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Observe dos nuevas representaciones en HD completa.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generación manual de representaciones Full HD {#manually-generating-full-hd-renditions}

Siga los pasos a continuación para generar representaciones en HD completas manualmente:

1. Haga clic en el vínculo Adobe Experience Manager (parte superior izquierda) y luego en el icono de martillo para poder hacer clic en las herramientas y en **Flujo de trabajo**.

   Haga clic en **Modelos**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. En la administración del modelo de flujo de trabajo, haga clic en el modelo **Screens Update Asset** y luego en **Iniciar flujo de trabajo** para abrir el cuadro de diálogo **Ejecutar flujo de trabajo**.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Haga clic en el vídeo que quiera en **Carga útil** y luego en **Ejecutar**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Vaya a **Assets**, explore en profundidad el recurso y haga clic en él.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra el carril lateral **Representaciones**. Observe las nuevas representaciones en HD completa.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
