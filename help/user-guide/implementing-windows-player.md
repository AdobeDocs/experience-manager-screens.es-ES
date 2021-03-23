---
title: Implementación del Reproductor de Windows 10
seo-title: Implementación del Reproductor de Windows 10
description: Siga esta página para obtener más información sobre la configuración del reproductor AEM Screens Windows 10.
seo-description: Siga esta página para obtener más información sobre la configuración del reproductor AEM Screens Windows 10.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administración de Screens, Reproductor de Windows
role: Administrador
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 1%

---


# Implementación del Reproductor de Windows 10 {#implementing-windows-player}

En esta sección se describe la configuración del reproductor AEM Screens Windows 10. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre qué configuración utilizar para el desarrollo y las pruebas.

## Instalación del Reproductor de Windows {#installing-windows-player}

Para implementar el Reproductor de Windows para AEM Screens, instale el Reproductor de Windows para AEM Screens.

Visite la página [**AEM 6.5 Descargas del reproductor**](https://download.macromedia.com/screens/).

>[!NOTE]
>No hay ningún modo de ventana en el reproductor de Windows. Siempre es modo de pantalla completa.

### Configuración del entorno para AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Debe configurar un entorno para el reproductor de Windows si utiliza AEM Screens 6.5.5 Service Pack.

Establezca el atributo **SameSite para las cookies de token de inicio de sesión** de **Lax** a **None** de la **Consola web de Adobe Experience Manager
Configuración** en todas AEM instancias de autor y publicación.

Complete los siguientes pasos:

1. Vaya a **Adobe Experience Manager Web Console
Configuración** mediante `http://localhost:4502/system/console/configMgr`.

1. Busque *Controlador de autenticación de token de Granite de Adobe*.

1. Establezca el atributo **SameSite para las cookies de token de inicio de sesión** de **Lax** a **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.

### Método ad hoc {#ad-hoc-method}

El método ad-hoc le permite instalar el último Reproductor de Windows (*.exe*). Visite la página [**AEM 6.5 Descargas del reproductor**](https://download.macromedia.com/screens/).

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad hoc:

1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuration** en el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de AEM a la que desea conectarse y haga clic en **Save**.
1. Vaya al enlace **Device** **Registration** del menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si **State** es **REGISTER**, verá que se rellenará el campo **Device id**.
>
>Si **State** es **UNREGISTER**, puede utilizar el **Token** para registrar el dispositivo.

## Cambio de las opciones predeterminadas en Windows Installer {#changing-default-options}

Siga esta sección para aprender a cambiar las opciones predeterminadas de Windows Installer y la lista de personalizaciones disponibles.

## Instalación utilizando CLI (PowerShell) {#install-powershell}

1. Cree una ubicación personalizada **dedicada** para Screens Player, por ejemplo:
   `C:\Users\User\screens-player`)
1. Instalar
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. Abra
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**Ejemplo**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Registro masivo del Reproductor de Windows {#bulk-registration}

Al implementar el reproductor de windows no es necesario configurar manualmente cada reproductor. En su lugar, puede actualizar el archivo JSON de configuración después de probarlo y de que esté listo para la implementación.

La configuración se asegurará de que todos los reproductores hagan ping al mismo servidor proporcionado en el archivo de configuración. Aún debe registrar manualmente cada reproductor.

Siga los pasos a continuación para configurar el Reproductor de Windows 10:

1. Instale Windows Player.
1. Busque el archivo de configuración en ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Actualice la configuración JSON utilizando la información siguiente y copie la misma carpeta en todos los sistemas en los que reside el reproductor.

### Atributos de política {#policy-attributes}

La siguiente tabla resume los atributos de política con un JSON de política de ejemplo para referencia:

| **Nombre de la directiva** | **Función** |
|---|---|
| server | Dirección URL del servidor de Adobe Experience Manager (AEM). |
| resolución | Resolución del dispositivo. |
| restartSchedule | La programación para reiniciar el reproductor. |
| enableAdminUI | Active la IU de administración para configurar el dispositivo en el sitio. Configúrelo en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de establecer en false una vez que esté completamente configurado y en producción. |
| enableActivityUI | Habilita para mostrar el progreso de actividades como descarga y sincronización. Habilite para solucionar problemas y deshabilite una vez que esté completamente configurado y en producción. |

#### Ejemplo de archivo JSON de directiva {#example-policy-json-file}

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

## Activación del modo de quiosco {#enabling-kiosk-mode}

Cuando se implementa el reproductor de Windows, es importante habilitar un modo de quiosco para que otras aplicaciones o la barra de tareas no aparezcan en el escritorio de Windows.

>[!CAUTION]
>
>Adobe recomienda una solución de administración de dispositivos para habilitar Kiosk para Windows. Siga los pasos que se indican a continuación si no dispone de una solución de administración de dispositivos para habilitar el modo Kiosk. Este método utiliza la función Shell Launcher disponible en Windows 10 enterprise y Edu. También se puede aplicar cualquier otro medio recomendado por Microsoft para aplicaciones que no sean de UWP para habilitar los kioscos, especialmente en otras ediciones de Windows.

Siga los pasos a continuación para habilitar el modo Kiosk:

>[!NOTE]
>
>Antes de seguir los pasos que se indican a continuación, asegúrese de utilizar Windows 10 Enterprise o Education.

1. Habilite Shell Launcher.

   Consulte la sección ***Configuración del lanzador del shell*** en la página **[Iniciador del shell](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** del soporte técnico de Microsoft Windows para obtener información adicional.

1. Cree un usuario no administrativo (si aún no tiene uno) para utilizarlo en Kiosk. Puede ser un usuario local o de dominio.
1. Instale el reproductor de Windows para ese usuario de Kiosk desde la página [Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/).
1. Consulte [Usar Shell Launcher para crear un quiosco de Windows 10](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) para modificar su script de PowerShell para obtener más información.

   Modifique el script de PowerShell para reemplazar el nombre de usuario por el que creó. Asegúrese de que la ruta al ejecutable de la aplicación sea correcta. Esto establecerá el shell personalizado como la aplicación del reproductor de Windows para el usuario del quiosco y establecerá el valor predeterminado como explorer.exe para otros usuarios.

1. Ejecute el script de PowerShell como administrador.
1. Reinicie e inicie sesión como el usuario de Kiosk y la aplicación del reproductor deberían iniciarse correctamente.

### Solución de problemas {#troubleshooting}

Si obtiene una pantalla negra cuando inicia sesión como usuario de Kiosk, significa que puede que haya especificado incorrectamente la ruta al ejecutable del reproductor de windows. Vuelva a iniciar sesión como administrador y verifique y vuelva a ejecutar el script.

La ruta de instalación predeterminada para el reproductor de Windows es:

***C:\Users\&amp;lt;su usuario>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

El script de ejemplo de los vínculos habilitará y deshabilitará el shell personalizado. Por lo tanto, es posible que tenga que dividir la secuencia de comandos en dos y habilitar/deshabilitar las siguientes líneas aplicables:

>[!NOTE]
>
>En algunos entornos de Windows, los scripts de PowerShell pueden estar restringidos por políticas (especialmente los scripts sin firmar). Para ejecutar el script, es posible que tenga que deshabilitar y volver a habilitar temporalmente esta restricción para ejecutar el script. Abra una ventana de PowerShell y utilice estos comandos.
>
>*set-execution policy sin restricciones* : para eliminar restricciones temporalmente
>
>*set-execution policy restringido* : para volver a habilitar la restricción después de ejecutar el script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

