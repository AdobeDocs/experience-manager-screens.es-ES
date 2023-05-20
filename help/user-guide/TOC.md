---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Ayuda de Adobe Experience Manager Screens
breadcrumb-title: Guía de AEM Screens
user-guide-description: Aprenda a utilizar una solución de señalización digital que le permita publicar interacciones y experiencias digitales dinámicas e interactivas.
feature-set: Experience Manager Screens
source-git-commit: 9d8b336c12d5e44beb831ba41f3df5031a6ca32d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 14%

---


# Guía del usuario de AEM Screens {#user-guide}

+ [Introducción a Screens](aem-screens-introduction.md)
+ Información general y guía de KickStart {#overview}
   + [Guía de KickStart](kickstart-for-aem-screens.md)
   + [Guía de prácticas recomendadas de Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/using/about-guide.html?lang=es)
   + [Términos clave](screens-glossary.md)
+ Conceptos básicos de red de publicidad dinámica {#digital-signage-network}
   + [Parte 1: Funciones y responsabilidades del proyecto](project-roles-responsibilities.md)
   + [Parte 2: Consideraciones a medida que los proyectos se amplían](project-considerations.md)
   + [Parte 3: Pruebas, POC, programas piloto y despliegues](testing-pocs-pilots-rollouts.md)
   + [Parte 4: Administración e implementación de proyectos](project-management-and-deployment.md)
   + [Parte 5: Consideraciones de soporte](support-considerations.md)
+ Configuración y administración {#administering}
   + [Configuraciones del servidor de Screens](configuring-screens-introduction.md)
   + [Configuración de Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Instalación del reproductor de Screens](installing-screens-player.md)
   + [Conexión del reproductor de Screens](working-with-screens-player.md)
   + [Registro de dispositivos](device-registration.md)
   + [Configuración de ACL](setting-up-acls.md)
   + [Lista de comprobación de seguridad de AEM Screens](security-checklist.md)
   + [Transición de ContentSync a SmartSync](smartsync.md)
   + [Nuevo importador de proyectos desde archivo](project-importer.md)
   + [Duplicación de Déclencheur de datos en servidores de publicación](replicating-data-triggers.md)
   + [Configuración de agentes de replicación de Screens](configure-screens-replication.md)
   + Consideraciones específicas del cliente {#installing-client}
      + [Reproductor de Chrome OS](implementing-chrome-os-player.md)
      + [Uso del reproductor Chrome como extensión para la resolución de problemas](using-chrome-player-as-an-extension.md)
      + [Reproductor de Android](implementing-android-player.md)
      + [Reproductor de Windows](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [Registro automático de reproductores](auto-registration-players.md)
      + [Uso del mando a distancia](implementing-remote-control.md)
   + Publicación de autor {#author-publish}
      + [Información general sobre la arquitectura de creación y publicación](author-publish-architecture-overview.md)
      + [Configuración de autor y publicación](author-and-publish.md)
   + Integración de Analytics con AEM Screens {#analytics-integration}
      + [Integración de Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configuración de Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Creación y ejemplos de casos de uso {#authoring}
   + Configuración de un proyecto de Screens {#setting-up-projects}
      + [Creación y administración de proyectos](creating-a-screens-project.md)
      + [Creación y administración de canales](managing-channels.md)
      + [Creación y administración de pantallas](managing-displays.md)
      + [Creación y administración de ubicaciones](managing-locations.md)
      + [Creación y administración de programas](managing-schedules.md)
      + [Administración de dispositivos](managing-devices.md)
      + Asignación de canales {#assigning-channels}
         + [Asignación de canales](channel-assignment-latest-fp.md)
         + [Asignación de canales: paquetes de funciones de AEM Screens anteriores](channel-assignment.md)
   + Uso de funciones de producto de código {#product-features}
      + [Superposición de texto](text-overlay.md)
      + [Actualización sin conexión masiva](bulk-offline-update.md)
      + [Servicio de notificaciones de AEM Screens](screens-notifications-service.md)
      + [Uso de fragmentos de experiencias](experience-fragments-in-screens.md)
      + [Activación de nivel de recurso](asset-level-scheduling.md)
      + [Activación de nivel de canal](channel-level-activation.md)
      + [Creación y administración de una Live Copy](managing-livecopy.md)
      + [Creación de un flujo de trabajo de relleno de vídeo](creating-a-video-padding-workflow.md)
      + [Adición de componentes a un canal](adding-components-to-a-channel.md)
      + [Secuencias incrustadas](embedded-sequences.md)
      + [Diseño de varias zonas](multi-zone-layout-aem-screens.md)
      + [Representaciones de vídeo](generating-renditions.md)
      + [Secuencia integrada dinámica](dynamic-embedded-sequences.md)
      + [Duración de reproducción masiva de imágenes a nivel de canal](channel-level-image-playback.md)
      + [Sincronización de comandos](using-command-sync.md)
      + [Creación con Déclencheur de datos](authoring-data-triggers.md)
      + [Reconocimiento de voz](voice-recognition.md)
      + [Informe de asignación de contenido](content-assignment-report.md)
      + [Compatibilidad con miniaturas para vídeos](thumbnail-support.md)
      + [Uso de representaciones adaptables en AEM Screens](using-adaptive-renditions.md)
   + Administración de actualizaciones de contenido {#content-updates}
      + [Actualización de contenido bajo demanda](on-demand-content.md)
      + [Actualización de contenido como servicio](content-update-as-a-service.md)
      + [Actualización de contenido mediante Screens Launch](launches.md)
   + Ejemplos de casos de uso {#use-case-examples}
      + [Canales de emergencia](emergency-channel.md)
      + [Activación de temperatura del centro de viajes](local-temperature-activation.md)
      + [Activación de reserva de hospitalidad](hospitality-reservation-activation.md)
      + [Activación segmentada de inventario comercial](retail-inventory-activation.md)
      + [Aplicación de transiciones](applying-transitions.md)
      + [Transiciones de varias zonas a una sola zona](multizone-to-singlezone.md)
      + [Canal de adquisición de un solo uso](single-use-takeover-channel.md)
      + [Canal de aceptación de uso permanente](perpetual-takeover-channel.md)
+ Recursos para desarrolladores y API {#developing}
   + [API de REST](rest-api.md)
   + [Desarrollo de un componente personalizado para AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canales sin conexión](offline-channels.md)
   + [Ampliación de un componente de AEM Screens](extending-component-tutorial-develop.md)
   + [Creación de componentes](creating-components.md)
   + [AEM SPA Incrustación de una aplicación REACT mediante el Editor de de trabajo e integración con AEM Screens Analytics](embedding-react-app.md)
   + [Configuración de ContextHub en AEM Screens](configuring-context-hub.md)
   + [Crear plantillas personalizadas para diseños de varias zonas](creating-custom-templates-multizone-layouts.md)
   + [Aplicación de estilo y marca personalizados a las superposiciones de texto](custom-branding-text-overlays.md)
   + [Representaciones adaptables: Información general de arquitectura y configuraciones](/help/user-guide/adaptive-renditions.md)
+ Resolución de problemas y preguntas frecuentes {#troubleshooting}
   + [Preguntas frecuentes sobre AEM Screens](aem-screens-faqs.md)
   + [Solución de problemas del Centro de control de dispositivos](monitoring-screens.md)
   + [Configuración de reproducción de vídeo](troubleshoot-videos.md)
+ Notas de la versión {#release-notes}
   + [Notas de la versión del paquete de funciones 202204](release-notes-fp-202204.md)
   + [Notas de la versión del paquete de funciones 202203](release-notes-fp-202203.md)
   + [Notas de la versión del paquete de funciones 202112](release-notes-fp-202112.md)
   + [Notas de la versión del paquete de funciones 202109](release-notes-fp-202109.md)
   + [Notas de la versión del paquete de funciones 202105](release-notes-fp-202105.md)
   + [Notas de la versión del paquete de funciones 202103](release-notes-fp-202103.md)
   + [Notas de la versión del paquete de funciones 202011](release-notes-fp-202011.md)
   + [Notas de la versión del paquete de funciones 202008](release-notes-fp-202008.md)
   + [Notas de la versión del paquete de funciones 202004](release-notes-fp-202004.md)
   + [Notas de la versión del paquete de funciones 202001](release-notes-fp-202001.md)
   + [Notas de la versión del paquete de funciones 201909](release-notes-fp-201909.md)
   + [Notas de la versión del paquete de funciones 201907](release-notes-fp-201907.md)
   + [Notas de la versión del paquete de funciones 201905](screens-release-notes-fp-201905.md)
   + [Notas de la versión del paquete de funciones 201812](release-notes-fp-201812.md)
   + [Notas de la versión del paquete de funciones 201809](screens-release-notes.md)
