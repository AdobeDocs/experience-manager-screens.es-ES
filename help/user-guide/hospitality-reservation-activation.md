---
title: Activación de reservación de hospitalidad
seo-title: Activación de reservación de hospitalidad
description: El siguiente caso de uso muestra el uso de la activación de reservación hospitalaria en base a los valores completados en las hojas de Google.
seo-description: El siguiente caso de uso muestra el uso de la activación de reservación hospitalaria en base a los valores completados en las hojas de Google.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# Activación de reservación de hospitalidad {#hospitality-reservation-activation}

El siguiente caso de uso muestra el uso de la activación de reservación hospitalaria en base a los valores completados en las hojas de Google.

## Descripción {#description}

Para este caso de uso, la hoja de Google se rellena con el porcentaje de reserva en dos restaurantes **Restaurant1** y **Restaurant2**. Se aplica una fórmula basada en los valores de Restaurant1 y Restaurant2 y según la fórmula, el valor 1 o 2 se asigna a la columna **AdTarget**.

Si el valor de **Restaurant1** > **Restaurant2**, a **AdTarget** se le asigna el valor **1** de lo contrario **AdTarget** se le asigna el valor **2**. El valor 1 genera la opción *Alimentos de carne* y el valor 2 muestra la opción *comida tailandesa* en la pantalla de visualización.

## Precondiciones {#preconditions}

Antes de implementar la activación de inicios, debe aprender a configurar ***Almacén de datos***, ***Segmentación de Audiencias*** y ***Habilitar el objetivo para Canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de la activación de reservación de hospitalidad para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google y agregar la fórmula.**

   Por ejemplo, aplique la fórmula a la tercera columna **AdTarget**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuración de segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación por Audiencia*** en **[Configuración de ContextHub en la página AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione las **Hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** como **igual** en el menú desplegable

   1. Escriba el **valor** como **1**

   1. Del mismo modo, seleccione las **Hojas A1 2** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable en **Nombre de propiedad**

   1. Seleccione **Operador** como **2**

1. Navegue y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenRestaurant**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las Audiencias deben estar preconfiguradas como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** mediante la ficha canal **Propiedades** —> **Personalización**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccione **Objetivo** en el editor y seleccione **Marca** y la **Actividad** en el menú desplegable y haga clic en **Objetivo de Inicio**.
1. **Comprobación de la Previsualización**

   1. Haga clic en **Previsualización.** Además, abra las hojas de Google y actualice su valor.
   1. Actualice el valor en las columnas **Restaurant1** y **Restaurant2**. Si **Restaurant1** > **Restaurant2,** debería poder vista una imagen de *comida de carne* de lo contrario, *comida tailandesa* se muestra en la pantalla una imagen de la comida.

   ![result5](assets/result5.gif)

