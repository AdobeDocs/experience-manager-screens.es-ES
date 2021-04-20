---
title: Preguntas frecuentes sobre AEM Screens
seo-title: Preguntas frecuentes sobre AEM Screens
description: Siga esta página para obtener respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.
seo-description: Siga esta página para obtener respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
feature: Digital Signage, Content
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 1%

---


# Preguntas más frecuentes de AEM Screens {#aem-screens-faqs}

La siguiente sección proporciona respuestas a algunas de las preguntas frecuentes más frecuentes relacionadas con un proyecto de AEM Screens.

## Problema de pantalla en blanco {#blank-screen}

>[!NOTE]
>Las comprobaciones obligatorias enumeradas que deben ser probadas por el soporte principal o por el soporte del lado del cliente antes de plantear un problema.

### 1. ¿Cuáles deben ser los pasos de solución de problemas de First aid para cualquier cliente que se enfrente a una pantalla negra o a contenido que no se esté reproduciendo? {#troubleshooting-blank-screen}

* Compruebe si la vista previa del canal funciona.
* Comprobar si la vista previa de visualización funciona
* Intente registrar el reproductor como una extensión de navegador en su sistema en la misma pantalla y compruebe si funciona.
* Con el reproductor funcionando en su sistema, vaya a `http://localhost:24502`. Compruebe si todo el contenido se descarga correctamente.
* Compruebe los recursos que se han creado las representaciones adecuadas y que se está reproduciendo la representación correcta.
* Compruebe si hay contenido programado y si las horas son correctas. Compruebe si la hora configurada en el reproductor es correcta.
* Inspect utiliza los registros de la consola del reproductor y compruebe si hay errores. Haga clic con el botón derecho e inspeccione para ver los registros de la consola. Si utiliza el reproductor de windows, pulse `CTRL + ALT +I` para que aparezca la consola dev para ver los registros.

### 2. ¿Cómo resolver el problema de la pantalla gris en AEM Screens mediante la creación de un canal o programa predeterminado?

Para evitar las pantallas en blanco o en gris del campo, cree un canal global o una programación predeterminados, asignados a cada pantalla con la prioridad menos 1. En caso de que algo salga mal con las actualizaciones de contenido (debido a la red, el reproductor, el servidor o la replicación), ya que los reproductores ya tienen este contenido almacenado en caché en el disco, debería reproducirse bien y evitar las pantallas grises.

El resto del contenido, como los canales o las programaciones, tendrá prioridad buena a 1, por lo que el otro contenido tendrá prioridad y el contenido de programación o canal global (con prioridad 1) solo se reproducirá como opción de reserva.

## Administración de canales {#channel-management}

### 1. ¿Cuál es la diferencia entre un canal en línea y un canal sin conexión? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en línea*** mostrará el contenido actualizado en el entorno en tiempo real, mientras que ***un canal sin conexión*** muestra el contenido almacenado en caché.

### 2. ¿Cómo hago un canal en línea? {#how-do-i-make-a-channel-online}

Seleccione el canal y vaya a las propiedades del canal desde la barra de acciones. Marque **Developer mode (forzar el canal en línea)** en la pestaña **Channel** para que el canal esté en línea.

### 3. ¿Cuál es el uso del campo Rol del canal? {#what-is-the-use-of-the-channel-role-field}

La función de canal es la abstracción del canal real que se ejecuta para que el autor pueda centrarse directamente en la experiencia genérica. Puede considerarlo un tipo de etiqueta que identifica de forma exclusiva el canal en su contexto (visualización o programación).

### 4. ¿Cómo se produce la resolución real del canal? {#how-does-actual-channel-resolution-happen}

Para *referencias estáticas*, la resolución solo sigue la ruta especificada.

Para *referencias dinámicas*, la resolución se produce una vez que el canal se asigna a la visualización (no a la programación). La ruta de visualización se convierte en el contexto del canal y la resolución se produce de la siguiente manera (de la prioridad más alta a la más baja):

1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La pantalla tiene un nodo del mismo nivel que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia

Y así sucesivamente, hasta que llegue a la carpeta de ubicaciones y se detenga allí en ese momento (por lo que no puede hacer referencia a un canal que estaría en la carpeta de canales, por ejemplo, solo los canales en el subárbol de ubicaciones).

## Registro de dispositivos {#device-registration}

### 1. Si descubro extremos como solicitudes de incorporación y registro de dispositivos, puedo crear scripts de un gran número de dispositivos y registrar estos dispositivos. Además de bloquear esto a una sucursal Wi-Fi, ¿es posible asegurar estas solicitudes? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Actualmente, el registro solo es posible en la instancia de autor. Aunque el servicio de registro no está autenticado, solo creará un dispositivo pendiente en AEM y no registrará el dispositivo ni asignará ninguna pantalla.

