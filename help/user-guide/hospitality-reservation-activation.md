---
title: Activación de reserva de hospitalidad
seo-title: Activación de reserva de hospitalidad
description: El siguiente caso de uso demuestra el uso de la activación de reservaciones hospitalarias en base a los valores completados en las hojas de Google.
seo-description: El siguiente caso de uso demuestra el uso de la activación de reservaciones hospitalarias en base a los valores completados en las hojas de Google.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Activación de reserva de hospitalidad {#hospitality-reservation-activation}

El siguiente caso de uso demuestra el uso de la activación de reservaciones hospitalarias en base a los valores completados en las hojas de Google.

## Descripción {#description}

Para este caso de uso, la hoja de Google se llena con el porcentaje de reserva en dos restaurantes **Restaurant1** y **Restaurant2**. Una fórmula se aplica en función de los valores de Restaurant1 y Restaurant2 y, en función de la fórmula, el valor 1 o 2 se asigna a la columna **AdTarget** .

Si el valor de **Restaurant1** &gt; **Restaurant2**, **AdTarget** tiene asignado el valor **1** ; de lo contrario, **AdTarget** **** tiene asignado el valor2. El valor 1 genera la opción *Steak food* y el valor 2 muestra la opción de comida ** tailandesa en la pantalla.

## Condiciones previas {#preconditions}

Antes de empezar a implementar la activación de la reserva, debe aprender a configurar el almacén ***de*** datos, la segmentación ***de*** audiencias y ***habilitar la segmentación de canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso de activación de la reserva de hospitalidad para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google y agregar la fórmula.**

   Por ejemplo, aplique la fórmula a la tercera columna **AdTarget**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuración de segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte el ***paso 2: Configuración de la segmentación*** de audiencias en la página **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Seleccione las **hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **operador** como **igual** en el menú desplegable

   1. Introduzca el **valor** como **1**

   1. Del mismo modo, seleccione las **hojas A1 2** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **operador** como **2**

1. Navegue y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenRestaurant**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y Audiencias debe preconfigurarse como se describe en [Configuración de ContextHub en pantallas](configuring-context-hub.md)AEM.

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Debería haber configurado las **** configuraciones **de ContextHub** mediante la ficha **Propiedades** del canal —&gt; **Personalización** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccione **Objetivo** en el editor, seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.
1. **Comprobación de la vista previa**

   1. Haga clic en **Vista previa.** Además, abra las hojas de Google y actualice su valor.
   1. Actualice el valor en las columnas **Restaurant1** y **Restaurant2** . Si **Restaurante1** &gt; **Restaurante2,** debería poder ver una imagen de la comida *al vapor* , la imagen de la comida *tailandesa* se muestra en la pantalla.
   ![result5](assets/result5.gif)

