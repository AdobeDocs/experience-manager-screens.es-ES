---
title: Creación con activadores de datos
seo-title: Creación con activadores de datos
description: Siga esta página para aprender a crear con activadores de datos.
translation-type: tm+mt
source-git-commit: a7d3ec582dde83ed6efb08a6c3c6a75cc0820970

---


# Creación con activadores de datos {#authoring-with-data-triggers}

Esta sección resalta cómo habilitar la segmentación en los canales.

>[!IMPORTANT]
> La versión mínima que admite activadores de datos en un canal de AEM Screens es AEM 6.5.3 Feature Pack 3.

## Requisitos previos {#prereqs}

Antes de seguir los pasos que se describen a continuación para activar la segmentación en canales, debe conocer los términos [clave en Configuración en pantallas](configuring-context-hub.md) de AEM necesarios para comprender ContextHub y la determinación de objetivos en pantallas de AEM.

>[!IMPORTANT]
> Se recomienda que comprenda y configure las configuraciones de ContextHub antes de habilitar la segmentación en un canal de AEM Screens.

Siga los vínculos siguientes para obtener más información:

1. **[Configuración del almacén de datos](configuring-context-hub.md)**
1. **[Configuración de la segmentación de audiencias](configuring-context-hub.md)**

Una vez que haya completado los pasos anteriores, estará listo para habilitar la segmentación en los canales.

## Información general sobre la creación con activadores de datos {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Activación del objetivo en un canal de pantallas de AEM {#enabling-targeting}

Siga los pasos a continuación para habilitar la segmentación en los canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación mediante **DataDrivenRetail** *(canal de secuencia)* creado en un canal de pantallas de AEM.

1. Seleccione el canal **DataDrivenRetail** y haga clic en **Propiedades** en la barra de acciones.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Seleccione la ficha **Personalización** para configurar las configuraciones de ContextHub.

   1. Seleccione la Ruta **de** ContextHub como **bibliotecas** > **configuración** > **configuración** de nube > **predeterminada** **** ****> Configuraciones de ContextHub y haga clic enSeleccionar.

   1. Seleccione la Ruta **de** segmentos como **conf** > **We.Retail** > **configuración** > **wcm** **** ****> segmentosy haga clic en Seleccionar.

   1. Haga clic en **Guardar y cerrar**.
   >[!NOTE]
   >
   >Utilice ContextHub y la ruta de segmentos, donde inicialmente guardó las configuraciones y los segmentos del concentrador de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navegue y seleccione **DataDrivenRetail** en **DataDrivenAssets** > **Canales** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte los recursos en el editor de canales.

   >[!NOTE]
   >
   >Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Haga clic en **Objetivo**.

1. Seleccione **Marca** y la **actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.

### Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para su proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

1. **[Activación de objetivo de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de la temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**

