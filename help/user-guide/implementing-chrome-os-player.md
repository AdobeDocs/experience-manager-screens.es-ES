---
title: Implementación de Chrome OS Player
seo-title: Implementación de Chrome OS Player
description: Siga esta página para conocer la implementación del reproductor de Chrome OS mediante la consola de administración de Chrome.
seo-description: Siga esta página para conocer la implementación del reproductor de Chrome OS mediante la consola de administración de Chrome.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# Implementación de Chrome OS Player {#implementing-chrome-os-player}

En esta sección se describe cómo implementar el reproductor de Chrome OS mediante la consola de administración de Chrome.

## Uso de la Consola de administración de Chrome {#using-chrome-management-console}

Siga los pasos a continuación para configurar la consola de administración de Chrome:

1. Regístrese en la consola de administración de Chrome. Debe obtener una licencia para la consola de administración de Chrome. Póngase en contacto con [Soporte técnico de Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) para administrar la configuración del dispositivo Chrome para obtener más información.
1. Inscriba el dispositivo operativo Chrome en el dominio espere 15 minutos para que el dispositivo se sincronice con la consola de administración de Chrome. Para obtener más información sobre cómo matricular dispositivos cromados, haga clic [aquí](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome Player estará disponible en la tienda web de Chrome.

>[!NOTE]
>
>Se recomienda una solución de administración de dispositivos como la consola de administración de Chrome para la implementación y administración de dispositivos Chrome OS. Aunque este documento proporciona implementación para la consola de administración de Chrome, hay otros proveedores que afirman proporcionar una funcionalidad similar. Póngase en contacto con el proveedor del software de administración de dispositivos.

### Activación del modo de kiosko {#enabling-kiosk-mode}

Siga los pasos a continuación para habilitar el modo de kiosco:

1. Inicie sesión en la consola de desarrollador de Chrome.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Vaya a **Administración de dispositivos** > **Administración de Chrome** > **Configuración de dispositivos**.
1. Desplácese hacia abajo hasta **Configuración de kiosco** y haga clic en **Administrar aplicaciones de kiosco**.

   ![kiosco](assets/kiosk.png)

1. Seleccione AEM Screens Player en la tienda web de Chrome.

   >[!NOTE]
   >
   >Una aplicación publicada recientemente puede tardar unos 15 minutos en aparecer en esta lista.

1. Seleccione **AEM Screens Player** en la lista desplegable **Aplicación de kiosko de inicio automático**.

   Los cambios pueden tardar unos minutos, dependiendo de la red, en surtir efecto. Se recomienda reiniciar.

#### Comprobación del estado del dispositivo remoto {#checking-remote-device-status}

1. Inicie sesión en la consola de desarrollador de Chrome.
1. Vaya a **Administración de dispositivos** > **Dispositivos Chrome** y seleccione el dispositivo que desea controlar.
1. Haga clic en **Actividad del sistema y solución de problemas**.
1. Compruebe las propiedades **Dispositivo de reinicio** y **Captura de pantalla** del dispositivo. También puede comprobar el estado del dispositivo y la información de estado.

>[!NOTE]
>
>Tenga en cuenta que esta configuración puede habilitarse varios minutos después de que el dispositivo esté matriculado. Cada opción puede habilitarse con el tiempo.

### Configuración remota de reproductores de Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player es una aplicación habilitada para Kiosk que también habilita la Configuración de directivas remotas para reproductores de Chrome OS.

Siga los pasos a continuación para configurar las distintas opciones del reproductor:

1. Inicie sesión en la consola de administración de Chrome.
1. Haga clic en **Administración de dispositivos** > **Administración de Chrome** > **Administración de aplicaciones**. El Reproductor de AEM Screens se muestra en la lista.
1. Haga clic en la aplicación **AEM Screens Player**.
1. Haga clic en **Configuración de kiosko** y seleccione su organización (*si utiliza un entorno de prueba*).
1. Haga clic en **cargar archivo de configuración** y cargue la directiva de configuración (*archivo Json*).
1. Haga clic en **Guardar.** Debe reiniciar el dispositivo para sincronizar la directiva.

>[!NOTE]
>
>Reinicie el dispositivo para sincronizar los cambios de directiva.

#### Ejemplo de archivo JSON de directiva {#example-policy-json-file}

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

En la tabla siguiente se resumen las políticas con sus funciones.

| **Nombre de directiva** | **Función** |
|---|---|
| *server* | La dirección URL del servidor de Adobe Experience Manager |
| *resolución* | La resolución del dispositivo operativo Chrome |
| *RestartSchedule* | La programación para reiniciar el reproductor de Chrome |
| *enableAdminUI* | Habilite la IU de administración para que los técnicos configuren el dispositivo en el sitio. Establezca en false una vez que esté completamente configurado y en producción. |
| *enableOSD* | Habilite la interfaz de usuario del conmutador de canal para que los usuarios puedan cambiar de canal en el dispositivo. Considere establecer en false una vez que esté completamente configurado y en producción. |
| *enableActivityUI* | Active esta opción para mostrar el progreso de actividades como la descarga y la sincronización. Habilite la solución de problemas y deshabilite una vez que esté completamente configurado y en producción. |

>[!NOTE]
>
>Las configuraciones de directiva se aplican estrictamente y no se anulan manualmente en la IU de administración del reproductor. Para permitir la configuración manual del reproductor para una directiva en particular, no especifique la directiva en la configuración de ***directiva,*** por ejemplo, si desea permitir la configuración manual para la programación de reinicio, no especifique la clave ***RestartSchedule*** en la configuración de directiva.
