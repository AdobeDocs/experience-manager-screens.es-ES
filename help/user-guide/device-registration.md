---
title: Registro de dispositivos
seo-title: Registro de dispositivos
description: En esta página se describe el proceso de registro del dispositivo en un proyecto de AEM Screens.
seo-description: En esta página se describe el proceso de registro del dispositivo en un proyecto de AEM Screens.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 1%

---


# Registro de dispositivos {#device-registration}

En la página siguiente se describe el proceso de registro del dispositivo en un proyecto de AEM Screens.

## Registro de un dispositivo {#registering-a-device}

El proceso de registro del dispositivo se realiza en dos equipos distintos:

* El dispositivo real que se va a registrar, por ejemplo, la visualización de señales
* El servidor AEM que se utiliza para registrar el dispositivo

>[!NOTE]
>
>Una vez que descargue la versión más reciente de Windows Player (*.exe*), desde [AEM página de descargas](https://download.macromedia.com/screens/) del reproductor 6.4, siga los pasos del reproductor para completar la instalación ad-hoc:
>
>1. Presione largo tiempo en la esquina superior izquierda para abrir el panel de administración.
>1. Vaya a **Configuración** en el menú de acción de la izquierda, introduzca la dirección de ubicación de la instancia de AEM en **Servidor** y haga clic en **Guardar**.
>1. Haga clic en el vínculo **Registro** desde el menú de acción de la izquierda y en los pasos siguientes para completar el proceso de registro del dispositivo.

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. En el dispositivo, inicio AEM Screens Player. Se muestra la interfaz de usuario de registro.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. En AEM, vaya a la carpeta **Dispositivos** del proyecto.

   >[!NOTE]
   >
   >Para obtener más información sobre la creación de un nuevo proyecto para Pantallas en el panel de AEM, consulte [Crear y gestionar proyecto](creating-a-screens-project.md)de pantallas.

1. Toque o haga clic en el botón Administrador **de dispositivos** de la barra de acciones.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Toque o haga clic en el botón Registro **del** dispositivo en la parte superior derecha.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Seleccione el dispositivo requerido (igual que el paso 1) y toque o haga clic en **Registrar dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. En AEM, espere a que el dispositivo envíe su código de registro.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. En el dispositivo, compruebe el código **de registro**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Si el código **de** registro es el mismo en ambos equipos, toque o haga clic en el botón **Validar** en AEM, como se muestra en el paso (6).
1. Defina el nombre que desee para el dispositivo y haga clic en **Registrar**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Tap/click **Finish** to complete the registration process.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >El **Registro de nuevo** le permite registrar un nuevo dispositivo.
   >
   >La pantalla **Asignar** permite agregar directamente el dispositivo a una pantalla.

   Si hace clic en **Finalizar**, deberá asignar el dispositivo a una pantalla.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Para obtener más información sobre la creación y administración de una pantalla para su proyecto de Pantallas, consulte [Creación y administración de pantallas](managing-displays.md).

### Asignación de un dispositivo a una pantalla {#assigning-device-to-a-display}

Si no ha asignado el dispositivo a una pantalla, siga los pasos a continuación para asignar el dispositivo a una pantalla del proyecto de AEM Screens:

1. Seleccione el dispositivo y haga clic en **Asignar dispositivo** en la barra de acciones.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Seleccione la ruta de la pantalla en Ruta **de** visualización/configuración del dispositivo.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Haga clic en **Asignar** cuando seleccione la ruta.

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. Haga clic en **Finalizar** una vez que el dispositivo se haya asignado correctamente, como se muestra en la figura siguiente.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Además, puede vista del panel de visualización al hacer clic en **Finalizar**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Limitaciones en el registro del dispositivo {#limitations-on-device-registration}

Las restricciones de contraseña de usuario para todo el sistema podrían provocar un error en el registro del dispositivo. El registro del dispositivo utiliza una contraseña generada al azar para crear el usuario del dispositivo.

Si la configuración *AuthorizableActionProvider* restringe la contraseña, es posible que se produzca un error al crear el usuario del dispositivo.

>[!NOTE]
>
>La contraseña aleatoria actual se compone de 36 caracteres ASCII, que oscilan entre 33 y 122 (incluye casi todos los caracteres especiales).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Recursos adicionales {#additional-resources}

Para obtener más información sobre AEM Screens Player, consulte [AEM Screens Player](working-with-screens-player.md).
