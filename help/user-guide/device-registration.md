---
title: Registro de dispositivos
description: Obtenga información acerca del proceso de registro de dispositivos en un proyecto de AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Registro de dispositivos {#device-registration}

En la siguiente página se describe el proceso de registro de dispositivos en un proyecto de AEM Screens.

## Registro de un dispositivo {#registering-a-device}

El proceso de registro del dispositivo se realiza en dos equipos independientes:

* El dispositivo real que se va a registrar, por ejemplo, la pantalla de señalización
* AEM El servidor de utilizado para registrar el dispositivo

>[!NOTE]
>
>AEM Después de descargar el Reproductor de Windows más reciente (*.exe*), desde la página [Descargas del Reproductor de 6.4](https://download.macromedia.com/screens/), siga los pasos que aparecen en el reproductor para completar la instalación ad hoc:
>
>1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
>1. AEM Vaya a **Configuración** desde el menú de acción de la izquierda, escriba la dirección de ubicación de la instancia de la instancia en **Servidor** y haga clic en **Guardar**.
>1. Haga clic en el vínculo **Registro** del menú de acción de la izquierda y siga los pasos a continuación para completar el proceso de registro del dispositivo.
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. En el dispositivo, inicie AEM Screens Player. Se muestra la interfaz de usuario de registro.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. AEM En la carpeta **Dispositivos** de su proyecto, vaya a la carpeta de su proyecto.

   >[!NOTE]
   >
   >Para obtener más información sobre la creación de un proyecto para Screens AEM en el panel de control de, consulte [Crear y administrar un proyecto de Screens](creating-a-screens-project.md).

1. Haga clic en el botón **Administrador de dispositivos** de la barra de acciones.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Haga clic en el botón **Registro de dispositivo** en la parte superior derecha.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Haga clic en el dispositivo requerido (igual que en el paso 1) y luego haga clic en **Registrar dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. AEM En, espere a que el dispositivo envíe su código de registro.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. En tu dispositivo, comprueba el **Código de registro**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. AEM Si el **código de registro** es el mismo en ambos equipos, haga clic en el botón **Validar** en, tal y como se muestra en el paso (6).
1. Defina el nombre que desee para el dispositivo y haga clic en **Registrar**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Haga clic en **Finalizar** para completar el proceso de registro.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >**Registrar nuevo** le permite registrar un dispositivo nuevo.
   >
   >**Asignar pantalla** le permite agregar directamente el dispositivo a una pantalla.

   Si hace clic en **Finalizar**, asigne el dispositivo a una pantalla.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Para obtener más información sobre cómo crear y administrar una pantalla para el proyecto de Screens, consulte [Crear y administrar pantallas](managing-displays.md).

### Asignación de dispositivos a una pantalla {#assigning-device-to-a-display}

Si no ha asignado el dispositivo a una pantalla, siga los pasos a continuación para asignar el dispositivo a una pantalla del proyecto de AEM Screens:

1. Haga clic en el dispositivo y luego en **Asignar dispositivo** en la barra de acciones.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Haga clic en la ruta de acceso de la pantalla en **Ruta de acceso de configuración de pantalla/dispositivo**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Haga clic en **Asignar** al hacer clic en la ruta.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Haga clic en **Finalizar** una vez que el dispositivo se haya asignado correctamente, como se muestra en la figura siguiente.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Además, puede ver el panel de visualización seleccionando **Finalizar**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Búsqueda de un dispositivo desde el Administrador de dispositivos {#search-device}

Cuando haya registrado dispositivos en el reproductor, puede ver todos los dispositivos desde la interfaz de usuario del Administrador de dispositivos.

1. Vaya a la interfaz de usuario del Administrador de dispositivos desde su proyecto de AEM Screens, por ejemplo, **DemoScreens** > **Dispositivos**.

1. Haga clic en la carpeta **Dispositivos** y luego en **Administrador de dispositivos** en la barra de acciones.

   ![imagen](/help/user-guide/assets/device-manager/device-manager-1.png)

1. Se muestra la lista de dispositivos registrados.

1. Si tiene una larga lista de dispositivos registrados, ahora puede buscar mediante el icono de búsqueda de la barra de acciones

   ![imagen](/help/user-guide/assets/device-manager/device-manager-2.png)

   O bien,

   Seleccione `/` (barra diagonal) para invocar la funcionalidad de búsqueda.

   ![imagen](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitaciones en la funcionalidad de búsqueda {#limitations}

* El usuario puede buscar cualquier palabra que exista en *id. de dispositivo* o *nombre de dispositivo*.

  >[!NOTE]
  >Se recomienda crear los nombres de dispositivos con varias palabras, como *`Boston Store Lobby`*, en lugar de con un solo *`BostonStoreLobby`*.

* Si creó nombres de dispositivo como *`Boston Store Lobby`*, buscará cualquier palabra *`boston`*, *`store`* o *`lobby`*. Sin embargo, si el nombre del dispositivo es *`BostonStoreLobby`*, la búsqueda de *`boston`* no muestra ningún resultado.

* Se admite el comodín `*` para la búsqueda. Si desea encontrar todos los dispositivos con nombres que empiecen por *`boston`*, puede usar *`boston`**.

* Si el nombre del dispositivo es *`BostonStoreLobby`* y la búsqueda de *`boston`* no devuelve el resultado, al usar *`boston`** en los criterios de búsqueda se devuelve el resultado.

## Limitaciones en el registro de dispositivos {#limitations-on-device-registration}

Las restricciones de contraseña de usuario en todo el sistema pueden provocar errores en el registro de dispositivos. El registro del dispositivo utiliza una contraseña generada aleatoriamente para crear el usuario del dispositivo.

Si la configuración de *AuthorizableActionProvider* restringe la contraseña, es posible que se produzca un error al crear el usuario del dispositivo.

>[!NOTE]
>
>La contraseña aleatoria generada actualmente está compuesta por 36 caracteres ASCII, que van del 33 al 122 (incluye casi todos los caracteres especiales).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Otros recursos {#additional-resources}

Para obtener más información acerca del Reproductor de AEM Screens, consulte [Reproductor de AEM Screens](working-with-screens-player.md).
