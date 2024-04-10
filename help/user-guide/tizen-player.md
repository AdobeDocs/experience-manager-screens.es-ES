---
title: Tizen Player
description: Esta página describe la instalación y el funcionamiento de Tizen Player.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 1%

---

# Implementación de Tizen Player {#tizen-player}

## Instalación de Tizen Player {#installing-tizen-player}

Siga los pasos a continuación para implementar Tizen Player para AEM Screens:

1. Vaya a [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/) para que pueda descargar el reproductor Tizen.

1. Instalación del reproductor Tizen *(.zip)* desde el equipo local.

## Configuración del servidor http {#setting-local-server}

>[!NOTE]
> Extraiga el archivo zip y haga que el reproductor Tizen esté disponible a través de un `http server`. (La `http server` no es necesario que sea local o servidor Apache).

Complete los siguientes pasos:

1. Copie los dos archivos extraídos, como `AEMScreensPlayer.wgt` y `sssp_config.xml` al directorio raíz del servidor web Apache local.

   >[!NOTE]
   >El `AEMScreensPlayer.wgt`es la aplicación del reproductor Tizen real y `sssp_config.xml` contiene información sobre este mapa que le ayuda a instalarlo en el dispositivo Tizen.

1. Obtenga la IP o la URL del servidor HTTP local (y la ruta a la carpeta que contiene los archivos extraídos en el paso 2 si se extraen en una subcarpeta y no en una carpeta raíz).

1. El reproductor Tizen descarga el instalador desde el servidor local.

### Nombrar a Tizen Player {#name-tizen}

Puede asignar un nombre de dispositivo fácil de usar al reproductor Tizen, enviando así el nombre de dispositivo asignado a Adobe Experience Manager AEM (). Esta capacidad no solo le permite nombrar su reproductor Tizen, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Solo puede elegir el nombre del reproductor antes del registro. Una vez registrado el reproductor, el nombre del reproductor ya no se puede cambiar.

Siga los pasos a continuación para configurar el nombre en el reproductor Tizen:

1. Haz clic en el botón de menú del control remoto.
1. Vaya a **network** > **Nombre del dispositivo** para que pueda asignar un nombre al reproductor.

### Configuración de actualizaciones en el dispositivo Samsung {#config-updates}

Siga los pasos a continuación en el dispositivo Samsung para completar la instalación del reproductor AEM Screens en el dispositivo:

1. Vaya a su dispositivo Samsung y enciéndalo.
1. Haga clic en **MENÚ** del mando a distancia del dispositivo y desplácese hacia abajo hasta **Sistema** en la barra de navegación izquierda.
1. Desplácese hacia abajo y seleccione **Reproducir mediante** y cambie a. **Lanzador de URL** opción.
   ![imagen](/help/user-guide/assets/tizen/rms-2.png)
1. Una vez configurado el lanzador de URL, pulse el botón **Inicio** desde el mando a distancia.
1. Vaya a **Configuración del lanzador de URL** , introduzca la dirección IP del servidor localhost y haga clic en **Listo**.

   >[!NOTE]
   >El reproductor Tizen debe poder conectarse al servidor http.

1. AEM Screens Player se instala y se inicia automáticamente en el dispositivo Samsung.

   >[!NOTE]
   >Tanto el dispositivo Tizen como el `http` El servidor debe poder conectarse entre sí, es decir, el servidor debe ser accesible para el reproductor Tizen.


## Exención de agentes de usuario con el problema de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta sección se aplica a Adobe Experience Manager AEM AEM () 6.5.5 a la 6.5.7**
>
>Hay algunos motores de explorador que son incompatibles con el *`SameSite=None`* AEM AEM atributo utilizado en el token de inicio de sesión emitido por la versión 6.5.5 a la versión 6.5.7 de la. Normalmente, el problema se puede resolver actualizando el explorador a la última versión disponible. A veces, estas actualizaciones pueden no ser posibles, como con pantallas inteligentes, descodificadores u otros dispositivos con motores de exploración integrados.

Siga los pasos a continuación para eximir a estos clientes incompatibles al utilizar *SameSite=None*:

1. Actualice al paquete de servicio 6.5.7 de Adobe Experience Manager AEM ().

1. AEM Después de reiniciar el sistema, vaya a `/system/console/configMgr` y buscar **Controlador de autenticación de token de Granite de Adobe**. Establezca el valor de **SameSite** valor hasta **Ninguno**.

