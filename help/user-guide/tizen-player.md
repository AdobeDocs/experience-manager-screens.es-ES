---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
translation-type: tm+mt
source-git-commit: c1e7187ad3841cde08377d6daf700885d17706ba
workflow-type: tm+mt
source-wordcount: '691'
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

Siga los pasos a continuación para inscribir el dispositivo Tizen en el servicio de administración remota de Samsung (RMS) y configurar de forma remota el iniciador de URL:

>[!NOTE]
>Compruebe la configuración de red y el monitor.

1. Vaya a **Menú** -> **Red** -> **Configuración de red del servidor** y pulse **Intro**.

   >[!NOTE]
   >Compruebe que la pantalla está configurada para reproducir mediante el iniciador de URL.

1. Vaya a Dirección del servidor, escriba en el acceso a la URL de MagicInfo y pulse Listo.

1. Configurar TLS para usar o no usar según el caso
   1. Vaya al puerto y seleccione el número de puerto en el servidor.
   1. Pulse Guardar cuando las opciones estén listas.

1. Vaya a la ficha Dispositivo una vez que haya iniciado sesión en MIS
   1. Busque el dispositivo que acaba de configurar mirando la dirección IP o su dirección Mac.
   1. Una vez encontrado el dispositivo, haga clic en la casilla de verificación y seleccione Aprobar.

1. Una vez que se haya hecho clic en el botón Aprobado, aparecerá la siguiente ventana emergente
   1. Rellene la información requerida
   1. seleccionar un grupo de dispositivos
   1. Haga clic en el botón Aceptar para finalizar el proceso de aprobación.

1. Una vez aprobado el dispositivo, debe aparecer como sigue en la Lista del dispositivo.
   1. Haga clic en el botón Información ubicado en el cuadro &quot;i&quot; del dispositivo

1. La ventana emergente Información del dispositivo aparecerá como sigue y haga clic en el botón Editar.

1. Edite las opciones de Dispositivo y seleccione la ficha **Configuración**.

1. Vaya a la sección **Iniciador de URL** e introduzca la dirección URL que aloja el wgt y `SSSP config file` para instalar una aplicación `SSSP`, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Haga clic en **Guardar** para que los cambios surtan efecto en la pantalla de visualización.




