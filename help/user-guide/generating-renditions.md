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
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Representaciones de vídeo {#video-renditions}

Puede generar representaciones Full HD manuales y automáticas. En la siguiente sección se describe el flujo de trabajo para agregar representaciones a los recursos.

## Generar automáticamente representaciones Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Si las representaciones de vídeo de AEM Screens no se reproducen de forma óptima en el dispositivo, póngase en contacto con el proveedor de hardware para obtener las especificaciones del vídeo. Esto ayuda a obtener el mejor rendimiento en el dispositivo y, por lo tanto, crea su propio perfil de vídeo personalizado donde proporciona los parámetros adecuados para que FFMPEG genere su representación. A continuación, siga los pasos a continuación para agregar su perfil de vídeo personalizado a la lista de perfiles.
>
>Consulte también [Vídeos de resolución de problemas](troubleshoot-videos.md) para depurar y solucionar problemas de reproducción de vídeo en el canal.

Siga los pasos a continuación para generar automáticamente representaciones en HD completas:

1. Seleccione el vínculo Adobe Experience Manager (parte superior izquierda) y seleccione el icono de martillo para poder seleccionar **Flujo de trabajo**.

   Seleccionar **Modelos**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. En la administración del modelo de flujo de trabajo, seleccione **Recurso de actualización DAM** modelo y seleccione **Editar** de la barra de acciones.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. En el **Recurso de actualización DAM** , haga doble clic en la **Transcodificación FFmpeg** paso.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Seleccione el **Proceso** pestaña.
1. Introduzca los perfiles de HD completos en la lista de **Argumentos** como se indica a continuación:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Seleccionar **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Seleccionar **Guardar** en la parte superior izquierda de la **Recurso de actualización DAM** pantalla.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Vaya a **Assets** y cargue un nuevo vídeo. Seleccione el vídeo y abra el carril lateral Representaciones. Observe los dos vídeos en HD completa.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Abrir **Representaciones** desde la barra lateral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Observe dos nuevas representaciones en HD completa.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generación manual de representaciones Full HD {#manually-generating-full-hd-renditions}

Siga los pasos a continuación para generar manualmente representaciones en HD completas:

1. Seleccione el enlace de Adobe Experience Manager (parte superior izquierda) y seleccione el icono de martillo para poder seleccionar herramientas y seleccionar **Flujo de trabajo**.

   Seleccionar **Modelos**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. En la administración del modelo de flujo de trabajo, seleccione **Actualizar recurso de Screens** y seleccione el modelo de **Iniciar flujo de trabajo** para abrir **Ejecutar flujo de trabajo** Cuadro de diálogo.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Seleccione el vídeo que desee en la **Carga útil** y seleccione **Ejecutar**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Vaya a **Assets**, explore en profundidad el recurso y selecciónelo.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra el **Representaciones** raíl lateral. Observe las nuevas representaciones en HD completa.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