1. Debería ver una nueva opción *`User agents to be exempted from samesite attribute`*. Rellene esto con una regex correspondiente al agente de usuario que sea incompatible con el *SameSite=None* atributo.

   >[!NOTE]
   >
   >Consulte [SameSite=None: Clientes incompatibles conocidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obtener más información. Para el reproductor Tizen, utilice la expresión regular: `(.*)Tizen(.*)`.

1. AEM Registre el reproductor Tizen en su instancia de la versión 6.5.5 y superior de la y deberá registrarse y mostrar el contenido normalmente.

## Aprovisionamiento remoto del reproductor Tizen {#remote-provisioning}

El aprovisionamiento remoto de Tizen Player le permite implementar cientos y miles de pantallas Samsung Tizen sin mucho esfuerzo. Evita el esfuerzo manual de configurar cada reproductor con la URL del servidor, el código de registro masivo u otros parámetros. Y, si hay AEM Screens as a Cloud Service, para configurar el modo de nube y el token de nube.

Esta función le permite configurar de forma remota el reproductor Tizen y también actualizar esas configuraciones de forma centralizada, si es necesario. Todo lo que necesita es el `HTTP` servidor utilizado para alojar la aplicación Tizen `(wgt and xml file)` y un editor de texto para guardar `config.json` con los parámetros adecuados.

Asegúrese de haber configurado la dirección del lanzador de URL en el dispositivo Tizen, es decir, botón de inicio > Configuración del lanzador de URL.
En el `HTTP` servidor que aloja la aplicación Tizen, coloque el archivo `config.json` en la misma ubicación que el `wgt` archivo. El nombre de archivo debe ser `config.json`.
El reproductor Tizen instala y, en el momento del inicio (y cada vez que se reinicia), comprueba y aplica los ajustes de la `config.json` archivo.

### Ejemplo de directiva JSON {#example-json}

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

En la tabla siguiente se resumen las directivas con sus funciones.

>[!NOTE]
>Las configuraciones de directiva se aplican estrictamente y no se anulan manualmente en la IU de administración del reproductor. Para permitir la configuración manual del reproductor para una directiva en particular, no especifique la directiva en la configuración de la directiva.
>Por ejemplo, si desea permitir la configuración manual de la programación de reinicio, no especifique la clave `rebootSchedule` en la configuración de la directiva. Las configuraciones de directivas se leen cada vez que el reproductor se vuelve a cargar.

| **Nombre de política** | **Finalidad** |
|---|---|
| servidor | La dirección URL del servidor de Adobe Experience Manager AEM (). |
| registrationKey | Se utiliza para el registro masivo de dispositivos mediante una clave previamente compartida. |
| resolución | La resolución del dispositivo. |
| rebootSchedule | Programación para reiniciar el reproductor. |
| enableAdminUI | Habilite la IU de administración para configurar el dispositivo en el sitio. Se establece en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de establecer en false, una vez que esté completamente configurado y en producción. |
| enableActivityUI | Habilite para que pueda mostrar el progreso de las actividades como descarga y sincronización. Habilite para la resolución de problemas y deshabilite una vez que esté completamente configurado y en producción. |
| cloudMode | Configúrelo en true si desea que el reproductor Tizen se conecte a Screens as a Cloud Service. AEM Configúrelo en False para conectarse a AMS o a la red local de servicios (On-). |
| cloudToken | Token de registro para registrarse en Screens as a Cloud Service. |


## Inscripción del dispositivo Tizen en el servicio de administración remota de Samsung (RMS) {#enroll-tizen-device-rms}

Siga los pasos a continuación para inscribir el dispositivo Tizen en el servicio de administración remota de Samsung (RMS) y configurar de forma remota el lanzador de URL:

>[!NOTE]
>Compruebe la configuración de red y el monitor.

1. Vaya a **Menú** -> **Red** -> **Configuración de red del servidor** y pulse **Entrar**.

1. Vaya a Dirección del servidor y escriba la dirección URL de MagicInfo para acceder y pulse **Listo**.

1. Configure TLS si es necesario. Vaya al puerto, seleccione el número de puerto del servidor y seleccione **Guardar**.

1. Vaya a **Dispositivo** y compruebe el dispositivo que ha configurado. Cuando se encuentre un dispositivo, active la casilla de verificación y, a continuación, seleccione **Aprobar**.

   >![imagen](/help/user-guide/assets/tizen/rms-3.png)

1. Rellene la información necesaria y seleccione un grupo de dispositivos. Seleccionar **OK**.

   >![imagen](/help/user-guide/assets/tizen/rms-7.png)

1. Cuando se aprueba el Dispositivo, aparece en la Lista de dispositivos. Seleccionar *Información* en el cuadro del dispositivo, como se muestra en el siguiente ejemplo.

   >![imagen](/help/user-guide/assets/tizen/rms-6.png)

1. Aparece el cuadro de diálogo información del dispositivo. Seleccione el **Información del dispositivo** y seleccione **Editar**.

   >![imagen](/help/user-guide/assets/tizen/rms-5.png)

1. Edite las opciones del dispositivo y seleccione **Configurar** pestaña. Vaya a **Lanzador de URL** e introduzca la dirección URL que aloja el wgt y `SSSP config file` para poder instalar un `SSSP` aplicación, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/tizen/rms-9.png)

1. Seleccione **Guardar**.

### Uso del control remoto de Screens {#using-remote-control}

AEM Screens proporciona la funcionalidad Control remoto. Obtenga más información acerca de esta función aquí: [Control remoto de Screens](implementing-remote-control.md)
