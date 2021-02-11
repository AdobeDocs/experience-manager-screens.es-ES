---
title: 'Configuración del flujo de trabajo de colocación directa '
seo-title: Configuración del flujo de trabajo de colocación directa
description: Esta página resalta la configuración del flujo de trabajo de colocación directa.
seo-description: Esta página resalta la configuración del flujo de trabajo de colocación directa.
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Configuración del flujo de trabajo de colocación directa {#direct-placement-workflow}

Siga esta página para obtener información sobre la configuración de un flujo de trabajo de recursos que le permite insertar mediante programación un recurso en un canal de AEM Screens predefinido.

Esta sección abarca los siguientes temas:

* Información general
* Configuración del flujo de trabajo de colocación directa

## Información general {#overview}

La configuración de flujo de trabajo de colocación directa asigna un canal de proyecto de AEM Screens a una carpeta específica de recursos y permite colocar cualquier recurso en dicha carpeta. Se recomienda realizar un déclencheur de la actualización sin conexión masiva para completar la publicación.

Como autor de contenido, también puede hacer clic manualmente en **Actualizar contenido sin conexión**.

>[!NOTE]
>
>Para obtener información sobre cómo utilizar la actualización sin conexión masiva, consulte [Content Update As a Service](/help/user-guide/content-update-as-a-service.md).

## Configuración del flujo de trabajo de colocación directa {#configuring-workflow}

>[!IMPORTANT]
>
>Antes de realizar el inicio de la configuración, debe instalar el [paquete de demostración](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Una vez que haya instalado el paquete, debería poder vista y acceder a él desde su instancia de AEM —> Herramientas (icono) —> **Flujo de trabajo** —> **Modelos de flujo de trabajo**.

Siga los pasos a continuación para configurar el flujo de trabajo de colocación directa:

1. Vaya a AEM Screens desde su instancia de AEM y cree un proyecto de Pantallas denominado **Flujo de trabajo de recursos**.

1. Cree un canal con el título **Workflow-Assets** en **Canales**.

