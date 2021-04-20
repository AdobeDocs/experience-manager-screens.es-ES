---
title: Creación con Déclencheur de datos
seo-title: Creación con Déclencheur de datos
description: Siga esta página para aprender a crear con déclencheur de datos.
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---


# Creación con Déclencheur de datos {#authoring-with-data-triggers}

En esta sección se explica cómo habilitar la segmentación en los canales.

>[!IMPORTANT]
>
>La versión mínima que admite déclencheur de datos en un canal de AEM Screens es AEM 6.5.3 Feature Pack 3.

## Requisitos previos {#prereqs}

Antes de seguir los pasos a continuación para habilitar la segmentación en los canales, debe conocer los [Términos clave en Configuración en AEM Screens](configuring-context-hub.md) necesarios para comprender ContextHub y la determinación de objetivos en AEM Screens.

>[!IMPORTANT]
>
>Se recomienda comprender y configurar las configuraciones de ContextHub antes de habilitar la segmentación en un canal de AEM Screens.

Para obtener más información, siga los vínculos siguientes:

1. **[Configuración del almacén de datos](configuring-context-hub.md)**
1. **[Configuración de la segmentación de audiencia](configuring-context-hub.md)**

Una vez completados los pasos anteriores, ya puede activar la segmentación en los canales.

## Información general sobre la creación con Déclencheur de datos {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Habilitar la determinación de objetivos en un canal de AEM Screens {#enabling-targeting}

Siga los pasos a continuación para habilitar la segmentación en sus canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación mediante el uso de **DataDrivenRetail** *(canal de secuencia)* creado en un canal de AEM Screens.

1. Seleccione el canal **DataDrivenRetail** y haga clic en **Properties** en la barra de acciones.

   ![screen_shot_2019-05-01at4332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Seleccione la pestaña **Personalization** para configurar las configuraciones de ContextHub y seleccione la ruta de ContextHub y Segments .

   1. Seleccione **Ruta de ContextHub** como **libs** > **configuración** > **configuración de nube** > **configuración predeterminada** > **Configuraciones de ContextHub** y haga clic en &lt;a12/ Seleccione **.**

   1. Seleccione la **Ruta de segmentos** como **conf** > **We.Retail** > **configuración** > **wcm** > **segmentos** y haga clic en **Seleccionar** 3/>.

   1. Haga clic en **Guardar y cerrar**.
   >[!NOTE]
   >
   >Utilice ContextHub y la ruta Segments, donde inicialmente guardó las configuraciones y segmentos de Context Hub.

   ![screen_shot_2019-05-01at4030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Desplácese y seleccione **DataDrivenRetail** en **DataDrivenAssets** > **Channels** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte los recursos en el editor de canales.

   >[!NOTE]
   >
   >Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Haga clic en **Segmentación**.

1. Seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar orientación**.

### Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para su proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por los datos desempeñan un papel vital en diferentes industrias:

1. **[Activación de destino de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de la temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**
