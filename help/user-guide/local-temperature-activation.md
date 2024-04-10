---
title: Activación de temperatura del centro de viajes
seo-title: Travel Center Temperature Activation
description: El siguiente caso de uso muestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en Hojas de cálculo de Google.
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Activación de temperatura del centro de viajes {#travel-center-temperature-activation}

El siguiente caso de uso muestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en Hojas de cálculo de Google.

## Descripción {#description}

Para este caso de uso, si las hojas de Google tienen un valor menor que 50, se mostrará una imagen con bebidas calientes y si el valor es mayor o igual que 50, se mostrará la imagen con bebidas frías. En caso de que haya otro valor o ningún valor, el reproductor mostrará una imagen predeterminada.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de temperatura local del centro de viajes, debe aprender a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar la segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso Activación de temperatura local del centro de viajes:

1. **Rellenar las hojas de Google**

   1. Navegue hasta la hoja de Google de ContextHubDemo.
   1. Añadir una columna con **Encabezado1** con el valor correspondiente a la temperatura.

   ![screen_shot_2019-05-08a112911m](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuración de los segmentos en Audiences según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** in **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione el **Hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccionar **googlesheets/value/1/0** de la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** as **mayor o igual que** en el menú desplegable

   1. Introduzca el **Valor** as **50**

   1. Del mismo modo, seleccione la **Hojas A1 2** y haga clic en **Editar**.

   1. Seleccione el **Propiedad de comparación: valor** y haga clic en el icono configurar para editar las propiedades.
   1. Seleccionar **googlesheets/value/1/0** de la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** as **less-than** en el menú desplegable

   1. Introduzca el **Valor** as **50**

1. Desplácese, seleccione el canal () y haga clic en **Editar** de la barra de acciones. En el ejemplo siguiente, **DataDrivenWeather**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las audiencias deben preconfigurarse como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08a113022m](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** uso del canal **Propiedades** > **Personalización** pestaña.

   ![screen_shot_2019-05-08a114106m](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccionar **Segmentación** en el editor, seleccione **Marca** y el **Actividad** en el menú desplegable y haga clic en **Iniciar segmentación**.

   ![new_activity3](assets/new_activity3.gif)

1. **Comprobación de la previsualización**

   1. Clic **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Si cambia el valor a menos de 50, debería poder ver una imagen de las bebidas de verano. Si el valor de la hoja de Google es 50 o mayor de lo que debería ser, se puede ver una imagen de una bebida caliente.

   ![result3](assets/result3.gif)
