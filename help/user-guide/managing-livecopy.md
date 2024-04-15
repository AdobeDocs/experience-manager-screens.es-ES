---
title: Creación y administración de una Live Copy
description: Aprenda a crear y administrar Live Copies de canales en AEM Screens.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 1%

---

# Creación y administración de una Live Copy {#creating-and-managing-a-live-copy}

En esta página se describe la creación y administración de Live Copies de canales.

A ***Live Copy*** es una copia de contenido de un sitio específico para el que se mantiene una relación activa con el origen. Esta relación activa permite que la Live Copy herede el contenido y las propiedades de página del origen.

En esta página se describe la creación de una Live Copy de un canal, la visualización de propiedades, la comprobación de estado y la propagación de cambios de un canal a su Live Copy.


## Creación de una Live Copy {#creating-a-live-copy}

Siga los pasos a continuación para crear una Live Copy de un canal en la carpeta del proyecto.

1. Seleccione el vínculo de Adobe Experience Manager (parte superior izquierda) y, a continuación, **Screens**. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.

1. Vaya al proyecto de Pantallas y seleccione **Canales**.
1. Seleccionar **Crear** y seleccione **Live Copy** para poder crear una live copy del canal.
1. Seleccione el destino y seleccione **Siguiente**.
1. Seleccione la ubicación donde puede residir la Live Copy.
1. Introduzca el **Título** y **Nombre** en el **Crear Live Copy** página.

1. Seleccionar **Abrir** para ver el contenido de la nueva live copy o **Listo** para volver a la página principal.

Alternativamente, consulte los pasos siguientes para obtener una representación visual para crear una nueva Live Copy de un canal.

El siguiente ejemplo muestra la creación de una Live Copy (***IdleLiveCopy***) para ***Canal inactivo*** con la carpeta de destino como ***Canales***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Visualización del contenido del canal de Live Copy {#viewing-content-of-the-live-copy-channel}

Una Live Copy es una copia de un canal que existe.

Para ver el contenido de su Live Copy, consulte los pasos a continuación:

1. Vaya al proyecto de Pantallas y seleccione la ubicación en la que creó originalmente la Live Copy, como se muestra en la sección anterior. (En este caso, la ubicación se eligió como **Canales** folder)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Seleccionar **Editar** de la barra de acciones.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Cuando vea contenido para un canal de Live Copy, verá un elemento adicional en el menú como **Estado de Live Copy**. Consulte la sección siguiente para obtener más información.

### Visualización de propiedades de una Live Copy {#viewing-properties-of-a-live-copy}

Además, puede ver las propiedades del canal de Live Copy.

1. Vaya al canal de Live Copy y seleccione **Propiedades** de la barra de acciones.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Seleccione el **Live Copy** para poder ver los detalles del canal.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Estado de Live Copy   {#live-copy-status}

El modo **Estado de Live Copy**, como se muestra en la figura siguiente, permite ver el estado de relación de todos los recursos del canal.

1. Seleccionar **Editar** para que pueda elegir el **Estado de Live Copy** y ver la asociación del contenido del canal con el canal original (desde el que se genera la live copy).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Seleccionar **Estado de Live Copy** para poder mostrar la página de vista previa.

   Todos los recursos con borde verde muestran que el contenido se hereda del canal original.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Romper la herencia {#breaking-the-inheritance}

También puede cancelar la herencia de la Live Copy, por lo que el contenido se vuelve independiente de la rama original.

El siguiente ejemplo muestra que selecciona la imagen en el modo de edición y selecciona el símbolo de herencia cancel en la parte superior derecha.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagación de cambios en el canal de Live Copy {#propagating-changes-to-the-live-copy-channel}

Si realiza cambios o actualizaciones en el canal original, propague esos cambios a su canal de Live Copy también.

Siga los pasos a continuación para asegurarse de que los cambios se propagan del canal original al canal de Live Copy:

1. Seleccione el canal original (***Canal inactivo***) y seleccione **Editar** de la barra de acciones.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Edite el contenido de este canal. Por ejemplo, elimine una imagen de este canal.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Seleccione la Live Copy del canal (***IdleLiveCopy***) y seleccione **Editar** de la barra de acciones. Observe que la imagen que ha eliminado sigue visible en la Live Copy.

   Para propagar los cambios, sincronice el canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. AEM Para propagar los cambios al canal de Live Copy, vaya al panel de control de y seleccione el canal de Live Copy y haga clic en **Propiedades** de la barra de acciones.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Seleccione el **Live Copy** y seleccione **Sincronizar** de la barra de acciones.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Seleccionar **Sincronización**, luego seleccione **Guardar y cerrar** AEM para volver al panel de control de la.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Observe que la imagen ahora también se elimina del canal de Live Copy.
