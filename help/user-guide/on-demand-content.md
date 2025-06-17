---
title: Actualización de contenido bajo demanda
description: Obtenga información acerca de la actualización de contenido bajo demanda para administrar publicaciones.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Actualización de contenido bajo demanda {#on-demand}

En esta sección se describe el contenido bajo demanda para la administración de publicaciones.

## Administrar publicación: enviar actualizaciones de contenido del autor a la publicación en el dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Puede publicar y cancelar la publicación de contenido desde AEM Screens. **Administrar publicación** le permite enviar actualizaciones de contenido del autor a la publicación en el dispositivo. Puede publicar/cancelar la publicación del contenido de todo el proyecto de AEM Screens o solo de uno de los canales, la ubicación, el dispositivo, la aplicación o una programación.

### Administrar la publicación de un proyecto de AEM Screens {#managing-publication-for-an-aem-screens-project}

Siga los pasos a continuación para enviar actualizaciones de contenido de autor a publicación en dispositivo para un proyecto de AEM Screens:

1. Vaya al proyecto de AEM Screens.
1. Haga clic en **Administrar publicación** en la barra de acciones para poder publicar el proyecto en la instancia de publicación.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. Se abre el asistente **Administrar publicación**. Puede hacer clic en **Acción** y también programar la hora de publicación para ahora o más tarde. Haga clic en **Siguiente**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Marque la casilla para que pueda hacer clic en todo el proyecto desde el asistente **`Manage Publication`**.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Haga clic en **+ Incluir elementos secundarios** en la barra de acciones, desmarque todas las opciones para poder publicar todos los módulos del proyecto y haga clic en **Agregar** para publicar.

   >[!NOTE]
   >
   >De forma predeterminada, todas las casillas están marcadas y debe desmarcar manualmente las casillas para publicar todos los módulos del proyecto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Comprender el cuadro de diálogo Incluir elementos secundarios**

   Los pasos mencionados anteriormente muestran cómo publicar todo el contenido. Si desea utilizar las otras tres alternativas disponibles, debe marcar esa opción en particular.
Por ejemplo, la siguiente imagen muestra cómo puede administrar y actualizar solo las páginas modificadas del proyecto:
   ![imagen](assets/author-publish-manage.png)

   Siga las explicaciones siguientes para comprender las opciones disponibles:

   1. **Incluir solo elementos secundarios inmediatos**:
Esta opción permite administrar las actualizaciones únicamente en los subnodos de la estructura del proyecto.
   1. **Incluir solo las páginas modificadas**:
Esta opción le permite administrar las actualizaciones únicamente en las páginas modificadas del proyecto en las que los cambios se encuentren en la estructura del proyecto.
   1. **Incluir solo las páginas ya publicadas**:
Esta opción le permite administrar las actualizaciones solo de las páginas publicadas anteriormente.


1. En **`Manage Publication wizard`**, haga clic en **Publicar**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.
   >
   >
   >    1. El flujo de trabajo no funcionará si no hay cambios en el proyecto ni nada para **Actualizar contenido sin conexión**.
   >    1. El flujo de trabajo no funciona si el autor no completa el proceso de replicación (el contenido se está cargando en la instancia de publicación) después de seleccionar el botón **Publicar** en el flujo de trabajo de administración de publicaciones.

   >[!CAUTION]
   >Como creador de contenido, si desea ver los cambios en los dispositivos adjuntos a la instancia de autor, haga clic en **Actualizar contenido sin conexión** en el panel del canal o seleccionando el proyecto. En este caso, la actualización del contenido sin conexión solo se realiza en la instancia de autor.

1. Vaya al proyecto y haga clic en **Actualizar contenido sin conexión** desde la barra de acciones. Esta acción reenvía el mismo comando a la instancia de publicación, de modo que los archivos zip sin conexión se crean también en la instancia de publicación.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Después de completar el flujo de trabajo de administración de publicaciones y si hay un reproductor que apunte a la instancia de autor, almacene en déclencheur el contenido sin conexión de la actualización en autor. Al hacerlo, la actualización se crea sin conexión en la instancia de autor.

   >[!CAUTION]
   >
   >Almacene en déclencheur el contenido sin conexión de actualización en la instancia de autor, si tiene un reproductor registrado en el servidor de autor. No es necesario actualizar el contenido sin conexión para el reproductor registrado en la instancia de publicación.

### Administrar la publicación de un canal {#managing-publication-for-a-channel}

Siga los pasos a continuación para entregar actualizaciones de contenido de Autor > Publicar > Dispositivo para un canal en un proyecto de AEM Screens:

>[!NOTE]
>
>Siga esta sección solo si hay cambios en un canal. Si un canal no tiene ningún cambio después de la actualización anterior del contenido sin conexión, el flujo de trabajo de administración de publicaciones de un canal individual no funcionará.

1. Vaya al proyecto de AEM Screens y haga clic en el canal.
1. Haga clic en **Administrar publicación** en la barra de acciones para poder publicar el canal en la instancia de publicación.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. Se abre el asistente **Administrar publicación**. Puede hacer clic en **Acción** y también programar la hora de publicación para ahora o más tarde. Haga clic en **Siguiente**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Haga clic en **Publicar** en el asistente de **`Manage Publication`**.

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Espere unos segundos/minutos para que el contenido llegue a la instancia de publicación.

1. Al activar **Actualizar contenido sin conexión** en el panel del canal, solo se inserta el contenido sin conexión en la instancia de autor, pero no en la instancia de publicación. Los pasos del 1 al 4 sirven para insertar contenido sin conexión en una instancia de publicación.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Publique primero y, a continuación, almacene en déclencheur el contenido sin conexión de actualización como se resume en los pasos anteriores.

### Reasignación de canales y dispositivos: {#channel-and-device-re-assignment}

Si ha reasignado un dispositivo, publique la visualización inicial y la nueva visualización, una vez que el dispositivo se haya reasignado a la nueva visualización.

Del mismo modo, si ha reasignado un canal, publique tanto la visualización inicial como la nueva visualización, una vez que el canal se haya reasignado a la nueva visualización.
