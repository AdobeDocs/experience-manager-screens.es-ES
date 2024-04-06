---
title: Preguntas frecuentes sobre AEM Screens
seo-title: AEM Screens FAQs
description: Siga esta página para obtener respuestas a las preguntas frecuentes relacionadas con un proyecto de AEM Screens.
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '2168'
ht-degree: 0%

---

# Preguntas frecuentes sobre AEM Screens {#aem-screens-faqs}

En la siguiente sección se proporcionan respuestas a algunas de las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.

## Problema de pantalla en blanco {#blank-screen}

>[!NOTE]
>Las comprobaciones obligatorias enumeradas que debe probar el servicio de asistencia primaria o el servicio de asistencia al cliente antes de plantear un problema.

### 1. ¿Cuáles deben ser los pasos de solución de problemas de primeros auxilios para cualquier cliente que se enfrente a una pantalla en negro o a contenido que no se esté reproduciendo? {#troubleshooting-blank-screen}

* Compruebe si la previsualización del canal funciona.
* Comprobar si la previsualización de visualización funciona
* Intente registrar el reproductor como una extensión de explorador en el sistema en la misma pantalla y compruebe si esto funciona.
* Con el reproductor en ejecución en el sistema, vaya a `http://localhost:24502`. Compruebe si todo el contenido se descarga correctamente.
* Compruebe los recursos que se han creado las representaciones adecuadas y que se está reproduciendo la representación correcta.
* Compruebe si hay contenido programado y si las horas son correctas. Compruebe si la hora configurada en el reproductor es correcta.
* Inspect inicia sesión en la consola del reproductor y comprueba si hay errores. Haga clic con el botón derecho e inspeccione para ver los registros de la consola. Si utiliza el reproductor de Windows, pulse `CTRL + ALT +I` para que aparezca dev console para ver los registros.

### 2. ¿Cómo resolver un problema de pantalla gris en AEM Screens al crear un canal o un horario predeterminado?

Para evitar las pantallas en blanco o grises en el campo, cree un canal global o una programación predeterminados, asignados a cada pantalla con la menor prioridad 1. En caso de que haya algún problema con las actualizaciones de contenido (debido a la red, el reproductor, el servidor o la replicación), ya que los reproductores ya tienen este contenido en la caché del disco, lo cual debería reproducirse correctamente y evitar las pantallas grises.

El resto del contenido, como canales o programaciones, tendrá una prioridad mayor que 1, por lo que el resto del contenido tiene prioridad y el contenido del canal global o de la programación (con prioridad 1) solo se reproducirá como opción de reserva.

## Administración de canales {#channel-management}

### 1. ¿Cuál es la diferencia entre un canal en línea y uno sin conexión? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***Canal en línea***, mostrará el contenido actualizado en el entorno de tiempo real, mientras que un ***Canal sin conexión***, muestra el contenido almacenado en caché.

### 2. ¿Cómo hago un canal en línea? {#how-do-i-make-a-channel-online}

Seleccione el canal y vaya a las propiedades del canal en la barra de acciones. Marque **Modo de desarrollador (forzar al canal a estar en línea)** bajo **Canal** para que el canal esté en línea.

### 3. ¿Cuál es el uso del campo Rol del canal? {#what-is-the-use-of-the-channel-role-field}

La función Canal es la abstracción del canal real que se ejecuta para que el autor pueda centrarse directamente en la experiencia genérica. Se puede considerar como un tipo de etiqueta que identifica de forma exclusiva el canal en su contexto (visualización o programación).

### 4. ¿Cómo se produce la resolución real del canal? {#how-does-actual-channel-resolution-happen}

Para *referencias estáticas*, la resolución solo sigue la ruta especificada.

Para *referencias dinámicas*, la resolución se produce una vez que el canal se asigna a la pantalla (no a la programación). La ruta de visualización se convierte en el contexto del canal y la resolución se produce de la siguiente manera (de mayor a menor prioridad):

1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la visualización tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal general de la visualización tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia

Y así sucesivamente, hasta que llegue a la carpeta de ubicaciones y se detenga allí en el momento (por lo que no puede hacer referencia a un canal que estaría en la carpeta de canales, por ejemplo, solo a canales en el subárbol de ubicaciones).

