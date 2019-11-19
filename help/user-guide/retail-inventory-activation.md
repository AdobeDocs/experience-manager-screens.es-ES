---
title: Activación de objetivo de inventario comercial
seo-title: Activación de objetivo de inventario comercial
description: Este Caso de uso muestra el stock de inventario minorista para tres jerseys de diferentes colores. En función del número de jerseys disponibles en stock que se haya grabado en Google Sheets, se mostrará en pantalla la imagen (camisa roja, verde o azul) con el número más alto.
seo-description: Este Caso de uso muestra el stock de inventario minorista para tres jerseys de diferentes colores. En función del número de jerseys disponibles en stock que se haya grabado en Google Sheets, se mostrará en pantalla la imagen (camisa roja, verde o azul) con el número más alto.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Activación de objetivo de inventario comercial {#retail-inventory-targeted-activation}

El siguiente caso de uso muestra tres imágenes diferentes basadas en los valores de la hoja de Google.

## Descripción {#description}

Este Caso de uso muestra el stock de inventario minorista para tres jerseys de diferentes colores. En función del número de jerseys disponibles en stock que se haya grabado en Google Sheets, se mostrará en pantalla la imagen (camisa roja, verde o azul) con el número más alto.

Para este caso de uso, el suéter rojo, verde o azul se mostrará en la pantalla en función del valor más alto del número de suéteres disponibles.

## Condiciones previas {#preconditions}

Antes de empezar a implementar la activación de segmentación de inventario minorista, debe aprender a configurar el almacén ***de*** datos, la segmentación ***de*** audiencias y ***habilitar la segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de activación de inventario comercial:

1. **Rellenar las hojas de Google**

   1. Vaya a la hoja de Google de ContextHubDemo.
   1. Agregue tres columnas (Rojo, Verde y Azul) con los valores correspondientes para tres camisas azules diferentes.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuración de las audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte el ***paso 2: Configuración de la segmentación*** de audiencias en la página **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Agregue tres nuevos segmentos **For_Red**, **For_Green** y **For_Blue**.

   1. Seleccione **For_Red** y haga clic en **Editar** en la barra de acciones.

   1. Arrastre y suelte la **comparación: Propiedad: propiedad** del editor y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable en Nombre de la **propiedad**

   1. Seleccione el **Operador** como **mayor que **en el menú desplegable

   1. Seleccione Tipo **** de datos como **número**

   1. Seleccione **googlesheets/value/1/1** en la lista desplegable del nombre de la **segunda propiedad**

   1. Arrastre y suelte **otra comparación: Propiedad: propiedad **al editor y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable en Nombre de la **propiedad**

   1. Seleccione el **Operador** como **mayor que **en el menú desplegable

   1. Seleccionar tipo **de datos** como **número**

   1. Seleccione **googlesheets/value/1/0** en la lista desplegable del nombre de la **segunda propiedad**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación al segmento **For_Blue** como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación al segmento** For_Green **como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Observará que para los segmentos **For_Green** y **For_Green**, los datos no se pueden resolver en el editor, ya que sólo la primera comparación es válida a partir de ahora según los valores de la hoja de Google.

1. Navegue y seleccione el canal **DataDrivenRetail** (un canal secuencial) y haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Debería haber configurado las **** configuraciones **de ContextHub** mediante la ficha **Propiedades** del canal —&gt; **Personalización** .

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Debe seleccionar tanto la **marca** como el **área** para que las actividades se muestren correctamente al iniciar el proceso de objetivo.

1. **Adición de una imagen predeterminada**

   1. Agregue una imagen predeterminada al canal y haga clic en **Objetivo**.
   1. Seleccione **Marca** y la **actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.

   1. Haga clic en **Iniciar Targeting**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Antes de empezar a establecer el objetivo, debe agregar los segmentos (**For_Green**, **For_Red** y **For_Blue**) haciendo clic en **+ Agregar segmentación** de experiencias desde el carril lateral, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Agregue las imágenes a los tres escenarios diferentes como se muestra a continuación.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Comprobación de la vista previa**

   1. Haga clic en **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor de las tres columnas diferentes y observará las actualizaciones de la imagen de visualización según el valor más alto del inventario.
   ![retail_result](assets/retail_result.gif)

