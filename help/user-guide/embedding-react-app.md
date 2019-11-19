---
title: Incrustación de una aplicación REACT mediante el Editor de AEM SPA e integración con análisis de AEM Screens
seo-title: Incrustación de una aplicación REACT mediante el Editor de AEM SPA e integración con análisis de AEM Screens
description: Siga esta página para aprender a incrustar una aplicación de una sola página interactiva con REACT (o Angular) mediante el editor de AEM SPA que pueden configurar los profesionales empresariales en AEM y también cómo integrar su aplicación interactiva con Adobe Analytics sin conexión.
seo-description: Siga esta página para aprender a incrustar una aplicación de una sola página interactiva con REACT (o Angular) mediante el editor de AEM SPA que pueden configurar los profesionales empresariales en AEM y también cómo integrar su aplicación interactiva con Adobe Analytics sin conexión.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Incrustación de una aplicación REACT mediante el Editor de AEM SPA e integración con análisis de AEM Screens {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

En esta sección se describe cómo incrustar una aplicación de una sola página interactiva mediante REACT (o Angular) mediante el editor de AEM SPA que pueden configurar los profesionales empresariales en AEM y también cómo integrar la aplicación interactiva con Adobe Analytics sin conexión.

## Uso del Editor de AEM SPA {#using-the-aem-spa-editor}

Siga los pasos a continuación para utilizar el Editor de AEM SPA:

1. Clona la repo del editor de AEM SPA en [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Este arquetipo crea un proyecto mínimo de Adobe Experience Manager como punto de partida para sus propios proyectos de SPA. Las propiedades que deben proporcionarse al utilizar este arquetipo permiten asignar el nombre que desee a todas las partes de este proyecto.

1. Siga las instrucciones Léame para crear un proyecto de arquetipo de editor de AEM SPA:

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
   >Utilizamos **GroupId** como ***com.adobe.aem.screen*** y **ArtiactId** como ***Mi SPA*** de muestra (que son los valores predeterminados). Puede elegir el suyo propio según sea necesario.

1. Una vez creado el proyecto, utilice un IDE o editor de su elección e importe el proyecto Maven generado.
1. Implemente en la instancia local de AEM mediante el comando ***mvn clean install -PautoInstallPackage***.

### Edición de contenido en la aplicación REACT {#editing-content-in-the-react-app}

Para editar el contenido en la aplicación REACT:

1. Vaya a `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (reemplace el nombre del host, el puerto y el nombre del proyecto según corresponda).
1. Debería poder editar el texto que se muestra en la aplicación Hello world.

### Adición de la aplicación interactiva REACT a AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Siga los pasos a continuación para añadir la aplicación interactiva REACT a AEM Screens:

1. Cree un nuevo proyecto de AEM Screens. Consulte [Creación y administración de proyectos](creating-a-screens-project.md) para obtener más detalles.

   >[!NOTE]
   >
   >Cree un canal **de secuencia** mientras crea un canal en la carpeta **Canales** del proyecto Pantallas.
   >
   >
   >Consulte [Creación y administración de canales](managing-channels.md) para obtener más detalles.

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Edite cualquier canal de secuencia y arrastre y suelte un componente de página incrustado.

   Consulte [Adición de componentes a un canal](adding-components-to-a-channel.md) para obtener más información.

   >[!NOTE]
   >
   >Asegúrese de agregar el evento de interacción del usuario al asignar el canal a la pantalla.

1. Haga clic en **Editar** en la barra de acciones para editar las propiedades del canal de secuencia.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Arrastre y suelte el componente Página **** incrustada y seleccione la página principal en la aplicación mysamplespa, por ejemplo, ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registre un reproductor en este proyecto y debería poder ver cómo se ejecuta la aplicación interactiva en AEM Screens.

   Consulte Registro [del](device-registration.md) dispositivo para obtener información detallada sobre cómo registrar un dispositivo.

## Integración de SPA con Adobe Analytics con funciones sin conexión mediante AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Siga los pasos que se describen a continuación para integrar SPA con Adobe Analytics con funciones sin conexión mediante AEM Screens:

1. Configure Adobe Analytics en AEM Screens.

   Consulte [Configuración de Adobe Analytics con AEM Screens (configuración-adobe-analytics-aem-screen.md) para aprender a secuenciar en Adobe Analytics con AEM Screens y enviar eventos personalizados con Adobe Analytics sin conexión.

1. Edite la aplicación de reacción en el IDE/editor de su elección (especialmente el componente de texto u otro componente que desee que comience a emitir eventos).
1. En el evento click u otro evento que desee capturar para su componente, agregue la información de análisis usando el modelo de datos estándar.

   Consulte [Configuración de Adobe Analytics con](configuring-adobe-analytics-aem-screens.md)pantallas AEM para obtener más información.

1. Llame a la API de análisis de AEM Screens para guardar el evento sin conexión y enviarlo por ráfagas a Adobe Analytics.

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

