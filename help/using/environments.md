---
title: Entornos para pantallas [!UICONTROL AEM]
seo-title: Entornos para pantallas [!UICONTROL AEM]
description: En esta página se describen los entornos de un proyecto de AEM Screens.
seo-description: Esta página resalta los entornos de un proyecto de AEM Screens.
translation-type: tm+mt
source-git-commit: 0d91aa653508969cf1f4ccfba23a570e22e6414c

---


# Entornos {#environments}

Determine de antemano qué entornos AEM tiene el cliente y qué espera que utilice, tanto para *desarrollo* como para *implementación*.

>[!NOTE]
>
>AEM Screens requiere varios paquetes para que los proyectos funcionen. Todos los entornos deben ejecutar la misma versión de Adobe Experience Manager.

Siga las directrices que se indican a continuación para configurar el entorno de su proyecto de AEM Screens:

1. Ejecute las versiones más recientes de los siguientes paquetes para su versión de Adobe Experience Manager:

   * **AEM Service Pack**
   * **Paquete de funciones para pantallas**
   * **AEM Cumulative Fix Pack**

1. Identifique los paquetes de desarrollo (por ejemplo, componentes principales de WCM) o los juegos de herramientas de terceros (por ejemplo, híbridos de SAP) que sean necesarios.

1. Instale los mismos paquetes de software en los entornos de desarrollo locales.

1. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Las configuraciones de servidor no coincidentes crean problemas al implementar y probar.
