---
title: Actualización sin conexión masiva
description: Descubra cómo puede actualizar todos los canales de forma masiva.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
TQID: https://experienceleague.adobe.com/PxlKWiWPvedqs2krdj3UH5Chshni2X3RaTmZI1wW2-Q
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: ba4275ba-c29a-4197-90dc-5a633402ca3cid: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 0%

---

# Actualización sin conexión masiva {#bulk-offline-update}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Esta sección cubre los siguientes temas sobre la actualización masiva sin conexión:

* **Información general**
* **Usando actualización sin conexión en lotes**

<!--
OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share.
-->

## Información general {#overview}

Bulk Offline Update, permite actualizar todos los canales de forma masiva. Esto evita la molestia de navegar a un canal en particular y actualizar el contenido. En su lugar, puede actualizar todo el contenido de los canales de un proyecto específico en un instante.

También puede programar esta actividad para un momento de menor tráfico de red.

>[!NOTE]
>
>La función Actualización sin conexión en lote está optimizada para actualizar solo los canales que se han modificado.

## Uso de actualización sin conexión masiva {#using-bulk-offline-update}

Puede utilizar manualmente la actualización sin conexión masiva desde la interfaz de usuario (IU) o programar la actualización masiva desde los servicios OSGi.

### Uso de la interfaz de usuario de AEM Screens {#using-aem-screens-user-interface}

Siga los pasos a continuación para utilizar la actualización sin conexión masiva para un proyecto de AEM Screens:

1. Vaya al proyecto de AEM Screens.
1. Haga clic en el proyecto y luego en **Actualizar contenido sin conexión** en la barra de acciones para que pueda actualizar manualmente el contenido del canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuración de la consola web Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Siga los pasos a continuación para utilizar la actualización sin conexión masiva para un proyecto de AEM Screens:

1. Configuración de la consola web de Adobe Experience Manager.
1. Busque los servicios de actualización sin conexión masiva.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Añada las siguientes propiedades:

   **Ruta del proyecto** - Especifica la ruta de su proyecto de AEM Screens. La ruta de acceso suele ser `/content/screens/<Name of your project>`.

   *Por ejemplo*, `/content/screens/we-retail`. Puede encontrar esta ruta en la dirección URL seleccionando cualquier proyecto en AEM Screens (no haga clic en el icono).

   >[!NOTE]
   >
   >Especifique la ruta del proyecto relativa al canal.

   **Frecuencia de horario** - Especifica una hora, por ejemplo, 5:00 p. m. o 17:00 a la que este servicio debe actualizar el contenido sin conexión.

1. Haz clic en **Guardar** para guardar la configuración. El contenido se actualiza a la hora especificada.

