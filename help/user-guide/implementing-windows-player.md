---
title: Implementación del Reproductor de Windows 10
seo-title: Implementing Windows 10 Player
description: Siga esta página para obtener más información sobre la configuración del reproductor AEM Screens Windows 10.
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
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
source-git-commit: 97bc64ce3c01ac2de301b17bf9f8610662d45f88
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 1%

---

# Implementación del Reproductor de Windows 10 {#implementing-windows-player}

En esta sección se describe la configuración del reproductor AEM Screens Windows 10. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre qué configuración utilizar para el desarrollo y las pruebas.

## Instalación del Reproductor de Windows {#installing-windows-player}

Para implementar el Reproductor de Windows para AEM Screens, instale el Reproductor de Windows para AEM Screens.

Visite la [**Descargas del reproductor de AEM 6.5**](https://download.macromedia.com/screens/) página.

>[!NOTE]
>No hay ningún modo de ventana en el reproductor de Windows. Siempre es modo de pantalla completa.

### Configuración del entorno para AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Debe configurar un entorno para el reproductor de Windows si utiliza AEM Screens 6.5.5 Service Pack.

Configure las variables **Atributo SameSite para las cookies de token de inicio de sesión** from **Laxo** a **Ninguna** from **Configuración de la consola web de Adobe Experience Manager** en todas las instancias de creación y publicación de AEM.

Complete los siguientes pasos:

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** using `http://localhost:4502/system/console/configMgr`.

1. Buscar *Controlador de autenticación de token de Granite de Adobe*.

1. Configure las variables **Atributo SameSite para las cookies de token de inicio de sesión** from **Laxo** a **Ninguna**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.

### Método ad hoc {#ad-hoc-method}

El método Ad Hoc le permite instalar el último Reproductor de Windows (*.exe*). Visita [**Descargas del reproductor de AEM 6.5**](https://download.macromedia.com/screens/) página.

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad hoc:

1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuración** en el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de AEM a la que desea conectarse y haga clic en **Guardar**.
1. Vaya a la **Dispositivo** **Registro** vínculo desde el menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si la variable **Estado** es **REGISTRADO**, notará que la variable **ID del dispositivo** se rellenará.
>
>Si la variable **Estado** es **NO REGISTRADO**, puede usar la variable **Token** para registrar el dispositivo.

## Nombre del reproductor de Windows {#name-windows}

Puede asignar un nombre de dispositivo fácil de usar al reproductor de Windows, enviando así el nombre de dispositivo asignado a Adobe Experience Manager (AEM). Esta capacidad no solo le permite nombrar su reproductor de Windows, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Puede elegir el nombre del Jugador sólo antes de registrarse. Una vez registrado el Jugador, el nombre del Jugador ya no se puede cambiar.

Siga los pasos a continuación para configurar el nombre en el reproductor de Windows:

1. Haga clic en **start** —> **run**
1. Entrar `system.cpl`
1. Utilice la ficha nombre del equipo para establecer el nombre de host del equipo

## Cambio de las opciones predeterminadas en Windows Installer {#changing-default-options}

Siga esta sección para aprender a cambiar las opciones predeterminadas de Windows Installer y la lista de personalizaciones disponibles.

## Instalación mediante CLI (PowerShell) {#install-powershell}

1. Crear una ubicación personalizada **dedicated** para Screens Player, por ejemplo:
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

## Registro masivo de Windows Player {#bulk-registration}

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

   Consulte la sección ***Configurar Shell Launcher*** en **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** página de soporte técnico de Microsoft Windows para obtener más información.

1. Cree un usuario no administrativo (si aún no tiene uno) para utilizarlo en Kiosk. Puede ser un usuario local o de dominio.
1. Instale el reproductor de windows para ese usuario de Kiosk desde [Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/) página.
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
>*set-execution policy sin restricciones* - Eliminar temporalmente las restricciones
>
>*set-execution policy restringido* - para volver a habilitar la restricción después de ejecutar el script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Uso del control remoto de Screens {#using-remote-control}

AEM Screens proporciona funcionalidad de control remoto. Obtenga más información sobre esta función aquí: [Control remoto de Screens](implementing-remote-control.md)