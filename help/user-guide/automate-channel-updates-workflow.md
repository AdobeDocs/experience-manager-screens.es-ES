---
title: Utilizar el flujo de trabajo para automatizar las actualizaciones de recursos para un canal de AEM Screens
seo-title: Utilizar el flujo de trabajo para automatizar las actualizaciones de recursos para un canal de AEM Screens
description: Obtenga información sobre cómo crear un flujo de trabajo para procesar automáticamente los recursos cargados en Adobe Experience Manager y asignarlos de forma dinámica a un canal de Screens. En este ejemplo, cuando se añade una imagen a una carpeta específica, se activa un flujo de trabajo que aplica una marca de agua dinámica y asigna la imagen a un canal de Screens. Las lecciones aprendidas de este ejemplo se pueden aplicar a una amplia variedad de escenarios de automatización.
seo-description: Obtenga información sobre cómo crear un flujo de trabajo para procesar automáticamente los recursos cargados en Adobe Experience Manager y asignarlos de forma dinámica a un canal de Screens. En este ejemplo, cuando se añade una imagen a una carpeta específica, se activa un flujo de trabajo que aplica una marca de agua dinámica y asigna la imagen a un canal de Screens. Las lecciones aprendidas de este ejemplo se pueden aplicar a una amplia variedad de escenarios de automatización.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Desarrollo de pantallas
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 1667fd10f415214a5301e9740d205eb33cc34f89
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---


# Utilizar el flujo de trabajo para automatizar las actualizaciones de recursos para un canal de AEM Screens {#automate-channel-updates-workflow}

Obtenga información sobre cómo crear un flujo de trabajo para procesar automáticamente los recursos cargados en Adobe Experience Manager y asignarlos de forma dinámica a un canal de Screens. En este ejemplo, cuando se añade una imagen a una carpeta específica, se activa un flujo de trabajo que aplica una marca de agua dinámica y asigna la imagen a un canal de Screens. Las lecciones aprendidas de este ejemplo se pueden aplicar a una amplia variedad de escenarios de automatización.

## Requisitos previos {#prerequisites}

Para completar este tutorial, es necesario lo siguiente:

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=es)
1. [AEM Service Pack 8 o bueno](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=es)
1. [AEM 6.5 Screens FP7 o bueno](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## Configuración rápida {#quick-setup}

El siguiente vídeo ilustra cómo instalar un paquete de código de ejemplo que introduce un nuevo flujo de trabajo en Adobe Experience Manager. Esta función permite al usuario actualizar las propiedades de una carpeta en AEM Assets para que apunte a un canal de Screens. Siempre que se añada una imagen a esa carpeta, se agregará al canal de pantallas especificado.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Descargue el paquete de código compilado: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Instale el paquete anterior mediante AEM Administrador de paquetes.

## Modelo de flujo de trabajo {#workflow-model}

Se ha creado un esquema de metadatos de carpeta personalizado para capturar el canal Screens de destino en el que se deben añadir imágenes. Se utilizan dos modelos de flujos de trabajo para automatizar el procesamiento de recursos. El flujo de trabajo **DAM Update Asset** se modifica para llamar a un flujo de trabajo personalizado, **Screens Demo Asset Processing** que inspeccionará la carpeta contenedora del recurso para determinar el canal Screens de destino. El flujo de trabajo **Screens Demo Asset Processing** también es responsable de aplicar la marca de agua a la imagen.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Pasos personalizados del proceso de flujo de trabajo {#workflow-process-step}

Inspect realiza dos pasos personalizados de proceso de flujo de trabajo que se utilizan como parte del flujo de trabajo **Screens Demo Asset Processing**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` es un proceso de flujo de trabajo personalizado que realiza una comprobación en la carga útil del flujo de trabajo para determinar si la carga útil es un recurso y si la carpeta contenedora está configurada para apuntar a un canal de Screens. Si se cumplen los requisitos, el paso del proceso mantiene dos propiedades, `screen-channel` y `asset-path`, en los metadatos del flujo de trabajo.

`AddAssetToChannel.java` es un paso de proceso de flujo de trabajo personalizado que inspecciona los metadatos del flujo de trabajo y actualiza el canal de Screens para hacer referencia a la imagen.

1. Descargue el código fuente: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Descomprima y vea el código usando su IDE favorito.
