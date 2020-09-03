---
title: Implementación de Windows 10 Player
seo-title: Implementación de Windows 10 Player
description: Siga esta página para obtener información sobre la configuración del reproductor AEM Screens Windows 10.
seo-description: Siga esta página para obtener información sobre la configuración del reproductor AEM Screens Windows 10.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: a179b6be273b0b0ca166bae755399f8254091ee6
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 1%

---


# Implementación de Windows 10 Player {#implementing-windows-player}

Esta sección describe cómo configurar el reproductor AEM Screens Windows 10. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre las opciones que se utilizarán para el desarrollo y la prueba.

## Instalación de Windows Player {#installing-windows-player}

Para implementar Windows Player para AEM Screens, instale Windows Player para AEM Screens.

Visite la página de descargas [**del reproductor**](https://download.macromedia.com/screens/) AEM 6.5.

### Configuración de Entorno para AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

Debe configurar un entorno para el reproductor de Windows si utiliza AEM Screens 6.5.5 Service Pack.

Establezca el atributo **SameSite para las cookies** de inicio de sesión de **Lax** a **None** desde **Adobe Experience Manager Web ConsoleConfiguration** en todas las instancias de creación y publicación AEM.

Complete los siguientes pasos:

1. Vaya a **Adobe Experience Manager Web ConsoleConfiguration** mediante `http://localhost:4502/system/console/configMgr`.

1. Busque el controlador de autenticación *Adobe Granite Token*.

1. Establezca el atributo **SameSite para las cookies** de inicio de sesión de **Lax** a **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Haga clic en **Guardar**.

### Método ad-hoc {#ad-hoc-method}

El método ad-hoc permite instalar el último Reproductor de Windows (*.exe*). Visite [**AEM página de descargas**](https://download.macromedia.com/screens/) del reproductor 6.5.

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad-hoc:

1. Presione largo tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuración** desde el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de AEM con la que desea conectarse y haga clic en **Guardar**.
1. Vaya al vínculo **Registro del** dispositivo **** desde el menú de acción de la izquierda para comprobar el estado del proceso de registro del dispositivo.

>[!NOTE]
>
>Si el **estado** está **REGISTRADO**, verá que se rellenará el campo ID **del** dispositivo.
>
>Si el **estado** es **NO REGISTRADO**, puede utilizar el **testigo** para registrar el dispositivo.

### Configuración del servidor masivo: Registro de varios reproductores de Windows 10 con una configuración {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

Una vez que haya instalado el reproductor de Windows, puede registrar varios reproductores con una configuración.

>[!NOTE]
>
>**Registro masivo de Windows Player**
>
>Al implementar el reproductor de Windows no es necesario configurar manualmente cada reproductor. En su lugar, puede actualizar el archivo JSON de configuración una vez que se haya probado y esté listo para la implementación.
>
>La configuración se asegurará de que todos los reproductores que hagan ping al mismo servidor proporcionado en el archivo de configuración. Aún debe registrar manualmente cada reproductor.

Siga los pasos a continuación para configurar el Reproductor de Windows 10:

1. Instale Windows Player.
1. Busque el archivo de configuración en ***%appdata%\com.adobe.aem.screen.player\config.json***.
1. Actualice el JSON de configuración con la información siguiente y copie la misma carpeta en todos los sistemas en los que reside el reproductor.

### Atributos de directiva {#policy-attributes}

La siguiente tabla resume los atributos de política con un JSON de política de ejemplo para referencia:

| **Nombre de directiva** | **Función** |
|---|---|
| server | Dirección URL del servidor de Adobe Experience Manager (AEM). |
| resolución | La resolución del dispositivo. |
| RestartSchedule | La programación para reiniciar el reproductor. |
| enableAdminUI | Habilite la interfaz de usuario del administrador para configurar el dispositivo en el sitio. Establezca en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canal para que los usuarios puedan cambiar de canal en el dispositivo. Considere establecer en false una vez que esté completamente configurado y en producción. |
| enableActivityUI | Active esta opción para mostrar el progreso de actividades como la descarga y la sincronización. Habilite la solución de problemas y deshabilite una vez que esté completamente configurado y en producción. |

#### Ejemplo de archivo JSON de política {#example-policy-json-file}

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

## Activación del modo de kiosco {#enabling-kiosk-mode}

Al implementar el reproductor de Windows, es importante habilitar un modo de kiosco para que otras aplicaciones o la barra de tareas no aparezcan en el escritorio de Windows.

>[!CAUTION]
>
>Adobe recomienda una solución de administración de dispositivos para habilitar Kiosk para Windows. Siga los pasos a continuación si no dispone de una solución de administración de dispositivos para activar el modo Kiosk. Este método utiliza la función del iniciador de shell disponible en Windows 10 Enterprise y Edu. Cualquier otro medio recomendado por Microsoft para aplicaciones que no sean de UWP también se puede aplicar para habilitar Kiosk, especialmente en otras ediciones de Windows.

Siga los pasos a continuación para habilitar el modo de kiosco:

>[!NOTE]
>
>Antes de seguir los pasos a continuación, asegúrese de utilizar Windows 10 Enterprise o Education.

1. Habilitar el iniciador de shell.

   Consulte la sección ***Configurar el iniciador*** de shell en la página **[del iniciador](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** de shell de Microsoft Windows para obtener más información.

1. Cree un usuario que no sea administrativo (si ya no tiene uno) para utilizarlo en Kiosk. Puede ser un usuario local o de dominio.
1. Instale Windows Player para ese usuario de Kiosk desde la página de descargas [de](https://download.macromedia.com/screens/) AEM Screens Player.
1. Consulte [Uso del iniciador de shell para crear un quiosco](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) de Windows 10 para modificar el script de PowerShell para obtener más información.

   Modifique la secuencia de comandos de PowerShell para reemplazar el nombre de usuario por el que ha creado. Asegúrese de que la ruta de acceso al archivo ejecutable de la aplicación es correcta. Esto establecerá el shell personalizado como la aplicación de Windows Player para el usuario del quiosco y establecerá el valor predeterminado como explorer.exe para otros usuarios.

1. Ejecute el script de PowerShell como administrador.
1. Reinicie e inicie sesión como el usuario de Kiosk y la aplicación del reproductor deberían estar en inicio.

### Solución de problemas {#troubleshooting}

Si obtiene una pantalla negra cuando inicia sesión como usuario de Kiosk, significa que puede que haya especificado incorrectamente la ruta al ejecutable del reproductor de Windows. Vuelva a iniciar sesión como administrador y compruebe y vuelva a ejecutar la secuencia de comandos.

La ruta de instalación predeterminada para el reproductor de Windows es:

***C:\Users\&amp;lt;su usuario>\AppData\Local\Programs\@aem-screensscreen-player-electron\AEM Screens Player.exe***

La secuencia de comandos de ejemplo de los vínculos habilitará y deshabilitará el shell personalizado. Por lo tanto, es posible que tenga que dividir la secuencia de comandos en dos y habilitar/deshabilitar las líneas siguientes aplicables:

>[!NOTE]
>
>En algunos entornos de Windows, los scripts de PowerShell pueden estar restringidos por políticas (especialmente los scripts sin firmar). Para ejecutar la secuencia de comandos, es posible que tenga que deshabilitar y volver a habilitar temporalmente esta restricción para ejecutar la secuencia de comandos. Abra una ventana de PowerShell y utilice estos comandos.
>
>*set-execute policy sin restricciones* - para eliminar restricciones temporalmente
>
>*set-execute policy restringido* : para volver a habilitar la restricción después de ejecutar la secuencia de comandos

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