### 5. ¿Cómo configurar la configuración sin conexión clientlib personalizada en el canal de AEM Screens?

Cuando se utiliza un código personalizado integrado del lado del cliente `clientlib` en un canal de AEM Screens, se deben realizar los siguientes pasos para asegurarse de que la variable `clientlib` Los archivos de se han cargado correctamente en el canal (`manifest.json`) y contendrán la ruta del `clientlib`.

Siga los pasos a continuación desde el editor de canales:

1. Seleccione un canal y haga clic en **Editar** en la barra de acciones para abrir el editor de canales.
1. Seleccione el componente en el que desea agregar el personalizado `clientlib`.
1. Haga clic en el botón de configuración (el icono de la llave inglesa).
1. Vaya a **Configuración sin conexión** y agregue la ruta a la clientlib personalizada en **Bibliotecas del lado del cliente**.

## Registro de dispositivos {#device-registration}

### 1. Si descubro puntos finales como solicitudes de incorporación y registro de dispositivos, puedo crear una secuencia de comandos de un gran número de dispositivos y registrarlos. Además de bloquear esto a una sucursal Wi-Fi, ¿es posible asegurar estas solicitudes? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Actualmente, el registro solo es posible en la instancia de autor. AEM Aunque el servicio de registro no está autenticado, solo creará un dispositivo pendiente en el sistema de registro y no registrará el dispositivo ni asignará ninguna pantalla.

AEM AEM Para registrar un dispositivo (lo que significa crear un usuario para el dispositivo en el que se ha realizado el registro), aún debe autenticarse para el registro y, en la actualidad, seguir manualmente el asistente de registro para completar el registro. AEM Teóricamente, un usuario malintencionado puede crear varios dispositivos pendientes, pero no puede registrar ninguno sin iniciar sesión en un servicio de inicio de sesión de la aplicación de la aplicación de forma.

### 2. ¿Existe alguna manera de transformar las solicitudes de GET HTTP en un POST HTTP con alguna forma de autenticación? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La solicitud de registro es una solicitud de POST.

Se recomienda obtener el ID del dispositivo de la sesión en lugar de pasarlo como parámetro. Esto limpiaría los registros del servidor, la caché del explorador, etc. Actualmente no es un problema de seguridad. Tenga en cuenta que se utiliza semánticamente la GET cuando no hay ningún cambio de estado en el servidor y el POST cuando hay un cambio de estado.

### 3. ¿Hay alguna manera de rechazar una solicitud de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

No puede rechazar las solicitudes de registro. En su lugar, las solicitudes de registro deben caducar después de un tiempo de espera que se haya configurado en `Adobe Experience Manager Web Console`. De forma predeterminada, este valor se establece en un día y se almacena en una caché de memoria.

## Monitorización de dispositivos e informes de estado {#device-monitoring-and-health-reports}

### 1. ¿Cómo puedo solucionar problemas si mi reproductor de AEM Screens muestra una pantalla en blanco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Compruebe las siguientes posibilidades para solucionar el problema de la pantalla en blanco:

* AEM No se ha podido insertar el contenido sin conexión
* El canal no tiene ningún contenido
* Ninguno de los recursos está programado para mostrarse en este momento

### 2. ¿Qué puedo hacer si el reproductor AEM Screens no se puede registrar y su estado se muestra como Error? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Debe habilitar la opción Permitir que el filtro de referente de Apache Sling esté vacío. Esto es necesario para un funcionamiento óptimo del protocolo de control entre el reproductor de AEM Screens y el servidor de AEM Screens.

1. Vaya a **Configuración de la consola web Adobe Experience Manager**
1. Compruebe la **allow.empty** opción.
1. Haga clic en **Guardar**.

### 3. ¿Cómo solucionar problemas si al registrar un reproductor AEM Screens, el dispositivo muestra FAILURE y los registros de la consola muestran un error ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Este problema puede ocurrir si el reproductor no puede encontrar el DNS del servidor de AEM Screens. Puede intentar utilizar la dirección IP para conectarse. Para obtener la IP del servidor, utilice: *arp &lt;server_dns_name>*.

