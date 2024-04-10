---
title: Implementación del Reproductor de Windows 10
description: Obtenga información acerca de la configuración del reproductor AEM Screens Windows 10.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 1%

---

# Implementación del Reproductor de Windows 10 {#implementing-windows-player}

En esta sección se describe la configuración del reproductor AEM Screens Windows 10. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre los ajustes que se deben utilizar para el desarrollo y las pruebas.

## Instalación del Reproductor de Windows {#installing-windows-player}

Para implementar el Reproductor de Windows para AEM Screens, instale el Reproductor de Windows para AEM Screens.

Visite la [**AEM Descargas del reproductor de 6.5 en**](https://download.macromedia.com/screens/) página.

>[!NOTE]
>No hay modo de ventana en el reproductor de Windows. Siempre es modo de pantalla completa.

### Configuración del entorno para el paquete de servicio de AEM Screens 6.5.5 {#fp-environment-setup}

>[!NOTE]
>Configure un entorno para el reproductor de Windows si utiliza el paquete de servicio de AEM Screens 6.5.5.

Configure las variables **Atributo SameSite para las cookies de token de inicio de sesión** de **Laxo** hasta **Ninguno** de **Configuración de la consola web Adobe Experience Manager** AEM en todas las instancias de autor y publicación de la.

Complete los siguientes pasos:

1. Vaya a **Configuración de la consola web Adobe Experience Manager** usando `http://localhost:4502/system/console/configMgr`.

1. Buscar por *Controlador de autenticación de token de Granite de Adobe*.

1. Configure las variables **Atributo SameSite para las cookies de token de inicio de sesión** de **Laxo** hasta **Ninguno**.
   ![imagen](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.

### Método ad hoc {#ad-hoc-method}

El método Ad Hoc permite instalar el último Reproductor de Windows (*.exe*). Visita [**AEM Descargas del reproductor de 6.5 en**](https://download.macromedia.com/screens/) página.

Una vez que descargue la aplicación, siga los pasos del reproductor para completar la instalación ad-hoc:

1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuración** AEM en el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de a la que desea conectarse y haga clic en **Guardar**.
1. Vaya a **Dispositivo** **Registro** vínculo del menú de acción de la izquierda para poder comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si la variable **Estado** es **REGISTRADO**, observe que la variable **ID de dispositivo** El campo se rellena.
>
>Si la variable **Estado** es **NO REGISTRADO**, puede utilizar el **Token** para registrar el dispositivo.

## Nombrar el Reproductor de Windows {#name-windows}

Puede asignar un nombre de dispositivo descriptivo al reproductor de Windows y, de este modo, enviar el nombre de dispositivo asignado a Adobe Experience Manager AEM (). Esta capacidad no solo le permite asignar un nombre al reproductor de Windows, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Solo puede elegir el nombre del reproductor antes del registro. Una vez registrado el reproductor, el nombre del reproductor ya no se puede cambiar.

Siga los pasos a continuación para configurar el nombre en el reproductor de Windows:

1. Clic **start** > **correr**.
1. Entrar `system.cpl`.
1. Utilice la ficha nombre de equipo para establecer el nombre de host del equipo.

## Cambiar las opciones predeterminadas en Windows Installer {#changing-default-options}

Siga esta sección para aprender a cambiar las opciones predeterminadas de Windows Installer y la lista de personalizaciones disponibles.

## Instalación mediante CLI (PowerShell) {#install-powershell}

1. Crear una ubicación personalizada **dedicado** para el reproductor Screens, por ejemplo:
   `C:\Users\User\screens-player`)
1. Instalar
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. Abrir
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**Ejemplo**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Registro masivo del Reproductor de Windows {#bulk-registration}

Al implementar el reproductor de Windows, no es necesario configurar manualmente todos los reproductores. En su lugar, puede actualizar el archivo JSON de configuración una vez que se haya probado y esté listo para la implementación.

La configuración garantiza que todos los reproductores hagan ping al mismo servidor proporcionado en el archivo de configuración. Registre manualmente cada reproductor.

Siga los pasos a continuación para configurar el Reproductor de Windows 10:

1. Instale el Reproductor de Windows.
1. Busque el archivo de configuración en ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Actualice el JSON de configuración con la información siguiente y, a continuación, copie la misma carpeta en todos los sistemas en los que reside el reproductor.

### Atributos de política {#policy-attributes}

La siguiente tabla resume los atributos de la política con un ejemplo de JSON de política para referencia:


| **Nombre de política** | **Finalidad** |
|---|---|
| servidor | La dirección URL del servidor de Adobe Experience Manager AEM (). |
| registrationKey | Se utiliza para el registro masivo de dispositivos mediante una clave previamente compartida. |
| resolución | La resolución del dispositivo. |
| rebootSchedule | Programación para reiniciar el reproductor. |
| enableAdminUI | Habilite la IU de administración para configurar el dispositivo en el sitio. Se establece en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de establecer en false, una vez que esté completamente configurado y en producción. |
| enableActivityUI | Habilite para que pueda mostrar el progreso de las actividades como descarga y sincronización. Habilite para la resolución de problemas y deshabilite una vez que esté completamente configurado y en producción. |
| cloudMode | Configúrelo en true si desea que el reproductor de Windows se conecte a Screens as a Cloud Service. AEM Configúrelo en False para conectarse a AMS o a la red local de servicios (On-). |
| cloudToken | Token de registro para registrarse en Screens as a Cloud Service. |

#### Archivo JSON de política de ejemplo {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## Activando modo de quiosco {#enabling-kiosk-mode}

Al implementar el reproductor de Windows, es importante habilitar el modo Quiosco para que otras aplicaciones o la barra de tareas no aparezcan en el escritorio de Windows.

>[!CAUTION]
>
>Adobe recomienda una solución de administración de dispositivos para habilitar Kiosk para Windows. Siga los pasos a continuación si no tiene una solución de administración de dispositivos para habilitar el modo Quiosco. Este método utiliza la función Shell Launcher disponible en Windows 10 enterprise y Edu. También se puede aplicar cualquier otro medio recomendado por Microsoft para aplicaciones que no sean UWP para activar Kiosk, especialmente en otras ediciones de Windows.

Siga los pasos a continuación para habilitar el modo Quiosco:

>[!NOTE]
>
>Antes de seguir los pasos siguientes, asegúrese de usar Windows 10 Enterprise o Education.

1. Habilite el lanzador de shell.

   Consulte ***Configurar el lanzador de shell*** in **[Iniciador de shell](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/customize/shell-launcher)** página de soporte de Microsoft® Windows para obtener más información.

1. Cree un usuario no administrativo (si todavía no tiene uno) para utilizarlo en el quiosco. Puede ser un usuario local o de dominio.
1. Instale el reproductor de Windows para ese usuario del quiosco desde [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/) página.
1. Consulte [Utilice Shell Launcher para crear un quiosco de Windows 10](https://learn.microsoft.com/en-us/windows/configuration/assigned-access/shell-launcher/?tabs=intune) para modificar el script de PowerShell y obtener más información.

   Modifique el script de PowerShell para poder reemplazar el nombre de usuario por el que ha creado. Asegúrese de que la ruta de acceso al ejecutable de la aplicación sea correcta. Esto establece el shell personalizado como la aplicación del reproductor de Windows para el usuario del quiosco y establece el valor predeterminado como explorer.exe para otros usuarios.

1. Ejecute el script de PowerShell como administrador.
1. Reinicie e inicie sesión como el usuario del quiosco y la aplicación de reproducción deben iniciarse de inmediato.

### Solución de problemas {#troubleshooting}

Si aparece una pantalla en negro después de iniciar sesión como el usuario del quiosco, significa que es posible que haya especificado incorrectamente la ruta al ejecutable del reproductor de Windows. Vuelva a iniciar sesión como administrador y compruebe y vuelva a ejecutar el script.

La ruta de instalación predeterminada del reproductor de Windows es:

***C:\Users\&lt;your user=&quot;&quot;>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

El script de ejemplo de los vínculos habilita y deshabilita el shell personalizado. Por lo tanto, divida la secuencia de comandos en dos y habilite/deshabilite las siguientes líneas aplicables:

>[!NOTE]
>
>En algunos entornos de Windows, las directivas pueden restringir los scripts de PowerShell (especialmente los scripts sin firmar). Para ejecutar el script, deshabilite y vuelva a habilitar temporalmente esta restricción para ejecutarlo. Abra una ventana de PowerShell y utilice estos comandos.
>
>*`set-executionpolicy unrestricted`* - para eliminar temporalmente las restricciones.
>
>*`set-executionpolicy restricted`* - para volver a habilitar la restricción después de ejecutar la secuencia de comandos.

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Uso del control remoto de Screens {#using-remote-control}

AEM Screens proporciona la funcionalidad Control remoto. Obtenga más información acerca de esta función aquí: [Control remoto de Screens](implementing-remote-control.md)