---
title: Superposición de texto
seo-title: Text Overlay
description: La superposición de texto es una función disponible en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen. Siga esta página para obtener más información.
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# Superposición de texto {#text-overlay}

Esta sección cubre los siguientes temas:

* **Información general**
* **Uso de la superposición de texto**
* **Explicación de las propiedades de superposición de texto**
* **Uso de valores de ContextHub en superposición de texto**

>[!CAUTION]
>
>La variable **Superposición de texto** esta función solo está disponible si ha instalado AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

## Información general {#overview}

La superposición de texto es una función disponible en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen.

Para aprender a crear su propio componente personalizado, consulte **Ampliación de un componente de AEM Screens**.

En esta sección solo se muestra cómo utilizar y aplicar el componente de póster en un proyecto de AEM Screens y cómo utilizarlo como superposición de texto en uno de los canales de secuencia.

## Uso de la superposición de texto {#using-text-overlay}

En la siguiente sección se describe el uso de la superposición de texto en un proyecto de AEM Screens.

**Requisitos previos**

Antes de empezar a implementar esta funcionalidad, asegúrese de que ha configurado un proyecto como requisito previo para comenzar a implementar la superposición de texto. Por ejemplo,

* Crear un proyecto de AEM Screens (en este ejemplo, **TextOverlayDemo**)

* Cree un canal de secuencia denominado como **TextSample** under **Canales** carpeta

* Añada contenido a su **TextSample** Canal

La siguiente imagen muestra la variable **TextOverlayDemo** proyecto con **TextSample** canal en **Canales** carpeta.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Siga los pasos a continuación para utilizar la superposición de texto en un canal de AEM Screens:

1. Vaya a **TextOverlayDemo** —> **Canales** —> **TextSample** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleccione la imagen y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleccione el **Superposición de texto** de la barra de navegación del cuadro de diálogo, como se muestra en la figura siguiente.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Explicación de las propiedades de superposición de texto {#understanding-text-overlay-properties}

Con las propiedades Superposición de texto , puede añadir texto a cualquiera de los componentes del proyecto de Screens. En la siguiente sección se proporciona una descripción general de las propiedades disponibles en Superposición de texto:

![text](assets/text.gif)

Puede agregar texto al cuadro de texto y agregar énfasis tipográfico, como negrita, cursiva y subrayado.

**Variante de color** Esta opción permite que el texto sea Oscuro (texto en color negro) o Claro (texto en color blanco).

**Tamaño y colocación** Esta opción permite al usuario alinear el texto horizontal o verticalmente, o también utilizar herramientas específicas para la alineación del texto.

>[!NOTE]
>
>Para utilizar correctamente herramientas específicas, asegúrese de identificar la posición correcta en píxeles utilizando (px) como sufijo, por ejemplo 200 px. El resultado de esta expresión es de 200 píxeles desde el punto inicial.

## Uso de valores de ContextHub en superposición de texto {#using-text-overlay-context-hub}

En la siguiente sección se describe el uso de los valores de un almacén de datos, por ejemplo, hojas de google en el componente de superposición de texto.

**Requisitos previos**

Configure las configuraciones de ContextHub para su proyecto de AEM Screens.

Para obtener información sobre cómo configurar y administrar los cambios en los recursos impulsados por datos mediante un almacén de datos, consulte [Configuración de ContextHub en AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Una vez que haya configurado las configuraciones necesarias para su proyecto, siga los pasos a continuación para utilizar los valores de las hojas de google:

1. Vaya a **TextOverlayDemo** —> **Canales** —> **TextSample** y haga clic en **Propiedades** de la barra de acciones.

1. Seleccione el **Personalización** para configurar las configuraciones de ContextHub.

   1. Seleccione el **Ruta de ContextHub** como **libs** > **configuración** > **cloudsettings** > **default** > **Configuraciones de ContextHub** y haga clic en **Select**.

   1. Seleccione el **Ruta de segmentos** como **conf** > **pantallas** > **configuración** > **wcm** > **segmentos** y haga clic en **Select**.

   1. Haga clic en **Guardar y cerrar**.

      >[!NOTE]
      >
      >Utilice ContextHub y la ruta Segments, donde inicialmente guardó las configuraciones y segmentos de Context Hub.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Vaya a **TextOverlayDemo** —> **Canales** —> **TextSample** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Agregue un componente de superposición de imagen y texto a la imagen como se describe en [Uso de la superposición de texto](/help/user-guide/text-overlay.md#using-text-overlay) de esta página.

1. Haga clic en **Configurar** (icono de llave inglesa) para abrir el **Imagen** para abrir el Navegador.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Vaya a la **ContextHub** en la ficha **Imagen** para abrir el Navegador. Haga clic en **Agregar**.

   >[!NOTE]
   >Si no ha configurado las configuraciones de ContextHub, esta opción está deshabilitada para el proyecto.

1. Entrar **Valor** en el **Marcador de posición** campo . Seleccione la fila en la que desea obtener el valor de la hoja de Google **Variable ContextHub**. En este caso, el valor se recupera de las filas 2 y 1 de las hojas de Google. A continuación, introduzca la variable **Valor predeterminado** como **20**, como se muestra en la figura siguiente. Cuando haya terminado, haga clic en la marca de verificación.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Para su referencia, la siguiente imagen muestra el valor que se recupera de las hojas de google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Vuelva a la página **Superposición de texto** en el cuadro de diálogo Imagen y añada el texto *Temperatura actual {Valor}*, como se muestra en la figura siguiente.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Haga clic en **Vista previa** para ver el resultado deseado.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
