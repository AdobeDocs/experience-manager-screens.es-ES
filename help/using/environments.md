---
title: Entornos para [!UICONTROL AEM Screens]
seo-title: Environments for [!UICONTROL AEM Screens]
description: En esta página se describen los entornos de un proyecto de AEM Screens.
seo-description: This page highlights the environments for an AEM Screens project.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# Entornos {#environments}

AEM Determine de antemano qué entornos de tiene el cliente y que espera que utilice, tanto para *desarrollo* y *implementación*.

>[!NOTE]
>
>AEM Screens requiere varios paquetes para que los proyectos funcionen. Todos los entornos deben ejecutar la misma versión de Adobe Experience Manager.

Siga las directrices siguientes para configurar el entorno de su proyecto de AEM Screens:

1. Ejecute las versiones más actuales de los siguientes paquetes para su versión de Adobe Experience Manager:

   * **Paquete de servicio de AEM**
   * **Paquete de funciones de Screens**
   * **Paquete de correcciones acumulativas de AEM**

1. Identifique los paquetes de desarrollo (por ejemplo, los componentes principales de WCM) o los kits de herramientas de terceros (por ejemplo, SAP Hybris) que sean necesarios.

1. Instale los mismos paquetes de software en los entornos de desarrollo local.

1. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Si las configuraciones del servidor no coinciden, se crearán problemas al implementar y probar.
