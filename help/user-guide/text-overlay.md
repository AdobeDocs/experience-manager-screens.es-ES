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
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Superposición de texto {#text-overlay}

Esta sección abarca los siguientes temas:

* **Información general**
* **Uso de la superposición de texto**
* **Requisitos previos**
* **Explicación de las propiedades de superposición de texto**

>[!CAUTION]
>
>La función **Texto superpuesto** solo está disponible si ha instalado AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

## Información general {#overview}

La superposición de texto es una función disponible en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen.

Para obtener información sobre cómo crear su propio componente personalizado, consulte **Ampliación de un componente** de pantallas de AEM.

En esta sección solo se muestra cómo utilizar y aprovechar el componente de póster en un proyecto de AEM Screens y utilizarlo como superposición de texto en uno de los canales de secuencias.

## Uso de la superposición de texto {#using-text-overlay}

En la sección siguiente se describe el uso de la superposición de texto en un proyecto de AEM Screens.

### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de haber configurado un proyecto como requisito previo para empezar a implementar la superposición de texto. Por ejemplo,

* Creación de un proyecto de AEM Screens (en este ejemplo, **TextOverlayDemo**)

* Creación de un canal como **TextSample** en la carpeta **Canales**

* Agregar contenido al canal **TextSample**

La siguiente imagen muestra el proyecto **TextOverlayDemo** con el canal **TextSample** en la carpeta **Channels** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. Vaya a **TextOverlayDemo** —&gt; **Canales** —&gt; **TextSample** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleccione la imagen y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleccione la opción **Superposición** de texto en la barra de navegación del cuadro de diálogo, como se muestra en la figura siguiente.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Explicación de las propiedades de superposición de texto {#understanding-text-overlay-properties}

Mediante las propiedades de superposición de texto, puede añadir texto a cualquiera de los componentes del proyecto Pantallas. La sección siguiente proporciona información general sobre las propiedades disponibles en la superposición de texto:

![texto](assets/text.gif)

Puede agregar texto al cuadro de texto y agregar énfasis tipográfico, como negrita, cursiva, subrayado, etc.

**Variante** de color Esta opción permite que el texto sea Oscuro (texto en color negro) o Claro (texto en color blanco).

**Cambio de tamaño y posición** Esta opción permite al usuario alinear el texto horizontal o verticalmente o, además, utilizar herramientas específicas para la alineación del texto.

>[!NOTE]
>
>Para utilizar correctamente las herramientas específicas, asegúrese de identificar la posición correcta en píxeles utilizando (px) como sufijo, por ejemplo 200 px. El resultado de esta expresión será de 200 píxeles desde el punto inicial.

