---
title: Activación de temperatura del centro de viajes
description: Con AEM Screens, descubra cómo este caso de uso demuestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en Hojas de cálculo de Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
TQID: https://experienceleague.adobe.com/C8FAKzAKUjdochkR96MShKiu2Ig-g-9BDnoX09g4xnM
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ff2b9b37-92e0-45fc-b853-379d44c08c89
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 500
ht-degree: 0%

---

# Activación de temperatura del centro de viajes {#travel-center-temperature-activation}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

El siguiente caso de uso muestra el uso de la activación de temperatura local del centro de viajes en función de los valores rellenados en Hojas de cálculo de Google.

## Descripción {#description}

Para este caso de uso, si el valor de las hojas de Google es menor que 50, se muestra una imagen con bebidas calientes. Si el valor es mayor o igual que 50, se muestra una imagen con bebidas frías. Si hay algún otro valor o ningún valor, el reproductor muestra una imagen predeterminada.

## Condiciones previas {#preconditions}

Antes de comenzar a implementar la activación de temperatura local del centro de viajes, aprende a configurar ***Almacén de datos***, ***Segmentación de audiencia*** y ***Habilitar segmentación para canales*** en un proyecto de AEM Screens.

Consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md) para obtener información detallada.

## Flujo básico {#basic-flow}

Siga los pasos a continuación para implementar el caso de uso Activación de temperatura local del centro de viajes:

1. **Rellenando las hojas de Google**

   1. Navegue hasta la hoja de Google de ContextHubDemo.
   1. Agregue una columna con **`Heading1`** con el valor correspondiente de temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuración de los segmentos en Audiences según los requisitos**

   1. Vaya a los segmentos de su audiencia (consulte ***Paso 2: Configuración de la segmentación de audiencia*** en la página **[Configuración de ContextHub en AEM Screens](configuring-context-hub.md)** para obtener más información).

   1. Haga clic en **Hojas A1 1** y luego en **Editar**.

   1. Haga clic en la propiedad de comparación y en el icono de configuración.
   1. Haga clic en **googlesheets/value/1/0** en la lista desplegable de **Nombre de propiedad**

   1. Haga clic en el **Operador** como **mayor o igual que** en el menú desplegable

   1. Escriba **Value** como **50**

   1. Del mismo modo, seleccione las **hojas A1 2** y haga clic en **Editar**.

   1. Haga clic en **Propiedad de comparación - Valor** y seleccione el icono de configuración.
   1. Haga clic en **googlesheets/value/1/0** en la lista desplegable de **Nombre de propiedad**

   1. Haga clic en el **Operador** como **menor que** en el menú desplegable

   1. Escriba **Value** como **50**

1. Desplácese, seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el ejemplo siguiente, **DataDrivenWeather**, se usa un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   >
   >El canal ya debería tener una imagen predeterminada y las audiencias deberían preconfigurarse como se describe en [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Tu **ContextHub** **configuraciones** que usan el canal **Propiedades** > pestaña **Personalization** ya debería estar configurada.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Haga clic en **Segmentación** en el editor, luego haga clic en **Marca** y en la **Actividad** en el menú desplegable y luego haga clic en **Iniciar segmentación**.

   ![nueva_actividad3](assets/new_activity3.gif)

1. **Comprobando la vista previa**

   1. Haga clic en **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor por debajo de 50. Puede ver una imagen de una bebida fría. Si el valor de Google Sheets es 50 o superior, debería ver una imagen de una bebida caliente.

   ![resultado3](assets/result3.gif)
