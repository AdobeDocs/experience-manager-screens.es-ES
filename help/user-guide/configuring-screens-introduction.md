---
title: Configuración e implementación de AEM Screens
description: El reproductor AEM Screens está disponible para Android& trade;, Chrome OS, iOS y Windows. Obtenga información acerca de la configuración y la implementación de AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 1%

---

# Configuración e implementación de AEM Screens {#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Screens en sus dispositivos.

## Configuración del servidor {#server-configuration}

>[!IMPORTANT]
>
>El Reproductor de AEM Screens no utiliza el token de falsificación de solicitud entre sitios (CSRF). AEM Por lo tanto, para configurar el servidor de para que esté listo para usarse en AEM Screens, omita el filtro de referente y permita los referentes vacíos.

## Marco de comprobación de estado {#health-check-framework}

El marco de comprobación de estado permite al usuario comprobar si se han establecido dos configuraciones necesarias antes de ejecutar un proyecto de AEM Screens.

Permite al usuario comprobar las dos comprobaciones de configuración siguientes para ejecutar un proyecto de AEM Screens, es decir, para comprobar el estado de los dos filtros siguientes:

1. **Permitir referente vacío**
2. **https**

Siga los pasos a continuación para comprobar si estas dos configuraciones vitales están habilitadas para AEM Screens:

1. Vaya a [Comprobación de estado de Sling de la consola web de Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![recursos](assets/health-check1.png)


2. Haga clic en **Ejecutar las comprobaciones de estado seleccionadas** para ejecutar la validación de dos propiedades enumeradas anteriormente.

   Si ambos filtros están habilitados, el **Servicio de mantenimiento de configuración de Screens** muestra el **Resultado** como **Aceptar** con ambas configuraciones como habilitadas.

   ![recursos](assets/health-check2.png)

   Si uno o ambos filtros están desactivados, se muestra una alerta para el usuario, como se muestra en la figura siguiente.

   La siguiente alerta muestra si ambos filtros están deshabilitados:
   ![recursos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar el **Filtro de referente de Apache Sling**, consulte [Permitir solicitudes de referente vacías](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Para habilitar el servicio **HTTP**, consulte [Servicio HTTP basado en Apache Felix Jetty](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).

### Requisitos previos {#prerequisites}

AEM Los siguientes puntos clave ayudan a configurar y a configurar el servidor para que esté listo para su uso en AEM Screens.

#### Permitir solicitudes de referente vacías {#allow-empty-referrer-requests}

1. Vaya a la **configuración de la consola web de Adobe Experience Manager AEM** mediante la instancia de la instancia de > icono de martillo > **Operaciones** > **Consola web**.

   ![imagen](assets/config/empty-ref1.png)

1. **Se abre la configuración de la consola web de Adobe Experience Manager**. Busque el referente de sling.

   Para buscar en la propiedad sling referrer, presione **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **Permitir vacío**, como se muestra en la figura siguiente.

   ![imagen](assets/config/empty-ref2.png)

1. Haga clic en **Guardar** para habilitar la opción Permitir filtro de referente de Apache Sling vacío.


#### Servicio HTTP basado en Apache Felix Jetty {#allow-apache-felix-service}

1. Vaya a la **configuración de la consola web de Adobe Experience Manager AEM** mediante la instancia de la instancia de > icono de martillo > **Operaciones** > **Consola web**.

   ![imagen](assets/config/empty-ref1.png)

1. **Se abre la configuración de la consola web de Adobe Experience Manager**. Busque el servicio HTTP basado en Apache Felix Jetty.

   Para buscar en esta propiedad, presione **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **ENABLE HTTP**, como se muestra en la figura siguiente.

   ![imagen](assets/config/config-1.png)

1. Haga clic en **Guardar** para habilitar el servicio *Http*.

#### Habilitar la IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere una interfaz de usuario táctil y no funciona con la IU clásica de Adobe Experience Manager AEM ().

1. Navegue hasta `*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. Asegúrese de que el **modo predeterminado de la interfaz de usuario de creación** esté establecido en **TOUCH**, como se muestra en la figura siguiente

También puede realizar la misma configuración con las herramientas de su instancia de autor *>* (icono de martillo) > **Operaciones** > **Consola web** y buscar el servicio del modo de IU de creación de **WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

AEM La ejecución de la producción de la utiliza el modo de ejecución **NOSAMPLECONTENT**. Quite el encabezado *X-Frame-Options=SAMEORIGIN* (en la sección de encabezado de respuesta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Esta eliminación es necesaria para que el Reproductor de AEM Screens reproduzca canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los cambios más recientes en ***DeviceServiceImpl***, no tiene que quitar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl*** desde el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios del dispositivo de pantalla:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga los pasos a continuación para configurar ***DeviceServiceImpl***:

1. Vaya a la **configuración de la consola web de Adobe Experience Manager AEM** a través de su instancia de la instancia de la instancia de la > icono del martillo > **Operaciones** > **Consola web**.

1. **Se abre la configuración de la consola web de Adobe Experience Manager**. Busque `*deviceservice*`. Para buscar en la propiedad, presione **Comando+F** para macOS y **Control+F** para Microsoft® Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuración de Dispatcher {#dispatcher-configuration}

Para aprender a configurar Dispatcher para un proyecto de AEM Screens, consulte [Configuración de Dispatcher para un proyecto de AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codificación Java™ {#java-encoding}

Establezca la codificación ***Java™*** en Unicode. Por ejemplo, `*Dfile.encoding=Cp1252*` no funciona.

>[!NOTE]
>
>Utilice HTTPS para AEM Screens Server en el uso de producción.
