---
title: Reproductor Tizen
description: Obtenga información acerca de la instalación y el funcionamiento del reproductor Tizen.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 1%

---

# Implementación del reproductor Tizen {#tizen-player}

## Instalación del reproductor Tizen {#installing-tizen-player}

Siga los pasos a continuación para implementar el reproductor Tizen para AEM Screens:

1. Vaya a la página [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/) para poder descargar el reproductor Tizen.

1. Instale el archivo Tizen player *(.zip)* desde su equipo local.

## Configuración del servidor http {#setting-local-server}

>[!NOTE]
> Extraiga el archivo zip y haga que el reproductor Tizen esté disponible a través de un `http server`. (No se requiere que `http server` sea un servidor local o Apache).

Complete los siguientes pasos:

1. Copie los dos archivos extraídos, como `AEMScreensPlayer.wgt` y `sssp_config.xml`, al directorio raíz del servidor web Apache local.

   >[!NOTE]
   >`AEMScreensPlayer.wgt` es la aplicación de reproducción Tizen real y `sssp_config.xml` contiene información sobre este mapa que le ayudará a instalarlo en el dispositivo Tizen.

1. Obtenga la IP o la URL del servidor HTTP local (y la ruta a la carpeta que contiene los archivos extraídos en el paso 2 si se extraen en una subcarpeta y no en una carpeta raíz).

1. El reproductor Tizen descarga el instalador desde el servidor local.

### Nombrando reproductor Tizen {#name-tizen}

Puede asignar un nombre de dispositivo fácil de usar al reproductor Tizen, enviando así el nombre de dispositivo asignado a Adobe Experience Manager (AEM). Esta capacidad no solo le permite asignar un nombre al reproductor Tizen, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Solo puede elegir el nombre del reproductor antes del registro. Una vez registrado el reproductor, el nombre ya no se puede cambiar.

Siga los pasos a continuación para configurar el nombre en el reproductor Tizen:

1. Haz clic en el botón de menú del control remoto.
1. Vaya a **Red** > **Nombre del dispositivo** para que pueda asignar un nombre al reproductor.

### Configuración de actualizaciones en el dispositivo Samsung {#config-updates}

Siga los pasos a continuación en el dispositivo Samsung para completar la instalación del Reproductor de AEM Screens en el dispositivo:

1. Vaya a su dispositivo Samsung y enciéndalo.
1. Haz clic en el botón **MENÚ** del control remoto del dispositivo y desplázate hacia abajo hasta **Sistema** desde la barra de navegación izquierda.
1. Desplácese hacia abajo y haga clic en la opción **Reproducir mediante** y cámbiela a la opción **Lanzador de URL**.
   ![imagen](/help/user-guide/assets/tizen/rms-2.png)
1. Cuando el lanzador de URL esté configurado, presiona el botón **Inicio** desde tu control remoto.
1. Vaya a **Configuración del lanzador de URL**, escriba la dirección IP del servidor host local y haga clic en **Listo**.

   >[!NOTE]
   >El reproductor Tizen debe poder conectarse al servidor HTTP.

1. AEM Screens Player se instala y se inicia automáticamente en el dispositivo Samsung.

   >[!NOTE]
   >Tanto el dispositivo Tizen como el servidor `http` deben poder conectarse entre sí; es decir, el servidor debe estar accesible para el reproductor Tizen.


## Exención de agentes de usuario con el problema de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta sección se aplica a Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>
>Hay algunos motores de explorador que son incompatibles con el atributo *`SameSite=None`* utilizado en el token de inicio de sesión emitido por AEM 6.5.5 a AEM 6.5.7. Normalmente, el problema se puede resolver actualizando el explorador a la última versión disponible. A veces, estas actualizaciones pueden no ser posibles, como con pantallas inteligentes, descodificadores u otros dispositivos con motores de exploración integrados.

Siga los pasos a continuación para eximir a estos clientes incompatibles cuando use *SameSite=None*:

1. Actualice a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Después de reiniciar AEM, vaya a `/system/console/configMgr` y busque **Controlador de autenticación de token de Adobe Granite**. Establezca el valor del valor de **SameSite** en **None**.

