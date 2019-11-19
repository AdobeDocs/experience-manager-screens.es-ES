---
title: Activación de la temperatura del centro de viajes
seo-title: Activación de la temperatura del centro de viajes
description: El siguiente caso de uso muestra el uso de la activación de la temperatura local del centro de viajes en función de los valores rellenados en las hojas de Google.
seo-description: El siguiente caso de uso muestra el uso de la activación de la temperatura local del centro de viajes en función de los valores rellenados en las hojas de Google.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Activación de la temperatura del centro de viajes {#travel-center-temperature-activation}

El siguiente caso de uso muestra el uso de la activación de la temperatura local del centro de viajes en función de los valores rellenados en las hojas de Google.

## Descripción {#description}

Para este caso de uso, si las hojas de Google tienen un valor inferior a 50, se mostrará una imagen con bebidas calientes y si el valor es mayor o igual a 50, se mostrará la imagen con bebidas frías. En el caso de algún otro valor o ninguno, el reproductor mostrará una imagen predeterminada.

## Condiciones previas {#preconditions}

Antes de empezar a implementar la activación de la temperatura local del centro de viajes, debe aprender a configurar el almacén ***de*** datos, la segmentación ***de*** audiencias y ***habilitar la segmentación de canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de activación de temperatura local del centro de viajes:

1. **Rellenar las hojas de Google**

   1. Vaya a la hoja de Google de ContextHubDemo.
   1. Agregue una columna con **Encabezado1** con el valor correspondiente para la temperatura.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuración de segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte el ***paso 2: Configuración de la segmentación*** de audiencias en la página **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione las **hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **operador** como **mayor que o igual **en el menú desplegable

   1. Introduzca el **valor** como **50**

   1. Del mismo modo, seleccione las hojas** A1 2 ** y haga clic en **Editar**.

   1. Seleccione Propiedad de **comparación - Valor** y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **Operador** como **menor que **en el menú desplegable

   1. Introduzca el **valor** como **50**

1. Navegue y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenWeather**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y Audiencias debe preconfigurarse como se describe en [Configuración de ContextHub en pantallas](configuring-context-hub.md)AEM.

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Debería haber configurado las **** configuraciones **de ContextHub** mediante la ficha **Propiedades** del canal —&gt; **Personalización** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccione **Objetivo** en el editor, seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.

   ![new_activity3](assets/new_activity3.gif)

1. **Comprobación de la vista previa**

   1. Haga clic en **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor a menos de 50, debería poder ver una imagen de las bebidas de verano. Si el valor de la hoja de Google es 50 o mayor que el que debería poder ver la imagen de una bebida caliente.
   ![result3](assets/result3.gif)

