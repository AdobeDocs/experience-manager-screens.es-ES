---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
translation-type: tm+mt
source-git-commit: 092be09ec9477c9ff7561347d8f05641a90a9b40
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 0%

---


# Implementación de Tizen Player {#tizen-player}

## Instalación de Tizen Player {#installing-tizen-player}

Siga los pasos a continuación para implementar Tizen Player para AEM Screens:

1. Vaya a la página [Descargas del reproductor de AEM 6.5](https://download.macromedia.com/screens/) para descargar Tizen Player.

1. Instale el archivo Tizen player *(.zip)* desde el equipo local.

## Exención de los agentes de usuario con el problema de cookie de Samesite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta sección se aplica a Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Hay algunos motores de navegador que son incompatibles con el atributo *SameSite=None* utilizado en el token de inicio de sesión emitido por AEM 6.5 a AEM 6.7. En la mayoría de los casos, el problema se puede resolver actualizando el explorador a la versión más reciente disponible. En algunos casos, estas actualizaciones pueden no ser posibles, como con pantallas inteligentes, cuadros superiores establecidos u otros dispositivos con motores de navegación integrados.

Siga los pasos a continuación para eximir a estos clientes incompatibles al utilizar *SameSite=None*:

1. Actualice a Adobe Experience Manager (AEM) Service Pack 6.5.8.

1. Vaya a `/system/console/bundles` en AEM y haga clic en el botón `install/update`.

1. Instale el archivo jar `crx-auth-token`. Es posible que deba apagar y reiniciar AEM después de instalar este tarro porque está relacionado con la autenticación.

1. Después de reiniciar AEM vaya a `/system/console/configMgr` y busque **Controlador de autenticación de token granito de Adobe**. Establezca el valor del valor **SameSite** en **None**.

1. Debe ver una nueva opción *Agentes de usuario para quedar exentos del mismo atributo*. Rellene esto con un regex correspondiente al agente de usuario que sea(es) incompatible con el atributo *SameSite=None*.
   >[!NOTE]
   >Consulte [SameSite=None: Clientes incompatibles conocidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obtener más información. Para el reproductor Tizen utilice el regex: `(.*)Tizen (4|5)(.*)`.

1. Registre el reproductor Tizen en su instancia de AEM 6.5.5 y superior y debe registrar y mostrar el contenido normalmente.


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
   ![image](/help/user-guide/assets/tizen/rms-2.png)

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
   >![image](/help/user-guide/assets/tizen/rms-2.png)

1. Vaya a Dirección del servidor, escriba en el acceso a la URL de MagicInfo y pulse Listo.

1. Configure TLS, si es necesario. Vaya al puerto y seleccione el número de puerto en el servidor. Haga clic en **Guardar**.

1. Vaya a la ficha **Dispositivo** y busque el dispositivo que acaba de configurar. Una vez encontrado el dispositivo, haga clic en la casilla de verificación y seleccione **Aprobar**.

1. Rellene la información necesaria y seleccione un grupo de dispositivos. Haga clic en **Aceptar** para completar el proceso de aprobación.

   >![image](/help/user-guide/assets/tizen/rms-7.png)

1. Una vez aprobado el dispositivo, debe aparecer en la Lista del dispositivo. Haga clic en el botón *Información* ubicado en el cuadro del dispositivo, es decir, **i**, como se muestra en la figura siguiente.

   >![image](/help/user-guide/assets/tizen/rms-6.png)

1. Aparece el cuadro de diálogo Información del dispositivo. Seleccione la ficha **Información del dispositivo** y haga clic en **Editar**.

   >![image](/help/user-guide/assets/tizen/rms-5.png)

1. Edite las opciones del dispositivo y seleccione la ficha **Configuración**. Vaya a la sección **Iniciador de URL** e introduzca la dirección URL que aloja el wgt y `SSSP config file` para instalar una aplicación `SSSP`, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Haga clic en **Guardar** para que los cambios aparezcan en la pantalla de visualización.




