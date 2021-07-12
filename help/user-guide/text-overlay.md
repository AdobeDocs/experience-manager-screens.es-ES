---
title: Superposición de texto
seo-title: Superposición de texto
description: La superposición de texto es una función disponible en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen. Siga esta página para obtener más información.
seo-description: La superposición de texto es una función disponible en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen. Siga esta página para obtener más información.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Creación en Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 3%

---

# Superposición de texto {#text-overlay}

Esta sección cubre los siguientes temas:

* **Información general**
* **Uso de la superposición de texto**
* **Explicación de las propiedades de superposición de texto**
* **Uso de valores de ContextHub en superposición de texto**

>[!CAUTION]
>
>La función **Text Overlay** solo está disponible si ha instalado AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

## Información general {#overview}

La superposición de texto es una función disponible en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen.

Para aprender a crear su propio componente personalizado, consulte **Ampliación de un componente de AEM Screens**.

En esta sección solo se muestra cómo utilizar y aprovechar el componente de póster en un proyecto de AEM Screens y cómo utilizarlo como superposición de texto en uno de los canales de secuencia.

## Uso de la superposición de texto {#using-text-overlay}

En la siguiente sección se describe el uso de la superposición de texto en un proyecto de AEM Screens.

**Requisitos previos**

Antes de empezar a implementar esta funcionalidad, asegúrese de que ha configurado un proyecto como requisito previo para comenzar a implementar la superposición de texto. Por ejemplo,

* Crear un proyecto de AEM Screens (en este ejemplo, **TextOverlayDemo**)

* Cree un canal de secuencia denominado como **TextSample** en la carpeta **Channels**

* Añadir contenido a su canal **TextSample**

La siguiente imagen muestra el proyecto **TextOverlayDemo** con el canal **TextSample** en la carpeta **Channels**.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Siga los pasos a continuación para utilizar la superposición de texto en un canal de AEM Screens:

1. Vaya a **TextOverlayDemo** —> **Channels** —> **TextSample** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleccione la imagen y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleccione la opción **Text Overlay** en la barra de navegación del cuadro de diálogo, como se muestra en la figura siguiente.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Explicación de las propiedades de superposición de texto {#understanding-text-overlay-properties}

Con las propiedades Superposición de texto , puede añadir texto a cualquiera de los componentes del proyecto de Screens. En la siguiente sección se proporciona una descripción general de las propiedades disponibles en Superposición de texto:

![texto](assets/text.gif)

Puede agregar texto al cuadro de texto y agregar énfasis tipográfico, como negrita, cursiva, subrayado, etc.

**Color** VariantEsta opción permite que el texto sea Oscuro (texto en color negro) o Claro (texto en color blanco).

**Tamaño y** posiciónEsta opción permite al usuario alinear el texto horizontal o verticalmente o, además, utilizar herramientas específicas para la alineación del texto.

>[!NOTE]
>
>Para utilizar correctamente herramientas específicas, asegúrese de identificar la posición correcta en píxeles utilizando (px) como sufijo, por ejemplo 200px. El resultado de esta expresión será de 200 píxeles desde el punto de inicio.

## Uso de valores de ContextHub en superposición de texto {#using-text-overlay-context-hub}

En la siguiente sección se describe el uso de los valores de un almacén de datos, por ejemplo, hojas de google en el componente de superposición de texto.

**Requisitos previos**

Debe configurar las configuraciones de ContextHub para el proyecto de AEM Screens.

Para aprender a configurar y administrar los cambios en los recursos impulsados por datos mediante un almacén de datos, consulte [Configuración de ContextHub en AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Una vez que haya configurado las configuraciones necesarias para su proyecto, siga los pasos a continuación para utilizar los valores de las hojas de google:

1. Vaya a **TextOverlayDemo** —> **Channels** —> **TextSample** y haga clic en **Propiedades** en la barra de acciones.

1. Seleccione la pestaña **Personalization** para configurar las configuraciones de ContextHub.

   1. Seleccione **Ruta de ContextHub** como **libs** > **configuración** > **configuración de nube** > **configuración predeterminada** > **Configuraciones de ContextHub** y haga clic en &lt;a12/ Seleccione **.**

   1. Seleccione **Ruta de segmentos** como **conf** > **pantallas** > **configuración** > **wcm** > **segmentos** y haga clic en **Seleccionar**>.

   1. Haga clic en **Guardar y cerrar**.

      >[!NOTE]
      >
      >Utilice ContextHub y la ruta Segments, donde inicialmente guardó las configuraciones y segmentos de Context Hub.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Vaya a **TextOverlayDemo** —> **Channels** —> **TextSample** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Agregue un componente de superposición de imagen y texto a la imagen como se describe en la sección [Uso de superposición de texto](/help/user-guide/text-overlay.md#using-text-overlay) de esta página.

1. Haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo **Imagen**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Vaya a la pestaña **ContextHub** en el cuadro de diálogo **Image**. Haga clic en **Agregar**.

   >[!NOTE]
   >Si no ha configurado las configuraciones de ContextHub, esta opción se deshabilitará para su proyecto.

1. Introduzca **Value** en el campo **Placeholder**, seleccione la fila que desea que obtenga el valor de la hoja de google en **Variable de ContextHub** (en este caso, el valor se recupera de la fila 2 y la columna 1 de las hojas de google) e introduzca **Valor predeterminado** como **20**, como se muestra en la figura siguiente. Una vez que haya terminado, haga clic en la marca de verificación.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Para su referencia, la siguiente imagen muestra el valor que se recupera de las hojas de google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Vuelva a la ficha **Superposición de texto** del cuadro de diálogo Imagen y añada el texto *Temperatura actual {Value}*, como se muestra en la figura siguiente.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Haga clic en **Preview** para ver el resultado deseado.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
