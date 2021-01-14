---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
translation-type: tm+mt
source-git-commit: 1ec3e3541755550f719dbe53e83326d9796de14f
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---


# Implementación de Tizen Player {#tizen-player}

## Instalación de Tizen Player {#installing-tizen-player}

Siga los pasos a continuación para implementar Tizen Player para AEM Screens:

1. Vaya a la página [Descargas del reproductor de AEM 6.5](https://download.macromedia.com/screens/) para descargar Tizen Player.

1. Instale el archivo Tizen player *(.zip)* desde el equipo local.

## Configuración del servidor local y extracción de archivos comprimidos {#setting-local-server}

Siga los pasos a continuación para configurar el servidor local y copiar los archivos extraídos:

1. Obtenga la dirección IP de su equipo local.
   >[!NOTE]
   >Revise la documentación oficial para saber cómo habilitar el servidor local en su plataforma.

1. Desde Terminal, vaya al mismo directorio de la carpeta del instalador descomprimido y compruebe si el host local está funcionando.

1. El reproductor Tizen descargará el instalador desde el servidor local.

1. Copie los dos archivos extraídos como `AEMScreensPlayer.wgt` y `sssp_config.xml` en el directorio raíz del servidor Web Apache local.

   >[!NOTE]
   >La `AEMScreensPlayer.wgt`es la aplicación real del reproductor Tizen y `sssp_config.xml` contiene información sobre este mapa que le ayuda a instalarlo en el dispositivo Tizen.

### Configuración de actualizaciones en el dispositivo Samsung {#config-updates}

Siga los pasos a continuación en el dispositivo Samsung para completar la instalación del reproductor de AEM Screens en el dispositivo:

1. Navegue hasta su dispositivo Samsung y encienda.

1. Haga clic en el botón **MENU** del mando a distancia del dispositivo y desplácese hacia abajo hasta **System** desde la barra de navegación izquierda.

1. Desplácese hacia abajo y seleccione la opción **Reproducir mediante el iniciador de URL**.
   ![image](/help/user-guide/assets/tizen/url-launcher.png)

1. Pulse el botón **Inicio** desde el mando a distancia.

1. Introduzca la dirección IP de su servidor localhost.

1. Seleccione **Remoto** en el **Modo de desarrollador**.

1. Haga clic en el botón **Inicio** desde el dispositivo remoto y seleccione **Iniciador de URL**.

1. Ahora, AEM Screens Player debe instalar e iniciar automáticamente en el dispositivo Samsung.

## Aprovisionamiento masivo de Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Puede ser un tedioso esfuerzo introducir manualmente la dirección de su servidor AEM en la interfaz de usuario de administración de todos y cada uno de los dispositivos para un gran número de dispositivos. Se recomienda utilizar la solución Administración remota de Samsung (RMS) para implementar y administrar la solución. Consulte [Incorporación del dispositivo Tizen al servicio de administración remota de Samsung (RMS)](#enroll-tizen-device-rm) para obtener más detalles.

Siga los pasos que se describen a continuación para aprovisionar la aplicación de forma masiva para que apunte a la instancia de creación de AEM cuando se inicie:

1. Descargue e instale el [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Abra el archivo `wgt` con Tizen studio.
1. Abra el archivo `firmware-platform.js`, busque `DEFAULT_PREFERENCES` y cambie la dirección URL del servidor a la dirección URL del autor AEM y guárdela.
1. Cree el nuevo archivo `wgt`.

   >[!NOTE]
   >Es posible que deba crear o configurar un certificado de firma.

1. Implemente este nuevo archivo RMS `wgt` y cuando el reproductor se inicie, deberá apuntar automáticamente a su servidor para que no necesite introducirlo manualmente en todos los dispositivos.

### Incorporación del dispositivo Tizen al servicio de administración remota de Samsung (RMS) {#enroll-tizen-device-rms}

Siga los pasos a continuación para inscribir el dispositivo Tizen en el servicio de administración remota de Samsung (RMS) y configurar el iniciador de URL de forma remota:

>[!NOTE]
>Compruebe la configuración de red y el monitor.

1. Pulse Menú en el mando a distancia y vaya a Sistema y, a continuación, pulse Intro en Reproducir vía.

   >[!NOTE]
   >Verifique que la pantalla esté configurada para reproducir mediante el iniciador de URL
1. Vaya a **Menú** -> **Red** -> **Configuración de red del servidor** y pulse **Intro**.

1. Vaya a Dirección del servidor, escriba en el acceso a la URL de MagicInfo y pulse Listo.

1. Vaya a la ficha Dispositivo una vez que haya iniciado sesión en MIS
1. Busque el dispositivo que acaba de configurar mirando la dirección IP o su dirección Mac.
1. Una vez encontrado el dispositivo, haga clic en la casilla de verificación y seleccione Aprobar
1. Verifique que la pantalla esté configurada para reproducir mediante el iniciador de URL
1. Pulse Menú en el mando a distancia y vaya a Sistema y, a continuación, pulse Intro en Reproducir mediante
1. Vaya al menú -> Red -> Configuración de red del servidor y pulse Intro
1. Vaya a Dirección del servidor y escriba en la dirección URL de MagicInfo el acceso y pulse Listo
1. Configurar TLS para usar o no usar según el caso
1. Vaya al puerto y seleccione el número de puerto en el servidor.
1. Pulse Guardar cuando las opciones estén listas.



