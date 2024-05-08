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
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Activación segmentada de inventario comercial {#retail-inventory-targeted-activation}

En el siguiente caso de uso se muestran tres imágenes diferentes basadas en los valores de la hoja de cálculo de Google.

## Descripción {#description}

Este caso de uso muestra el inventario minorista de existencias de tres sudaderas de colores diferentes. Según el número de sudaderas disponibles en stock que se registren en las Hojas de cálculo de Google, la imagen (sudadera roja, verde o azul) con el número más alto se muestra en la pantalla.

En este caso de uso, el suéter rojo, verde o azul se muestra en la pantalla en función del valor más alto de cantidad de suéters disponibles.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de segmentación de inventario comercial, aprenda a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar la segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso Activación de inventario comercial:

1. **Rellenar las hojas de Google**

   1. Navegue hasta la hoja de Google de ContextHubDemo.
   1. Agregue tres columnas (rojo, verde y azul) con los valores correspondientes para tres sudaderas diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuración de las audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** in **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Añadir tres segmentos nuevos **For_Red**, **For_Green**, y **For_Blue**.

   1. Clic **For_Red** y haga clic en **Editar** de la barra de acciones.

   1. Arrastre y suelte el **Comparación : propiedad/propiedad** al editor.
   1. Haga clic en **Configuración** icono.
   1. Clic **googlesheets/value/1/2** de la lista desplegable en **Nombre de la primera propiedad**.
   1. Haga clic en **Operador** as **greater-than** en el menú desplegable.
   1. Clic **Tipo de datos** as **número**.
   1. Clic **googlesheets/value/1/1** de la lista desplegable en **Nombre de la segunda propiedad**.
   1. Arrastrar y soltar **otra comparación : propiedad/propiedad** Vaya al editor y haga clic en **Configuración** icono.
   1. Clic **googlesheets/value/1/2** de la lista desplegable en **Nombre de la primera propiedad**.
   1. Haga clic en **Operador** as **greater-than** en el menú desplegable.
   1. Clic **Tipo de datos** as **número**.
   1. Clic **googlesheets/value/1/0** de la lista desplegable en **Nombre de la segunda propiedad**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación a **For_Blue** segmentar como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación a **For_Green** segmentar como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Tenga en cuenta que para los segmentos **For_Green** y **For_Green** Sin embargo, los datos no se pueden resolver en el editor, ya que solo la primera comparación es válida de momento, según los valores de la hoja de cálculo de Google.

1. Navegue y haga clic en **DataDrivenRetail** canal (un canal de secuencia).
1. Clic **Editar** de la barra de acciones.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** uso del canal **Propiedades** > **Personalización** pestaña.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Haga clic en ambos **Marca** y el **Área** para que las actividades se incluyan correctamente en la lista al iniciar el proceso de Orientación.

1. **Adición de una imagen predeterminada**

   1. Añada una imagen predeterminada al canal y haga clic en **Segmentación**.
   1. Clic **Marca** y el **Actividad** en el menú desplegable y haga clic en **Iniciar segmentación**.
   1. Clic **Iniciar segmentación**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Antes de empezar a segmentar, añada los segmentos (**For_Green**, **For_Red**, y **For_Blue**) seleccionando **+ Agregar segmentación de experiencias** desde el carril lateral como se muestra en la figura siguiente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Agregue las imágenes a los tres escenarios diferentes como se muestra a continuación.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Comprobación de la previsualización**

   1. Clic **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor de las tres columnas diferentes. Observe que la imagen de visualización se actualiza según el valor más alto del inventario.

   ![retail_result](assets/retail_result.gif)
