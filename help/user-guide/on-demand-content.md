---
title: Actualización de contenido bajo demanda
seo-title: Actualización de contenido bajo demanda
description: 'Siga esta página para obtener más información sobre la actualización de contenido bajo demanda.  '
seo-description: 'Siga esta página para obtener más información sobre la actualización de contenido bajo demanda.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---


# Actualización de contenido bajo demanda {#on-demand}

En esta sección se describe el contenido bajo demanda para administrar publicaciones.

## Administración de publicación: Envío de actualizaciones de contenido desde el autor a la publicación en el dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Puede publicar y cancelar la publicación de contenido desde AEM Screens. La función Administrar publicación le permite enviar actualizaciones de contenido desde el autor para publicarlas en el dispositivo. Puede publicar/cancelar la publicación de contenido para todo el proyecto de AEM Screens o solo para uno de los canales, la ubicación, el dispositivo, la aplicación o una programación.

### Administración de la publicación de un proyecto de AEM Screens {#managing-publication-for-an-aem-screens-project}

Siga los pasos a continuación para enviar las actualizaciones de contenido del autor para publicarlas en el dispositivo para un proyecto de AEM Screens:

1. Vaya al proyecto de AEM Screens.
1. Haga clic en **Administrar publicación** en la barra de acciones para publicar el proyecto en la instancia de publicación.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. Se abre el asistente **Administrar publicación**. Puede seleccionar **Action** y también programar la hora de publicación por ahora o más tarde. Haga clic en **Siguiente**. 

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Marque la casilla para seleccionar todo el proyecto en el asistente **Administrar publicación**.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Haga clic en **+ Incluir elementos secundarios** en la barra de acciones y desmarque todas las opciones para publicar todos los módulos en el proyecto y haga clic en **Agregar** para publicar.

   >[!NOTE]
   >
   >De forma predeterminada, todas las casillas están marcadas y tendrá que desmarcar manualmente las casillas para publicar todos los módulos en el proyecto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Comprender el cuadro de diálogo Incluir elementos secundarios**

   El paso mencionado anteriormente muestra cómo puede publicar todo el contenido. En caso de que desee utilizar las otras tres alternativas disponibles, deberá comprobar esa opción concreta.
Por ejemplo, la siguiente imagen le permite administrar y actualizar solo las páginas modificadas de su proyecto:
   ![image](assets/author-publish-manage.png)

   Siga las explicaciones a continuación para comprender las opciones disponibles:

   1. **Incluir solo elementos secundarios** inmediatos: Esta opción le permite administrar actualizaciones solo a los subnodos de la estructura del proyecto.
   1. **Incluir solo las páginas** modificadas: Esta opción le permite administrar actualizaciones solo a las páginas modificadas del proyecto en las que se encuentren los cambios en la estructura del proyecto.
   1. **Incluir solo las páginas** ya publicadas: Esta opción permite administrar actualizaciones solo a las páginas publicadas anteriormente.


1. Haga clic en **Publicar** en el asistente **Administrar publicación.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.
   >
   >
   >    1. El flujo de trabajo no funcionará si no hay cambios en el proyecto y no hay nada para **Actualizar contenido sin conexión**.
   >    1. El flujo de trabajo no funcionará si el autor no completa el proceso de replicación (el contenido sigue cargándose en la instancia de publicación) después de hacer clic en el botón **Publish** del flujo de trabajo de administración de publicación.


   >[!CAUTION]
   >Si, como autor o creador de contenido, desea ver los cambios en los dispositivos conectados a la instancia de autor, haga clic en **Actualizar contenido sin conexión** en el panel del canal o seleccione el proyecto. En este caso, el contenido sin conexión de actualización solo se realiza en la instancia de autor.

1. Vaya al proyecto y haga clic en **Actualizar contenido sin conexión** en la barra de acciones. Esta acción reenvía el mismo comando para publicar instancias, de modo que los zip sin conexión también se creen en la instancia de publicación.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Una vez que haya completado el flujo de trabajo de administración de publicación y si hay un reproductor que apunte a la instancia de autor, debe almacenar en déclencheur el contenido sin conexión de actualización en author, lo que creará la actualización sin conexión en la instancia de autor.

   >[!CAUTION]
   >
   >Debe almacenar en déclencheur el contenido sin conexión de actualización en la instancia de autor si tiene un reproductor registrado en el servidor de creación. No es necesario actualizar el contenido sin conexión para el reproductor registrado en la instancia de publicación.

### Administración de la publicación de un canal {#managing-publication-for-a-channel}

Siga los pasos a continuación para enviar las actualizaciones de contenido del autor para publicarlas en el dispositivo para un canal en un proyecto de AEM Screens:

>[!NOTE]
>
>Siga esta sección solo si hay cambios en un canal. Si un canal no tiene ningún cambio después de la actualización anterior del contenido sin conexión, el flujo de trabajo de administración de la publicación para un canal individual no funcionará.

1. Vaya al proyecto Screens y seleccione el canal .
1. Haga clic en **Administrar publicación** en la barra de acciones para publicar el canal en la instancia de publicación.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. Se abre el asistente **Administrar publicación**. Puede seleccionar **Action** y también programar la hora de publicación por ahora o más tarde. Haga clic en **Siguiente**. 

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Haga clic en **Publicar** en el asistente **Administrar publicación.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.

1. Déclencheur **Actualizar contenido sin conexión** en el panel del canal solo insertará el contenido sin conexión en la instancia de autor, pero no en la instancia de publicación. Los pasos del 1 al 4 sirven para insertar contenido sin conexión en la instancia de publicación.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Primero debe publicar y luego almacenar en déclencheur el contenido sin conexión de actualización, como se resume en los pasos anteriores.

### Reasignación de canales y dispositivos: {#channel-and-device-re-assignment}

Si ha reasignado un dispositivo, debe publicar tanto la visualización inicial como la nueva, una vez que el dispositivo se haya reasignado a la nueva pantalla.

Del mismo modo, si ha reasignado un canal, debe publicar tanto la visualización inicial como la nueva, una vez que el canal se haya reasignado a la nueva pantalla.