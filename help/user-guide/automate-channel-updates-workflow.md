---
title: Uso de un flujo de trabajo para automatizar las actualizaciones de recursos de un canal de AEM Screens
description: Obtenga información sobre cómo crear un flujo de trabajo para procesar automáticamente los recursos cargados en Adobe Experience Manager y asignarlos dinámicamente a un canal de Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---


# Uso de un flujo de trabajo para automatizar las actualizaciones de recursos de un canal de AEM Screens {#automate-channel-updates-workflow}

Obtenga información sobre cómo crear un flujo de trabajo para procesar automáticamente los recursos cargados en Adobe Experience Manager y asignarlos dinámicamente a un canal de Screens. En este ejemplo, se activa un flujo de trabajo cuando se añade una imagen a una carpeta específica. El flujo de trabajo aplica una superposición de texto dinámico (proceso de marca de agua) y asigna la imagen a un canal de Screens. Las lecciones aprendidas de este ejemplo se pueden aplicar a una amplia variedad de escenarios de automatización.

## Requisitos previos {#prerequisites}

Para completar este tutorial, es necesario lo siguiente:

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. AEM [Paquete de servicio 8 de o superior](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/release-notes/release-notes)
1. AEM [6.5 Screens FP7 o superior](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## Configuración rápida {#quick-setup}

El siguiente vídeo ilustra cómo instalar un paquete de código de ejemplo que introduce un nuevo flujo de trabajo en Adobe Experience Manager. Esta función permite al usuario actualizar las propiedades de una carpeta en AEM Assets para que apunten a un canal de Screens. Cada vez que se agrega una imagen a esa carpeta, se agrega al canal de AEM Screens especificado.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Descargue el paquete de código compilado: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. AEM Instale el paquete anterior mediante el Administrador de paquetes de la.

## Modelo de flujo de trabajo {#workflow-model}

Se ha creado un esquema de metadatos de carpeta personalizado para capturar el canal de Screens de destino al que se deben agregar imágenes. Se utilizan dos modelos de flujo de trabajo para automatizar el procesamiento de recursos. El flujo de trabajo **DAM Update Asset** se ha editado para llamar a un flujo de trabajo personalizado, **Screens Demo Asset Processing, que inspecciona la carpeta contenedora del recurso para determinar el canal de Screens de destino. El flujo de trabajo **Screens Demo Asset Processing** también es responsable de aplicar la marca de agua a la imagen.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Pasos del proceso de flujo de trabajo personalizado {#workflow-process-step}

Inspect cuenta con dos pasos de proceso de flujo de trabajo personalizados que se usan como parte del flujo de trabajo **Procesamiento de recursos de demostración de Screens**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

El flujo de trabajo personalizado `AssetProcessingCheck.java` es un proceso que realiza una comprobación de la carga útil del flujo de trabajo. Determina si la carga útil es un recurso y si la carpeta contenedora está configurada para señalar a un canal de AEM Screens. Si se cumplen los requisitos, el paso del proceso conserva dos propiedades, `screen-channel` y `asset-path`, en los metadatos del flujo de trabajo.

El flujo de trabajo personalizado `AddAssetToChannel.java` es un paso del proceso que inspecciona los metadatos del flujo de trabajo y actualiza el canal de AEM Screens para hacer referencia a la imagen.

1. Descargar el código fuente: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Descomprima y vea el código usando su IDE favorito.
