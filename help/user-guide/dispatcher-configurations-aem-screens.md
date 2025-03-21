---
title: Configuraciones de Dispatcher para AEM Screens
description: En esta página se destacan las directrices para configurar una Dispatcher para un proyecto de AEM Screens.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Configuraciones de Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager, o ambas.

En la siguiente página se proporcionan las directrices para configurar un Dispatcher para un proyecto de AEM Screens.

>[!NOTE]
>
>Si hay un Dispatcher disponible, las conexiones al servlet de registro se pueden evitar filtrando en las reglas de Dispatcher.
>
>Si no hay ningún Dispatcher, deshabilite el servlet de registro en la lista de componentes OSGi.

Antes de configurar Dispatcher para un proyecto de AEM Screens, debe tener conocimientos previos de Dispatcher.
Consulte [Configuración de Dispatcher](https://experienceleague.adobe.com/es_es/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration) para obtener más información.

## Configurar Dispatcher para la versión 2 de manifiesto {#configuring-dispatcher}

>[!IMPORTANT]
>Las siguientes configuraciones de Dispatcher se aplican únicamente a la versión v2 del manifiesto. Consulte [Configuraciones de Dispatcher para la versión de manifiesto 3](#configuring-dispatcherv3) para la versión de manifiesto 3.

Los reproductores o dispositivos de AEM Screens también utilizan una sesión autenticada para acceder a los recursos de las instancias de publicación. Cuando tiene varias instancias de publicación, las solicitudes siempre deben ir a la misma instancia de publicación para que la sesión autenticada sea válida para todas las solicitudes procedentes de los reproductores o dispositivos de AEM Screens.

Siga los pasos a continuación para configurar Dispatcher para un proyecto de AEM Screens.

### Activar sesiones fijas {#enable-sticky-session}

Si desea utilizar varias instancias de publicación delante de un solo Dispatcher, actualice el archivo `dispatcher.any` para habilitar la permanencia.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si tiene una instancia de publicación delante de una Dispatcher, habilitar la adherencia en Dispatcher no ayuda, ya que el equilibrador de carga puede enviar cada solicitud a Dispatcher. En este caso, haga clic en **Habilitar** en el campo **Adherencia** para activarlo en su nivel de equilibrador de carga, como se muestra en la figura siguiente:

![imagen](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Por ejemplo, si está usando AWS ALB, consulte [Grupos de destino para los equilibradores de carga de la aplicación](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para habilitar la permanencia en el nivel ALB. Active la adherencia durante un día.

### Paso 1: Configuración de los encabezados de cliente {#step-configuring-client-headers}

Agregue lo siguiente a la sección `/clientheaders`:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Paso 2: Configuración de filtros de Screens {#step-configure-screens-filters}

Para configurar los filtros de Screens, agregue lo siguiente a ***`/filter`***.

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

Deshabilite el almacenamiento en caché de Dispatcher para ***/content/screens/path***.

Los reproductores de Screens utilizan sesiones autenticadas, por lo que Dispatcher no almacena en caché ninguna de las solicitudes de reproductores de pantallas para `channels/assets`.

Para habilitar la caché de los recursos de modo que se proporcionen desde la caché de Dispatcher, haga lo siguiente:

* Agregar `/allowAuthorization 1` en la sección `/cache`
* Agregar las siguientes reglas a la sección `/rules` de `/cache`

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

## Configurar Dispatcher para la versión 3 de manifiesto{#configuring-dispatcherv3}

Asegúrese de permitir estos filtros y reglas de caché en los distribuidores que frontan las instancias de publicación para el funcionamiento de Screens.

### Requisitos previos para la versión de manifiesto v3{#prerequisites3}

Siga estos dos requisitos previos antes de configurar un Dispatcher (manifiesto versión v3) para AEM Screens:

* Asegúrese de que está usando `v3 manifests`. Vaya a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` y asegúrese de que `Enable ContentSync Cache` esté desmarcado.

* Asegúrese de que el agente de vaciado de Dispatcher esté configurado en `/etc/replication/agents.publish/dispatcher1useast1Agent` en la instancia de publicación.

  ![imagen](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![imagen](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtros {#filter-v3}

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

* Agregar `/allowAuthorized "1"` a la sección `/cache` en `publish_farm.any`.

* Todos los reproductores de AEM Screens AEM utilizan una sesión autenticada para conectarse a la red (autor/publicación. De forma predeterminada, una Dispatcher no almacena en caché estas direcciones URL, por lo que debe habilitarlas.

* Agregar `statfileslevel "10"` a la sección `/cache` en `publish_farm.any`
Esta regla admite el almacenamiento en caché de hasta diez niveles desde la caché docroot e invalida en consecuencia cuando se publica contenido, en lugar de invalidar todo. No dude en cambiar este nivel en función de la profundidad de la estructura de contenido

* Agregar lo siguiente a `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* Agregue las siguientes reglas a la sección `/rules` de `/cache` en `publish_farm.any` o en un archivo incluido en `publish_farm.any`:

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

### Añadir regla de invalidación para segments.js {#invalidsegmentjs}

Si está usando campañas de destino con AEM Screens, entonces el `segments.js file` servido por Dispatcher AEM debe invalidarse, a medida que agregue y publique nuevos segmentos en el sitio web de. Sin esta regla de invalidación, las nuevas campañas segmentadas no funcionan en el reproductor de AEM Screens (muestra el contenido predeterminado en su lugar).

* Agregar una regla de invalidación a `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Esta es la regla que se debe agregar:

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Esta regla garantiza que el archivo `segments.js` se invalidará y que se recuperará la última versión cuando se modifique.
