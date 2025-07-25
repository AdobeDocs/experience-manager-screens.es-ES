---
title: Preguntas frecuentes sobre AEM Screens
description: Respuestas a preguntas frecuentes relacionadas con un proyecto de AEM Screens.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 0%

---

# Preguntas frecuentes sobre AEM Screens {#aem-screens-faqs}

En este tema encontrará respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.

## Problema de pantalla en blanco {#blank-screen}

>[!NOTE]
>La variable obligatoria indicada comprueba que el servicio de asistencia primaria o el servicio de asistencia al cliente deben probarse antes de plantear un problema.

### &#x200B;1. ¿Cuáles deben ser los pasos de solución de problemas de primeros auxilios para cualquier cliente que se enfrente a una pantalla en negro o a contenido que no se esté reproduciendo? {#troubleshooting-blank-screen}

* Compruebe si la previsualización del canal funciona.
* Comprobar si la previsualización de visualización funciona
* Intente registrar el reproductor como una extensión de explorador en el sistema en la misma pantalla y compruebe si funciona.
* Con el reproductor en ejecución en el sistema, vaya a `http://localhost:24502`. Compruebe si todo el contenido se descarga correctamente.
* Compruebe los recursos para asegurarse de que se crean las representaciones adecuadas y de que se reproduce la representación correcta.
* Compruebe si hay contenido programado y si las horas son correctas. Compruebe si la hora configurada en el reproductor es correcta.
* Inspeccione los registros de la consola del reproductor y compruebe si hay errores. Haga clic con el botón derecho e inspeccione para ver los registros de la consola. Si está usando el Reproductor de Windows, presione `CTRL + ALT +I` para que aparezca la consola de desarrollo y se vean los registros.

### &#x200B;2. ¿Cómo resolver un problema de pantalla gris en AEM Screens al crear un canal o un horario predeterminado?

Para evitar las pantallas en blanco o grises en el campo, cree un canal global o una programación predeterminados, asignados a cada pantalla con la menor prioridad 1. En caso de que algo salga mal con las actualizaciones de contenido, porque los reproductores ya han almacenado este contenido en caché en el disco. Debe jugar bien y evitar las pantallas grises.

El resto del contenido, como canales o programaciones, tiene una prioridad mayor que 1, por lo que el otro contenido tiene prioridad y el contenido del canal global o de la programación (con prioridad 1) solo se reproduce como opción de reserva.

## Administración de canales {#channel-management}

### &#x200B;1. ¿Cuál es la diferencia entre un canal en línea y uno sin conexión? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en línea*** muestra el contenido actualizado en tiempo real, mientras que un ***canal sin conexión*** muestra el contenido almacenado en caché.

### &#x200B;2. ¿Cómo hago un canal en línea? {#how-do-i-make-a-channel-online}

Haga clic en el canal y navegue hasta las propiedades del canal desde la barra de acciones. Marque el **modo de desarrollador (forzar al canal a estar en línea)** en la ficha **Canal** para que el canal esté en línea.

### &#x200B;3. ¿Cuál es el uso del campo Rol del canal? {#what-is-the-use-of-the-channel-role-field}

La función Canal es la abstracción del canal real que se ejecuta para que el autor pueda centrarse directamente en la experiencia genérica. Se puede considerar como un tipo de etiqueta que identifica de forma exclusiva el canal en su contexto (visualización o programación).

### &#x200B;4. ¿Cómo se produce la resolución real del canal? {#how-does-actual-channel-resolution-happen}

Para *referencias estáticas*, la resolución solo sigue la ruta especificada.

Para *referencias dinámicas*, la resolución se produce una vez que el canal se asigna a la pantalla (no a la programación). La ruta de visualización se convierte en el contexto del canal y la resolución se produce de la siguiente manera (de mayor a menor prioridad):

1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la visualización tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal general de la visualización tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia

Y así sucesivamente, hasta que llegue a la carpeta de ubicaciones. Deténgase en este momento (para que no pueda hacer referencia a un canal que estaría en la carpeta de canales, por ejemplo, solo a canales del subárbol de ubicación).

### &#x200B;5. ¿Cómo configurar la configuración sin conexión clientlib personalizada en el canal de AEM Screens?

