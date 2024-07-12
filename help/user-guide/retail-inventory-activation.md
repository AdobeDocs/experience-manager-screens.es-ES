---
title: Activación segmentada de inventario comercial
description: Obtenga información acerca de este caso de uso de AEM Screens que muestra el inventario de existencias minoristas de tres sudaderas de colores diferentes.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Activación segmentada de inventario comercial {#retail-inventory-targeted-activation}

En el siguiente caso de uso se muestran tres imágenes diferentes basadas en los valores de la hoja de cálculo de Google.

## Descripción {#description}

Este caso de uso muestra el inventario minorista de existencias de tres sudaderas de colores diferentes. En función del número de sudaderas disponibles en stock que se registren en las Hojas de cálculo de Google, se mostrará la imagen (sudadera roja, verde o azul) con el número más alto.

El suéter rojo, verde o azul se muestra en función del valor más alto del número de suéters disponibles.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de segmentación de inventario comercial, aprende a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso Activación de inventario comercial:

1. **Rellenando las hojas de Google**

   1. Navegue hasta la hoja de Google de ContextHubDemo.
   1. Agregue tres columnas (rojo, verde y azul) con los valores correspondientes para tres sudaderas diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuración de las audiencias según los requisitos**

   1. Vaya a los segmentos de su audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** en la página **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Agregue tres nuevos segmentos **For_Red**, **For_Green** y **For_Blue**.

   1. Haga clic en **For_Red** y luego en **Editar** en la barra de acciones.

   1. Arrastre y suelte la **Comparación : propiedad - propiedad** en el editor.
   1. Haga clic en el icono **Configuración**.
   1. Haga clic en **googlesheets/value/1/2** en la lista desplegable de **Nombre de la primera propiedad**.
   1. Haga clic en **Operador** y seleccione **mayor que** en el menú desplegable.
   1. Haga clic en **Tipo de datos** y como **número**.
   1. Haga clic en **googlesheets/value/1/1** en la lista desplegable de **Second Property name**.
   1. Arrastre y suelte **otra comparación : propiedad - propiedad** en el editor y haga clic en el icono **Configuración**.
   1. Haga clic en **googlesheets/value/1/2** en la lista desplegable de **Nombre de la primera propiedad**.
   1. Haga clic en **Operador** y seleccione **mayor que** en el menú desplegable.
   1. Haga clic en **Tipo de datos** y como **número**.
   1. Haga clic en **googlesheets/value/1/0** en la lista desplegable de **Second Property name**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Del mismo modo, edite y agregue reglas de propiedades de comparación al segmento **For_Blue**, tal como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Del mismo modo, edite y agregue reglas de propiedades de comparación al segmento **For_Green**, tal como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Tenga en cuenta que para los segmentos **For_Green** y **For_Green**, los datos no se pueden resolver en el editor ya que solo la primera comparación es válida a partir de ahora según los valores de la hoja de cálculo de Google.

1. Navegue y haga clic en su canal **DataDrivenRetail** (un canal de secuencia).
1. Haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Ya debería haber configurado **ContextHub** **Configuraciones** con la pestaña **Propiedades** > **Personalization** del canal.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Haga clic en **Marca** y en **Área** para que las actividades se incluyan en la lista correcta al iniciar el proceso de segmentación.

1. **Agregando una imagen predeterminada**

   1. Agregue una imagen predeterminada a su canal y haga clic en **Segmentación**.
   1. Haga clic en **Marca** y en la **Actividad** del menú desplegable y luego haga clic en **Iniciar segmentación**.
   1. Haga clic en **Iniciar segmentación**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Antes de empezar a segmentar, agrega los segmentos (**For_Green**, **For_Red** y **For_Blue**) seleccionando **+ Agregar segmentación de experiencia** del carril lateral como se muestra en la figura siguiente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Agregue las imágenes a los tres escenarios diferentes como se muestra a continuación.

   ![direccionamiento_comercial](assets/retail_targeting.gif)

1. **Comprobando la vista previa**

   1. Haga clic en **Vista previa.** Además, abra la hoja Google Sheet y actualice su valor.
   1. Cambie el valor de las tres columnas diferentes. Observe que la imagen para mostrar se actualiza según el valor más alto del inventario.

   ![retail_result](assets/retail_result.gif)
