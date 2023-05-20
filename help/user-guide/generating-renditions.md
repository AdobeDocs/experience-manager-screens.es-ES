---
title: Representaciones de vídeo
seo-title: Video Renditions
description: Siga esta página para obtener más información sobre la generación de representaciones Full HD para su proyecto de Screens.
seo-description: Follow this page to learn about generating full HD renditions for your Screens project.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Representaciones de vídeo {#video-renditions}

Puede generar representaciones Full HD manuales y automáticas. En la siguiente sección se describe el flujo de trabajo para agregar representaciones a los recursos.

## Generar automáticamente representaciones Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Si las representaciones de vídeo de AEM Screens no se reproducen de forma óptima en el dispositivo, póngase en contacto con el proveedor de hardware para obtener las especificaciones del vídeo. Esto le ayudará a obtener el mejor rendimiento en el dispositivo y, por lo tanto, a crear su propio perfil de vídeo personalizado donde proporcionará los parámetros adecuados para que FFMPEG genere su representación. Posteriormente, siga los pasos a continuación para agregar su perfil de vídeo personalizado a la lista de perfiles.
>
>Además, consulte [Vídeos de resolución de problemas](troubleshoot-videos.md) para depurar y solucionar problemas de reproducción de vídeo en el canal.

Siga los pasos a continuación para generar automáticamente representaciones en HD completas:

1. Seleccione el vínculo de Adobe Experience Manager (parte superior izquierda) y haga clic en el icono de martillo para seleccionar las herramientas que desea seleccionar **Flujo de trabajo**.

   Clic **Modelos** para introducir la administración de modelos de flujo de trabajo.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Seleccione el **Recurso de actualización DAM** y haga clic en Editar en la barra de acciones para abrir **Recurso de actualización DAM** ventana.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Haga doble clic en **Transcodificación FFmpeg** paso.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Seleccione el **Proceso** para editar los argumentos del proceso. Introduzca los perfiles de HD completos en la lista de **Argumentos** como: ***,profile:fullhd-bp,profile:fullhd-hp*** y haga clic en **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Clic **Guardar** en la parte superior izquierda de la **Recurso de actualización DAM** pantalla.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Vaya a **Assets** y cargue un nuevo vídeo. Haga clic en el vídeo y abra el carril lateral Representaciones y verá los dos vídeos de alta definición completa.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Abrir **Representaciones** desde la barra lateral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Observará dos nuevas representaciones en HD completa.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generación manual de representaciones Full HD {#manually-generating-full-hd-renditions}

Siga los pasos a continuación para generar manualmente representaciones en HD completas:

1. Seleccione el vínculo de Adobe Experience Manager (parte superior izquierda) y haga clic en el icono de martillo para seleccionar las herramientas que desea seleccionar **Flujo de trabajo**.

   Clic **Modelos** para introducir la administración de modelos de flujo de trabajo.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Seleccione el **Actualizar recurso de Screens** y haga clic en el **Iniciar flujo de trabajo** para abrir **Ejecutar flujo de trabajo** Cuadro de diálogo.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Seleccione el vídeo que desee en la **Carga útil** y haga clic en **Ejecutar**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Vaya a **Assets**, explore en profundidad el recurso y haga clic en él.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra el **Representaciones** y se darán cuenta de las nuevas representaciones en HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
