---
title: Activación de la temperatura del centro de viajes
seo-title: Activación de la temperatura del centro de viajes
description: El siguiente caso de uso muestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en las hojas de Google.
seo-description: El siguiente caso de uso muestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en las hojas de Google.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# Activación de temperatura del centro de viajes {#travel-center-temperature-activation}

El siguiente caso de uso muestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en las hojas de Google.

## Descripción {#description}

Para este caso de uso, si las hojas de Google tienen un valor inferior a 50, se mostrará una imagen con bebidas calientes y si el valor es bueno o igual a 50, se mostrará la imagen con bebidas frías. En el caso de algún otro valor o ninguno, el reproductor mostrará una imagen predeterminada.

## Precondiciones {#preconditions}

Antes de realizar el inicio de implementar la activación de temperatura local del centro de viajes, debe aprender a configurar ***Almacén de datos***, ***Segmentación de Audiencia*** y ***Habilitar objetivo para Canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de la Activación de temperatura local del centro de viajes:

1. **Rellenar las hojas de Google**

   1. Vaya a la hoja de Google de ContextHubDemo.
   1. Añada una columna con **Encabezado1** con el valor correspondiente para la temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuración de segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación por Audiencia*** en **[Configuración de ContextHub en la página AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione las **Hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** en la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** como **bueno o igual** en el menú desplegable

   1. Introduzca el **valor** como **50**

   1. Del mismo modo, seleccione las **Hojas A1 2** y haga clic en **Editar**.

   1. Seleccione la **Propiedad de comparación - Valor** y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** en la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** como **menor que** en el menú desplegable

   1. Introduzca el **valor** como **50**

1. Navegue y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenWeather**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las Audiencias deben estar preconfiguradas como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** mediante la ficha canal **Propiedades** —> **Personalización**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccione **Objetivo** en el editor y seleccione **Marca** y la **Actividad** en el menú desplegable y haga clic en **Objetivo de Inicio**.

   ![new_actividad3](assets/new_activity3.gif)

1. **Comprobación de la Previsualización**

   1. Haga clic en **Previsualización.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor a menos de 50, debería poder vista la imagen de las bebidas de verano. Si el valor de la hoja de Google es 50 o bueno, debería poder vista de una imagen de bebida caliente.

   ![result3](assets/result3.gif)

