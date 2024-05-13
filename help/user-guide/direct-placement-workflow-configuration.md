---
title: Configuración del flujo de trabajo de ubicación directa
description: Esta página resalta la configuración del flujo de trabajo de colocación directa.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# Configuración del flujo de trabajo de ubicación directa {#direct-placement-workflow}

Siga esta página para obtener más información sobre la configuración de un flujo de trabajo de recursos que le permite insertar mediante programación un recurso en un canal de AEM Screens predefinido.

Esta sección trata los siguientes temas:

* Información general
* Configuración del flujo de trabajo Direct Placement

## Información general {#overview}

La configuración del flujo de trabajo de colocación directa asigna un canal de proyecto de AEM Screens a una carpeta específica de los recursos y permite colocar cualquier recurso en esa carpeta. El Adobe recomienda almacenar en déclencheur una actualización masiva sin conexión para completar la publicación.

Como autor de contenido, también puede hacer clic manualmente en **Actualizar contenido sin conexión**.

>[!NOTE]
>
>Para obtener información sobre cómo utilizar la actualización sin conexión masiva, consulte [Actualización de contenido como servicio](/help/user-guide/content-update-as-a-service.md).

## Configuración del flujo de trabajo Direct Placement {#configuring-workflow}

>[!IMPORTANT]
>
>Antes de iniciar la configuración, instale el `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. AEM Una vez instalado el paquete, debe poder verlo y acceder a él desde su instancia de > Herramientas (icono) > **Flujo de trabajo** > **Modelos de flujo de trabajo**.

Siga los pasos a continuación para configurar el flujo de trabajo de ubicación directa:

1. Navegue hasta AEM Screens AEM desde la instancia de y cree un proyecto de Screens con el título **Flujo de trabajo de recursos**.

1. Cree un canal con el título **Workflow-Assets** en el **Canales** carpeta.

