---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
feature: Administración de pantallas, reproductores
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 3bda698ca44f58c177f8e87a5c50b789966909de
workflow-type: tm+mt
source-wordcount: '1229'
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

1. El reproductor Tizen descarga el instalador desde el servidor local.

### Nomenclatura del reproductor Tizen {#name-tizen}

Puede asignar un nombre de dispositivo fácil de usar al reproductor Tizen, enviando así el nombre de dispositivo asignado a Adobe Experience Manager (AEM). Esta capacidad no solo le permite nombrar a su reproductor Tizen, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Puede elegir el nombre del Jugador sólo antes de registrarse. Una vez registrado el Jugador, el nombre del Jugador ya no se puede cambiar.

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
>Algunos motores de navegador son incompatibles con el atributo *SameSite=None* utilizado en el token de inicio de sesión emitido por AEM 6.5 a AEM 6.7. Normalmente, el problema se puede resolver actualizando el explorador a la última versión disponible. En algunos casos, estas actualizaciones pueden no ser posibles, como con pantallas inteligentes, cuadros superiores establecidos u otros dispositivos con motores de navegación integrados.

Siga los pasos a continuación para eximir a estos clientes incompatibles cuando utilice *SameSite=None*:

1. Actualice a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Después de reiniciar AEM vaya a `/system/console/configMgr` y busque **Controlador de autenticación de token de Granite de Adobe**. Establezca el valor del valor **SameSite** en **None**.

1. Debería ver una nueva opción *Agente de usuario a eximir del atributo samesite*. Rellene esto con una regex correspondiente al agente de usuario que sea(es) incompatible con el atributo *SameSite=None*.
   >[!NOTE]
   >Consulte [SameSite=None: Clientes incompatibles conocidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obtener más información. Para el reproductor Tizen use la regex: `(.*)Tizen(.*)`.

1. Registre el reproductor Tizen en su instancia AEM 6.5.5 y superior y debe registrar y mostrar el contenido normalmente.

## Aprovisionamiento remoto de Tizen Player {#remote-provisioning}

El aprovisionamiento remoto de Tizen Player le permite implementar cientos y miles de pantallas de Samsung Tizen sin ningún esfuerzo. Evita el tedioso esfuerzo manual de configurar cada reproductor con la URL del servidor y el código de registro masivo, u otros parámetros y, en el caso de Screens como Cloud Service, configurar el modo de nube y el token de nube.

Esta función le permite configurar remotamente el reproductor Tizen y también actualizar dichas configuraciones de forma centralizada, si es necesario. Todo lo que necesita es el servidor `HTTP` utilizado para alojar la aplicación Tizen `(wgt and xml file)` y un editor de texto para guardar el `config.json` con los parámetros apropiados.

Asegúrese de haber configurado la dirección del iniciador de URL en el dispositivo Tizen, es decir, el botón principal —> la configuración del iniciador de URL.
En el servidor `HTTP` que aloja la aplicación Tizen, coloque el archivo `config.json` en la misma ubicación que el archivo `wgt`. El nombre del archivo debe ser `config.json`.
El reproductor Tizen se instalará y al inicio (y cada reinicio) comprobará y aplicará la configuración en el archivo `config.json`.

### Ejemplo de política JSON {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### Atributos y propósito de la política {#policy-attributes}

La siguiente tabla resume las políticas con sus funciones.

>[!NOTE]
>Las configuraciones de directiva se aplican estrictamente y no se anulan manualmente en la IU de administración del reproductor. Para permitir la configuración manual del reproductor para una directiva en particular, no especifique la directiva en la configuración de directiva; por ejemplo, si desea permitir la configuración manual para la programación de reinicio, no especifique la clave `rebootSchedule` en la configuración de directiva. Las configuraciones de directiva se leen cada vez que el reproductor se vuelve a cargar.

| **Nombre de la directiva** | **Función** |
|---|---|
| server | Dirección URL del servidor de Adobe Experience Manager (AEM). |
| registrationKey | Se utiliza para el registro masivo de dispositivos con clave previamente compartida. |
| resolución | Resolución del dispositivo. |
| restartSchedule | La programación para reiniciar el reproductor. |
| enableAdminUI | Active la IU de administración para configurar el dispositivo en el sitio. Configúrelo en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de establecer en false, una vez que esté completamente configurado y en producción. |
| enableActivityUI | Habilita para mostrar el progreso de actividades como descarga y sincronización. Habilite para solucionar problemas y deshabilite una vez que esté completamente configurado y en producción. |
| cloudMode | Configúrelo en true si desea que el reproductor Tizen se conecte a Screens como Cloud Service. Configúrelo en false para conectarse a AMS o a AEM local. |
| cloudToken | Token de registro para registrarse en Screens como Cloud Service. |


## Incorporación del dispositivo Tizen al servicio de administración remota de Samsung (RMS) {#enroll-tizen-device-rms}

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