Para registrar un dispositivo (lo que significa crear un usuario para el dispositivo en AEM), sigue siendo necesario autenticarse en AEM y actualmente seguir manualmente el asistente de registro para completar el registro. Teóricamente, un usuario malintencionado puede crear varios dispositivos pendientes, pero no puede registrar ninguno sin un inicio de sesión AEM.

### 2. ¿Existe alguna forma de transformar las solicitudes de GET HTTP en POST HTTP con alguna forma de autenticación? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La solicitud de registro es una solicitud del POST.

Se recomienda obtener el ID de dispositivo de la sesión en lugar de pasarlo como parámetro. Esto limpiaría los registros del servidor, la caché del explorador, etc. Actualmente no es un problema de seguridad. Tenga en cuenta que la GET semántica se utiliza cuando no hay ningún cambio de estado en el servidor y el POST se utiliza cuando hay un cambio de estado.

### 3. ¿Existe alguna forma de rechazar una solicitud de registro de dispositivos? {#is-there-a-way-to-decline-a-device-registration-request}

No puede rechazar las solicitudes de registro. En su lugar, las solicitudes de registro deben caducar después de un tiempo de espera configurado en [Adobe Experience Manager Web Console](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl). De forma predeterminada, este valor se establece en un día y se almacena en una caché de memoria.

## Informes de estado y monitorización de dispositivos {#device-monitoring-and-health-reports}

### 1. ¿Cómo puedo solucionar problemas si mi reproductor AEM Screens muestra una pantalla en blanco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Compruebe las siguientes posibilidades para solucionar el problema de la pantalla en blanco:

* AEM no puede insertar el contenido sin conexión
* El canal no tiene contenido
* Ninguno de los recursos está programado para mostrarse en este momento

### 2. ¿Qué puedo hacer si el reproductor AEM Screens no se puede registrar y su estado se muestra como Fallo? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Debe habilitar el filtro de referente Apache Sling Allow Empty. Esto es necesario para el funcionamiento óptimo del protocolo de control entre AEM Screens Player y el servidor de AEM Screens.

1. Vaya a **Configuración de la consola web de Adobe Experience Manager**
1. Marque la opción **allow.empty** .
1. Haga clic en **Guardar**.

### 3. ¿Cómo solucionar problemas si al registrar un reproductor de AEM Screens, el dispositivo muestra FAILURE y los registros de la consola muestran el error ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Este problema puede ocurrir si el reproductor no puede encontrar el DNS del servidor de AEM Screens. Puede intentar utilizar la dirección IP para conectarse. Para obtener la IP del servidor, utilice: *arp &lt;server_dns_name>*.

### 4. ¿AEM recomienda implementar un Watchdog para Android en todos los dispositivos? ¿Se incluye el complemento Watchdog (Cordova) como parte de la APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un control de Android multiplataforma que utiliza API de Android puras ya forma parte de la apk. No se necesita software adicional, pero dependiendo del dispositivo que utilice, es posible que tenga que renunciar al apk para obtener privilegios del sistema para un ciclo de alimentación completo (api de Powermanager). Si no se renuncia usando las claves del fabricante, se cerrará y reiniciará la aplicación, pero no el ciclo de alimentación.

Para obtener más información sobre cómo implementar el Reproductor de Android, consulte [**Implementación del Reproductor de Android**](implementing-android-player.md).

### 5. ¿Qué herramientas (software) de supervisión y alerta remota de terceros recomiendan Adobe/AMS para monitorizar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Dependiendo de lo que desee de la supervisión y las alertas, una nueva función que el servicio de notificaciones de AEM Screens le notifica si un dispositivo no ha pasado un rato por el ping. Las herramientas de terceros dependerán del sistema operativo (OS), de sus capacidades y de las necesidades específicas del cliente.

Para obtener más información sobre dónde puede monitorizar la actividad del dispositivo, consulte [**Servicio de notificaciones de AEM Screens**](screens-notifications-service.md).

## Reproductor de AEM Screens {#aem-screens-player}

### 1. ¿Cómo instalar el reproductor ChromeOS como complemento del explorador Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

El reproductor ChromeOS se puede instalar como complemento del explorador Chrome en el modo de desarrollador sin necesidad de un dispositivo de reproducción Chrome. Para la instalación, siga los pasos a continuación:

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar la última versión de Chrome Player.
1. Descomprima y guárdelo en el disco.
1. Abra el explorador Chrome y seleccione **Extensiones** en el menú o navegue directamente a ***chrome://extensions***.
1. Active el **Developer mode** desde la esquina superior derecha.
1. Haga clic en **Cargar desempaquetado** desde la esquina superior izquierda y cargue el reproductor Chrome descomprimido.
1. Compruebe el complemento **AEM Screens Chrome Player** si está disponible en la lista de extensiones.
1. Abra una nueva pestaña y haga clic en el icono **Aplicaciones** en la esquina superior izquierda o navegue directamente a ***chrome://apps***.
1. Haga clic en **AEM Screens** Plugin para iniciar Chrome Player. De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **esc** para salir del modo de pantalla completa.