Al utilizar un código personalizado del lado del cliente `clientlib` creado en un canal de AEM Screens, son necesarios los siguientes pasos. Los pasos garantizan que los archivos de `clientlib` se carguen correctamente en el canal (`manifest.json`) y que contengan la ruta de acceso de `clientlib`.

Siga los pasos a continuación desde el editor de canales:

1. Haga clic en un canal y luego en **Editar** en la barra de acciones.
1. Haga clic en el componente donde desee agregar el(la) `clientlib` personalizado(a).
1. Haga clic en el botón de configuración (el icono de la llave inglesa ).
1. Vaya a la pestaña **Configuración sin conexión** y agregue la ruta a su clientlib personalizada en **Bibliotecas del lado del cliente**.

## Registro de dispositivos {#device-registration}

### &#x200B;1. Si descubro puntos finales como solicitudes de incorporación y registro de dispositivos, puedo crear secuencias de comandos de muchos dispositivos y registrarlos. Además de bloquearlo en una sucursal Wi-Fi, ¿es posible asegurar estas solicitudes? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Actualmente, el registro solo es posible en la instancia de autor. Aunque el servicio de registro no está autenticado, solo crea un dispositivo pendiente en AEM y no registra el dispositivo ni asigna ninguna visualización.

Para registrar un dispositivo (crear un usuario para el dispositivo en AEM), realice la autenticación en AEM y siga manualmente el asistente de registro para completar el registro. En teoría, un usuario malintencionado puede crear varios dispositivos pendientes, pero no puede registrar ninguno si no tiene un inicio de sesión de AEM.

### &#x200B;2. ¿Existe alguna manera de transformar las solicitudes HTTP GET en HTTP POST con alguna forma de autenticación? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La solicitud de registro es una solicitud de POST.

Se recomienda obtener el ID del dispositivo de la sesión en lugar de pasarlo como parámetro. Al hacerlo, se limpian los registros del servidor, la caché del explorador, etc. No es un problema de seguridad. Semánticamente. GET se utiliza cuando no hay ningún cambio de estado en el servidor y POST se utiliza cuando hay un cambio de estado.

### &#x200B;3. ¿Hay alguna manera de rechazar una solicitud de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

No puede rechazar las solicitudes de registro. En su lugar, las solicitudes de registro deben caducar después de un tiempo de espera que se ha configurado en `Adobe Experience Manager Web Console`. De forma predeterminada, este valor se establece en un día y se almacena en una caché de memoria.

## Monitorización de dispositivos e informes de estado {#device-monitoring-and-health-reports}

### &#x200B;1. ¿Cómo puedo solucionar problemas si mi reproductor de AEM Screens muestra una pantalla en blanco?

Compruebe las siguientes posibilidades para solucionar el problema de la pantalla en blanco:

* AEM no puede insertar el contenido sin conexión
* El canal no tiene ningún contenido
* No se ha programado la visualización de ninguno de los recursos en este momento

### &#x200B;2. ¿Qué puedo hacer si el Reproductor de AEM Screens no se puede registrar y su estado se muestra como Error?

Active el Filtro de referente de Apache Sling Permitir vacío. Necesario para un funcionamiento óptimo del protocolo de control entre el Reproductor de AEM Screens y el servidor de AEM Screens.

1. Vaya a **Configuración de la consola web de Adobe Experience Manager**
1. Marque la opción **allow.empty**.
1. Haga clic en **Guardar**.

### &#x200B;3. ¿Cómo solucionar problemas si al registrar un reproductor de AEM Screens, el dispositivo muestra FAILURE y los registros de la consola muestran un error ENAME_NOT_FOUND?

Este problema puede ocurrir si el reproductor no puede encontrar el DNS del servidor de AEM Screens. Puede intentar utilizar la dirección IP para conectarse. Para obtener la IP del servidor, use: *arp &lt;server_dns_name>*.

### &#x200B;4. ¿AMS recomienda implementar un Android™ Watchdog en todos los dispositivos? ¿El complemento Watchdog (Cordova) está incluido como parte del APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Ya forma parte del apk un vigilante multiplataforma de Android™ que utiliza API puras de Android™. No se necesita software adicional. Sin embargo, dependiendo del dispositivo que use, puede renunciar al apk para obtener privilegios del sistema para un ciclo de energía completo (`Powermanager` api), si es necesario. Si no se resigna con las claves del fabricante, se cierra y se reinicia la aplicación, pero no se apaga.

