---
title: Actualización masiva sin conexión
seo-title: Actualización masiva sin conexión
description: Siga esta página para conocer cómo puede actualizar todos los canales de forma masiva.
seo-description: Siga esta página para conocer cómo puede actualizar todos los canales de forma masiva.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Actualización masiva sin conexión {#bulk-offline-update}

Esta sección trata los siguientes temas sobre Actualización masiva sin conexión:

* **Información general**
* **Uso de la actualización masiva sin conexión**

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Información general {#overview}

Actualización masiva sin conexión, le permite actualizar todos los canales de forma masiva. Evita la molestia de desplazarse a un canal en particular y actualizar el contenido. En su lugar, puede actualizar todo el contenido en los canales para un proyecto específico en un instante.

También puede programar esta actividad para un tiempo de tráfico de red menor.

>[!NOTE]
>
>La función Actualización masiva sin conexión está optimizada para actualizar solo los canales que se han modificado.

## Uso de la actualización masiva sin conexión {#using-bulk-offline-update}

Puede utilizar manualmente la actualización sin conexión masiva desde la interfaz de usuario (IU) o programar la actualización masiva desde los servicios OSGi.

### Uso de la interfaz de usuario de AEM Screens {#using-aem-screens-user-interface}

Siga los pasos a continuación para utilizar la actualización masiva sin conexión para un proyecto de AEM Screens:

1. Vaya a su proyecto de AEM Screens.
1. Seleccione el proyecto y haga clic en **Actualizar contenido** sin conexión en la barra de acciones para actualizar manualmente el contenido del canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuración de la consola web de Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Siga los pasos a continuación para utilizar la actualización masiva sin conexión para un proyecto de AEM Screens:

1. Configuración de la consola web de Adobe Experience Manager.
1. Busque servicios de actualización sin conexión masiva.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Agregue las siguientes propiedades:

   **Ruta** del proyecto Especifique la ruta del proyecto de AEM Screens. La ruta suele ser `/content/screens/<Name of your project>`.

   *Por ejemplo*, `/content/screens/we-retail`. Puede encontrar esta ruta en la URL seleccionando cualquier proyecto en AEM Screens (no haga clic en el icono).

   >[!NOTE]
   >
   >Especifique la ruta del proyecto en relación con el canal.

   **Frecuencia** de programación Especifique una hora, por ejemplo, 5:00 pm o 17:00, en la que este servicio debe actualizar el contenido sin conexión.

1. Haga clic en **Guardar** para guardar la configuración y el contenido se actualizará a la hora especificada.
