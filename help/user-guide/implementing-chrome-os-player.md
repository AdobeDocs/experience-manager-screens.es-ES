---
title: Implementación del Reproductor del sistema operativo Chrome
description: Obtenga información acerca de la implementación del Reproductor del sistema operativo Chrome mediante Chrome Management Console.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# Implementación del Reproductor del sistema operativo Chrome {#implementing-chrome-os-player}

En esta sección se describe cómo implementar el Reproductor del sistema operativo Chrome mediante Chrome Management Console.

## Uso de la consola de administración de Chrome {#using-chrome-management-console}

Siga los pasos a continuación para configurar la consola de administración de Chrome:

1. Regístrese en Chrome Management Console. Debe obtener una licencia para Chrome Management Console. Póngase en contacto con el [Soporte técnico de Google](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995) para administrar la configuración del dispositivo Chrome y obtener más información.
1. Registre el dispositivo Chrome OS en el dominio y espere 15 minutos a que el dispositivo se sincronice con Chrome Management Console. Para obtener más información sobre cómo inscribir un dispositivo Chrome, haga clic [aquí](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. El Reproductor de Chrome está disponible en Chrome Web Store.

>[!NOTE]
>
>Se recomienda una solución de administración de dispositivos como Chrome Management Console para la implementación y administración de dispositivos del sistema operativo Chrome. Aunque este documento proporciona implementación para Chrome Management Console, hay otros proveedores que afirman proporcionar una funcionalidad similar. Póngase en contacto con el proveedor del software de administración de dispositivos.

## Nombrar el reproductor Chrome OS {#name-chrome}

Puede asignar un nombre de dispositivo descriptivo al reproductor de Chrome, enviando así el nombre de dispositivo asignado a Adobe Experience Manager (AEM). Esta capacidad no solo le permite asignar un nombre al reproductor de Chrome, sino que también le permite asignar fácilmente el contenido adecuado.

>[!NOTE]
>Solo puede elegir el nombre del reproductor antes del registro. Una vez registrado el reproductor, el nombre ya no se puede cambiar.

Siga los pasos a continuación para configurar el nombre en el Reproductor de Chrome:

1. Opcionalmente, puede permitir a los integradores de audio y vídeo o a los administradores de TI establecer el ID y la ubicación del recurso como parte de la inscripción empresarial.

   ![imagen](/help/user-guide/assets/chrome-device/chrome1.png)

1. Se le presentarán las opciones para inscribir el dispositivo.

   ![imagen](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Puede establecer el ID de recurso como parte de la inscripción empresarial y en Chrome Management Console.

   ![imagen](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Los reproductores de Chrome deben estar inscritos en una inscripción empresarial y el reproductor de Chrome debe implementarse mediante Chrome Management Console; de lo contrario, el ID de recurso devuelve un valor en blanco (por ejemplo, Chrome como extensión). El nombre del dispositivo solo se registra en el momento del registro. Adobe Experience Manager (AEM) no recoge los cambios futuros.

### Activando modo de quiosco {#enabling-kiosk-mode}

Siga los pasos a continuación para habilitar el modo Quiosco:

1. Inicie sesión en Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Vaya a **Administración de dispositivos** > **Administración de Chrome** > **Configuración de dispositivos**.
1. Desplácese hacia abajo hasta **Configuración de quiosco** y haga clic en **Administrar aplicaciones de quiosco**.

   ![quiosco](assets/kiosk.png)

1. Haga clic en el Reproductor de AEM Screens desde la Tienda web de Chrome.

   >[!NOTE]
   >
   >Una aplicación publicada recientemente puede tardar unos 15 minutos en aparecer en esta lista.

1. Haga clic en **Reproductor de AEM Screens** en el menú desplegable **Iniciar automáticamente la aplicación del quiosco**.

   Los cambios pueden tardar unos minutos en surtir efecto en función de la red. Se recomienda reiniciar.

#### Comprobación del estado del dispositivo remoto {#checking-remote-device-status}

1. Inicie sesión en Chrome Developer Console.
1. Vaya a **Administración de dispositivos** > **Dispositivos Chrome** y haga clic en el dispositivo que desee controlar.
1. Haga clic en **Actividad del sistema y resolución de problemas**.
1. Compruebe las propiedades del dispositivo **Reboot Device** y **Screen Capture**. También puede comprobar el estado del dispositivo y la información de estado.

>[!NOTE]
>
>Esta configuración se puede habilitar varios minutos después de inscribir el dispositivo. Cada opción se puede activar con el tiempo.

### Configuración remota de reproductores del sistema operativo Chrome {#configuring-remote-configuration-of-chrome-os-players}

El Reproductor de AEM Screens es una aplicación habilitada para quioscos que también habilita la Configuración de directivas remotas para reproductores del sistema operativo Chrome.

Siga los pasos a continuación para configurar las distintas opciones del reproductor:

1. Inicie sesión en Chrome Management Console.
1. Haga clic en **Administración de dispositivos** > **Administración de Chrome** > **Administración de aplicaciones**. El Reproductor de AEM Screens se muestra en la lista.
1. Haga clic en la aplicación **AEM Screens Player**.
1. Haga clic en **Configuración del quiosco** y luego en su organización (*si usa un entorno de prueba*).
1. Haga clic en **cargar archivo de configuración** y cargue la directiva de configuración (*archivo JSon*).
1. Haga clic en **Guardar**. Reinicie el dispositivo para poder sincronizar la directiva.

>[!NOTE]
>
>Reinicie el dispositivo para sincronizar los cambios de directiva.

#### Archivo JSON de política de ejemplo {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### Atributos y propósito de la política {#policy-attributes-and-purpose}

En la tabla siguiente se resumen las directivas con sus funciones.

| **Nombre de directiva** | **Propósito** |
|---|---|
| servidor | La URL del servidor de Adobe Experience Manager (AEM). |
| registrationKey | Se utiliza para el registro masivo de dispositivos mediante una clave previamente compartida. |
| resolución | La resolución del dispositivo. |
| rebootSchedule | Programación para reiniciar el reproductor. |
| enableAdminUI | Habilite la IU de administración para configurar el dispositivo en el sitio. Se establece en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canales para que los usuarios cambien de canal en el dispositivo. Considere la posibilidad de configurarlo como False una vez que esté completamente configurado y en producción. |
| enableActivityUI | Habilite para que pueda mostrar el progreso de las actividades, como la descarga y la sincronización. Habilite para la resolución de problemas y deshabilite una vez que esté completamente configurado y en producción. |
| cloudMode | Configúrelo en true si desea que el Reproductor de Chrome se conecte a Screens as a Cloud Service. Configúrelo en False para conectarse a AMS o a AEM local. |
| cloudToken | Token de registro para registrarse en Screens as a Cloud Service. |

>[!NOTE]
>
>Las configuraciones de directiva se aplican estrictamente y la IU de administración del reproductor no se anula manualmente. Para permitir la configuración manual del reproductor para una directiva en particular, no especifique la directiva en la ***configuración de directiva***. Por ejemplo, si desea permitir la configuración manual de la programación de reinicio, no especifique la clave ***rebootSchedule*** en la configuración de la directiva.

### Uso del control remoto de Screens {#using-remote-control}

AEM Screens proporciona la funcionalidad Control remoto. Obtenga más información acerca de esta característica aquí: [Control remoto de Screens](implementing-remote-control.md)
