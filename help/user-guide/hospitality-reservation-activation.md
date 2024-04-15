---
title: Activación de reserva de hospitalidad
description: Descubra cómo este caso de uso demuestra el uso de la activación de reserva de hospitalidad en función de los valores rellenados en Hojas de cálculo de Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Activación de reserva de hospitalidad {#hospitality-reservation-activation}

En el siguiente caso de uso se muestra el uso de la activación de reserva de hospital en función de los valores rellenados en las Hojas de cálculo de Google.

## Descripción {#description}

Para este caso de uso, la hoja de cálculo de Google se rellena con el porcentaje de reservas en dos restaurantes **`Restaurant1`** y **`Restaurant2`**. Se aplica una fórmula basada en los valores de `Restaurant1` y `Restaurant2` y en función de la fórmula, el valor 1 o 2 se asigna al **AdTarget** Columna.

Si el valor de **`Restaurant1`** > **`Restaurant2`**, entonces **AdTarget** se ha asignado un valor **1** de otro modo **AdTarget** se ha asignado un valor **2**. El valor 1 genera *Comida para filetes* Opción y Valor dos resultados en la visualización de *Comida tailandesa* en la pantalla de visualización.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de la reserva, aprenda a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar la segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos del caso de uso a continuación para implementar la activación de la reserva de hospitalidad para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google y agregar la fórmula**.

   Por ejemplo, aplique la fórmula a la tercera columna **AdTarget**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuración de los segmentos en Audiences según los requisitos**

   1. Vaya a los segmentos de la audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** in **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).
   1. Seleccione el **Hojas A1 1** y seleccione **Editar**.
   1. Seleccione la propiedad de comparación y seleccione **Configuración** icono.
   1. Seleccionar **googlesheets/value/1/2** de la lista desplegable en **Nombre de propiedad**.
   1. Seleccione el **Operador** as **igualar** en el menú desplegable.
   1. Introduzca el **Valor** as **1**.
   1. Del mismo modo, seleccione la **Hojas A1 2** y seleccione **Editar**.
   1. Seleccione la propiedad de comparación y seleccione **Configuración** icono.
   1. Seleccionar **googlesheets/value/1/2** de la lista desplegable en **Nombre de propiedad**.
   1. Seleccione el **Operador** as **2**.

1. Desplácese, seleccione el canal () y seleccione **Editar** de la barra de acciones. En el ejemplo siguiente, **DataDrivenRestaurant**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debe tener una imagen predeterminada y las audiencias deben preconfigurarse como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Debería haber configurado su **ContextHub** **Configuraciones** uso del canal **Propiedades** > **Personalización** pestaña.

   ![screen_shot_2019-05-08a114106m](assets/screen_shot_2019-05-08at114106am.png)

1. Seleccionar **Segmentación** en el editor, seleccione **Marca** y el **Actividad** en el menú desplegable y seleccione **Iniciar segmentación**.
1. **Comprobación de la previsualización**

   1. Seleccionar **Vista previa.** Además, abra las Hojas de cálculo de Google y actualice su valor.
   1. Actualice el valor en **`Restaurant1`** y **`Restaurant2`** columnas. If **`Restaurant1`** > **`Restaurant2`,** debería poder ver una imagen de *Filete* comida de otro modo, *Tailandés* la imagen de la comida se muestra en la pantalla.

   ![result5](assets/result5.gif)
