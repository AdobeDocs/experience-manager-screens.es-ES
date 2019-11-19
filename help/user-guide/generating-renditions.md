---
title: Representaciones de vídeo
seo-title: Representaciones de vídeo
description: Consulte esta página para obtener información sobre la generación de representaciones en Full HD para el proyecto Screens.
seo-description: Consulte esta página para obtener información sobre la generación de representaciones en Full HD para el proyecto Screens.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Representaciones de vídeo {#video-renditions}

Puede generar representaciones en Full HD manuales o automáticas. En la siguiente sección se describe el flujo de trabajo para añadir representaciones a los recursos.

## Generación automática de representaciones en Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Si las representaciones de vídeo de AEM Screens no se reproducen de forma óptima en el dispositivo, póngase en contacto con el proveedor de hardware para conocer las especificaciones de vídeo. De este modo, podrá obtener el mejor rendimiento en el dispositivo y crear así un perfil de vídeo personalizado propio donde se proporcionan los parámetros correspondientes para que FFMPEG genere la representación. Posteriormente, siga los pasos que se indican a continuación para agregar el perfil de vídeo personalizado a la lista de perfiles.
>
>Además, consulte [Solución de problemas con los vídeos](troubleshoot-videos.md) para la depuración y solución de problemas del vídeo que se reproduce en el canal.

Siga los pasos a continuación para generar automáticamente representaciones en Full HD:

1. Seleccione el vínculo de Adobe Experience Manager (esquina superior izquierda) y haga clic en el icono de martillo para seleccionar herramientas que permiten seleccionar el **Flujo de trabajo**.

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Seleccione el modelo **DAM Update Asset **y haga clic en Editar en la barra de acciones para abrir la ventana **DAM Update Asset **ventana.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Haga doble clic en la etapa **Transcodificación FFmpeg**. 

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Seleccione la ficha **Proceso** para editar los argumentos de proceso. Enter the full HD profiles to the list in **Arguments** as: ***,profile:fullhd-bp,profile:fullhd-hp*** and click **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Haga clic en **Guardar **en la parte superior izquierda de la pantalla **Recurso de actualización DAM **.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Vaya a **Recursos** y cargue un nuevo vídeo. Haga clic en el vídeo y abra la barra lateral Representaciones y verá los dos vídeos HD completos.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Open **Renditions** from the side rail.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Verá dos nuevas representaciones en Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generación manual de representaciones en Full HD {#manually-generating-full-hd-renditions}

Siga los pasos a continuación para generar manualmente representaciones en Full HD:

1. Seleccione el vínculo de Adobe Experience Manager (esquina superior izquierda) y haga clic en el icono de martillo para seleccionar herramientas que permiten seleccionar el **Flujo de trabajo**.

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Select the **Screens Update Asset **model, and click the **Start Workflow** to open the **Run Workflow** dialog box.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Select the desired video in the **Payload** and click the **Run**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Vaya a **Recursos**, desplácese hasta el recurso y haga clic en él. 

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra el carril lateral **Representaciones**. Verá nuevas representaciones en Full HD. 

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

