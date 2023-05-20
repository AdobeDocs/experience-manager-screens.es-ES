---
title: Actualización de contenido como servicio
seo-title: Content Update As a Service
description: Siga esta página para obtener más información sobre Actualización de contenido como servicio.
seo-description: Follow this page to learn about Content Update As a Service.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 4%

---

# Actualización de contenido como servicio {#content-update-as-a-service}

Esta sección trata los siguientes temas sobre la actualización de contenido como servicio:

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
