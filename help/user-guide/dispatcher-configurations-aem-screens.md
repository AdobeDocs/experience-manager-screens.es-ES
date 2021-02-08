---
title: Configuraciones de Dispatcher para AEM Screens
seo-title: Configuraciones de Dispatcher para AEM Screens
description: Esta página resalta las directrices para configurar el despachante de un proyecto de AEM Screens.
seo-description: Esta página resalta las directrices para configurar el despachante de un proyecto de AEM Screens.
translation-type: tm+mt
source-git-commit: 230e513ff24647e934ed850ecade60b19f4ab331
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 6%

---


# Configuraciones de Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager.

La página siguiente proporciona las directrices para configurar el despachante para un proyecto de AEM Screens.

>[!NOTE]
>
>Si hay un despachante disponible, las conexiones al servlet de registro se pueden evitar filtrando las reglas del despachante.
>
>Si no hay ningún distribuidor, deshabilite el servlet de registro en la lista de componentes OSGi.

## Requisitos previos {#pre-requisites}

Antes de configurar el despachante para un proyecto de AEM Screens, debe tener conocimientos previos de Dispatcher.

Consulte [Configuración de Dispatcher](https://docs.adobe.com/content/help/es-ES/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obtener más detalles.

## Configuración de Dispatcher {#configuring-dispatcher}

Los reproductores y dispositivos de AEM Screens utilizan una sesión autenticada para acceder también a los recursos de las instancias de publicación. Por lo tanto, cuando tenga varias instancias de publicación, las solicitudes siempre deben ir a la misma instancia de publicación para que la sesión autenticada sea válida para todas las solicitudes procedentes de reproductores o dispositivos AEM Screens.

Siga los pasos a continuación para configurar el despachante de un proyecto de AEM Screens.

### Activación de sesiones adhesivas {#enable-sticky-session}

Si desea utilizar varias instancias de publicación delante de un único despachante, deberá actualizar el archivo `dispatcher.any` para habilitar la permanencia

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si tiene una instancia de publicación delante de un despachante, la activación del adhesivo en el despachante no ayudará, ya que el equilibrador de carga puede enviar cada solicitud al despachante. En este caso, debe activar la adherencia en el nivel de equilibrador de carga.

Por ejemplo, si está utilizando ALB de AWS, consulte [Grupos destinatarios para los equilibradores de carga de la aplicación](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para habilitar la permanencia en el nivel ALB. Habilite la permanencia durante 1 día.

### Paso 1: Configuración de encabezados de cliente {#step-configuring-client-headers}

Añada lo siguiente a la sección `/clientheaders`:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Paso 2: Configuración de Filtros de pantalla {#step-configuring-screens-filters}

Para configurar filtros de Pantallas, agregue lo siguiente a ***/filter***.

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

### Paso 3: Deshabilitando la caché de Dispatcher {#step-disabling-dispatcher-cache}

Deshabilite el almacenamiento en caché del despachante para ***/ruta de contenido/pantallas***.

Los reproductores de pantallas utilizan una sesión autenticada, por lo que el despachante no almacena en caché ninguna de las solicitudes de reproductores de pantallas para `channels/assets`.

Para habilitar la caché de los recursos para que se proporcionen desde la caché del despachante, debe:

* Añadir `/allowAuthorization 1` en la sección `/cache`
* Añada las siguientes reglas a la sección `/rules` de `/cache`

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
