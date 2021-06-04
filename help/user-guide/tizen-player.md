---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
feature: Administración de pantallas, reproductores
role: Administrator
level: Intermediate
source-git-commit: 7fa4207be0d89a6c7d0d9d9a04722cd40d035634
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 1%

---


# Implementación de Tizen Player {#tizen-player}

## Instalación de Tizen Player {#installing-tizen-player}

Siga los pasos a continuación para implementar Tizen Player para AEM Screens:

1. Vaya a la página [AEM Screens Player Downloads](https://download.macromedia.com/screens/) para descargar el reproductor Tizen.

1. Instale el archivo del reproductor Tizen *(.zip)* desde el equipo local.

## Configuración del servidor local y extracción de archivos comprimidos {#setting-local-server}

>[!NOTE]
> Extraiga el archivo zip y haga que el reproductor Tizen esté disponible a través de `http server`. (No es necesario que el `http server` sea un servidor Local o Apache).

Complete los siguientes pasos:

1. Copie los dos archivos extraídos como `AEMScreensPlayer.wgt` y `sssp_config.xml` en el directorio raíz del servidor web Apache local.

   >[!NOTE]
   >El `AEMScreensPlayer.wgt`es la aplicación real del reproductor Tizen y `sssp_config.xml` contiene información sobre este mapa que le ayuda a instalarlo en el dispositivo Tizen.

1. Obtenga la dirección IP o URL del servidor HTTP local (y la ruta a la carpeta que contiene los archivos extraídos en el paso 2 si se extraen en una subcarpeta y no en una carpeta raíz)

1. El reproductor Tizen descargará el instalador del servidor local.

### Nomenclatura del reproductor Tizen {#name-tizen}

Puede asignar un nombre de dispositivo fácil de usar al reproductor Tizen, enviando así el nombre de dispositivo asignado a Adobe Experience Manager (AEM). Esta capacidad no solo le permite nombrar a su reproductor Tizen, sino que también le permite asignar fácilmente el contenido adecuado.

Siga los pasos a continuación para configurar el nombre en el reproductor Tizen:

1. Haga clic en el botón de menú del control remoto.
1. Vaya a **network** —> **Device Name** para asignar un nombre al reproductor.

### Configuración de actualizaciones en el dispositivo Samsung {#config-updates}

Siga los pasos que se indican a continuación en el dispositivo Samsung para completar la instalación del reproductor AEM Screens en el dispositivo:

1. Vaya a su dispositivo Samsung y active.

1. Haga clic en el botón **MENU** del mando a distancia del dispositivo y desplácese hacia abajo hasta **System** desde la barra de navegación izquierda.

1. Desplácese hacia abajo y seleccione la opción **Reproducir mediante** y cambie a la opción **Iniciador de URL**.
   ![image](/help/user-guide/assets/tizen/rms-2.png)

1. Una vez configurado el Iniciador de URL, pulse el botón **Home** desde el control remoto.

1. Vaya a **URL Launcher Settings**, introduzca la dirección IP de su servidor host local y haga clic en **Listo**.
   >[!NOTE]
   >El reproductor Tizen debe poder conectarse al servidor http.

1. El Reproductor de AEM Screens debe instalar e iniciar automáticamente en su dispositivo Samsung.

   >[!NOTE]
   >Tanto el dispositivo Tizen como el servidor `http` deben poder conectarse entre sí, es decir, el servidor debe ser accesible para el reproductor Tizen.


## Exención de agentes de usuario con el problema de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta sección se aplica a Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Algunos motores de navegador son incompatibles con el atributo *SameSite=None* utilizado en el token de inicio de sesión emitido por AEM 6.5 a AEM 6.7. En la mayoría de los casos, el problema se puede resolver actualizando el explorador a la última versión disponible. En algunos casos, estas actualizaciones pueden no ser posibles, como con pantallas inteligentes, cuadros superiores establecidos u otros dispositivos con motores de navegación integrados.

Siga los pasos a continuación para eximir a estos clientes incompatibles cuando utilice *SameSite=None*:

1. Actualice a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Después de reiniciar AEM vaya a `/system/console/configMgr` y busque **Controlador de autenticación de token de Granite de Adobe**. Establezca el valor del valor **SameSite** en **None**.

1. Debería ver una nueva opción *Agente de usuario a eximir del atributo samesite*. Rellene esto con una regex correspondiente a los agentes de usuario que sea(n) incompatible con el atributo *SameSite=None*.
   >[!NOTE]
   >Consulte [SameSite=None: Clientes incompatibles conocidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obtener más información. Para el reproductor Tizen use la regex: `(.*)Tizen(.*)`.

1. Registre el reproductor Tizen en su instancia AEM 6.5.5 y superior y debe registrar y mostrar el contenido normalmente.

## Aprovisionamiento masivo de Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Puede ser un esfuerzo tedioso introducir manualmente la dirección de su servidor AEM en la IU de administración de todos y cada uno de los dispositivos para un gran número de dispositivos. Se recomienda utilizar la solución de administración remota de Samsung (RMS) para implementar y administrar soluciones más grandes. Para obtener más información, consulte [Incorporación del dispositivo Tizen al servicio de administración remota de Samsung (RMS)](#enroll-tizen-device-rm) .

Siga los pasos a continuación para aprovisionar la aplicación de forma masiva para que apunte a la instancia de autor de AEM cuando se inicie:

1. Descargue e instale [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Abra el archivo `wgt` utilizando Tizen studio.
1. Abra el archivo `firmware-platform.js`, busque `DEFAULT_PREFERENCES`, cambie la URL del servidor a la URL del autor AEM y guárdela.
1. Cree el nuevo archivo `wgt`.

   >[!NOTE]
   >Es posible que deba crear o configurar un certificado de firma.

1. Implemente este nuevo archivo `wgt` utilizando RMS o URL Launcher y cuando el reproductor inicie, debería apuntar automáticamente a su servidor para que no necesite introducirlo manualmente en todos los dispositivos.

### Incorporación del dispositivo Tizen al servicio de administración remota de Samsung (RMS) {#enroll-tizen-device-rms}

Siga los pasos a continuación para inscribir el dispositivo Tizen en el Servicio de administración remota de Samsung (RMS) y configurar de forma remota el iniciador de URL:

>[!NOTE]
>Compruebe la configuración de red y el monitor.

1. Vaya a **Menú** -> **Red** -> **Configuración de red del servidor** y pulse **Entrar**.

1. Vaya a la dirección del servidor, escriba la dirección URL de MagicInfo y presione **Listo**.

1. Configure TLS, si es necesario. Vaya al puerto, seleccione el número de puerto del servidor y haga clic en **Save**.

1. Vaya a la pestaña **Device** y compruebe el dispositivo que acaba de configurar. Una vez que se encuentra un dispositivo, haga clic en la casilla de verificación y seleccione **Aprobar**.

   >![image](/help/user-guide/assets/tizen/rms-3.png)

1. Rellene la información necesaria y seleccione un grupo de dispositivos. Haga clic en **OK** para completar el proceso de aprobación.

   >![image](/help/user-guide/assets/tizen/rms-7.png)

1. Una vez aprobado el dispositivo, debe aparecer en la lista de dispositivos. Haga clic en el botón *Information* situado en el cuadro del dispositivo, es decir, **i**, como se muestra en la figura siguiente.

   >![image](/help/user-guide/assets/tizen/rms-6.png)

1. Aparece el cuadro de diálogo de información del dispositivo. Seleccione la pestaña **Device Info** y haga clic en **Edit**.

   >![image](/help/user-guide/assets/tizen/rms-5.png)

1. Edite las opciones del dispositivo y seleccione la pestaña **Setup**. Vaya a la sección **URL Launcher** e introduzca la URL que aloja el wgt y `SSSP config file` para instalar una aplicación `SSSP`, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Haga clic en **Save** para que los cambios aparezcan en la pantalla de visualización.

