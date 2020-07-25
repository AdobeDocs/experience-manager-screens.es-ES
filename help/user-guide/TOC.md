---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Ayuda de las pantallas de Adobe Experience Manager
user-guide-description: Learn to use AEM Screens to publish interactive digital experiences involving different types of screens.
translation-type: tm+mt
source-git-commit: 5f3fc27ae60de86ae40ba71a67cdc6ff43dea4fb
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 13%

---


# Guía del usuario de AEM Screens {#user-guide}

+ [Introducción a las pantallas](aem-screens-introduction.md)
+ Información general y guía de inicio rápido {#overview}
   + [Guía de inicio rápido](kickstart-for-aem-screens.md)
   + [Guía de prácticas recomendadas de pantallas](https://docs.adobe.com/content/help/es-ES/experience-manager-screens/using/about-guide.html)
   + [Términos clave](screens-glossary.md)
+ Conceptos básicos de la red de publicidad dinámica {#digital-signage-network}
   + [Parte 1: Funciones y responsabilidades del proyecto](project-roles-responsibilities.md)
   + [Parte 2: Consideraciones a medida que se programan los proyectos](project-considerations.md)
   + [Parte 3: Pruebas, puntos de interés, programas piloto y lanzamientos](testing-pocs-pilots-rollouts.md)
   + [Parte 4: Administración e implementación de proyectos](project-management-and-deployment.md)
   + [Parte 5: Consideraciones de soporte](support-considerations.md)
+ Configuración y administración {#administering}
   + [Configuraciones del servidor de pantallas](configuring-screens-introduction.md)
   + [Configuración de configuraciones de Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Instalación de Screens Player](installing-screens-player.md)
   + [Conexión del reproductor de pantallas](working-with-screens-player.md)
   + [Registro de dispositivos](device-registration.md)
   + [Configuración de ACL](setting-up-acls.md)
   + [Lista de comprobación de seguridad de AEM Screens](security-checklist.md)
   + [Transición de ContentSync a SmartSync](smartsync.md)
   + [Nuevo importador de proyectos a partir de archivo](project-importer.md)
   + [Replicar activadores de datos en servidores de publicación](replicating-data-triggers.md)
   + Consideraciones específicas del cliente {#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [Uso de Chrome Player como extensión para la resolución de problemas](using-chrome-player-as-an-extension.md)
      + [Android Player](implementing-android-player.md)
      + [Reproductor de Windows](implementing-windows-player.md)
   + Author Publish {#author-publish}
      + [Descripción general de la arquitectura de creación y publicación](author-publish-architecture-overview.md)
      + [Configuración del autor y la publicación](author-and-publish.md)
   + Integración de Analytics con AEM Screens {#analytics-integration}
      + [Integración de Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configuración de Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Creación y ejemplos de casos de uso {#authoring}
   + Configuración de un proyecto de pantallas {#setting-up-projects}
      + [Creación y administración de proyectos](creating-a-screens-project.md)
      + [Crear y administrar canales](managing-channels.md)
      + [Crear y administrar visualizaciones](managing-displays.md)
      + [Crear y administrar ubicaciones](managing-locations.md)
      + [Crear y administrar programaciones](managing-schedules.md)
      + [Administración de dispositivos](managing-devices.md)
      + [Asignación de canales](channel-assignment.md)
   + Uso de las funciones principales del producto {#product-features}
      + [Superposición de texto](text-overlay.md)
      + [Actualización masiva sin conexión](bulk-offline-update.md)
      + [Servicio de notificaciones de AEM Screens](screens-notifications-service.md)
      + [Uso de fragmentos de experiencias](experience-fragments-in-screens.md)
      + [Activación de nivel de recurso](asset-level-scheduling.md)
      + [Activación de nivel de Canal](channel-level-activation.md)
      + [Creación y administración de Live Copy](managing-livecopy.md)
      + [Creación de un flujo de trabajo de relleno de vídeo](creating-a-video-padding-workflow.md)
      + [Añadir componentes a un canal](adding-components-to-a-channel.md)
      + [Secuencias integradas](embedded-sequences.md)
      + [Diseño de varias zonas](multi-zone-layout-aem-screens.md)
      + [Representaciones de vídeo](generating-renditions.md)
      + [Secuencia integrada dinámica](dynamic-embedded-sequences.md)
      + [Duración de la reproducción masiva de imágenes en el nivel de Canal](channel-level-image-playback.md)
      + [Sincronización de comandos](using-command-sync.md)
      + [Creación con activadores de datos](authoring-data-triggers.md)
   + Administración de actualizaciones de contenido {#content-updates}
      + [Actualización de contenido bajo demanda](on-demand-content.md)
      + [Actualización del contenido como servicio](content-update-as-a-service.md)
      + [Actualización de contenido con Screens Launch](launches.md)
   + Ejemplos de casos de uso {#use-case-examples}
      + [Canales de emergencia](emergency-channel.md)
      + [Activación de la temperatura del centro de viajes](local-temperature-activation.md)
      + [Activación de reservación de hospitalidad](hospitality-reservation-activation.md)
      + [Activación de objetivo de inventario comercial](retail-inventory-activation.md)
      + [Aplicación de Transiciones](applying-transitions.md)
      + [Transiciones de zonas múltiples a zonas únicas](multizone-to-singlezone.md)
      + [Canal TakeOver de un solo uso](single-use-takeover-channel.md)
      + [Uso perpetuo Canal de TakeOver](perpetual-takeover-channel.md)
+ Recursos para desarrolladores y API {#developing}
   + [API de REST](rest-api.md)
   + [Desarrollo de un componente personalizado para AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canales sin conexión](offline-channels.md)
   + [Ampliación del componente AEM Screens](extending-component-tutorial-develop.md)
   + [Creación de componentes](creating-components.md)
   + [Incrustación de una aplicación REACT mediante el Editor de AEM SPA e integración con AEM Screens Analytics](embedding-react-app.md)
   + [Configuración de ContextHub en AEM Screens](configuring-context-hub.md)
   + [Creación de plantillas personalizadas para diseños de varias zonas](creating-custom-templates-multizone-layouts.md)
   + [Aplicación de personalización de marca y estilo para superposiciones de texto](custom-branding-text-overlays.md)
+ Resolución de problemas y preguntas más frecuentes {#troubleshooting}
   + [Preguntas más frecuentes sobre AEM Screens](aem-screens-faqs.md)
   + [Resolución de problemas del centro de control de dispositivos](monitoring-screens.md)
   + [Configuración de reproducción de vídeo](troubleshoot-videos.md)
+ Notas de la versión {#release-notes}
   + [Notas de la versión de Feature Pack 2004](release-notes-fp-202004.md)
   + [Notas de la versión de Feature Pack 2001](release-notes-fp-202001.md)
   + [Notas de la versión de Feature Pack 201909](release-notes-fp-201909.md)
   + [Notas de la versión de Feature Pack 201907](release-notes-fp-201907.md)
   + [Notas de la versión de Feature Pack 201905](screens-release-notes-fp-201905.md)
   + [Notas de la versión de Feature Pack 201812](release-notes-fp-201812.md)
   + [Notas de la versión de Feature Pack 201809](screens-release-notes.md)
