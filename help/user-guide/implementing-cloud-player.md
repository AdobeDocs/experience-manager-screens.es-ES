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
source-git-commit: 718ef76b620accd7096be2e4b7ac53658cb7fce7
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Implementación de Cloud Player  {#implementing-cloud-player}

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

### Opción de instalación de Cloud Player {#cloud-player-install-option}

1. La opción de instalación de un PWA también se conoce como &quot;Añadir a la pantalla de inicio&quot; o función A2HS.  La compatibilidad para instalar PWA desde la web varía según el explorador y la plataforma.
1. Cada navegador tiene diferentes criterios para comprobar si la aplicación del PWA se puede instalar o no. Generalmente, el explorador comprueba lo siguiente (más detalles aquí):
   * Si la aplicación tiene un archivo json de manifiesto con las claves mínimas requeridas para instalar la aplicación en la plataforma, es decir, nombre, iconos, start_url, mostrar
   * Si la aplicación tiene un archivo de trabajo de servicio con un detector de eventos de captura.
   * La aplicación debe proporcionarse a través de https.
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

