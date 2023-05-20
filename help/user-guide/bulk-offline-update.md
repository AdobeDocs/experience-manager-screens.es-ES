---
title: Actualización sin conexión masiva
seo-title: Bulk Offline Update
description: Siga esta página para aprender a actualizar todos los canales de forma masiva.
seo-description: Follow this page to learn how you can update all the channels in bulk.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 4%

---

# Actualización sin conexión masiva {#bulk-offline-update}

Esta sección cubre los siguientes temas sobre la actualización masiva sin conexión:

* **Información general**
* **Uso de actualización sin conexión masiva**

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens AEM AEM solo está disponible si ha instalado el paquete de funciones 3 de 6.3 o el paquete de funciones 1 de Screens de 6.3 o de 6.4.
>
>Para obtener acceso a este paquete de funciones, debe ponerse en contacto con el Soporte técnico de Adobe y solicitar acceso. Una vez que tenga los permisos necesarios, puede descargarlo desde Package Share.

## Información general {#overview}

Actualización sin conexión en lote, le permite actualizar todo el canal en lote. Esto evita la molestia de navegar a un canal en particular y actualizar el contenido. En su lugar, puede actualizar todo el contenido de los canales de un proyecto específico en un instante.

También puede programar esta actividad para un momento de menor tráfico de red.

>[!NOTE]
>
>La función Actualización sin conexión en lote está optimizada para actualizar solo los canales que se han modificado.

## Uso de actualización sin conexión masiva {#using-bulk-offline-update}

Puede utilizar manualmente la actualización sin conexión masiva desde la interfaz de usuario (IU) o programar la actualización masiva desde los servicios OSGi.

### Uso de la interfaz de usuario de AEM Screens {#using-aem-screens-user-interface}

Siga los pasos a continuación para utilizar la actualización sin conexión masiva para un proyecto de AEM Screens:

1. Vaya al proyecto de AEM Screens.
1. Seleccione el proyecto y haga clic en **Actualizar contenido sin conexión** en la barra de acciones para actualizar manualmente el contenido del canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuración de la consola web de Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Siga los pasos a continuación para utilizar la actualización sin conexión masiva para un proyecto de AEM Screens:

1. Configuración de la consola web de Adobe Experience Manager.
1. Busque servicios de actualización sin conexión en bloque.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Añada las siguientes propiedades:

   **Ruta de proyecto** Especifique la ruta del proyecto de AEM Screens. El camino suele ser `/content/screens/<Name of your project>`.

   *Por ejemplo*, `/content/screens/we-retail`. Puede encontrar esta ruta en la dirección URL seleccionando cualquier proyecto en AEM Screens (no haga clic en el icono).

   >[!NOTE]
   >
   >Especifique la ruta del proyecto relativa al canal.

   **Frecuencia de programación** Especifique la hora, por ejemplo, 5:00 p. m. o 17:00 p. m. a la que este servicio debe actualizar el contenido sin conexión.

1. Clic **Guardar** para guardar la configuración, y el contenido se actualizará a la hora especificada.
