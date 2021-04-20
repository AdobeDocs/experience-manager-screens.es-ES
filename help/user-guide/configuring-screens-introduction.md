---
title: Configuración e implementación de AEM Screens
seo-title: Configurar e implementar Screens
description: El reproductor AEM Screens está disponible para Android, Chrome OS, iOS y Windows. Esta página describe la configuración y la implementación de AEM Screens y también resume las directrices de selección h/w para el dispositivo de reproducción.
seo-description: El reproductor AEM Screens está disponible para Android, Chrome OS, iOS y Windows. Esta página describe la configuración y la implementación de AEM Screens y también resume las directrices de selección h/w para el dispositivo de reproducción.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 1%

---


# Configuración e implementación de AEM Screens {#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Screens en sus dispositivos.

## Configuración del servidor {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>El reproductor de AEM Screens no utiliza el token de Falsificación de solicitudes entre sitios (CSRF). Por lo tanto, para configurar y AEM servidor que esté listo para usar con AEM Screens, omita el filtro de referente permitiendo referentes vacíos.

## Marco de comprobación de estado {#health-check-framework}

El marco de comprobación de estado permite al usuario comprobar si se han configurado dos configuraciones necesarias antes de ejecutar un proyecto de AEM Screens.

Permite al usuario verificar las dos comprobaciones de configuración siguientes para ejecutar un proyecto de AEM Screens, es decir, para comprobar el estado de los dos filtros siguientes:

1. **Permitir referente vacío**
2. **https**

Siga los pasos a continuación para comprobar si estas dos configuraciones vitales están habilitadas para AEM Screens:

1. Vaya a [Adobe Experience Manager Web Console Sling Health Check](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![activos](assets/health-check1.png)


2. Haga clic en **Ejecutar comprobaciones de estado seleccionadas** para ejecutar la validación de dos propiedades enumeradas arriba.

   Si ambos filtros están habilitados, el **Servicio de mantenimiento de configuración de Screens** muestra el **Resultado** como **Aceptar** con ambas configuraciones, según se haya habilitado.

   ![activos](assets/health-check2.png)

   Si uno de los filtros o ambos están desactivados, se mostrará una alerta para el usuario, como se muestra en la figura siguiente.

   La siguiente alerta muestra si ambos filtros están desactivados:
   ![activos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar el **Filtro de referente de Apache Sling**, consulte [Permitir solicitudes de referente vacías](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Para habilitar el servicio **HTTP**, consulte [Servicio HTTP basado en Apache Felix Jetty](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Requisitos previos {#prerequisites}

Los siguientes puntos clave ayudan a configurar y AEM servidor para que esté listo para usar con AEM Screens.

#### Permitir solicitudes de referente vacías {#allow-empty-referrer-requests}

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Busque el referente de sling.

   Para buscar la propiedad del referente de sling, presione **Command+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **Permitir vacío**, como se muestra en la figura siguiente.

   ![image](assets/config/empty-ref2.png)

1. Haga clic en **Guardar** para habilitar el filtro de referente Apache Sling Allow Empty.


#### Servicio HTTP basado en Apache Felix Jetty {#allow-apache-felix-service}

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Busque el servicio HTTP basado en Apache Felix Jetty.

   Para buscar esta propiedad, presione **Command+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **ENABLE HTTP** como se muestra en la figura siguiente.

   ![image](assets/config/config-1.png)

1. Haga clic en **Save** para habilitar el servicio *http*.

#### Habilitar la IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere la IU TÁCTIL y no funcionará con la IU CLÁSICA de Adobe Experience Manager (AEM).

1. Vaya a *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Asegúrese de que el **modo de IU de creación predeterminado** está configurado en **TOUCH**, como se muestra en la figura siguiente

Como alternativa, también puede realizar la misma configuración utilizando las herramientas *->* (icono de martillo) -> **Operaciones** -> **Consola web** y buscar **Servicio de modo de IU de creación WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

La ejecución de AEM en producción utiliza el modo de ejecución **NOSAMPLECONTENT**. Elimine el encabezado *X-Frame-Options=SAMEORIGIN* (en la sección adicional del encabezado de respuesta) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Esto es necesario para que el Reproductor de AEM Screens reproduzca los canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los cambios más recientes en ***DeviceServiceImpl***, no es necesario eliminar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl*** desde el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios de dispositivos de pantallas:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga los pasos a continuación para configurar ***DeviceServiceImpl***:

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Busque *servicio de dispositivos*. Para buscar la propiedad, presione **Command+F** para macOS y **Control+F** para Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuración de Dispatcher {#dispatcher-configuration}

Para aprender a configurar Dispatcher para un proyecto de AEM Screens, consulte [Configuración de Dispatcher para un proyecto de AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codificación Java {#java-encoding}

Establezca la ***codificación Java*** en Unicode. Por ejemplo, *Dfile.encoding=Cp1252* no funcionará.

>[!NOTE]
>**Recomendación:**
>Se recomienda utilizar HTTPS para el servidor de AEM Screens en uso de producción.








