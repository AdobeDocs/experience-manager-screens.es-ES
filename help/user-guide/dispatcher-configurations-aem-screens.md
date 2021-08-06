---
title: Configuraciones de Dispatcher para AEM Screens
seo-title: Configuraciones de Dispatcher para AEM Screens
description: Esta página resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.
seo-description: Esta página resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.
feature: Administración de Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 7e4d3c5ed7299d6439bf9be6d49ec9224dcf71ed
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 4%

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

## Configuración de Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>Las siguientes configuraciones de Dispatcher solo se aplican a la versión v2 de Manifiesto. Consulte [Configuraciones de Dispatcher para la versión de manifiesto v3]{#configuring-dispatcherv3} para la versión V3 de manifiesto.

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

## Configuración de Dispatcher para la versión de manifiesto v3{#configuring-dispatcherv3}

Asegúrese de permitir estos filtros y reglas de caché en los distribuidores que se encuentran delante de las instancias de publicación para el funcionamiento de Screens.

## Requisitos previos para la versión v3 de manifiesto{#prerequisites3}

Asegúrese de cumplir estos dos requisitos previos antes de utilizar la configuración de Dispatcher para AEM Screens:

* Asegúrese de que está utilizando `v3 manifests`. Vaya a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` y asegúrese de que `Enable ContentSync Cache` está desmarcada.

* Asegúrese de que el agente de vaciado de Dispatcher esté configurado en `/etc/replication/agents.publish/dispatcher1useast1Agent` en la instancia de publicación.

   ![image](/help/user-guide/assets/dispatcher/dispatcher-1.png)

### Filtros  {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Reglas de caché {#cache-rules-v3}

* Agregue `/allowAuthorized "1"` a la sección `/cache` en `publish_farm.any`.

* Todos los reproductores de Screens utilizarán una sesión autenticada para conectarse a AEM (autor/publicación). Dispatcher no almacena en caché estas direcciones URL, por lo que deberíamos habilitarlas.

* Agregar `statfileslevel "10"` a la sección `/cache` en `publish_farm.any`
Esto admitirá el almacenamiento en caché de hasta 10 niveles desde la raíz de documento de la caché y se invalidará según corresponda cuando se publique el contenido en lugar de invalidarlo todo. Siéntase libre de cambiar este nivel en función de la profundidad con que tenga la estructura de contenido

* Agregue lo siguiente a `/invalidate section in publish_farm.any`

```
/0003 {
    /glob "*.json"
    /type "allow"
}
```

Agregue las siguientes reglas a la sección `/rules` en `/cache` en `publish_farm.any` o en un archivo incluido desde `publish_farm.any`:

```
## Don't cache CSRF login tokens
/0001
    {
    /glob "/libs/granite/csrf/token.json"
    /type "deny"
    }
## Allow Dispatcher Cache for Screens channels
/0002
    {
        /glob "/content/screens/*.html"
        /type "allow"
    }
## Allow Dispatcher Cache for Screens offline manifests
/0003
    {
    /glob "/content/screens/*.manifest.json"
    /type "allow"
    }
## Allow Dispatcher Cache for Assets
/0004
    {
  
    /glob "/content/dam/*"
    /type "allow"
    }
## Disable Dispatcher Cache for Screens devices json
/0005
    {
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
## Disable Dispatcher Cache for Screens svc json
/0006
    {
    /glob "/content/screens/svc.json"
    /type "deny"
    }
```
