---
title: Creación con Déclencheur de datos
seo-title: Authoring with Data Triggers
description: Siga esta página para aprender a crear déclencheur de datos.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# Creación con Déclencheur de datos {#authoring-with-data-triggers}

En esta sección se explica cómo habilitar el direccionamiento en los canales.

>[!IMPORTANT]
>
>La versión mínima que admite déclencheur de datos en un canal de AEM Screens AEM es el paquete de funciones 3 de la versión 6.5.3 de.

## Requisitos previos {#prereqs}

Antes de seguir los pasos a continuación para habilitar el direccionamiento en los canales, debe conocer los siguientes pasos [Términos clave para la configuración en AEM Screens](configuring-context-hub.md) necesario para comprender ContextHub y la segmentación en AEM Screens.

>[!IMPORTANT]
>
>Se recomienda comprender y configurar las configuraciones de ContextHub antes de habilitar el direccionamiento en un canal de AEM Screens.

Siga los vínculos a continuación para obtener más información:

1. **[Configuración del almacén de datos](configuring-context-hub.md)**
1. **[Configuración de la segmentación de audiencia](configuring-context-hub.md)**

Una vez completados los pasos anteriores, puede habilitar el direccionamiento en sus canales.

## Información general sobre la creación con Déclencheur de datos {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Habilitar la segmentación en un canal de AEM Screens {#enabling-targeting}

Siga los pasos a continuación para habilitar el direccionamiento en sus canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación utilizando **DataDrivenRetail** *(canal de secuencia)* creado en un canal de AEM Screens.

1. Seleccione el canal **DataDrivenRetail** y haga clic en **Propiedades** de la barra de acciones.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Seleccione el **Personalización** para configurar las configuraciones de ContextHub y seleccionar la ruta de ContextHub y los segmentos.

   1. Seleccione el **Ruta de ContextHub** as **libs** > **configuración** > **cloudsettings** > **predeterminado** > **Configuraciones de ContextHub** y haga clic en **Seleccionar**.

   1. Seleccione el **Ruta de segmentos** as **conf** > **We.Retail** > **configuración** > **wcm** > **segmentos** y haga clic en **Seleccionar**.

   1. Haga clic en **Guardar y cerrar**.

   >[!NOTE]
   >
   >Utilice ContextHub y la ruta de segmentos, donde guardó inicialmente las configuraciones y segmentos de Context Hub.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Desplácese y seleccione **DataDrivenRetail** de **DataDrivenAssets** > **Canales** y haga clic en **Editar** de la barra de acciones. Arrastre y suelte los recursos en el editor de canales.

   >[!NOTE]
   >
   >Si ha configurado todo correctamente, verá lo siguiente **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Clic **Segmentación**.

1. Seleccionar **Marca** y el **Actividad** en el menú desplegable y haga clic en **Iniciar segmentación**.

### Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para el proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

1. **[Activación segmentada de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**
