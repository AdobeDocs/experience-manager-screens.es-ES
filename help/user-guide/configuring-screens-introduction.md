---
title: Configuración e implementación de pantallas AEM
seo-title: Configurar e implementar Screens
description: El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows. En esta página se describe la configuración y la implementación de AEM Screens y también se resumen las directrices de selección h/w para el dispositivo de reproducción.
seo-description: El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows. En esta página se describe la configuración y la implementación de AEM Screens y también se resumen las directrices de selección h/w para el dispositivo de reproducción.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: 389a44e3f6175e0a43a6e99edd3048f2b8455d0b

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Pantallas en sus dispositivos.

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>El reproductor de AEM Screens no utiliza el distintivo de falsificación de solicitudes entre sitios (CSRF). Por lo tanto, para configurar y que el servidor AEM esté listo para usar en AEM Screens, omita el filtro de referente permitiendo que los referentes estén vacíos.

## Marco de comprobación de estado {#health-check-framework}

El marco de comprobación de estado permite al usuario comprobar si se han configurado dos configuraciones necesarias antes de ejecutar un proyecto de AEM Screens.

Permite al usuario verificar las dos comprobaciones de configuración siguientes para ejecutar un proyecto de AEM Screens, es decir, para comprobar el estado de los dos filtros siguientes:

1. **Permitir referente vacío**
2. **https**

Siga los pasos a continuación para comprobar si estas dos configuraciones vitales están habilitadas para AEM Screens:

1. Vaya a [Adobe Experience Manager Web ConsoleComprobación](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&overrideGlobalTimeout=)del estado de Sling.

   ![activos](assets/health-check1.png)


2. Haga clic en **Ejecutar las comprobaciones** de estado seleccionadas para ejecutar la validación de dos propiedades enumeradas arriba.

   Si ambos filtros están activados, el servicio **de mantenimiento de configuración de** pantallas muestra el **resultado** como **correcto** con ambas configuraciones como habilitadas.

   ![activos](assets/health-check2.png)

   Si uno o ambos filtros están desactivados, se muestra una alerta para el usuario, como se muestra en la figura siguiente.

   La siguiente alerta muestra si ambos filtros están desactivados:
   ![activos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar el filtro **de referente Sling de** Apache, consulte [Permitir solicitudes](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)de referente vacías.
>* Para habilitar el servicio **HTTP** , consulte Servicio [HTTP basado en](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)Apache Felix Jetty.


### Requisitos previos {#prerequisites}

Los siguientes puntos clave ayudan a configurar y a que el servidor AEM esté listo para su uso en AEM Screens.

#### Permitir solicitudes de referente vacías {#allow-empty-referrer-requests}

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Se abre la configuración** de la consola web de Adobe Experience Manager. Busque el referente sling.

   Para buscar la propiedad del referente sling, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. Marque la opción **Permitir vacío** , como se muestra en la figura siguiente.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. Haga clic en **Guardar** para habilitar el filtro de referente de sling de Apache que permite vaciar.

#### Servicio HTTP Apache Felix Jetty Basado en Jetty {#allow-apache-felix-service}

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Se abre la configuración** de la consola web de Adobe Experience Manager. Busque el servicio HTTP Apache Felix Jetty.

   Para buscar esta propiedad, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **HABILITAR HTTP** , como se muestra en la figura siguiente.

   ![screen_shot_2019-07-31at91807am](assets/http-image.png)

1. Haga clic en **Guardar** para habilitar el servicio *http* .

#### Activar IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere la IU TÁCTIL y no funcionará con la IU CLÁSICA de Adobe Experience Manager (AEM).

1. Vaya a *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Asegúrese de que el modo **predeterminado de la IU de creación esté establecido en** TOUCH ****, como se muestra en la figura siguiente

También puede realizar la misma configuración con *&lt;yourAuthorInstance>*->*herramientas (icono de martillo)* -> **Operaciones** -> Consola **** web y buscar el servicio **de modo de IU de creación de** WCM.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

La ejecución de AEM en producción utiliza el modo de ejecución **NOSAMPLECONTENT** . *Elimine el encabezado X-Frame-Options=SAMEORIGIN* (en la sección de encabezado de respuesta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Esto es necesario para que AEM Screens Player pueda reproducir los canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los últimos cambios en ***DeviceServiceImpl ***, no es necesario eliminar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl ***desde el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios de dispositivos de pantalla:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga los pasos a continuación para configurar ***DeviceServiceImpl ***:

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

1. **Configuración de la consola web de Adobe Experience Manager **se abre. Busque deviceService. Para buscar la propiedad, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

Para obtener información sobre cómo configurar el despachante para un proyecto de AEM Screens, consulte [Configuración de Dispatcher para un proyecto](dispatcher-configurations-aem-screens.md)de AEM Screens.

#### Codificación de Java {#java-encoding}

Establezca la codificación ******Java en Unicode. Por ejemplo,*Dfile.encoding=Cp1252 *no funcionará.

>[!NOTE]
>
>**Recomendación:**
>
>Se recomienda utilizar HTTPS para AEM Screens Server en el uso de producción.