Para obtener más información sobre cómo implementar el reproductor Android™, consulte [**Implementación del reproductor Android™**](implementing-android-player.md).

### &#x200B;5. ¿Qué herramientas (software) de monitorización y alertas remotas de terceros recomienda Adobe/AMS para monitorizar cada dispositivo? {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Según lo que desee en las alertas de monitorización, un nuevo servicio de notificaciones de AEM Screens le notificará si un dispositivo no ha hecho ping en un tiempo. Las herramientas de terceros dependen del sistema operativo, de sus capacidades y de las necesidades específicas del cliente.

Para obtener más información sobre dónde puede supervisar la actividad del dispositivo, consulte [**Servicio de notificaciones ns en pantalla de AEM**](screens-notifications-service.md).

## Reproductor de AEM Screens

### &#x200B;1. ¿Cómo instalar el reproductor ChromeOS como complemento del explorador Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

El reproductor ChromeOS se puede instalar como complemento del explorador de Chrome en modo de desarrollador sin necesidad de un dispositivo Chrome Player real. Para la instalación, siga los pasos a continuación:

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar el último reproductor de Chrome.
1. Descomprima y guárdelo en el disco.
1. Abra el explorador Chrome y haga clic en **Extensiones** en el menú o vaya directamente a ***chrome://extensions***.
1. Encienda el **modo de desarrollador** desde la esquina superior derecha.
1. Haga clic en **Cargar desempaquetado** en la esquina superior izquierda y cargue el reproductor de Chrome descomprimido.
1. Si está disponible en la lista de extensiones, consulte el complemento **AEM Screens Chrome Player**.
1. Abra una ficha nueva y haga clic en el icono **Aplicaciones** desde la esquina superior izquierda o navegue directamente a ***chrome://apps***.
1. Haga clic en el complemento **AEM Screens**. De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **Esc** para salir del modo de pantalla completa.

### &#x200B;2. ¿Cómo solucionar problemas si el reproductor de Screens no puede autenticarse a través de una instancia de publicación con un controlador de error personalizado?

Cuando se inicia el Reproductor de AEM Screens, realiza una solicitud a ***/content/screens/svc.ping.json***, cuando el reproductor recibe un error 404. El reproductor inicia una solicitud de autenticación para autenticarse en la instancia de publicación. Si hay un controlador de error personalizado en la instancia de publicación, asegúrese de devolver el código de estado 404 para un usuario anónimo en ***/content/screens/svc.ping.json***.

### &#x200B;3. ¿Cómo configurar la pantalla del dispositivo para que permanezca encendida en un reproductor Android™? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga los pasos a continuación para activar Permanecer despierto en cualquier reproductor de Android™:

1. Vaya a Configuración del reproductor Android™ > **Acerca de**.
1. Puntee siete veces en el número de compilación para habilitar **Opciones para desarrolladores** en **Configuración**.
1. Vaya a **Opciones para desarrolladores**.
1. Habilitar **Permanecer despierto**.

### &#x200B;4. ¿Cómo habilitar el modo de ventana para el Reproductor de Windows?{#enable-player}

No hay modo de ventana en Windows Player. Siempre está en modo de pantalla completa.

### &#x200B;5. ¿Cómo solucionar problemas si un reproductor de AEM Screens envía continuamente solicitudes de inicio de sesión?

Siga los pasos a continuación para solucionar problemas de un reproductor de AEM Screens que envía solicitudes continuamente a `/content/screens/svc.json` y `/libs/granite/core/content/login.validate/j_security_check`:

1. Cuando se inicia el Reproductor de AEM Screens, se solicita a `/content/screens/svc.json`. Cuando el reproductor obtiene un código de estado 404 en la respuesta, inicia una solicitud de autenticación utilizando `/libs/granite/core/content/login.validate/j_security_check` en la instancia *publish*. Si hay un controlador de error personalizado en la instancia *publish*, asegúrese de devolver el código de estado 404 para el usuario anónimo en `/content/screens/svc.json` o `/content/screens/svc.ping.json`.

