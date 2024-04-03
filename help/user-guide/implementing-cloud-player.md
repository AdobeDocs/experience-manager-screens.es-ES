---
title: Implementación de Cloud Player
seo-title: Implementing Cloud Player
description: Siga esta página para obtener más información sobre la implementación de Cloud Player.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 5b64ab8eea274aa85c61311d34b1ce065a5ba601
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Implementación de Cloud Player  {#implementing-cloud-player}

Tradicionalmente, AEM Screens ha ofrecido distintas aplicaciones de reproductor nativas para varias plataformas, incluidas ChromeOS, Windows, Android y Tizen. Sin embargo, en respuesta a la evolución de las necesidades de nuestros usuarios, hemos introducido una solución innovadora: AEM Screens Cloud Player.

Cloud Player representa una desviación significativa con respecto a nuestras aplicaciones nativas anteriores. Es una aplicación Progressive Web App (PWA), alojada en un servidor. Este enfoque transformador potencia a nuestros clientes con un reproductor independiente de la plataforma que se ejecuta directamente dentro de un explorador web.

Acceder a Cloud Player es tan sencillo como visitar https://player.adobescreens.com. Los usuarios pueden instalarlo en su dispositivo, independientemente de la plataforma, y disfrutar de experiencias de señalización digital sin problemas. La compatibilidad de Cloud Player depende de la presencia de un navegador moderno compatible con el PWA, lo que garantiza un rendimiento coherente en varios dispositivos. Despídete de las actualizaciones manuales y saluda a un reproductor que automáticamente ofrece correcciones y funciones, lo que te garantiza que siempre tendrás las últimas funciones al alcance de tu mano. Este cambio a un Cloud Player basado en PWA marca una interesante evolución en nuestras ofertas de publicidad dinámica, por lo que es más accesible, versátil y fácil de usar que nunca.

En esta sección se describe cómo implementar Cloud Player.

>[!NOTE]
>
>La compatibilidad de Cloud Player requiere un navegador moderno compatible con el PWA para garantizar un rendimiento coherente en varios dispositivos.

## Instalación de Cloud Player {#installing-cloud-player}

La instalación de Cloud Player puede variar en diferentes plataformas. En general, cualquier plataforma que tenga un explorador moderno puede ejecutar la aplicación del reproductor en la nube siguiendo estos pasos:

1. Abra el explorador e introduzca la variable [URL del reproductor en la nube](https://player.adobescreens.com) en la barra de direcciones.
1. El explorador comprueba si el reproductor en la nube es instalable y, a continuación, muestra un icono de instalación en la barra de direcciones.

   ![imagen](/help/user-guide/assets/cloud-player-install.png)

1. Haga clic en el icono de instalación e instale el botón en el cuadro de diálogo de confirmación. Cloud Player se instalará como una aplicación independiente en su dispositivo y se puede iniciar con un icono.

>[!NOTE]
>
>### Opción de instalación de Cloud Player {#cloud-player-install-option}
>
1. La opción de instalación de un PWA también se conoce como &quot;Añadir a la pantalla de inicio&quot; o función A2HS.  La compatibilidad para instalar PWA desde la web varía según el explorador y la plataforma.
1. Cada navegador tiene diferentes criterios para comprobar si la aplicación del PWA se puede instalar o no. Generalmente, el explorador comprueba lo siguiente (más detalles aquí):
>
* Si la aplicación tiene un archivo json de manifiesto con las claves mínimas requeridas para instalar la aplicación en la plataforma, es decir, nombre, iconos, start_url, mostrar
* Si la aplicación tiene un archivo de trabajo de servicio con un detector de eventos de captura.
* La aplicación debe proporcionarse a través de https.
>
1. La opción Instalar puede estar visible en diferentes ubicaciones de distintos exploradores y tipos de dispositivos. Algunos exploradores pueden ocultar el icono de instalación en la barra de menús de opciones.

## Aprovisionamiento masivo de Cloud Player {#bulk-provisioning}

Para realizar el aprovisionamiento masivo del reproductor en la nube en varios dispositivos:

1. Elija una solución de MDM que admita la ejecución de un explorador con una dirección URL en modo quiosco.
1. Puede aplicar las mismas configuraciones a todos los dispositivos siguiendo estos pasos:

   1. Aloje config.json en un servidor al que se pueda acceder mediante, por ejemplo: https://&lt;config_server_host>/config.json
   1. Para instalar el reproductor en la nube y aplicar las configuraciones alojadas, utilice la URL del reproductor en la nube como: https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. La aplicación Cloud Player busca config.json en la raíz de &lt;config_server_host>, analice el archivo config.json para obtener las configuraciones personalizadas y aplicarlas.
   1. Estas configuraciones se aplicarán en cada recarga del reproductor.

## Aprovisionamiento masivo en el sistema operativo Chrome {#bulk-provisioning-chrome}

Para obtener más información sobre el aprovisionamiento masivo en el sistema operativo Chrome, consulte: [Instalación de Cloud Player en el sistema operativo Chrome](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEM Configuración necesaria en instancias de {#bulk-provisioning-config-aem}

AEM AEM En función del tipo de instancia de, seleccione una de las siguientes guías para habilitar el reproductor en la nube y el reproductor en la nube CORS b/w:
* [AEM Local/AMS (en las instalaciones)](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

>[!NOTE]
>
## Degradación de aplicaciones Chrome de Google
>
1. Aplicaciones Chrome en Chrome OS Hardware:
>
Google ha estado desaprobando activamente las aplicaciones de Chrome en favor de las aplicaciones de PWA, con una migración planificada hasta enero de 2025. En consecuencia, la aplicación AEM Screens Player en Chrome OS dejará de funcionar en función de la cronología compartida. Instamos a nuestros clientes que actualmente utilizan Chrome Player en producción a que planifiquen la transición al reproductor en la nube de Screens.
>
1. Reproductor de extensiones de Chrome en Mac, Windows y Linux:
>
Debido al proceso de desaprobación de Google, a partir de la versión 114 de Google Chrome, el reproductor de extensiones de Screens Chrome ya no es compatible. Recomendamos encarecidamente la transición a nuestro reproductor Screens Cloud para todos sus requisitos de desarrollo y prueba.

## Compatibilidad sin conexión con la recuperación de contenido externo {#offline-support}

En varios casos de uso, los canales pueden requerir la recuperación de contenido de una fuente externa (por ejemplo, widgets meteorológicos o aplicaciones de una sola página integradas de Commerce) que no pueden proporcionar soporte sin conexión de forma inherente. Para habilitar la funcionalidad sin conexión para estos casos de uso específicos, Cloud Player ofrece compatibilidad con el encabezado personalizado.

Cloud Player utiliza una estrategia de caché de Network First, lo que significa que intenta recuperar contenido de la red (y actualizar la caché con la última versión) y volver al contenido almacenado en caché si está disponible. Para implementar la compatibilidad sin conexión para esta recuperación de contenido, el encabezado personalizado debe incluirse en la solicitud. Posteriormente, la solicitud con el encabezado personalizado se almacenará en caché en el reproductor, facilitando el acceso sin conexión al contenido y manteniendo al mismo tiempo la estrategia de caché de Network First.

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

¡Valoramos sus comentarios! Amablemente comparta sus pensamientos con nosotros a través de esto [formulario](https://forms.office.com/r/MQXX9JsuEd).
