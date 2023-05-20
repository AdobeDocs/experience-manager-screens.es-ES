---
title: Configuración del flujo de trabajo de ubicación directa
seo-title: Direct Placement Workflow Configuration
description: Esta página resalta la configuración del flujo de trabajo de colocación directa.
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Configuración del flujo de trabajo de ubicación directa {#direct-placement-workflow}

Siga esta página para obtener más información sobre la configuración de un flujo de trabajo de recursos que le permite insertar mediante programación un recurso en un canal de AEM Screens predefinido.

Esta sección trata los siguientes temas:

* Información general
* Configuración del flujo de trabajo Direct Placement

## Información general {#overview}

La configuración del flujo de trabajo de colocación directa asigna un canal de proyecto de AEM Screens a una carpeta específica de los recursos y permite colocar cualquier recurso en esa carpeta. Se recomienda almacenar en déclencheur la actualización sin conexión masiva para completar la publicación.

Como autor de contenido, también puede hacer clic manualmente en **Actualizar contenido sin conexión**.

>[!NOTE]
>
>Para aprender a utilizar la actualización sin conexión masiva, consulte [Actualización de contenido como servicio](/help/user-guide/content-update-as-a-service.md).

## Configuración del flujo de trabajo Direct Placement {#configuring-workflow}

>[!IMPORTANT]
>
>Antes de iniciar la configuración, debe instalar el [Paquete de demostración](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). AEM Una vez instalado el paquete, debe poder verlo y acceder a él desde la instancia de la aplicación —> Herramientas (icono) —> **Flujo de trabajo** —> **Modelos de flujo de trabajo**.

Siga los pasos a continuación para configurar el flujo de trabajo de ubicación directa:

1. Navegue hasta AEM Screens AEM desde la instancia de su y cree un proyecto de Screens con el título **Flujo de trabajo de recursos**.

1. Cree un canal con el título **Workflow-Assets** bajo **Canales** carpeta.