1. Debería ver una nueva opción *`User agents to be exempted from samesite attribute`*. Rellene esta opción con una regex correspondiente al agente de usuario que sea incompatible con el atributo *SameSite=None*.

   >[!NOTE]
   >
   >Consulte [SameSite=None: Clientes incompatibles conocidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obtener más información. Para el reproductor Tizen, use la expresión regular: `(.*)Tizen(.*)`.

1. Registre el reproductor Tizen con su AEM 6.5.5 y superior y debe registrarse y mostrar el contenido normalmente.

## Aprovisionamiento remoto del reproductor Tizen {#remote-provisioning}

El aprovisionamiento remoto del reproductor Tizen le permite implementar cientos y miles de pantallas Samsung Tizen sin mucho esfuerzo. Evita el esfuerzo manual de configurar cada reproductor con la URL del servidor, el código de registro masivo u otros parámetros. Y, si hay AEM Screens as a Cloud Service, para configurar el modo de nube y el token de nube.

Esta función le permite configurar de forma remota el reproductor Tizen y también actualizar esas configuraciones de forma centralizada, si es necesario. Todo lo que necesita es el servidor `HTTP` utilizado para hospedar la aplicación Tizen `(wgt and xml file)` y un editor de texto para guardar `config.json` con los parámetros apropiados.

Asegúrese de haber configurado la dirección URL del lanzador en el dispositivo Tizen. Haga clic en el botón Inicio > Configuración del lanzador de URL.
En el servidor `HTTP` que aloja la aplicación Tizen, coloque el archivo `config.json` en la misma ubicación que el archivo `wgt`. El nombre de archivo debe ser `config.json`.
El reproductor Tizen instala y en el inicio (y cada vez que se reinicia), comprueba y aplica la configuración del archivo `config.json`.

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
>Las configuraciones de la directiva de la IU de administración del reproductor se aplican estrictamente y no se anulan manualmente. Para permitir la configuración manual del reproductor para una directiva en particular, no especifique la directiva en la configuración de la directiva.
>&#x200B;>Por ejemplo, si desea permitir la configuración manual para la programación de reinicio, no especifique la clave `rebootSchedule` en la configuración de directiva. Las configuraciones de directivas se leen cada vez que el reproductor se vuelve a cargar.

| **Nombre de directiva** | **Propósito** |
|---|---|
| servidor | La URL del servidor de Adobe Experience Manager (AEM). |
| registrationKey | Se utiliza para el registro masivo de dispositivos mediante una clave previamente compartida. |
| resolución | La resolución del dispositivo. |
| rebootSchedule | Programación para reiniciar el reproductor. |
| enableAdminUI | Habilite la IU de administración para configurar el dispositivo en el sitio. Se establece en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de configurarlo como False una vez que esté completamente configurado y en producción. |
| enableActivityUI | Habilite para que pueda mostrar el progreso de las actividades, como la descarga y la sincronización. Habilite para la resolución de problemas y deshabilite una vez que esté completamente configurado y en producción. |
| cloudMode | Configúrelo en true si desea que el reproductor Tizen se conecte a Screens as a Cloud Service. Configúrelo en False para conectarse a AMS o a AEM local. |
| cloudToken | Token de registro para registrarse en Screens as a Cloud Service. |


## Inscripción del dispositivo Tizen en el servicio de administración remota de Samsung (RMS) {#enroll-tizen-device-rms}

Siga los pasos a continuación para inscribir el dispositivo Tizen en el servicio de administración remota de Samsung (RMS) y configurar de forma remota el lanzador de URL:

>[!NOTE]
>Compruebe la configuración de red y el monitor.

1. Vaya a **Menú** -> **Red** -> **Configuración de red del servidor** y presione **Entrar**.

1. Vaya a la dirección del servidor, escriba la URL de MagicInfo y pulse **Listo**.

1. Configure TLS si es necesario. Vaya al puerto, haga clic en el número de puerto del servidor y seleccione **Guardar**.

1. Vaya a la ficha **Dispositivo** y busque el dispositivo que configuró. Cuando se encuentre un dispositivo, haga clic en la casilla de verificación y luego en **Aprobar**.

   >![imagen](/help/user-guide/assets/tizen/rms-3.png)

1. Rellene la información necesaria y haga clic en un grupo de dispositivos. Haga clic en **OK**.

   >![imagen](/help/user-guide/assets/tizen/rms-7.png)

1. Cuando se aprueba el Dispositivo, aparece en la Lista de dispositivos. Haga clic en *Información* en el cuadro de dispositivo, como se muestra a continuación.

   >![imagen](/help/user-guide/assets/tizen/rms-6.png)

1. Aparece el cuadro de diálogo información del dispositivo. Haga clic en la ficha **Información del dispositivo** y luego en **Editar**.

   >![imagen](/help/user-guide/assets/tizen/rms-5.png)

1. Edite las opciones del dispositivo y haga clic en la ficha **Configuración**. Vaya a la sección **Iniciador de URL** e introduzca la URL que aloja el wgt y `SSSP config file` para que pueda instalar una aplicación `SSSP`, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/tizen/rms-9.png)

1. Haga clic en **Guardar**.

### Uso del control remoto de Screens {#using-remote-control}

AEM Screens proporciona la funcionalidad Control remoto. Obtenga más información acerca de esta característica aquí: [Control remoto de Screens](implementing-remote-control.md)