### 4. ¿AMS recomienda implementar un Android Watchdog en todos los dispositivos? ¿El complemento Watchdog (Cordova) está incluido como parte del APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un perro guardián de Android multiplataforma que utiliza API de Android puras ya es parte del apk. No se necesita software adicional, pero dependiendo del dispositivo que use, es posible que tenga que renunciar al apk para obtener privilegios del sistema para un ciclo de energía completo (api Powermanager). Si no se resigna con las claves del fabricante, se cerrará y se reiniciará la aplicación, pero no el ciclo de alimentación.

Para obtener más información sobre la implementación del Reproductor de Android, consulte [**Implementación del reproductor Android**](implementing-android-player.md).

### 5. ¿Qué herramientas (software) de monitorización y alertas remotas de terceros recomienda Adobe/AMS para monitorizar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Según lo que desee en las alertas de monitorización, un nuevo servicio de notificaciones de AEM Screens le notificará si un dispositivo no ha hecho ping en un tiempo. Las herramientas de terceros dependerán del sistema operativo, de sus capacidades y de las necesidades específicas del cliente.

Para obtener más información sobre dónde puede monitorizar la actividad del dispositivo, consulte [**Servicio de notificaciones de AEM Screens**](screens-notifications-service.md).

## Reproductor de AEM Screens {#aem-screens-player}

### 1. ¿Cómo instalar el reproductor ChromeOS como complemento del navegador Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

El reproductor ChromeOS se puede instalar como complemento del explorador Chrome en el modo de desarrollador sin requerir el dispositivo de reproductor Chrome real. Para la instalación, siga los pasos a continuación:

