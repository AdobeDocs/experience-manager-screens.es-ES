---
title: Entornos para [!UICONTROL AEM Screens]
description: Obtenga más información sobre los entornos de un proyecto de AEM Screens.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Entornos {#environments}

AEM Determine de antemano qué entornos de tiene el cliente y espera que use, tanto para *desarrollo* como para *implementación*.

>[!NOTE]
>
>AEM Screens requiere varios paquetes para que los proyectos funcionen. Todos los entornos deben ejecutar la misma versión de Adobe Experience Manager.

Siga las directrices siguientes para configurar el entorno de su proyecto de AEM Screens:

1. Ejecute las versiones más actuales de los siguientes paquetes para su versión de Adobe Experience Manager:

   * AEM **Paquete de servicio de**
   * **Paquete de funciones de Screens**
   * AEM **Paquete De Correcciones Acumulativas De**

1. Identifique los paquetes de desarrollo (por ejemplo, los componentes principales de WCM) o los kits de herramientas de terceros (por ejemplo, SAP Hybris) que sean necesarios.

1. Instale los mismos paquetes de software en su entorno de desarrollo local.

1. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Las configuraciones de servidor no coincidentes crean problemas al implementar y probar.
