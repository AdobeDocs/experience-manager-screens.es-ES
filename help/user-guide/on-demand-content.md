---
title: Actualización de contenido bajo demanda
seo-title: Actualización de contenido bajo demanda
description: 'Siga esta página para conocer la actualización de contenido bajo demanda.  '
seo-description: 'Siga esta página para conocer la actualización de contenido bajo demanda.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 221243c537e708aac44145c8d5d5a181ea80a293

---


# Actualización de contenido bajo demanda {#on-demand}

Esta sección describe el contenido bajo demanda para administrar publicaciones.

## Administración de publicación: Envío de actualizaciones de contenido desde el autor a la publicación en el dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Puede publicar y cancelar la publicación de contenido desde AEM Screens. La función Administrar publicación permite enviar actualizaciones de contenido desde el autor para publicarlas en el dispositivo. Puede publicar/cancelar la publicación de contenido para todo el proyecto de AEM Screens o solo para uno de sus canales, ubicaciones, dispositivos, aplicaciones o programaciones.

### Administración de publicaciones para un proyecto de AEM Screens {#managing-publication-for-an-aem-screens-project}

Siga los pasos a continuación para enviar actualizaciones de contenido del autor a un dispositivo para un proyecto de AEM Screens:

1. Vaya a su proyecto de AEM Screens.
1. Haga clic en **Administrar publicación** en la barra de acciones para publicar la instancia del proyecto para publicar.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. The **Manage Publication** wizard opens. Puede seleccionar la **acción** y también programar la hora de publicación de momento o posterior. Haga clic en **Siguiente**. 

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Marque la casilla para seleccionar todo el proyecto en el asistente **Administrar publicación** .

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Haga clic en **+ Incluir elementos secundarios** en la barra de acciones y desmarque todas las opciones para publicar todos los módulos del proyecto y haga clic en **Agregar** para publicarlos.

   >[!NOTE]
   >
   >De forma predeterminada, se activarán todas las casillas y deberá anular la selección manualmente para publicar todos los módulos del proyecto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Descripción del cuadro de diálogo Incluir elementos secundarios**

   El paso mencionado arriba muestra cómo puede publicar todo el contenido. En caso de que desee utilizar las otras tres alternativas disponibles, deberá comprobar esa opción en particular.
Por ejemplo, la siguiente imagen permite administrar y actualizar solo las páginas modificadas del proyecto:
   ![image](assets/author-publish-manage.png)

   Siga las explicaciones siguientes para comprender las opciones disponibles:

   1. **Incluir solo elementos secundarios**inmediatos:
Esta opción permite administrar las actualizaciones solo a los subnodos de la estructura del proyecto.
   1. **Incluir solo las páginas**modificadas:
Esta opción le permite administrar las actualizaciones únicamente en las páginas modificadas del proyecto en las que se encuentran los cambios en la estructura del proyecto.
   1. **Incluir solo las páginas**ya publicadas:
Esta opción permite administrar las actualizaciones solo en las páginas que se publicaron anteriormente.


1. Haga clic en **Publicar** en el asistente **Administrar publicación.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.
   >
   >
   >El proceso **Administrar publicación** con contenido sin conexión de actualización consta de dos pasos y los pasos deben estar en el orden correcto.
   >
   >
   >
   >    1. El flujo de trabajo no funcionará si se activa **Actualizar contenido** sin conexión antes de realizar la publicación mediante **Administrar publicación**.
      >
      >    
   1. El flujo de trabajo no funcionará si no hay cambios en el proyecto y no hay nada para **actualizar contenido** sin conexión.
   >    1. El flujo de trabajo no funcionará si el autor no completa el proceso de replicación (el contenido se sigue cargando en la instancia de publicación) después de hacer clic en el botón **Publicar** en el flujo de trabajo de administración de publicación.


1. Una vez que haya completado el flujo de trabajo de administración de publicaciones, debe activar la actualización de contenido sin conexión en el autor, lo que creará la actualización sin conexión en la instancia de creación.

   Vaya al proyecto y haga clic en **Actualizar contenido** sin conexión en la barra de acciones. Esta acción reenvía el mismo comando para publicar instancias, de modo que los archivos comprimidos sin conexión también se crean en la instancia de publicación.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)

   >[!CAUTION]
   >
   >Primero debe publicar y, a continuación, activar la actualización de contenido sin conexión, tal como se resume en los pasos anteriores.

### Administración de publicaciones para un canal {#managing-publication-for-a-channel}

Siga los pasos que se describen a continuación para enviar actualizaciones de contenido del autor a un dispositivo para un canal en un proyecto de AEM Screens:

>[!NOTE]
>
>Siga esta sección solo si hay cambios en un canal. Si un canal no tiene ningún cambio después del contenido sin conexión de la actualización anterior, el flujo de trabajo de administración de publicaciones para un canal individual no funcionará.

1. Vaya al proyecto Pantallas y seleccione el canal.
1. Haga clic en **Administrar publicación** en la barra de acciones para publicar la instancia de canal para publicar.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. The **Manage Publication** wizard opens. Puede seleccionar la **acción** y también programar la hora de publicación de momento o posterior. Haga clic en **Siguiente**. 

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Haga clic en **Publicar** en el asistente **Administrar publicación.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.

1. Una vez que haya completado el flujo de trabajo de administración de publicaciones, debe activar la actualización de contenido sin conexión en el autor, lo que creará la actualización sin conexión en la instancia de creación.

   Vaya al panel de canales y haga clic en **Actualizar contenido** sin conexión. Esta acción reenvía el mismo comando para publicar instancias, de modo que los archivos comprimidos sin conexión también se crean en la instancia de publicación.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Primero debe publicar y, a continuación, activar la actualización de contenido sin conexión, tal como se resume en los pasos anteriores.

### Reasignación de canal y dispositivo: {#channel-and-device-re-assignment}

Si ha reasignado un dispositivo, debe publicar tanto la pantalla inicial como la nueva, una vez que el dispositivo se haya reasignado a la nueva pantalla.

Del mismo modo, si ha reasignado un canal, debe publicar tanto la visualización inicial como la nueva, una vez que el canal se haya reasignado a la nueva pantalla.