---
title: Configuraciones de Dispatcher para AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: Esta página resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 13c9ed116a310c2c17fd1cc3d2c56ef74620df4b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 3%

---

# Configuraciones de Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager.

La siguiente página proporciona las directrices para configurar Dispatcher para un proyecto de AEM Screens.

>[!NOTE]
>
>Si dispatcher está disponible, las conexiones al servlet de registro se pueden prevenir filtrando en las reglas de Dispatcher.
>
>Si no hay Dispatcher, deshabilite el servlet de registro en la lista de componentes de OSGi.

Antes de configurar Dispatcher para un proyecto de AEM Screens, debe tener conocimientos previos de Dispatcher.
Consulte [Configuración de Dispatcher](https://docs.adobe.com/content/help/es-ES/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obtener más información.

## Configuración de Dispatcher para la versión de manifiesto v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Las siguientes configuraciones de Dispatcher solo se aplican a la versión v2 de Manifiesto. Consulte [Configuraciones de Dispatcher para la versión de manifiesto v3](#configuring-dispatcherv3) para la versión v3 del manifiesto.

Los reproductores o dispositivos de AEM Screens utilizan una sesión autenticada para acceder a los recursos de las instancias de publicación. Por lo tanto, cuando tiene varias instancias de publicación, las solicitudes siempre deben ir a la misma instancia de publicación para que la sesión autenticada sea válida para todas las solicitudes procedentes de los reproductores o dispositivos de AEM Screens.

Siga los pasos a continuación para configurar Dispatcher para un proyecto de AEM Screens.

### Habilitar sesiones adhesivas {#enable-sticky-session}

Si desea utilizar varias instancias de publicación frontadas por un solo Dispatcher, deberá actualizar la variable `dispatcher.any` para habilitar la permanencia

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si tiene una instancia de publicación delante de un despachante, habilitar la permanencia en el despachante no ayudará, ya que el equilibrador de carga puede enviar cada solicitud a Dispatcher. En este caso, haga clic en **Habilitar** en **Permanencia** para habilitarlo a nivel de equilibrador de carga, como se muestra en la figura siguiente:

![image](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Por ejemplo, si está utilizando AWS ALB, consulte [Grupos de destino de sus equilibradores de carga de aplicaciones](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para permitir la adherencia en el nivel ALB. Habilite la permanencia durante 1 día.

### Paso 1: Configuración de encabezados de cliente {#step-configuring-client-headers}

Agregue lo siguiente a `/clientheaders`sección:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Paso 2: Configuración de filtros de Screens {#step-configuring-screens-filters}

Para configurar filtros de Screens, agregue lo siguiente a ***/filter***.

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

Deshabilitar el almacenamiento en caché de Dispatcher para ***/content/screens ruta***.

Los reproductores de Screens utilizan una sesión autenticada, por lo que Dispatcher no almacena en caché ninguna de las solicitudes de reproductores de pantallas para `channels/assets`.

Para habilitar la caché para los recursos de modo que se proporcionen los recursos desde la caché de Dispatcher, debe:

* Agregar `/allowAuthorization 1` en `/cache` sección
* Agregue las siguientes reglas a `/rules` sección de `/cache`

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

### Requisitos previos para la versión v3 de manifiesto{#prerequisites3}

Asegúrese de cumplir estos dos requisitos previos antes de configurar Dispatcher (versión de manifiesto v3) para AEM Screens:

* Asegúrese de que está utilizando `v3 manifests`. Vaya a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` y `Enable ContentSync Cache` está desmarcada.

* Asegúrese de que el agente de vaciado de Dispatcher esté configurado en `/etc/replication/agents.publish/dispatcher1useast1Agent` en la instancia de publicación.

   ![image](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![image](/help/user-guide/assets/dispatcher/dispatcher-3.png)

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

* Agregar `/allowAuthorized "1"` a `/cache` en `publish_farm.any`.

* Todos los reproductores de Screens utilizarán una sesión autenticada para conectarse a AEM (autor/publicación). Dispatcher no almacena en caché estas direcciones URL, por lo que deberíamos habilitarlas.

* Agregar `statfileslevel "10"` a `/cache` en `publish_farm.any`
Esto admitirá el almacenamiento en caché de hasta 10 niveles desde la raíz de documento de la caché y se invalidará según corresponda cuando se publique el contenido en lugar de invalidarlo todo. Siéntase libre de cambiar este nivel en función de la profundidad con que tenga la estructura de contenido

* Agregue lo siguiente a `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Agregue las siguientes reglas a `/rules` en `/cache` en `publish_farm.any` o en un archivo incluido desde `publish_farm.any`:

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

### Agregar regla de invalidación para segments.js {#invalidsegmentjs}

Si agrega nuevos segmentos y los publica, el `segments.js` El archivo proporcionado por el dispatcher no tiene las nuevas entradas que estaban interrumpiendo el flujo de segmentación en el dispositivo screens. El archivo segments.js se está almacenando en caché en el nivel de Dispatcher, pero no había ninguna regla de invalidación para lo mismo. Como resultado, debe agregar una regla de invalidación.

* Añadir nuevos segmentos al `/conf/<project-name>/settings/wcm/segments.seg.js` archivo.

* Agregar una regla de invalidación a `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Esta es la regla para agregar:

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/personalisation-hub/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Esta regla garantiza que `segments.js` se invalida y se obtiene la última cuando se modifica.
