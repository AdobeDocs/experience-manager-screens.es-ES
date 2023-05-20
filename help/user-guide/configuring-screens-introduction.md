---
title: Configuración e implementación de AEM Screens
seo-title: Configuring and Deploying Screens
description: El reproductor AEM Screens está disponible para Android, Chrome OS, iOS y Windows. En esta página se describe la configuración y la implementación de AEM Screens y se resumen las directrices de selección de hardware para el dispositivo de reproducción.
seo-description: The AEM Screens player is available for Android, Chrome OS, iOS, and Windows. This page describes the configuration and deployment of AEM Screens and also summarizes the h/w selection guidelines for player device.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# Configuración e implementación de AEM Screens {#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Screens en sus dispositivos.

## Configuración del servidor {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>El reproductor de AEM Screens no utiliza el token de falsificación de solicitud en sitios múltiples (CSRF). AEM Por lo tanto, para configurar y utilizar el servidor de manera que esté listo para usar para AEM Screens, omita el filtro de referente y permita que los referentes estén vacíos.

## Marco de comprobación de estado {#health-check-framework}

El marco de trabajo de comprobación de estado permite al usuario comprobar si se han establecido dos configuraciones necesarias antes de ejecutar un proyecto de AEM Screens.

Permite al usuario comprobar las dos comprobaciones de configuración siguientes para ejecutar un proyecto de AEM Screens, es decir, para comprobar el estado de los dos filtros siguientes:

1. **Permitir referente vacío**
2. **https**

Siga los pasos a continuación para comprobar si estas dos configuraciones vitales están habilitadas para AEM Screens:

1. Vaya a [Comprobación de estado de Sling de la consola web Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![activos](assets/health-check1.png)


2. Haga clic en **Ejecutar las comprobaciones de estado seleccionadas** para ejecutar la validación de dos propiedades enumeradas anteriormente.

   Si ambos filtros están activados, la variable **Servicio de mantenimiento de configuración de Screens** muestra el **Resultado** as **OK** con ambas configuraciones como habilitadas.

   ![activos](assets/health-check2.png)

   Si uno o ambos filtros están desactivados, se muestra una alerta para el usuario, como se muestra en la figura siguiente.

   La siguiente alerta muestra si ambos filtros están deshabilitados:
   ![activos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar la variable **Filtro de referente de Apache Sling**, consulte [Permitir solicitudes de referente vacías](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Para habilitar la variable **HTTP** servicio, consulte [Servicio HTTP basado en Apache Felix Jetty](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Requisitos previos {#prerequisites}

AEM Los siguientes puntos clave ayudan a configurar y a configurar el servidor para que esté listo para su uso en AEM Screens.

#### Permitir solicitudes de referente vacías {#allow-empty-referrer-requests}

1. Vaya a **Configuración de la consola web Adobe Experience Manager** AEM vía instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![imagen](assets/config/empty-ref1.png)

1. **Configuración de la consola web Adobe Experience Manager** abre. Busque el referente de sling.

   Para buscar en la propiedad sling referrer, pulse **Comando + F** para **Mac** y **Control + F** para **Windows**.

1. Compruebe la **Permitir vaciado** , como se muestra en la figura siguiente.

   ![imagen](assets/config/empty-ref2.png)

1. Clic **Guardar** para habilitar el Filtro de referente de Apache Sling Permitir vacío.


#### Servicio HTTP basado en Apache Felix Jetty {#allow-apache-felix-service}

1. Vaya a **Configuración de la consola web Adobe Experience Manager** AEM vía instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![imagen](assets/config/empty-ref1.png)

1. **Configuración de la consola web Adobe Experience Manager** abre. Busque el servicio HTTP basado en Apache Felix Jetty.

   Para buscar en esta propiedad, presione **Comando + F** para **Mac** y **Control + F** para **Windows**.

1. Compruebe la **HABILITAR HTTP** , como se muestra en la figura siguiente.

   ![imagen](assets/config/config-1.png)

1. Clic **Guardar** para habilitar el *http* servicio.

#### Habilitar la IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere una interfaz de usuario táctil y no funcionará con la IU CLÁSICA de Adobe Experience Manager AEM ().

1. Vaya a *&lt;yourauthorinstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Asegúrese de que la variable **Modo de IU de creación predeterminado** se establece en **TOUCH**, como se muestra en la figura siguiente

Como alternativa, también puede realizar la misma configuración con AuthorInstance *->* herramientas (icono de martillo) -> **Operaciones** -> **Consola web** y buscar **Servicio de modo de IU de creación de WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

AEM La ejecución de la producción de utiliza **NOSAMPLECONTENT** modo de ejecución. Retire el *X-Frame-Options=SAMEORIGIN* encabezado (en la sección de encabezado de respuesta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Esto es necesario para que el Reproductor de AEM Screens reproduzca canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los cambios más recientes en ***DeviceServiceImpl***, no tiene que eliminar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl*** en el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios del dispositivo screens:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga los pasos a continuación para configurar ***DeviceServiceImpl***:

1. Vaya a **Configuración de la consola web Adobe Experience Manager** AEM vía instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

1. **Configuración de la consola web Adobe Experience Manager** abre. Buscar por *deviceservice*. Para buscar en la propiedad, pulse **Comando + F** para macOS y **Control + F** para Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuración de Dispatcher {#dispatcher-configuration}

Para aprender a configurar Dispatcher para un proyecto de AEM Screens, consulte [Configuración de Dispatcher para un proyecto de AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codificación Java {#java-encoding}

Configure las variables ***Codificación Java*** a Unicode. Por ejemplo, *Dfile.encoding=Cp1252* no funcionará.

>[!NOTE]
>**Recomendación:**
>Se recomienda utilizar HTTPS para AEM Screens Server en el uso de producción.
