---
title: Preguntas más frecuentes sobre AEM Screens
seo-title: Preguntas más frecuentes sobre AEM Screens
description: Siga esta página para obtener respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.
seo-description: Siga esta página para obtener respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: c615481f606a369fb9d4bafde74cbf00458f05fa
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 2%

---


# Preguntas más frecuentes sobre AEM Screens {#aem-screens-faqs}

La siguiente sección proporciona respuestas a algunas de las preguntas más frecuentes más frecuentes relacionadas con un proyecto de AEM Screens.

## Administración de Canales {#channel-management}

### 1. ¿Cuál es la diferencia entre un canal en línea y otro sin conexión? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en línea*** mostrará el contenido actualizado en el entorno en tiempo real, mientras que ***un canal sin conexión*** muestra el contenido almacenado en caché.

### 2. ¿Cómo hago un canal en línea? {#how-do-i-make-a-channel-online}

Seleccione el canal y vaya a las propiedades del canal desde la barra de acciones. Marque el modo **de desarrollador (forzar el canal a estar en línea)** en la ficha **Canal** para que el canal esté en línea.

### 3. ¿Cuál es el uso del campo Función de Canal? {#what-is-the-use-of-the-channel-role-field}

La función de Canal es la abstracción del canal real que se ejecuta para que el autor pueda centrarse directamente en la experiencia genérica. Puede considerarlo una especie de etiqueta que identifica de forma exclusiva al canal en su contexto (visualización o programación).

### 4. ¿Cómo se produce la resolución real del canal? {#how-does-actual-channel-resolution-happen}

Para las referencias ** estáticas, la resolución simplemente sigue la ruta especificada.

En el caso de las referencias ** dinámicas, la resolución se produce una vez que el canal está asignado a la visualización (no a la programación). La ruta de visualización se convierte en el contexto del canal y la resolución se produce de la siguiente manera (de la prioridad más alta a la más baja):

1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La pantalla tiene un nodo del mismo nivel que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia

Y así sucesivamente, hasta que llegue a la carpeta de ubicaciones y se detenga allí en este momento (por lo que no puede hacer referencia a un canal que estaría en la carpeta de canales, por ejemplo, solo canales en el subárbol de ubicaciones).

## Registro de dispositivos {#device-registration}

### 1. Si descubro extremos como solicitudes de integración y registro de dispositivos, puedo crear un script con un gran número de dispositivos y registrar estos dispositivos. Además de bloquear esto a una sucursal Wi-Fi, ¿es posible asegurar estas solicitudes? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Actualmente, el registro solo es posible en la instancia de autor. Aunque el servicio de registro no está autenticado, solo creará un dispositivo pendiente en AEM y no registrará el dispositivo ni asignará ninguna visualización.

Para registrar un dispositivo (lo que significa crear un usuario para el dispositivo en AEM), debe autenticarse en AEM y seguir manualmente el asistente para el registro para completar el registro. En teoría, un usuario malintencionado puede crear varios dispositivos pendientes pero no puede registrarse sin un inicio de sesión de AEM.

### 2. ¿Existe alguna forma de transformar las solicitudes HTTP GET en HTTP POST con alguna forma de autenticación? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La solicitud de registro es una solicitud POST.

Se recomienda obtener el ID del dispositivo de la sesión en lugar de pasarlo como parámetro. Esto limpiaría los registros del servidor, la caché del explorador, etc. Actualmente no se trata de un problema de seguridad. Tenga en cuenta que GET semánticamente se utiliza cuando no hay ningún cambio de estado en el servidor y POST se utiliza cuando hay un cambio de estado.

### 3. ¿Existe alguna forma de rechazar una solicitud de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

No puede rechazar las solicitudes de registro. En su lugar, las solicitudes de registro deben caducar después de un tiempo de espera configurado en la consola [web de](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)Adobe Experience Manager. De forma predeterminada, este valor se establece en un día y se almacena en una caché de memoria.

## Informes de estado y supervisión de dispositivos {#device-monitoring-and-health-reports}

### 1. ¿Cómo puedo solucionar problemas si mi reproductor de AEM Screens muestra la pantalla en blanco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Compruebe las siguientes posibilidades para solucionar el problema de la pantalla en blanco:

* AEM no puede insertar el contenido sin conexión
* Canal no tiene contenido
* Ninguno de los recursos está programado para mostrarse en este momento

### 2. ¿Qué puedo hacer si el reproductor de AEM Screens no se puede registrar y su estado se muestra como Error? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Debe activar el filtro Remitente del reenvío Sling de Apache para permitir que esté vacío. Esto es necesario para el funcionamiento óptimo del protocolo de control entre AEM Screens Player y el servidor de AEM Screens.

