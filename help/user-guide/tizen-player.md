---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
translation-type: tm+mt
source-git-commit: baefade9fa013bc77ed1f112d0ad2098c992dde5
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Implementación de Tizen Player {#tizen-player}

## Instalación de Tizen Player {#installing-tizen-player}

Siga los pasos a continuación para implementar Tizen Player para AEM Screens:

1. Vaya a la página de descargas [**del reproductor**](https://download.macromedia.com/screens/) AEM 6.5 para descargar Tizen Player.

1. Instale el archivo Tizen player (.zip) desde el equipo local.

1. Obtenga la dirección IP de su equipo local.

   >[!NOTE]
   >En el Terminal del equipo, escriba los siguientes comandos para:
   >**Mac** use, comando `ifconfig`
   >**Windows**, usar comando `ipconfig`

1. Desde Terminal, vaya al mismo directorio de la carpeta del instalador descomprimido y compruebe si el host local está funcionando.

   >[!NOTE]
   >Para **Mac**, escriba `http://localhost` y verifique si el `http` servidor se está ejecutando.

1. El reproductor Tizen descargará el instalador desde el servidor local.

1. Copie los dos archivos extraídos `AEMScreensPlayer.wgt` y `sssp_config.xml` en `/Library/WebServer/Documents`.

### Actualizaciones de configuración del dispositivo SamSung {#config-updates}

Siga los pasos a continuación en el dispositivo Samsung para completar la instalación del reproductor de AEM Screens en el dispositivo:

1. Haga clic en el botón **Inicio** desde el control remoto de Samsung.
1. Seleccione **Iniciador** de URL en la **Configuración**.
1. Seleccione **Remoto** en el modo de desarrollador.
1. Instale Web App e introduzca la dirección IP de su equipo.
AEM Screens Player debe instalarse automáticamente en el dispositivo Samsung.


