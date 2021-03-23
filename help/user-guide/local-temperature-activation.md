---
title: Activación de la temperatura del centro de viajes
seo-title: Activación de la temperatura del centro de viajes
description: El siguiente caso de uso demuestra el uso de la activación de la temperatura local del centro de viajes en función de los valores rellenados en Google Sheets.
seo-description: El siguiente caso de uso demuestra el uso de la activación de la temperatura local del centro de viajes en función de los valores rellenados en Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Creación en Screens
role: Administrador, Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---


# Activación de temperatura del centro de viajes {#travel-center-temperature-activation}

El siguiente caso de uso demuestra el uso de la activación de la temperatura local del centro de viajes en función de los valores rellenados en Google Sheets.

## Descripción {#description}

Para este caso de uso, si su Google Sheets tiene un valor inferior a 50, se mostrará una imagen con bebidas calientes y si el valor es bueno o igual a 50, se mostrará la imagen con bebidas frías. En el caso de algún otro valor o ningún, el reproductor mostrará una imagen predeterminada.

## Precondiciones {#preconditions}

Antes de comenzar a implementar la activación de la temperatura local del centro de viajes, debe aprender a configurar ***Data Store***, ***Segmentación de audiencias*** y ***Habilitar segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso Activación de temperatura local del centro de viajes:

1. **Rellenar las hojas de Google**

   1. Vaya a la hoja de Google de ContextHubDemo.
   1. Agregue una columna con **Heading1** con el valor correspondiente de temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuración de los segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** en **[Configuración de ContextHub en la página AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione **Sheets A1 1** y haga clic en **Edit**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** de la lista desplegable en **Property name**

   1. Seleccione **Operator** como **bueno que igual o igual** en el menú desplegable

   1. Introduzca el **Value** como **50**

   1. Del mismo modo, seleccione **Sheets A1 2** y haga clic en **Edit**.

   1. Seleccione **Comparison Property - Value** y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** de la lista desplegable en **Property name**

   1. Seleccione **Operator** como **less-than** en el menú desplegable

   1. Introduzca el **Value** como **50**

1. Desplácese y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenWeather**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las audiencias deben estar preconfiguradas tal y como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** utilizando la pestaña **Propiedades** —> **Personalización**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccione **Segmentación** en el editor y seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar orientación**.

   ![new_activity3](assets/new_activity3.gif)

1. **Comprobación de la vista previa**

   1. Haga clic en **Preview.** Además, abra la hoja de Google y actualice su valor.
   1. Si cambia el valor a menos de 50, debería poder ver la imagen de las bebidas del verano. Si el valor de la hoja de Google es 50 o bueno, debería poder ver una imagen de bebida caliente.

   ![result3](assets/result3.gif)

