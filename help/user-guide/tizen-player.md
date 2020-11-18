---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
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
   >Revise la documentación oficial para saber cómo habilitar el servidor local en su plataforma.

1. Desde Terminal, vaya al mismo directorio de la carpeta del instalador descomprimido y compruebe si el host local está funcionando.

1. El reproductor Tizen descargará el instalador desde el servidor local.

1. Copie los dos archivos extraídos como `AEMScreensPlayer.wgt` y `sssp_config.xml` en el directorio raíz del servidor local.

### Configuración de actualizaciones en el dispositivo Samsung {#config-updates}

Siga los pasos a continuación en el dispositivo Samsung para completar la instalación del reproductor de AEM Screens en el dispositivo:

1. Vaya a su dispositivo Samsung.

1. Haga clic en el botón **Inicio** mediante el control remoto del dispositivo y seleccione Configuración **del iniciador de** URL.

1. Introduzca la dirección IP de su servidor localhost.

1. Seleccione **Remoto** en el modo **de desarrollador**.

1. Haga clic en el botón **Inicio** del dispositivo remoto y seleccione Iniciador **de** URL.

1. Ahora, AEM Screens Player debe instalar e iniciar automáticamente en el dispositivo Samsung.