1. Clic [aquí](https://download.macromedia.com/screens/) para descargar el último reproductor de Chrome.
1. Descomprima y guárdelo en el disco.
1. Abra el navegador Chrome y seleccione **Extensiones** en el menú o vaya directamente a ***chrome://extensions***.
1. Encienda el **Modo de desarrollador** desde la esquina superior derecha.
1. Haga clic en **Cargar desempaquetado** desde la esquina superior izquierda y cargue el reproductor Chrome sin comprimir.
1. Marque **Reproductor de AEM Screens Chrome** complemento si está disponible en la lista de extensiones.
1. Abra una nueva pestaña y haga clic en **Aplicaciones** desde la esquina superior izquierda o navegue directamente a ***chrome://apps***.
1. Haga clic en **AEM Screens** Complemento para iniciar el reproductor Chrome. De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Prensa **esc** para salir del modo de pantalla completa.

### 2. ¿Cómo solucionar problemas si el reproductor Screens no puede autenticarse a través de la instancia de publicación con el controlador de error personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Cuando se inicia el reproductor de AEM Screens, se realiza una solicitud a ***/content/screens/svc.ping.json***, cuando el reproductor recibe un error 404. El reproductor inicia una solicitud de autenticación para autenticarse en la instancia de publicación. Si hay un controlador de error personalizado en la instancia de publicación, asegúrese de devolver el código de estado 404 para el usuario anónimo en ***/content/screens/svc.ping.json***.

### 3. ¿Cómo configurar la pantalla del dispositivo para que permanezca encendida en un reproductor Android? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga los pasos a continuación para activar Permanecer despierto en cualquier reproductor de Android:

1. Vaya a Configuración del reproductor de Android > **Acerca de**
1. Pulse 7 veces en el número de compilación para habilitar **Opciones de desarrollador** in **Configuración**
1. Vaya a **Opciones de desarrollador**
1. Activar **Manténgase despierto**

### 4. ¿Cómo activar el modo de ventana para el reproductor de Windows?{#enable-player}

No hay modo de ventana en el reproductor de Windows. Siempre es modo de pantalla completa.

### 5. ¿Cómo solucionar problemas si un reproductor de AEM Screens envía continuamente solicitudes de inicio de sesión?{#requests-login}

Siga los pasos a continuación para solucionar problemas de un reproductor de AEM Screens que envía solicitudes continuamente a `/content/screens/svc.json` y `/libs/granite/core/content/login.validate/j_security_check`:

1. Cuando se inicia el reproductor de AEM Screens, solicita a `/content/screens/svc.json`. Cuando el reproductor obtiene un código de estado 404 en la respuesta, inicia una solicitud de autenticación utilizando `/libs/granite/core/content/login.validate/j_security_check` contra el *publicar* ejemplo. Si hay un controlador de error personalizado en *publicar* Por ejemplo, asegúrese de devolver el código de estado 404 para el usuario anónimo en `/content/screens/svc.json` o `/content/screens/svc.ping.json`.

1. Compruebe si la configuración de Dispatcher permite estas solicitudes en la `/filters`.

   Consulte [Configuración de filtros de Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) para obtener más información.

1. Compruebe si las reglas de reescritura de Dispatcher están reescribiendo cualquiera de las rutas de pantallas a una ruta diferente.

1. Compruebe si tiene `/etc/map` reglas sobre *autor* o *publicar* las rutas de instancia y pantallas coinciden con `sling:match` y se redirige internamente a una ruta diferente. Resolución de la dirección URL exacta en `/system/console/jcrresolver` ayuda a identificar si la variable *publicar* está reescribiendo estas direcciones URL en cualquier otra ruta.

1. Compruebe si la configuración de la fábrica de Apache Sling Resource Resolver está causando reescrituras internas.

### 6. ¿Cómo obtener los detalles de la pantalla y el dispositivo desde la API del reproductor?

Puede obtener los detalles de la pantalla y el dispositivo a través de:

* **una API de JS interna**
* **una tienda de ContextHub**: Hay tres tiendas de ContextHub definidas en `/libs/screens/clientlibs/contexthub` para exponer canales, dispositivos y, muestre información.

  Siga los pasos a continuación para utilizar estos valores de tienda de ContentHub:

   * Edite las propiedades del canal y establezca la ruta de ContextHub en la pestaña de personalización con el valor (como se ha mencionado anteriormente)
   * En el JS de canal, puede utilizar lo siguiente:

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## Sugerencias generales de resolución de problemas {#general-troubleshooting-tips}

### 1. ¿Cómo deshabilitar Livefyre para evitar errores de pantallas A/P? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Para deshabilitar Livefyre y evitar errores de registro:

1. ***Deshabilitar paquete de Livefyre:***

   * Navegue hasta `https://<host>:<port>/system/console/bundles`
   * AEM Busque el paquete de Livefyre de la: `com.adobe.cq.social.cq-social-livefyre`
   * Clic **Detener**

1. ***Deshabilitar sondeo de Livefyre:***

   * En CRXDE Lite, vaya a `/etc/importers/polling/livefyre-poller/jcr:content`
   * Añadir una nueva propiedad *activado* type *Booleano*
   * Establecer **propiedad enabled** hasta **false**

### 2. ¿Cómo agregar información del índice Oak? {#add-oak-index-info}

AEM Screens crea definiciones de índice para las consultas utilizadas por el producto.
Si hay alguna *ADVERTENCIAS de recorrido de consulta* en el `error.log`, cree un índice personalizado para la consulta. Consulte [Configuración de los índices](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) para obtener más información.

También puede consultar un recurso adicional en [Documentación de Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. ¿Qué se necesita para configurar los manifiestos de la versión 3? {#configure-v3}

Para habilitar el manifiesto v3, debe:

* Actualice Dispatcher.
Consulte [Configurar Dispatcher para la versión 3 del manifiesto](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) para obtener más información.

* Actualizar componente personalizado.
Consulte [Plantilla para controladores personalizados](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) para obtener más información.

* Deshabilitar ContentSync en `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Habilitar SmartSync en `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Editar `channel/experience fragment/page components`.

* Vaya a **Configuración sin conexión** pestaña.

* Entrar `clientlibs `y carpetas para archivos estáticos que deben agregarse al manifiesto.

### 4. ¿Qué debe hacer si, después del paquete screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 y los paquetes principales de screens están instalados pero no están activos?

AEM Debe instalar una versión mínima del paquete de funciones 8 de 6.5 para que funcione el conector AMS. Consulte la [Disponibilidad](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) para obtener la versión mínima del paquete de funciones de Screens.

### 5. ¿Cómo configurar el servicio CQ Link Externalizer en Screens?

El servicio se utiliza para definir el nombre de host público para las instancias de autor y publicación, y los valores se utilizan para actualizar las URL del servidor de dispositivos y también para la segmentación de ContextHub.

El servicio CQ Link Externalizer en Screens se puede configurar mediante:

1. Navegue hasta `http://localhost:4502/system/console/configMgr`
1. Externalizador de vínculos CQ de día
1. Cambie el nombre de host para `author/publish` entradas según sea necesario