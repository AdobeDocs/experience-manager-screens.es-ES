---
title: Actualización de contenido bajo demanda
seo-title: On-Demand Content Update
description: Siga esta página para obtener más información sobre la actualización de contenido bajo demanda.
seo-description: Follow this page to learn about On-Demand Content Update.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Actualización de contenido bajo demanda {#on-demand}

En esta sección se describe el contenido bajo demanda para la administración de publicaciones.

## Administración de publicaciones: entrega de actualizaciones de contenido del autor para su publicación en el dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Puede publicar y cancelar la publicación de contenido desde AEM Screens. La función Administrar publicación permite enviar actualizaciones de contenido desde el autor a la publicación en el dispositivo. Puede publicar o cancelar la publicación del contenido de todo el proyecto de AEM Screens o solo de uno de los canales, ubicaciones, dispositivos, aplicaciones o una programación.

### Administración de la publicación de un proyecto de AEM Screens {#managing-publication-for-an-aem-screens-project}

Siga los pasos a continuación para enviar actualizaciones de contenido de autor a dispositivo para un proyecto de AEM Screens:

1. Vaya al proyecto de AEM Screens.
1. Clic **Administrar publicación** en la barra de acciones para publicar el proyecto en la instancia de publicación.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. El **Administrar publicación** se abre el asistente. Puede seleccionar el **Acción** y también programar la hora de publicación para ahora o más tarde. Haga clic en **Siguiente**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Marque la casilla para seleccionar todo el proyecto **Administrar publicación** asistente.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Clic **+ Incluir elementos secundarios** en la barra de acciones, desmarque todas las opciones para publicar todos los módulos del proyecto y haga clic en **Añadir** para publicar.

   >[!NOTE]
   >
   >De forma predeterminada, se marcarán todas las casillas y tendrá que desmarcar manualmente las casillas para publicar todos los módulos del proyecto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Descripción de Incluir elementos secundarios, cuadro de diálogo**

   El paso mencionado anteriormente muestra cómo publicar todo el contenido. Si desea utilizar las otras tres alternativas disponibles, tendrá que marcar esa opción en particular.
Por ejemplo, la siguiente imagen le permite administrar y actualizar solo las páginas modificadas del proyecto:
   ![imagen](assets/author-publish-manage.png)

   Siga las explicaciones siguientes para comprender las opciones disponibles:

   1. **Incluir solo los elementos secundarios inmediatos**: Esta opción le permite administrar las actualizaciones solo a los subnodos de la estructura del proyecto.
   1. **Incluir solo las páginas modificadas**: Esta opción le permite administrar las actualizaciones únicamente en las páginas modificadas del proyecto en las que los cambios se encuentren en la estructura del proyecto.
   1. **Incluir solo las páginas ya publicadas**: Esta opción permite administrar las actualizaciones solo en las páginas publicadas anteriormente.


1. Clic **Publish** desde el **Asistente Administrar publicación.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.
   >
   >
   >    1. El flujo de trabajo no funcionará si no hay cambios en el proyecto ni nada para **Actualizar contenido sin conexión**.
   >    1. El flujo de trabajo no funcionará si el autor no completa el proceso de replicación (el contenido aún se está cargando en la instancia de publicación) después de hacer clic en **Publish** en el flujo de trabajo de administración de publicaciones.


   >[!CAUTION]
   >Si, como autor o creador de contenido, desea ver los cambios en los dispositivos conectados a la instancia de autor, haga clic en **Actualizar contenido sin conexión** en el panel de canal o seleccionando el proyecto. En este caso, la actualización del contenido sin conexión solo se realiza en la instancia de autor.

1. Vaya al proyecto y haga clic en **Actualizar contenido sin conexión** de la barra de acciones. Esta acción reenvía el mismo comando a la instancia de publicación, de modo que los archivos zip sin conexión también se crean en la instancia de publicación.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Una vez completado el flujo de trabajo de administración de publicaciones y si hay un reproductor que apunte a la instancia de autor, debe almacenar en déclencheur el contenido sin conexión de la actualización en autor, lo que creará la actualización sin conexión en la instancia de autor.

   >[!CAUTION]
   >
   >Debe almacenar en déclencheur el contenido sin conexión de la actualización en la instancia de autor, si tiene un reproductor registrado en el servidor de autor. No es necesario actualizar el contenido sin conexión para el reproductor registrado en la instancia de publicación.

### Administración de la publicación de un canal {#managing-publication-for-a-channel}

Siga los pasos a continuación para enviar actualizaciones de contenido de autor a dispositivo para un canal en un proyecto de AEM Screens:

>[!NOTE]
>
>Siga esta sección solo si hay cambios en un canal. Si un canal no tiene ningún cambio después de la actualización anterior del contenido sin conexión, el flujo de trabajo de administración de publicaciones de un canal individual no funcionará.

1. Vaya al proyecto de Screens y seleccione el canal.
1. Clic **Administrar publicación** en la barra de acciones para publicar el canal en la instancia de publicación.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. El **Administrar publicación** se abre el asistente. Puede seleccionar el **Acción** y también programar la hora de publicación para ahora o más tarde. Haga clic en **Siguiente**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Clic **Publish** desde el **Asistente Administrar publicación.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.

1. Déclencheur **Actualizar contenido sin conexión** en el panel de canal, el contenido sin conexión solo se insertará en la instancia de autor, pero no en la instancia de publicación. Los pasos del 1 al 4 son para insertar contenido sin conexión en una instancia de publicación.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Primero debe publicar y luego almacenar en déclencheur el contenido sin conexión de la actualización, como se resume en los pasos anteriores.

### Reasignación de canales y dispositivos: {#channel-and-device-re-assignment}

Si ha reasignado un dispositivo, debe publicar tanto la visualización inicial como la nueva, una vez que el dispositivo se haya reasignado a la nueva visualización.

Del mismo modo, si ha reasignado un canal, debe publicar la visualización inicial y la nueva, una vez que el canal se haya reasignado a la nueva visualización.
