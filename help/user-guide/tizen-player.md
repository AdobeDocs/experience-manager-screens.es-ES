---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
translation-type: tm+mt
source-git-commit: 5275a4ff79404e946d5aa0806fc705ab3bce2fcd
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Implementación de Tizen Player {#tizen-player}

## Instalación de Tizen Player {#installing-tizen-player}

Siga los pasos a continuación para implementar Tizen Player para AEM Screens:

1. Vaya a la página de descargas [**del reproductor**](https://download.macromedia.com/screens/) AEM 6.5 para descargar Tizen Player.

1. Instale el archivo Tizen player (.zip) desde el equipo local.

## Configuración del servidor local y extracción de archivos comprimidos {#setting-local-server}

Siga los pasos a continuación para configurar el servidor local y copiar los archivos extraídos:

1. Obtenga la dirección IP de su equipo local.

   >[!NOTE]
   >Puede obtener la dirección IP desde el terminal del equipo mediante los siguientes comandos:
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. Desde Terminal, vaya al mismo directorio de la carpeta del instalador descomprimido y compruebe si el host local está funcionando.

   >[!NOTE]
   >Para **Mac**, escriba `http://localhost` y verifique si el `http` servidor se está ejecutando.

1. El reproductor Tizen descargará el instalador desde el servidor local.

1. Copie los dos archivos extraídos `AEMScreensPlayer.wgt` y `sssp_config.xml` en `/Library/WebServer/Documents`.

### Configuración de actualizaciones en el dispositivo Samsung {#config-updates}

Siga los pasos a continuación en el dispositivo Samsung para completar la instalación del reproductor de AEM Screens en el dispositivo:

1. Vaya a su dispositivo Samsung y señale a su servidor local host.
1. Seleccione Configuración **del iniciador de** URL e introduzca la dirección IP de su servidor localhost.
1. Instalación de la aplicación web.
1. Seleccione **Remoto** en el modo **de desarrollador**.
1. El Reproductor de AEM Screens ahora debe realizar el inicio automático de la instalación en el dispositivo Samsung.


