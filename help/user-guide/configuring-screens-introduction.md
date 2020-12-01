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
source-git-commit: 83ce95e5dc530c5792ec9a00dcb758a424202a7a
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---


# Configuración e implementación de AEM Screens {#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Pantallas en sus dispositivos.

## Configuración del servidor {#server-configuration}

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

1. Vaya a [Comprobación del estado de Sling de la consola web de Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![activos](assets/health-check1.png)


2. Haga clic en **Ejecutar las comprobaciones de estado seleccionadas** para ejecutar la validación de dos propiedades enumeradas arriba.

   Si ambos filtros están habilitados, el **Servicio de mantenimiento de configuración de pantallas** muestra el **Resultado** como **Aceptar** con ambas configuraciones como habilitadas.

   ![activos](assets/health-check2.png)

   Si uno o ambos filtros están desactivados, se muestra una alerta para el usuario, como se muestra en la figura siguiente.

   La siguiente alerta muestra si ambos filtros están desactivados:
   ![activos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar el **Filtro de Remitente del reenvío Sling de Apache**, consulte [Permitir solicitudes de Remitente del reenvío vacías](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Para habilitar el servicio **HTTP**, consulte [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Requisitos previos {#prerequisites}

Los siguientes puntos clave ayudan a configurar y AEM el servidor para que esté listo para su uso en AEM Screens.

#### Permitir solicitudes de Remitente del reenvío vacías {#allow-empty-referrer-requests}

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Buscar remitente del reenvío sling.

   Para buscar la propiedad de remitente del reenvío sling, presione **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **Permitir vacío**, como se muestra en la figura siguiente.

   ![image](assets/config/empty-ref2.png)

1. Haga clic en **Guardar** para habilitar el filtro de Remitente del reenvío Sling de Apache para permitir que esté vacío.


#### Servicio HTTP Apache Felix Jetty basado en {#allow-apache-felix-service}

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Busque el servicio HTTP Apache Felix Jetty.

   Para buscar esta propiedad, presione **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **HABILITAR HTTP**, como se muestra en la figura siguiente.

   ![image](assets/config/config-1.png)

1. Haga clic en **Guardar** para habilitar el servicio *http*.

#### Habilitar IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere la IU TÁCTIL y no funcionará con la IU CLÁSICA de Adobe Experience Manager (AEM).

1. Vaya a *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Asegúrese de que el **modo de IU de creación predeterminado** está establecido en **TOUCH**, como se muestra en la figura siguiente

También puede realizar la misma configuración con las herramientas *->* de AuthorInstance (icono de martillo) -> **Operaciones** -> **Consola Web** y buscar **Servicio de modo de IU de creación de WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

La ejecución de AEM en producción utiliza el modo de ejecución **NOSAMPLECONTENT**. Elimine el encabezado *X-Frame-Options=SAMEORIGIN* (en la sección del encabezado de respuesta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Esto es necesario para que AEM Screens Player pueda reproducir canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los últimos cambios realizados en ***DeviceServiceImpl***, no es necesario eliminar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl*** desde el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios del dispositivo de pantallas:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga los pasos a continuación para configurar ***DeviceServiceImpl***:

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Busque *servicio de dispositivos*. Para buscar la propiedad, presione **Comando+F** para macOS y **Control+F** para Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuración del despachante {#dispatcher-configuration}

Para obtener información sobre cómo configurar el despachante para un proyecto de AEM Screens, consulte [Configuración de Dispatcher para un proyecto de AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codificación de Java {#java-encoding}

Establezca la ***codificación de Java*** en Unicode. Por ejemplo, *Dfile.encoding=Cp1252* no funcionará.

>[!NOTE]
>**Recomendación:**
>Se recomienda utilizar HTTPS para AEM Screens Server en el uso de producción.