1. Compruebe si la configuración de Dispatcher permite estas solicitudes en `/filters`.

   Consulte [Configuración de filtros de Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters) para obtener más información.

1. Compruebe si las reglas de reescritura de Dispatcher están reescribiendo cualquiera de las rutas de pantalla a una ruta diferente.

1. Compruebe si tiene `/etc/map` reglas en la instancia *author* o *publish* y las rutas de pantallas coinciden con `sling:match` y se redirigen internamente a una ruta diferente. Resolver la dirección URL exacta en `/system/console/jcrresolver` ayuda a identificar si la instancia de *publish* está reescribiendo estas direcciones URL en cualquier otra ruta.

1. Compruebe si la configuración de Apache Sling Resource Resolver Factory provoca reescrituras internas.

### &#x200B;6. ¿Cómo obtener los detalles de la pantalla y el dispositivo desde la API del reproductor?

Puede obtener los detalles de la pantalla y el dispositivo mediante:

* **una API JS interna**
* **un almacén de ContextHub**: hay tres almacenes de ContextHub definidos en `/libs/screens/clientlibs/contexthub` para exponer canales, dispositivos y la información de visualización.

  Siga los pasos a continuación para utilizar estos valores de tienda de ContentHub:

   * Edite las propiedades del canal y establezca la ruta de ContextHub en la pestaña de personalización con el valor (como se ha mencionado anteriormente)
   * En el JS de canal, puede utilizar lo siguiente:

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## Sugerencias generales de resolución de problemas {#general-troubleshooting-tips}

### &#x200B;1. ¿Cómo deshabilitar Livefyre para evitar un error de Screens A/P?

Deshabilite Livefyre para evitar errores de registro haciendo lo siguiente.

1. ***Deshabilitar paquete de Livefyre:***

   * Navegue hasta `https://<host>:<port>/system/console/bundles`.
   * Busque el paquete de AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`.
   * Haga clic en **Detener**.

1. ***Deshabilitar sondeo de Livefyre:***

   * En CRXDE Lite, vaya a `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Agregue una propiedad *habilitada* de tipo *Boolean*.
   * Establezca la propiedad **Enabled** en **false**.

### &#x200B;2. ¿Cómo añadir información del índice de Oak? {#add-oak-index-info}

AEM Screens crea definiciones de índice para las consultas utilizadas por el producto.
Si hay *advertencias de recorrido de la consulta* en `error.log`, cree un índice personalizado para la consulta. Consulte [Configuración de los índices](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes) para obtener más información.

También puede ver un recurso adicional en [Documentación de Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### &#x200B;3. ¿Qué se necesita para configurar los manifiestos de la versión 3? {#configure-v3}

Para habilitar el manifiesto v3, haga lo siguiente:

* Actualice Dispatcher.
Consulte [Configuración de Dispatcher para la versión de manifiesto v3](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) para obtener más información.

* Actualizar componente personalizado.
Consulte [Plantilla para controladores personalizados](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers) para obtener más información.

* Deshabilitar ContentSync en `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Habilitar SmartSync en `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Editar `channel/experience fragment/page components`.

* Vaya a la pestaña **Configuración sin conexión**.

* Escriba `clientlibs ` y carpetas para los archivos estáticos que deben agregarse al manifiesto.

### &#x200B;4. ¿Qué debe hacer si, después del paquete screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 y los paquetes principales de screens están instalados pero no están activos?

Instale una versión mínima de AEM 6.5 Feature Pack 8 para que funcione el conector AMS. Consulta [Disponibilidad](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) para obtener la versión mínima del paquete de funciones de AEM Screens.

### &#x200B;5. ¿Cómo configurar el servicio CQ Link Externalizer en Screens?

El servicio se utiliza para definir el nombre de host público para las instancias de autor y publicación, y los valores se utilizan para actualizar las URL del servidor de dispositivos y también para la segmentación de ContextHub.

El servicio CQ Link Externalizer de Screens se puede configurar de la siguiente manera:

1. Navegue hasta `http://localhost:4502/system/console/configMgr`
1. Externalizador de vínculos CQ de día
1. Cambie el nombre de host para las `author/publish` entradas según sea necesario