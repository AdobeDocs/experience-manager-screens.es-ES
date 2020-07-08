---
title: Configuraciones de Dispatcher para AEM Screens
seo-title: Configuraciones de Dispatcher para AEM Screens
description: Esta página resalta las directrices para configurar el despachante para un proyecto de AEM Screens.
seo-description: Esta página resalta las directrices para configurar el despachante para un proyecto de AEM Screens.
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 7%

---


# Configuraciones de Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager.

La siguiente página proporciona las directrices para configurar el despachante para un proyecto de AEM Screens.

>[!NOTE]
>
>Si hay un despachante disponible, las conexiones al servlet de registro se pueden evitar filtrando las reglas del despachante.
>
>Si no hay ningún distribuidor, deshabilite el servlet de registro en la lista de componentes OSGi.

## Requisitos previos {#pre-requisites}

Antes de configurar el despachante para un proyecto de AEM Screens, debe tener conocimientos previos de Dispatcher.

Consulte [Configuración de Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obtener más información.

## Configuración de Dispatcher {#configuring-dispatcher}

Siga los pasos a continuación para configurar el despachante de un proyecto de AEM Screens.

### Paso 1: Configuración de encabezados de cliente {#step-configuring-client-headers}

Añada lo siguiente a la `/clientheaders`sección:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Paso 2: Configuración de Filtros de pantalla {#step-configuring-screens-filters}

Para configurar filtros de Pantallas, agregue lo siguiente a ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Paso 3: Desactivación de la caché de Dispatcher {#step-disabling-dispatcher-cache}

Deshabilite el almacenamiento en caché del despachante para la ruta ****** de contenido/pantallas.
