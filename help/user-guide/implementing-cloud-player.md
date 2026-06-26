---
title: Implementación de Cloud Player
description: Obtenga información acerca de la implementación de Cloud Player.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
TQID: https://experienceleague.adobe.com/cqLg9YgSbzZMZ9q0C1ZheiZ-e3cN38EI69hL-l7Tgeg
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 955
ht-degree: 0%

---

# Implementación de Cloud Player {#implementing-cloud-player}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Tradicionalmente, AEM Screens ha ofrecido distintas aplicaciones de reproductor nativo para diversas plataformas, incluidas ChromeOS, Windows, Android™ y `Tizen`. Sin embargo, en respuesta a la evolución de las necesidades de los usuarios, Adobe ha introducido una solución innovadora: AEM Screens Cloud Player.

Cloud Player representa una desviación significativa con respecto a las aplicaciones nativas anteriores de Adobe. Es una aplicación web progresiva (PWA), alojada en un servidor. Este enfoque transformador potencia a los clientes con un reproductor independiente de la plataforma que se ejecuta directamente dentro de un explorador web.

Acceder a Cloud Player es tan fácil como visitar `https://player.adobescreens.com`. Los usuarios pueden instalarlo en su dispositivo, independientemente de la plataforma, y disfrutar de experiencias de señalización digital sin problemas. La compatibilidad de Cloud Player depende de la presencia de un navegador moderno compatible con PWA, lo que garantiza un rendimiento coherente en varios dispositivos. Despídete de las actualizaciones manuales y saluda a un reproductor que automáticamente ofrece correcciones y funciones, lo que te garantiza que siempre tendrás las últimas funciones al alcance de tu mano. Este cambio a un reproductor en la nube basado en PWA marca una emocionante evolución en las ofertas de publicidad dinámica de Adobe, por lo que es más accesible, versátil y fácil de usar que nunca.

En esta sección se describe cómo implementar Cloud Player.

>[!NOTE]
>
>La compatibilidad de Cloud Player requiere un navegador moderno compatible con PWA para garantizar un rendimiento coherente en varios dispositivos.

## Instalación de Cloud Player {#installing-cloud-player}

La instalación de Cloud Player puede variar en diferentes plataformas. En general, cualquier plataforma que tenga un explorador moderno puede ejecutar la aplicación del reproductor en la nube siguiendo estos pasos:

1. Abra el explorador e introduzca la [URL del reproductor en la nube](https://player.adobescreens.com/content/dam/universal-player/firmware.html) en la barra de direcciones.
1. El explorador comprueba si Cloud Player se puede instalar y, a continuación, muestra un icono de instalación en la barra de direcciones.

   ![imagen](/help/user-guide/assets/cloud-player-install.png)

1. Haga clic en el icono Instalar y en el botón Instalar del cuadro de diálogo de confirmación. Cloud Player se instala como una aplicación independiente en el dispositivo y se puede iniciar con un icono.

>[!NOTE]
>
>### Opción de instalación de Cloud Player {#cloud-player-install-option}
>
>1. La opción de instalación para un PWA también se conoce como &quot;Añadir a la pantalla de inicio&quot; o función A2HS. La compatibilidad para instalar PWA desde la web varía según el explorador y la plataforma.
>1. Cada navegador tiene diferentes criterios para comprobar si la aplicación de PWA se puede instalar o no. Generalmente, el explorador puede comprobar (más detalles aquí):
>
>    * Si la aplicación tiene un archivo json de manifiesto con las claves mínimas requeridas para instalar la aplicación en la plataforma, es decir, nombre, iconos, start_url, mostrar
>    * Si la aplicación tiene un archivo de trabajo de servicio con un detector de eventos de captura
>    * La aplicación debe proporcionarse a través de https
>
>1. La opción de instalación puede estar visible en diferentes ubicaciones en diferentes exploradores y tipos de dispositivos. Algunos exploradores pueden ocultar el icono de instalación en la barra de menús de opciones.

## Aprovisionamiento masivo de Cloud Player {#bulk-provisioning}

Para realizar el aprovisionamiento masivo del reproductor en la nube en varios dispositivos:

1. Elija una solución de MDM que admita la ejecución de un explorador con una dirección URL en modo quiosco.
1. Puede aplicar las mismas configuraciones a todos los dispositivos siguiendo estos pasos:

   1. Aloje config.json en un servidor de forma que sea accesible como: `https://<config_server_host>/config.json`
   1. Para instalar el reproductor en la nube y aplicar las configuraciones alojadas, utilice la URL del reproductor en la nube como: `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. La aplicación Cloud Player busca config.json en la raíz de &lt;config_server_host> y, a continuación, analiza config.json para obtener las configuraciones personalizadas y aplicarlas.
   1. Estas configuraciones se aplican a cada recarga del reproductor.

## Aprovisionamiento masivo en el sistema operativo Chrome {#bulk-provisioning-chrome}

Obtenga más información sobre el aprovisionamiento masivo en el sistema operativo Chrome. Ver [Instalar Cloud Player en el SO Chrome](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/chromeos-install-cloud-player). <!-- `https://www.adobe.com/go/aem_screens_cloud_player_en` -->

## Configuración necesaria en instancias de AEM {#bulk-provisioning-config-aem}

En función del tipo de instancia de AEM, haga clic en una de las siguientes guías para habilitar CORS de AEM y Cloud Player:

* [AEM local/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams) <!-- `https://www.adobe.com/go/aem_screens_cors_ams_en` -->

* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs) <!-- `https://www.adobe.com/go/aem_screens_cors_aemaacs_en` -->


>[!NOTE]
>
>## Desaprobación de aplicaciones Chrome por Google
>
>1. Aplicaciones de Chrome en el hardware del sistema operativo Chrome:
>
>   Google ha estado desaprobando activamente las aplicaciones de Chrome en favor de las aplicaciones de PWA, con una migración planificada hasta enero de 2025. Por lo tanto, la aplicación del reproductor de AEM Screens en el sistema operativo Chrome deja de funcionar en función de la cronología compartida. Adobe insta a los usuarios que actualmente utilizan el Reproductor de Chrome en producción a que planifiquen la transición al Reproductor de Screens Cloud.
>
>1. Chrome Extension Player en Mac, Windows y Linux®:
>
>   Debido al proceso de desaprobación de Google, a partir de la versión 114 de Google Chrome, el reproductor de extensiones de Screens Chrome ya no es compatible. Adobe recomienda realizar la transición a su reproductor en la nube de Screens para todos los requisitos de desarrollo y prueba.

## Compatibilidad sin conexión con la recuperación de contenido externo {#offline-support}

En varios casos de uso, los canales pueden requerir la recuperación de contenido de una fuente externa (por ejemplo, widgets meteorológicos o aplicaciones de una sola página integradas de Commerce) que no puede proporcionar soporte sin conexión de forma inherente. Para habilitar la funcionalidad sin conexión para estos casos de uso específicos, Cloud Player ofrece compatibilidad con el encabezado personalizado.

Cloud Player utiliza una estrategia de caché de Network First, lo que significa que intenta recuperar contenido de la red (y actualizar la caché con la última versión) y volver al contenido almacenado en caché si está disponible. Para implementar la compatibilidad sin conexión para esta recuperación de contenido, el encabezado personalizado debe incluirse en la solicitud. A continuación, la solicitud con el encabezado personalizado se almacena en caché en el reproductor, lo que facilita el acceso sin conexión al contenido y mantiene la estrategia de caché de Network First.

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## Comentarios

Adobe valora sus comentarios. Comparta sus ideas con nosotros a través de este [formulario](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).

