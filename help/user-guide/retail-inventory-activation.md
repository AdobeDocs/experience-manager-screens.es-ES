---
title: Activación segmentada de inventario comercial
seo-title: Retail Inventory Targeted Activation
description: Este caso de uso muestra el inventario minorista de existencias de tres sudaderas de colores diferentes. Según el número de sudaderas disponibles en stock que se registren en las Hojas de cálculo de Google, la imagen (sudadera roja, verde o azul) con el número más alto se muestra en la pantalla.
seo-description: This Use Case showcases the retail inventory stock for three different colored sweatshirts. Depending on the number of sweatshirts available in stock that is recorded in Google Sheets, the image (red, green, or blue sweatshirt) with highest number is displayed on the screen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# Activación segmentada de inventario comercial {#retail-inventory-targeted-activation}

En el siguiente caso de uso se muestran tres imágenes diferentes basadas en los valores de la hoja de cálculo de Google.

## Descripción {#description}

Este caso de uso muestra el inventario minorista de existencias de tres sudaderas de colores diferentes. Según el número de sudaderas disponibles en stock que se registren en las Hojas de cálculo de Google, la imagen (sudadera roja, verde o azul) con el número más alto se muestra en la pantalla.

Para este caso de uso, el suéter rojo, verde o azul se mostrará en la pantalla en función del valor más alto del número de suéters disponibles.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de segmentación de inventario comercial, debe aprender a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar la segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso Activación de inventario comercial:

1. **Rellenar las hojas de Google**

   1. Navegue hasta la hoja de Google de ContextHubDemo.
   1. Agregue tres columnas (rojo, verde y azul) con los valores correspondientes para tres sudaderas diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuración de las audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ). ***Paso 2: Configuración de la segmentación de audiencia*** in **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Añadir tres segmentos nuevos **For_Red**, **For_Green**, y **For_Blue**.

   1. Seleccionar **For_Red** y haga clic en **Editar** de la barra de acciones.

   1. Arrastre y suelte el **Comparación : propiedad/propiedad** Vaya al editor y haga clic en el icono configurar para editar las propiedades.
   1. Seleccionar **googlesheets/value/1/2** de la lista desplegable en **Nombre de la primera propiedad**

   1. Seleccione el **Operador** as **greater-than** en el menú desplegable

   1. Seleccionar **Tipo de datos** as **número**

   1. Seleccionar **googlesheets/value/1/1** de la lista desplegable en **Nombre de la segunda propiedad**.

   1. Arrastrar y soltar **otra comparación : propiedad/propiedad** Vaya al editor y haga clic en el icono configurar para editar las propiedades.
   1. Seleccionar **googlesheets/value/1/2** de la lista desplegable en **Nombre de la primera propiedad**.

   1. Seleccione el **Operador** as **greater-than** en el menú desplegable

   1. Seleccionar **Tipo de datos** as **número**

   1. Seleccionar **googlesheets/value/1/0** de la lista desplegable en **Nombre de la segunda propiedad**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación a **For_Blue** segmentar como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación a** For_Green **segment, como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Observará que para los segmentos de **For_Green** y **For_Green** Sin embargo, los datos no se pueden resolver en el editor, ya que solo la primera comparación es válida de momento, según los valores de la hoja de cálculo de Google.

1. Desplácese y seleccione su **DataDrivenRetail** (un canal secuencial) y haga clic en **Editar** de la barra de acciones.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** uso del canal **Propiedades** > **Personalización** pestaña.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Debe seleccionar las dos opciones **Marca** y el **Área** para que las actividades se incluyan correctamente en la lista al iniciar el proceso de Orientación.

1. **Adición de una imagen predeterminada**

   1. Añada una imagen predeterminada al canal y haga clic en **Segmentación**.
   1. Seleccionar **Marca** y el **Actividad** en el menú desplegable y haga clic en **Iniciar segmentación**.

   1. Clic **Iniciar segmentación**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Antes de empezar a segmentar, debe añadir los segmentos (**For_Green**, **For_Red**, y **For_Blue**) haciendo clic en **+ Agregar segmentación de experiencias** desde el carril lateral como se muestra en la figura siguiente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Agregue las imágenes a los tres escenarios diferentes como se muestra a continuación.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Comprobación de la previsualización**

   1. Clic **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor de las tres columnas diferentes y verá que la imagen para mostrar se actualiza según el valor más alto del inventario.

   ![retail_result](assets/retail_result.gif)
