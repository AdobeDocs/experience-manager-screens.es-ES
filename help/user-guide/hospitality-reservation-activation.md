---
title: Activación de reserva de hospitalidad
seo-title: Activación de reserva de hospitalidad
description: El siguiente caso de uso demuestra el uso de la activación de reservas hospitalarias en función de los valores rellenados en Google Sheets.
seo-description: El siguiente caso de uso demuestra el uso de la activación de reservas hospitalarias en función de los valores rellenados en Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Creación en Screens
role: Administrador, Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Activación de reserva de hospitalidad {#hospitality-reservation-activation}

El siguiente caso de uso demuestra el uso de la activación de reservas hospitalarias en función de los valores rellenados en Google Sheets.

## Descripción {#description}

Para este caso de uso, la hoja de Google se rellena con un porcentaje de reserva en dos restaurantes **Restaurant1** y **Restaurant2**. Se aplica una fórmula basada en los valores de Restaurant1 y Restaurant2 y según la fórmula, el valor 1 o 2 se asigna a la columna **AdTarget**.

Si el valor de **Restaurant1** > **Restaurant2**, se asigna **AdTarget** al valor **1** de lo contrario **AdTarget** se asigna al valor **2**. El valor 1 genera la opción *Steak food* y el valor 2 resulta en la visualización de la opción *Thai food* en la pantalla de visualización.

## Precondiciones {#preconditions}

Antes de empezar a implementar la activación de reservas, debe aprender a configurar ***Data Store***, ***Segmentación de audiencias*** y ***Habilitar segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de activación de reserva de hospitalidad para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google y agregar la fórmula.**

   Por ejemplo, aplique la fórmula a la tercera columna **AdTarget**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuración de los segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** en **[Configuración de ContextHub en la página AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione **Sheets A1 1** y haga clic en **Edit**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** de la lista desplegable en **Property name**

   1. Seleccione **Operator** como **equal** en el menú desplegable

   1. Introduzca **Value** como **1**

   1. Del mismo modo, seleccione **Sheets A1 2** y haga clic en **Edit**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** de la lista desplegable en **Property name**

   1. Seleccione **Operator** como **2**

1. Desplácese y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenRestaurant**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las audiencias deben estar preconfiguradas tal y como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** utilizando la pestaña **Propiedades** —> **Personalización**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccione **Segmentación** en el editor y seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar orientación**.
1. **Comprobación de la vista previa**

   1. Haga clic en **Preview.** Además, abra las hojas de Google y actualice su valor.
   1. Actualice el valor en las columnas **Restaurant1** y **Restaurant2**. Si **Restaurant1** > **Restaurant2,** debería poder ver una imagen de *Steak* food de lo contrario, la imagen de comida *Thai* se muestra en la pantalla.

   ![result5](assets/result5.gif)

