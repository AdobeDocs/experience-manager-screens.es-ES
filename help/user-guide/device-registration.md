---
title: Registro de dispositivos
seo-title: Registro de dispositivos
description: En esta página se describe el proceso de registro de dispositivos en un proyecto de AEM Screens.
seo-description: En esta página se describe el proceso de registro de dispositivos en un proyecto de AEM Screens.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
feature: Administración de Screens, registro de dispositivos
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---

# Registro de dispositivos {#device-registration}

En la siguiente página se describe el proceso de registro de dispositivos en un proyecto de AEM Screens.

## Registro de un dispositivo {#registering-a-device}

El proceso de registro de dispositivos se realiza en dos equipos separados:

* El dispositivo real que se va a registrar, por ejemplo, la pantalla de señalización
* El servidor AEM que se utiliza para registrar el dispositivo

>[!NOTE]
>
>Una vez que descargue el último Reproductor de Windows (*.exe*), desde la página [AEM 6.4 Descargas del Reproductor](https://download.macromedia.com/screens/), siga los pasos del reproductor para completar la instalación ad hoc:
>
>1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
>1. Vaya a **Configuration** en el menú de acción de la izquierda, introduzca la dirección de ubicación de la instancia de AEM en **Server** y haga clic en **Save**.
>1. Haga clic en el enlace **Registration** del menú de acción de la izquierda y en los pasos siguientes para completar el proceso de registro del dispositivo.

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. En el dispositivo, inicie el Reproductor de AEM Screens. Se muestra la interfaz de usuario de registro.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. En AEM, vaya a la carpeta **Devices** del proyecto.

   >[!NOTE]
   >
   >Para obtener más información sobre la creación de un nuevo proyecto para Screens en el panel de AEM, consulte [Crear y administrar proyecto de Screens](creating-a-screens-project.md).

1. Toque o haga clic en el botón **Administrador de dispositivos** de la barra de acciones.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Toque o haga clic en el botón **Device Registration** en la parte superior derecha.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Seleccione el dispositivo requerido (igual que el paso 1) y toque o haga clic en **Registrar dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. En AEM, espere a que el dispositivo envíe su código de registro.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. En el dispositivo, compruebe el **Registration Code**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Si el **Código de registro** es el mismo en ambos equipos, pulse o haga clic en el botón **Validar** en AEM, como se muestra en el paso (6).
1. Establezca el nombre deseado para el dispositivo y haga clic en **Registrar**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Toque o haga clic en **Finish** para completar el proceso de registro.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >El **Registrar nuevo** permite registrar un nuevo dispositivo.
   >
   >La **Asignar pantalla** permite añadir directamente el dispositivo a una pantalla.

   Si hace clic en **Finish**, deberá asignar el dispositivo a una pantalla.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Para obtener más información sobre la creación y administración de una pantalla para su proyecto de Screens, consulte [Creación y administración de pantallas](managing-displays.md).

### Asignación del dispositivo a una pantalla {#assigning-device-to-a-display}

Si no ha asignado el dispositivo a una pantalla, siga los pasos a continuación para asignar el dispositivo a una pantalla de su proyecto de AEM Screens:

1. Seleccione el dispositivo y haga clic en **Asignar dispositivo** en la barra de acciones.

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. Seleccione la ruta de acceso de la visualización en **Display/Device Config Path**.

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. Haga clic en **Asignar** cuando seleccione la ruta.

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. Haga clic en **Finish** una vez que el dispositivo se haya asignado correctamente, como se muestra en la figura siguiente.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Además, puede ver el tablero de la pantalla al hacer clic en **Finish**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Búsqueda de un dispositivo desde el Administrador de dispositivos {#search-device}

Una vez que haya registrado dispositivos en su reproductor, puede ver todos los dispositivos desde la interfaz de usuario del Administrador de dispositivos.

1. Vaya a la interfaz de usuario del Administrador de dispositivos desde su proyecto de AEM Screens, por ejemplo, **DemoScreens** —> **Dispositivos**.

1. Seleccione la carpeta **Devices** y haga clic en **Device Manager** en la barra de acciones.

   ![image](/help/user-guide/assets/device-manager/device-manager-1.png)

1. Se muestra la lista de dispositivos registrados.

1. Si tiene una larga lista de dispositivos registrados, ahora puede buscar utilizando el icono de búsqueda de la barra de acciones

   ![image](/help/user-guide/assets/device-manager/device-manager-2.png)

   O bien,

   Haga clic en `/` (barra diagonal) para invocar la funcionalidad de búsqueda.

   ![image](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitaciones en la funcionalidad de búsqueda {#limitations}

* El usuario podrá buscar cualquier palabra existente en el *ID del dispositivo* o *Nombre del dispositivo*.

   >[!NOTE]
   >Se recomienda crear los nombres de los dispositivos con varias palabras, como *Boston Store Lobby* en lugar de con un solo *BostonStoreLobby*.

* Si crea nombres de dispositivos como *Boston Store Lobby*, permite buscar cualquier palabra *boston*, *store* o *vestíbulo*, pero si el nombre del dispositivo se denomina *BostonStoreLobby* al buscar *>boston* no mostrará los resultados.

* Comodín, `*` es compatible con la búsqueda. Si desea encontrar todos los dispositivos con nombres que empiecen por *boston*, puede utilizar *boston**.

* Si el nombre del dispositivo es *BostonStoreLobby* y la búsqueda de *Boston* no devolverá el resultado en su lugar utilizando *Boston** en los criterios de búsqueda, devolverá el resultado.

## Limitaciones en el registro de dispositivos {#limitations-on-device-registration}

Las restricciones de contraseña de usuario en todo el sistema podrían provocar un error en el registro del dispositivo. El registro del dispositivo utiliza una contraseña generada aleatoriamente para crear el usuario del dispositivo.

Si la contraseña está restringida por la configuración *AuthorizableActionProvider*, es posible que se produzca un error al crear el usuario del dispositivo.

>[!NOTE]
>
>La contraseña aleatoria generada actualmente se compone de 36 caracteres ASCII, que oscilan entre 33 y 122 (incluye casi todos los caracteres especiales).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Recursos adicionales {#additional-resources}

Para obtener más información sobre AEM Screens Player, consulte [AEM Screens Player](working-with-screens-player.md).
