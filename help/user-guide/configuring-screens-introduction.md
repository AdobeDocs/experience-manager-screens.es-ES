---
title: Configuración e implementación de AEM Screens
seo-title: Configurar e implementar Screens
description: El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows. Esta página describe la configuración y la implementación de AEM Screens y también resume las pautas de selección h/w para el dispositivo de reproductor.
seo-description: El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows. Esta página describe la configuración y la implementación de AEM Screens y también resume las pautas de selección h/w para el dispositivo de reproductor.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: acc0278631a4be2c90de7cc43d3b40a358ffa93e
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 1%

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Pantallas en sus dispositivos.

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>El reproductor de AEM Screens no utiliza el token de falsificación de solicitudes entre sitios (CSRF). Por lo tanto, para configurar y AEM servidor que esté listo para usar para AEM Screens, omita el filtro de remitente del reenvío permitiendo remitentes del reenvío vacíos.

## Marco de comprobación de estado {#health-check-framework}

El marco de comprobación de estado permite al usuario comprobar si hay dos configuraciones necesarias configuradas antes de ejecutar un proyecto de AEM Screens.

Permite al usuario comprobar las dos comprobaciones de configuración siguientes para ejecutar un proyecto de AEM Screens, es decir, para comprobar el estado de los dos filtros siguientes:

1. **Permitir Remitente del reenvío vacío**
2. **https**

Siga los pasos a continuación para comprobar si estas dos configuraciones vitales están habilitadas para AEM Screens:

1. Vaya a [Adobe Experience Manager Web Console Sling Health Check](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![activos](assets/health-check1.png)


2. Haga clic en **Ejecutar las comprobaciones** de estado seleccionadas para ejecutar la validación de dos propiedades enumeradas arriba.

   Si ambos filtros están habilitados, el servicio **de mantenimiento de configuración de** pantallas muestra el **resultado** como **correcto** con ambas configuraciones como habilitadas.

   ![activos](assets/health-check2.png)

   Si uno o ambos filtros están desactivados, se muestra una alerta para el usuario, como se muestra en la figura siguiente.

   La siguiente alerta muestra si ambos filtros están desactivados:
   ![activos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar el filtro **de Remitente del reenvío Sling de** Apache, consulte [Permitir solicitudes](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)de Remitente del reenvío vacías.
>* Para habilitar el servicio **HTTP** , consulte Servicio [HTTP basado en](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)Apache Felix Jetty.


### Requisitos previos {#prerequisites}

Los siguientes puntos clave ayudan a configurar y AEM el servidor para que esté listo para su uso en AEM Screens.

#### Permitir solicitudes de Remitente del reenvío vacías {#allow-empty-referrer-requests}

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante AEM instancia —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la Configuración** de Adobe Experience Manager Web Console. Buscar remitente del reenvío sling.

   Para buscar la propiedad de remitente del reenvío sling, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **Permitir vacío** , como se muestra en la figura siguiente.

   ![image](assets/config/empty-ref2.png)

1. Haga clic en **Guardar** para activar el filtro de Remitente del reenvío Sling de Apache Permitir vacío.


#### Servicio HTTP Apache Felix Jetty Basado en Jetty {#allow-apache-felix-service}

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante AEM instancia —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la Configuración** de Adobe Experience Manager Web Console. Busque el servicio HTTP Apache Felix Jetty.

   Para buscar esta propiedad, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **HABILITAR HTTP** , como se muestra en la figura siguiente.

   ![image](assets/config/config-1.png)

1. Haga clic en **Guardar** para habilitar el servicio *http* .

#### Habilitar la IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere la IU TÁCTIL y no funcionará con la IU CLÁSICA de Adobe Experience Manager (AEM).

1. Vaya a *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Asegúrese de que el modo **predeterminado de la IU de creación esté establecido en** TOUCH ****, como se muestra en la figura siguiente

También puede realizar la misma configuración con *&lt;yourAuthorInstance>*->*herramientas (icono de martillo)* -> **Operaciones** -> Consola **** web y buscar el servicio **de modo de IU de creación de** WCM.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en el modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

La ejecución de AEM en producción utiliza el modo de ejecución **NOSAMPLECONTENT** . *Elimine el encabezado X-Frame-Options=SAMEORIGIN* (en la sección de encabezado de respuesta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Esto es necesario para que AEM Screens Player pueda reproducir canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los últimos cambios en ***DeviceServiceImpl***, no es necesario eliminar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl*** desde el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios de dispositivos de pantalla:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga los pasos a continuación para configurar ***DeviceServiceImpl***:

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante AEM instancia —> icono de martillo —> **Operaciones** —> Consola **** web.

1. **Configuración de la consola web de Adobe Experience Manager **se abre. Busque deviceService. Para buscar la propiedad, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

Para obtener información sobre cómo configurar el despachante para un proyecto de AEM Screens, consulte [Configuración de Dispatcher para un proyecto](dispatcher-configurations-aem-screens.md)de AEM Screens.

#### Codificación de Java {#java-encoding}

Establezca la codificación ****** Java en Unicode. Por ejemplo, *Dfile.encoding=Cp1252* no funcionará.

>[!NOTE]
>
>**Recomendación:**
>
>Se recomienda utilizar HTTPS para AEM Screens Server en el uso de producción.








