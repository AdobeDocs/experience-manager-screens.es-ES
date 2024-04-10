---
title: Activación de reserva de hospitalidad
seo-title: Hospitality Reservation Activation
description: En el siguiente caso de uso se muestra el uso de la activación de reserva de hospital en función de los valores rellenados en las Hojas de cálculo de Google.
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Activación de reserva de hospitalidad {#hospitality-reservation-activation}

En el siguiente caso de uso se muestra el uso de la activación de reserva de hospital en función de los valores rellenados en las Hojas de cálculo de Google.

## Descripción {#description}

En este caso de uso, la hoja Google Sheet se rellena con el porcentaje de reserva en dos restaurantes **Restaurante1** y **Restaurante2**. Se aplica una fórmula basada en los valores de Restaurant1 y Restaurant2 y, según la fórmula, el valor 1 o 2 se asigna al **AdTarget** Columna.

Si el valor de **Restaurante1** > **Restaurante2**, entonces **AdTarget** se ha asignado un valor **1** de otro modo **AdTarget** se ha asignado un valor **2**. El valor 1 genera *Comida para filetes* y el valor 2 da como resultado la visualización de *Comida tailandesa* en la pantalla de visualización.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de la reserva, debe aprender a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar la segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de activación de reserva de hospitalidad para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google y agregar la fórmula.**

   Por ejemplo, aplique la fórmula a la tercera columna **AdTarget**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuración de los segmentos en Audiences según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** in **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione el **Hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccionar **googlesheets/value/1/2** de la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** as **igualar** en el menú desplegable

   1. Introduzca el **Valor** as **1**

   1. Del mismo modo, seleccione la **Hojas A1 2** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccionar **googlesheets/value/1/2** de la lista desplegable en **Nombre de propiedad**

   1. Seleccione el **Operador** as **2**

1. Desplácese, seleccione el canal () y haga clic en **Editar** de la barra de acciones. En el ejemplo siguiente, **DataDrivenRestaurant**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las audiencias deben preconfigurarse como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** uso del canal **Propiedades** > **Personalización** pestaña.

   ![screen_shot_2019-05-08a114106m](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccionar **Segmentación** en el editor, seleccione **Marca** y el **Actividad** en el menú desplegable y haga clic en **Iniciar segmentación**.
1. **Comprobación de la previsualización**

   1. Clic **Vista previa.** Además, abra las Hojas de cálculo de Google y actualice su valor.
   1. Actualice el valor en **Restaurante1** y **Restaurante2** columnas. If **Restaurante1** > **Restaurante2,** debería poder ver una imagen de *Filete* comida de otro modo, *Tailandés* la imagen de la comida se muestra en la pantalla.

   ![result5](assets/result5.gif)
