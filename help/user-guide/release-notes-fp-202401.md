---
title: Notas de la versión del paquete de funciones 202401 de Screens
description: Siga esta página para obtener información sobre el paquete de funciones de AEM Screens 202401 lanzado el 2 de enero de 2024.
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: e172d2a4a3d2c1f3b555edc8f8ea41b663fc0a30
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---

# Notas de la versión del paquete de funciones 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Se recomienda actualizar a la última versión de 6.5 Adobe Experience Manager AEM (6.5). Podemos obtener la información de la versión más reciente de [aquí](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## Disponibilidad {#availability}

AEM Screens AEM ha lanzado el paquete de funciones 11.1 de 6.5

Puede descargar el paquete de funciones más reciente para la versión 6.5.11.1 de AEM Screens en [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a **Adobe Experience Manager** pestaña y busque **Screens** para obtener el último paquete de funciones titulado **AEM Pantallas FP11.1 de 6.5**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202204 de AEM Screens es el 2 de enero de 2024.

### Novedades {#what-is-new}

Esta versión solo incluye correcciones de seguridad.

### Correcciones de errores {#bug-fixes}

* Problema XSS en el campo &quot;Texto inactivo&quot; del dispositivo AEM Screens. (SCRNS-2614)

* Problema XSS en `screens/dashboard/device.html` a través de `Clear cache` diálogo de acción. (SCRNS-2632)

* Problema XSS en la configuración del reproductor de Screens en `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Se almacena el XSS en déclencheur de título de dispositivos cuando se elimina un dispositivo. (SCRNS-2653)

* Problema XSS en `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS reflejado con el parámetro `item` en `/screens/register-device-wizard.html`. (SCRNS-2670)

* XSS reflejado en `screens/dashboard/device.html` a través de `returnPage` parámetro. (SCRNS-3056)

* Abra Redirigir en assign-device-wizard.html. (SCRNS-3444)

* Abra Redireccionar en el panel del dispositivo. (SCRNS-3443)

* Problema XSS en `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Corregido, Faltan los botones de Programación de periodicidad y Agregar programación: Se detectó un problema en la programación del canal. (SCRNS-2739)

#### Descargas del reproductor AEM Screens  {#aem-screens-player-downloads}

Para descargar el último reproductor de AEM Screens, consulte **[Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/index.html)**.
