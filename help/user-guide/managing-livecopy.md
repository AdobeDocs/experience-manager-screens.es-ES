---
title: Creación y administración de una Live Copy
seo-title: Administración de una copia activa
description: En esta página se describe la creación y la gestión de las copias activas de canales.
seo-description: Siga esta página para crear una copia activa de un canal, ver las propiedades, comprobar el estado y propagar cambios de un canal a su copia activa.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 81%

---


# Creación y administración de una Live Copy {#creating-and-managing-a-live-copy}

En esta página se describe la creación y la gestión de las copias activas de canales.

Una ***Live Copy*** es una copia del contenido específico del sitio para el que se mantiene una relación activa con el origen. Esta relación activa permite que la Live Copy herede contenido y propiedades de página del origen.

En esta página se describe cómo crear una copia activa de un canal, ver las propiedades, comprobar el estado y propagar cambios de un canal a su copia activa.


## Creación de una copia activa {#creating-a-live-copy}

Siga los pasos que se indican a continuación para crear una copia activa de un canal en la carpeta del proyecto.

1. Seleccione el vínculo de Adobe Experience Manager (superior izquierda) y, a continuación, **Screens**. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.

1. Vaya al proyecto Screens y haga clic en **Canales**.
1. Haga clic en **Create** y seleccione **Live Copy** para crear una Live Copy del canal.

1. Seleccione el destino y haga clic en **Siguiente**.
1. Seleccione la ubicación en la que residirá la copia activa.
1. Introduzca el **Título** y el **Nombre** en la página **Crear copia activa**.

1. Haga clic en **Abrir** para ver el contenido de la copia activa nueva o en **Hecho** para volver a la página principal.

Como alternativa, siga los pasos que se explican a continuación sobre la representación visual para crear una copia activa nueva de un canal.

En el ejemplo siguiente, se muestra la creación de una copia activa (***IdleLiveCopy***) para el ***canal inactivo*** en que la carpeta de destino es ***Canales***.

![Chlimage_1-2](assets/chlimage_1-2.gif)

## Ver el contenido del canal de la copia activa {#viewing-content-of-the-live-copy-channel}

Una copia activa es una copia de un canal que ya existe.

Para ver el contenido de la copia activa, siga los pasos que se indican a continuación:

1. Vaya al proyecto de Screens y haga clic en la ubicación en la que ha creado originalmente la copia activa, tal y como se muestra en la sección anterior. (En este caso, la ubicación se eligió como carpeta **Channels** )

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Haga clic en **Editar** en la barra de acciones para ver el contenido del canal.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Al ver el contenido del canal de la copia activa, verá un elemento adicional en el menú denominado **Estado de copia activa**. Consulte la sección incluida a continuación para obtener más información.

### Ver las propiedades de una copia activa {#viewing-properties-of-a-live-copy}

Además, puede ver las propiedades del canal de la copia activa.

1. Vaya al canal de la copia activa y haga clic en **Propiedades** en la barra de acciones.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Seleccione la pestaña **Copia activa** para ver los detalles del canal.

   ![imagen_1-21](assets/chlimage_1-21.png)

### Estado de Live Copy    {#live-copy-status}

El modo **Estado de copia activa**, tal y como se muestra en la figura siguiente, le permite ver el estado de la relación de todos los recursos del canal.

1. Haga clic en **Editar** para elegir el **Estado de Live Copy** y ver la asociación del contenido del canal con el canal original (desde el que se genera la Live Copy).

   ![imagen_1-22](assets/chlimage_1-22.png)

1. Seleccione **Estado de copia activa** para mostrar la página de vista previa.

   Todos los recursos con un borde verde muestran que el contenido se hereda del canal original.

   ![imagen_1-23](assets/chlimage_1-23.png)

### Cancelar la herencia {#breaking-the-inheritance}

También se puede cancelar la herencia de la copia activa, de modo que el contenido se desvincula de la rama original.

En el ejemplo siguiente, se muestra que ha seleccionado la imagen en el modo de edición y ha hecho clic en el símbolo Cancelar herencia en la parte superior derecha.

![imagen_1-24](assets/chlimage_1-24.png)

### Propagar cambios al canal de la copia activa {#propagating-changes-to-the-live-copy-channel}

Si realiza cambios o actualizaciones en el canal original, también debe propagarlos al canal de la copia activa.

Siga los pasos que se describen a continuación para asegurarse de que los cambios se hayan propagado del canal original al canal de la copia activa:

1. Seleccione el canal original (***canal inactivo***) y haga clic en **Editar** en la barra de acciones.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Realice modificaciones en este contenido del canal. Por ejemplo, elimine una imagen de este canal.

   ![imagen_1-26](assets/chlimage_1-26.png)

1. Seleccione la copia activa del canal (***IdleLiveCopy***) y haga clic en **Editar** en la barra de acciones. Verá que la imagen que ha eliminado sigue estando visible en la copia activa.

   Para propagar los cambios, tiene que sincronizar el canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Para propagar los cambios en el canal de la copia activa, vaya al tablero de AEM, seleccione el canal de la copia activa y haga clic en **Propiedades** en la barra de acciones.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Seleccione la pestaña **Copia activa** y haga clic en **Sincronizar** en la barra de acciones.

   ![imagen_1-21](assets/chlimage_1-29.png)

1. Haga clic en **Sincronizar** para confirmar los cambios. Haga clic en **Guardar y cerrar** para volver al tablero de AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Verá que la imagen ahora también se ha eliminado del canal de la copia activa.