1. Vaya a Configuración de la consola web de **Adobe Experience Manager**
1. Marque la opción **allow.empty** .
1. Haga clic en **Guardar**.

### 3. ¿Cómo solucionar problemas si al registrar un reproductor de AEM Screens, el dispositivo muestra FALLO y los registros de la consola muestran el error ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Este problema puede producirse si el reproductor no puede encontrar el DNS del servidor de pantallas de AEM. Puede intentar utilizar la dirección IP para conectarse. Para obtener la IP del servidor, utilice: *arp &lt;server_dns_name>*.

### 4. ¿AMS recomienda implementar un Watchdog para Android en todos los dispositivos? ¿Se incluye el complemento Watchdog (Cordova) como parte de la APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un organismo de control de Android multiplataforma que utiliza API de Android puras ya forma parte del paquete. No se necesita ningún software adicional, pero en función del dispositivo que utilice, es posible que tenga que renunciar al apk para obtener privilegios del sistema para un ciclo de alimentación completo (PowerManager api). Si no se renuncia usando las claves del fabricante, se cerrará y reiniciará la aplicación pero no el ciclo de alimentación.

Para obtener más información sobre cómo implementar el Reproductor de Android, consulte [**Implementación de dicho Reproductor **](implementing-android-player.md).

### 5. ¿Qué herramientas (software) de supervisión y alerta remota de terceros recomienda Adobe/AMS para supervisar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Según lo que desee del monitoreo y las alertas, una nueva función del servicio de notificaciones de pantallas de AEM le notifica si un dispositivo no ha pasado un rato. Las herramientas de terceros dependerán del sistema operativo (SO), sus capacidades y las necesidades específicas del cliente.

Para obtener más información sobre dónde puede supervisar la actividad de dispositivos, consulte el servicio [**de notificaciones de pantallas de **](screens-notifications-service.md)AEM.

## Reproductor de AEM Screens {#aem-screens-player}

### 1. ¿Cómo instalar el reproductor ChromeOS como complemento Chrome Browser? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

El reproductor ChromeOS se puede instalar como complemento Chrome Browser en el modo de desarrollador sin necesidad de un dispositivo de reproducción Chrome. Para la instalación, siga los pasos a continuación:

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar la versión más reciente de Chrome Player.
1. Descomprima y guárdelo en el disco.
1. Abra el navegador Chrome y seleccione **Extensiones** en el menú o navegue directamente a ***chrome://extensions***.
1. Encienda el modo **de** desarrollador desde la esquina superior derecha.
1. Haga clic en **Cargar sin empaquetar** desde la esquina superior izquierda y cargue el reproductor Chrome sin comprimir.
1. Compruebe **AEM Screens Chrome Player** si está disponible en la lista de extensiones.
1. Abra una nueva ficha y haga clic en el icono **Aplicaciones** en la esquina superior izquierda o navegue directamente a ***chrome://apps***.
1. Haga clic en **AEM Screens** Plugin para iniciar Chrome Player. De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **esc** para salir del modo de pantalla completa.

### 2. ¿Cómo solucionar problemas si el reproductor de Pantallas no puede autenticarse mediante la instancia de publicación con un controlador de error personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Cuando AEM Screens Player inicio, realiza una solicitud a ***/content/screens/svc.ping.json***, cuando el reproductor recibe un error 404. El reproductor inicia una solicitud de autenticación para autenticarse con la instancia de publicación. Si hay un controlador de error personalizado en la instancia de publicación, asegúrese de devolver el código de estado 404 para un usuario anónimo en ***/content/screens/svc.ping.json***.

### 3. ¿Cómo configurar la permanencia de la pantalla del dispositivo en un reproductor de Android? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga los pasos a continuación para activar Permanecer despierto en cualquier reproductor de Android:

1. Vaya a la configuración del reproductor de Android —> **Acerca de**
1. Toque 7 veces en el número de compilación para habilitar las opciones **de** desarrollador en **Configuración**
1. Vaya a Opciones **de desarrollador**
1. Habilitar **Permanecer despierto**

## Sugerencias generales para la resolución de problemas {#general-troubleshooting-tips}

### 1. ¿Cómo desactivar Livefyre para evitar un error en las pantallas A/P? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Para deshabilitar Livefyre para evitar errores de registro:

1. ***Deshabilitar paquete Livefyre:***

   * Ir a `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Busque el paquete de AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`
   * Haga clic en **Detener**

1. ***Deshabilitar el sondeo de Livefyre:***

   * En CRXDE Lite, vaya a `/etc/importers/polling/livefyre-poller/jcr:content`
   * Añadir una nueva propiedad *habilitada* tipo *Boolean*
   * Establecer la propiedad **** enabled en **false**

