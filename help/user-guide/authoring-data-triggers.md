---
title: Creación con Déclencheur de datos
description: Obtenga más información sobre cómo crear déclencheur de datos en un canal de AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
TQID: https://experienceleague.adobe.com/Iqb4pREvZNLalXSE6sNTZPV-uwqzBJKmztLuQtWfCW0
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
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 421
ht-degree: 0%

---

# Creación con Déclencheur de datos {#authoring-with-data-triggers}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

En esta sección se explica cómo habilitar el direccionamiento en los canales.

>[!IMPORTANT]
>
>La versión mínima que admite déclencheur de datos en un canal de AEM Screens es AEM 6.5.3 Feature Pack 3.

## Requisitos previos {#prereqs}

Antes de seguir los pasos siguientes para habilitar el direccionamiento en los canales, aprenda los [términos clave en Configuración en AEM Screens](configuring-context-hub.md) necesarios para comprender ContextHub y el direccionamiento en AEM Screens.

>[!IMPORTANT]
>
>Se recomienda comprender y configurar las configuraciones de ContextHub antes de habilitar el direccionamiento en un canal de AEM Screens.

Siga los vínculos a continuación para obtener más información:

1. **[Configurando almacén de datos](configuring-context-hub.md)**
1. **[Configurando la segmentación de audiencia](configuring-context-hub.md)**

Cuando haya completado los pasos anteriores, estará listo para habilitar el direccionamiento en sus canales.

## Información general sobre la creación con Déclencheur de datos {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Habilitar la segmentación en un canal de AEM Screens {#enabling-targeting}

Siga los pasos a continuación para habilitar el direccionamiento en sus canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar el direccionamiento mediante **DataDrivenRetail** *(canal de secuencia)* creado en un canal de AEM Screens.

1. Haga clic en el canal **DataDrivenRetail** y, a continuación, haga clic en **Propiedades** en la barra de acciones.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Haga clic en la ficha **Personalization** para configurar las configuraciones de ContextHub y hacer clic en la ruta de acceso de ContextHub y segmentos.

   1. Haga clic en la ruta de acceso de **ContextHub** como **libs** > **settings** > **cloudsettings** > **default** > **Configuraciones de ContextHub** y haga clic en **Click**.

   1. Haga clic en la ruta de acceso de **segmentos** como **conf** > **`We.Retail`** > **settings** > **wcm** > **segments** y haga clic en **Click**.

   1. Haga clic en **Guardar y cerrar**.

   >[!NOTE]
   >
   >Utilice ContextHub y la ruta de segmentos, donde guardó inicialmente las configuraciones y segmentos de Context Hub.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navegue y haga clic en **DataDrivenRetail** desde **DataDrivenAssets** > **Canales** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte los recursos en el editor de canales.

   >[!NOTE]
   >
   >Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Haga clic en **Segmentación**.

1. Haga clic en **Marca** y en la **Actividad** del menú desplegable y luego haga clic en **Iniciar segmentación**.

### Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para el proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

1. **[Activación objetivo de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de temperatura en el centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**

