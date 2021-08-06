---
title: Configuraciones de Dispatcher para AEM Screens
seo-title: Configuraciones de Dispatcher para AEM Screens
description: Esta página resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.
seo-description: Esta página resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.
feature: Administración de Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: d3903605e50668a568e5c336b47ad4c6d8cd1dc0
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 5%

---

# Configuraciones de Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager.

La siguiente página proporciona las directrices para configurar Dispatcher para un proyecto de AEM Screens.

>[!NOTE]
>
>Si dispatcher está disponible, las conexiones al servlet de registro se pueden prevenir filtrando en las reglas de Dispatcher.
>
>Si no hay Dispatcher, deshabilite el servlet de registro en la lista de componentes de OSGi.

## Requisitos previos {#prerequisites}

>[!IMPORTANT]
>Antes de configurar Dispatcher para un proyecto de AEM Screens, debe tener conocimientos previos de Dispatcher.
>Consulte [Configuración de Dispatcher](https://docs.adobe.com/content/help/es-ES/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obtener más información.

Asegúrese de cumplir estos dos requisitos previos antes de utilizar la configuración de Dispatcher para AEM Screens:

* Asegúrese de que está utilizando `v3 manifests`. Vaya a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` y asegúrese de que `Enable ContentSync Cache` está desmarcada.

* Asegúrese de que el agente de vaciado de Dispatcher esté configurado en `/etc/replication/agents.publish/dispatcher1useast1Agent` en la instancia de publicación.

   ![image](/help/user-guide/assets/dispatcher/dispatcher-1.png)

## Configuración de Dispatcher {#configuring-dispatcher}

Los reproductores o dispositivos de AEM Screens utilizan una sesión autenticada para acceder a los recursos de las instancias de publicación. Por lo tanto, cuando tiene varias instancias de publicación, las solicitudes siempre deben ir a la misma instancia de publicación para que la sesión autenticada sea válida para todas las solicitudes procedentes de los reproductores o dispositivos de AEM Screens.

Siga los pasos a continuación para configurar Dispatcher para un proyecto de AEM Screens.

### Habilitar sesiones adhesivas {#enable-sticky-session}

Si desea utilizar varias instancias de publicación frontadas por un solo Dispatcher, deberá actualizar el archivo `dispatcher.any` para habilitar la permanencia

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si tiene una instancia de publicación delante de un despachante, habilitar la permanencia en el despachante no ayudará, ya que el equilibrador de carga puede enviar cada solicitud a Dispatcher. En este caso, haga clic en **Enable** en el campo **Stickiness** para habilitarlo a nivel de equilibrador de carga, como se muestra en la figura siguiente:

![image](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Por ejemplo, si está utilizando ALB de AWS, consulte [Grupos de destino para sus equilibradores de carga de aplicaciones](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para habilitar la permanencia en el nivel ALB. Habilite la permanencia durante 1 día.

### Paso 1: Configuración de encabezados de cliente {#step-configuring-client-headers}

Agregue lo siguiente a la sección `/clientheaders`:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Paso 2: Configuración de filtros de Screens {#step-configuring-screens-filters}

Para configurar los filtros de Screens, agregue lo siguiente a ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Paso 3: Desactivación de la caché de Dispatcher {#step-disabling-dispatcher-cache}

Deshabilite el almacenamiento en caché de Dispatcher para ***/content/screens path***.

Los reproductores de Screens utilizan una sesión autenticada, por lo que Dispatcher no almacena en caché ninguna de las solicitudes de reproductores de pantallas para `channels/assets`.

Para habilitar la caché para los recursos de modo que se proporcionen los recursos desde la caché de Dispatcher, debe:

* Agregar `/allowAuthorization 1` en la sección `/cache`
* Agregue las siguientes reglas a la sección `/rules` de `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
