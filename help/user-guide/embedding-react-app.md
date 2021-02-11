---
title: Incrustación de una aplicación REACT mediante el Editor de SPA de AEM e integración con AEM Screens Analytics
seo-title: Incrustación de una aplicación REACT mediante el Editor de SPA de AEM e integración con AEM Screens Analytics
description: Siga esta página para aprender a incrustar una aplicación de una sola página interactiva mediante REACT (o Angular) mediante el editor de SPA AEM que pueden configurar los profesionales empresariales en AEM y también cómo integrar su aplicación interactiva con Adobe Analytics sin conexión.
seo-description: Siga esta página para aprender a incrustar una aplicación de una sola página interactiva mediante REACT (o Angular) mediante el editor de SPA AEM que pueden configurar los profesionales empresariales en AEM y también cómo integrar su aplicación interactiva con Adobe Analytics sin conexión.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---


# Incrustación de una aplicación REACT mediante el Editor de SPA de AEM e integración con AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

En esta sección se describe cómo incrustar una aplicación de una sola página interactiva mediante REACT (o Angular) mediante el editor de SPA de AEM que pueden configurar los profesionales empresariales en AEM y también cómo integrar la aplicación interactiva con Adobe Analytics sin conexión.

## Uso del Editor de SPA de AEM {#using-the-aem-spa-editor}

Siga los pasos a continuación para utilizar el Editor de SPA de AEM:

1. Clona la repo del Editor SPA de AEM en [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Este arquetipo crea un proyecto mínimo de Adobe Experience Manager como punto de partida para sus propios proyectos de SPA. Las propiedades que deben proporcionarse al utilizar este arquetipo permiten asignar el nombre que desee a todas las partes de este proyecto.

1. Siga las instrucciones Léame para crear un proyecto de arquetipo de editor de SPA AEM:

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Utilizamos el **GroupId** como ***com.adobe.aem.screen*** y el **ArtiactId** como ***Mi muestra SPA*** (que es el valor predeterminado). Puede elegir el suyo propio según sea necesario.

1. Una vez creado el proyecto, utilice un IDE o editor de su elección e importe el proyecto Maven generado.
1. Implementar en la instancia de AEM local mediante el comando ***mvn clean install -PautoInstallPackage***.

### Edición de contenido en la aplicación REACT {#editing-content-in-the-react-app}

Para editar el contenido en la aplicación REACT:

1. Vaya a `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (reemplace el nombre del host, el puerto y el nombre del proyecto según corresponda).
1. Debería poder editar el texto que se muestra en la aplicación Hello world.

### Añadir la aplicación interactiva REACT a AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Siga los pasos a continuación para añadir la aplicación interactiva REACT a AEM Screens:

1. Cree un nuevo proyecto de AEM Screens. Consulte [Creación y administración de proyectos](creating-a-screens-project.md) para obtener más detalles.

   >[!NOTE]
   >
   >Cree un **Canal de secuencia** mientras crea un canal en la carpeta **Canales** del proyecto Screens.
   >
   >
   >Consulte [Creación y administración de Canales](managing-channels.md) para obtener más detalles.

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Edite cualquier canal de secuencia y arrastre y suelte un componente de página incrustado.

   Consulte [Añadir componentes a un Canal](adding-components-to-a-channel.md) para obtener más información.

   >[!NOTE]
   >
   >Asegúrese de agregar el evento de interacción del usuario al asignar el canal a la pantalla.

1. Haga clic en **Editar** en la barra de acciones para editar las propiedades del canal de secuencia.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Arrastre y suelte el componente **Página integrada** y seleccione la página de inicio en la aplicación mysamplespa, por ejemplo, ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registre un reproductor en este proyecto y ahora debería poder ver la aplicación interactiva que se está ejecutando en AEM Screens.

   Consulte [Registro del dispositivo](device-registration.md) para obtener información detallada sobre cómo registrar un dispositivo.

## Integración del SPA con Adobe Analytics con la capacidad sin conexión a través de AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Siga los pasos a continuación para integrar la SPA con Adobe Analytics con la capacidad sin conexión a través de AEM Screens:

1. Configure Adobe Analytics en AEM Screens.

   Consulte [Configuración de Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md) para obtener información sobre cómo realizar secuenciaciones en Adobe Analytics con AEM Screens y enviar eventos personalizados mediante Adobe Analytics sin conexión.

1. Edite la aplicación de reacción en el IDE/editor de su elección (especialmente el componente de texto u otro componente que desee utilizar como inicio para emitir eventos).
1. En el evento de clic u otro evento que desee capturar para el componente, agregue la información de análisis mediante el modelo de datos estándar.

   Consulte [Configuración de Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md)s para obtener más detalles.

1. Llame a la API de AEM Screens Analytics para guardar el evento sin conexión y enviarlo por ráfagas a Adobe Analytics.

   Por ejemplo,

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >El firmware del reproductor agrega automáticamente más detalles sobre el reproductor y su entorno de tiempo de ejecución a los datos de análisis personalizados que envía. Por lo tanto, es posible que no necesite capturar detalles de dispositivos o sistemas operativos de bajo nivel a menos que sea absolutamente necesario. Solo tiene que centrarse en los datos de análisis de negocios.

