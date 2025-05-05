---
title: Superposición de texto
description: Obtenga información sobre la superposición de texto en AEM Screens que le permite crear una experiencia atractiva en un canal de secuencia proporcionando un título o una descripción superpuestos sobre una imagen.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 1%

---

# Superposición de texto {#text-overlay}

Esta sección trata los siguientes temas:

* **Información general**
* **Usando superposición de texto**
* **Explicación de las propiedades de superposición de texto**
* **Uso de valores de ContextHub en superposición de texto**

>[!CAUTION]
>
>AEM AEM La característica **Superposición de texto** solo está disponible si ha instalado el paquete de características 5 o 3 de la versión 6.3 de la versión 6.3 de la versión 6.3 de la versión de.

## Información general {#overview}

La superposición de texto es una función disponible en AEM Screens. Permite crear una experiencia atractiva en un canal de secuencias al proporcionar un título o una descripción superpuestos sobre una imagen.

Para aprender a crear su propio componente personalizado, vea **Ampliar un componente de AEM Screens**.

Esta sección solo muestra cómo utilizar y aplicar el componente de póster en un proyecto de AEM Screens. También muestra cómo se utiliza como superposición de texto en uno de los canales de la secuencia.

## Uso de superposición de texto {#using-text-overlay}

En la siguiente sección se describe el uso de la superposición de texto en un proyecto de AEM Screens.

**Requisitos previos**

Antes de implementar esta funcionalidad, asegúrese de haber configurado un proyecto como requisito previo para comenzar a implementar la superposición de texto. Por ejemplo,

* Cree un proyecto de AEM Screens (en este ejemplo, **TextOverlayDemo**)

* Cree un canal de secuencia con el título **TextSample** en la carpeta **Canales**

* Agregar contenido a su canal **TextSample**

La siguiente imagen muestra el proyecto **TextOverlayDemo** con el canal **TextSample** en la carpeta **Channels**.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Siga los pasos a continuación para utilizar la superposición de texto en un canal de AEM Screens:

1. Vaya a **TextOverlayDemo** > **Canales** > **TextSample** y haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Haga clic en la imagen y luego en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Haga clic en la opción **Superposición de texto** de la barra de navegación del cuadro de diálogo, como se muestra en la figura siguiente.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Explicación de las propiedades de superposición de texto {#understanding-text-overlay-properties}

Con las propiedades de Superposición de texto, puede agregar texto a cualquiera de los componentes del proyecto de Screens. En la siguiente sección se ofrece una descripción general de las propiedades disponibles en Superposición de texto:

![texto](assets/text.gif)

Puede agregar un texto al cuadro de texto y agregar énfasis tipográfico como negrita, cursiva y subrayado.

**Variante de color** Esta opción permite que el texto sea Oscuro (texto en color negro) o Claro (texto en color blanco).

**Cambiar el tamaño y la posición** Esta opción permite al usuario alinear el texto horizontal o verticalmente, o usar herramientas específicas para alinear el texto.

>[!NOTE]
>
>Cuando utilice herramientas específicas, asegúrese de identificar la posición correcta en píxeles con (px) como sufijo; por ejemplo, 200 px. El resultado de esta expresión es de 200 píxeles desde el punto de inicio.

## Uso de valores de ContextHub en la superposición de texto {#using-text-overlay-context-hub}

En la siguiente sección se describe el uso de valores de un almacén de datos, por ejemplo, hojas de Google en el componente de superposición de texto.

**Requisitos previos**

Configure las opciones de ContextHub para el proyecto de AEM Screens.

Para obtener información sobre cómo configurar y administrar los cambios de recursos impulsados por datos mediante un almacén de datos, consulte [Configuración de ContextHub en AEM Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

Después de configurar las configuraciones necesarias para el proyecto, siga los pasos a continuación para utilizar los valores de las Hojas de cálculo de Google:

1. Vaya a **TextOverlayDemo** > **Canales** > **TextSample** y haga clic en **Propiedades** desde la barra de acciones.

1. Haga clic en la ficha **Personalization** para configurar las configuraciones de ContextHub.

   1. Haga clic en la ruta de acceso de **ContextHub** como **libs** > **settings** > **cloudsettings** > **default** > **Configuraciones de ContextHub** y haga clic en **Seleccionar**.

   1. Haga clic en la ruta de acceso de **segmentos** como **conf** > **screens** > **settings** > **wcm** > **segments** y haga clic en **Select**.

   1. Haga clic en **Guardar y cerrar**.

      >[!NOTE]
      >
      >Utilice ContextHub y la ruta de segmentos, donde guardó inicialmente las configuraciones y segmentos de Context Hub.

      ![imagen1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Vaya a **TextOverlayDemo** > **Canales** > **TextSample** y haga clic en **Editar** en la barra de acciones.

   ![imagen1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Agregue un componente de superposición de texto e imagen a su imagen tal como se describe en la sección [Usar superposición de texto](/help/user-guide/text-overlay.md#using-text-overlay) de esta página.

1. Haz clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo **Imagen**.

   ![imagen1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Vaya a la pestaña **ContextHub** del cuadro de diálogo **Imagen**. Haga clic en **Agregar**.

   >[!NOTE]
   >Si no ha definido la configuración de ContextHub, esta opción está desactivada para el proyecto.

1. Escriba **Value** en el campo **Placeholder**. Haga clic en la fila de la que desee obtener el valor de la hoja Google en **Variable de ContextHub**. En este caso, el valor se recupera de la fila 2 y la columna 1 de las hojas de Google. Ahora, ingrese el **Valor predeterminado** como **20**, como se muestra en la figura siguiente. Cuando haya terminado, haga clic en la marca de verificación.

   ![imagen1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Para su referencia, la siguiente imagen muestra el valor recuperado de las hojas de Google:

   ![imagen1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Vuelva a la ficha **Superposición de texto** del cuadro de diálogo Imagen y agregue el texto *Temperatura actual {Value}*, como se muestra en la figura siguiente.

   ![imagen1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Haga clic en **Vista previa**.

   ![imagen1](/help/user-guide/assets/text-overlay/text-overlay10.png)
