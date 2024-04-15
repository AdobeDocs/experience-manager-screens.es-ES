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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Actualización sin conexión masiva {#bulk-offline-update}

Esta sección cubre los siguientes temas sobre la actualización masiva sin conexión:

* **Información general**
* **Uso de actualización sin conexión masiva**

<!-- OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share. -->

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
1. Seleccione el proyecto y luego seleccione **Actualizar contenido sin conexión** desde la barra de acciones para poder actualizar manualmente el contenido del canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuración de la consola web Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

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

1. Seleccionar **Guardar** para guardar la configuración. El contenido se actualiza a la hora especificada.