### 2. ¿Cómo solucionar problemas si el reproductor Screens no puede autenticarse a través de la instancia de publicación con el controlador de error personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Cuando se inicia el reproductor AEM Screens, realiza una solicitud a ***/content/screens/svc.ping.json***, cuando el reproductor recibe un error 404. El reproductor inicia una solicitud de autenticación para autenticarse con la instancia de publicación. Si hay un controlador de error personalizado en la instancia de publicación, asegúrese de devolver el código de estado 404 para un usuario anónimo en ***/content/screens/svc.ping.json***.

### 3. ¿Cómo se establece la permanencia de la pantalla del dispositivo en un reproductor Android? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga los pasos a continuación para activar Permanecer despierto en cualquier reproductor Android:

1. Vaya a la configuración del reproductor Android —> **Acerca de**
1. Toque 7 veces en el número de compilación para habilitar **Opciones de desarrollador** en **Configuración**
1. Vaya a **Opciones de desarrollador**
1. Habilitar **Permanecer despierto**

### 4. ¿Cómo habilitar el modo de ventana para el reproductor de Windows?{#enable-player}

No hay ningún modo de ventana en el reproductor de Windows. Siempre es modo de pantalla completa.

### 5. ¿Cómo solucionar problemas si un reproductor de AEM Screens envía continuamente solicitudes de inicio de sesión?{#requests-login}

Siga los pasos a continuación para solucionar problemas de un reproductor de AEM Screens que envía solicitudes continuamente a `/content/screens/svc.json` y `/libs/granite/core/content/login.validate/j_security_check`:

1. Cuando se inicia el reproductor AEM Screens, se solicita a `/content/screens/svc.json`. Cuando el reproductor obtiene un código de estado 404 en la respuesta, inicia una solicitud de autenticación utilizando `/libs/granite/core/content/login.validate/j_security_check` contra la instancia *publish*. Si hay un controlador de error personalizado en la instancia *publish*, asegúrese de devolver el código de estado 404 para el usuario anónimo en `/content/screens/svc.json` o `/content/screens/svc.ping.json`.

1. Compruebe si la configuración de Dispatcher permite estas solicitudes en el `/filters`.

   Consulte [Configuración de filtros de Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) para obtener más información.

1. Compruebe si las reglas de reescritura de Dispatcher están reescribiendo cualquiera de las rutas de pantallas a una ruta diferente.

1. Compruebe si tiene reglas `/etc/map` en la instancia *author* o *publish* y si las rutas de acceso de las pantallas coinciden con `sling:match` y se redirigen internamente a una ruta diferente. La resolución de la dirección URL exacta en `/system/console/jcrresolver` ayuda a identificar si la instancia *publish* está reescribiendo estas direcciones URL en cualquier otra ruta.

1. Compruebe si la configuración de fábrica de Apache Sling Resource Resolver está causando reescrituras internas.

### 6. ¿Cómo obtener los detalles de la visualización y el dispositivo desde la API del reproductor?

Puede obtener los detalles de la pantalla y el dispositivo mediante:

* **una API de JS interna**
* **un almacén de ContextHub**: Se definen tres almacenes de ContextHub en  `/libs/screens/clientlibs/contexthub` para exponer canales, dispositivos e información de visualización.

   Siga los pasos a continuación para utilizar estos valores de almacenamiento de ContentHub:

   * Edite las propiedades del canal y establezca la ruta de ContextHub en la pestaña de personalización al valor (como se mencionó anteriormente)
   * En el canal JS, puede utilizar:

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## Consejos generales para la resolución de problemas {#general-troubleshooting-tips}

### 1. ¿Cómo deshabilitar Livefyre para evitar un error de Screens A/P? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Para deshabilitar Livefyre y evitar errores de registro :

1. ***Desactive el paquete Livefyre:***

   * Ir a `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Busque el paquete AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`
   * Haga clic en **Stop**

1. ***Desactive el encuestador de Livefyre:***

   * En el CRXDE Lite, vaya a `/etc/importers/polling/livefyre-poller/jcr:content`
   * Agregue una nueva propiedad *enabled* tipo *Boolean*
   * Establezca **la propiedad habilitada** en **false**

### 2. ¿Cómo añadir la información del índice Oak? {#add-oak-index-info}

AEM Screens crea definiciones de índice para las consultas utilizadas por el producto.
Si hay *Query Traversal WARNs* en el `error.log`, cree un índice personalizado para la consulta. Consulte [Configuración de los índices](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) para obtener más información.

También puede consultar un recurso adicional en [Documentación Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


