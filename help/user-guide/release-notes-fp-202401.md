---
title: Notas de la versión de Feature Pack 202401 de Screens
description: Obtenga información acerca del paquete de funciones 202401 de AEM Screens lanzado el 2 de enero de 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 4%

---

# Notas de la versión del paquete de funciones 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>El Adobe recomienda actualizar a la última versión de 6.5 Adobe Experience Manager AEM (6.5). Obtenga la información de la versión más reciente de [aquí](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/release-notes/release-notes).

## Disponibilidad {#availability}

AEM Screens AEM ha lanzado el paquete de funciones 11.1 de 6.5.

Puede descargar el paquete de funciones más reciente para la versión 6.5.11.1 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens AEM** para obtener el último paquete de funciones con el título **6.5 Screens FP11.1**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202204 de AEM Screens es el 2 de enero de 2024.

### Novedades {#what-is-new}

Esta versión solo incluye correcciones de seguridad.

### Correcciones de errores {#bug-fixes}

* Problema XSS en el campo &quot;Texto inactivo&quot; del dispositivo AEM Screens. (SCRNS-2614)

* Problema XSS en `screens/dashboard/device.html` mediante el cuadro de diálogo de acción `Clear cache`. (SCRNS-2632)

* Problema XSS en la configuración del reproductor de Screens en `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Se almacena el XSS en déclencheur de título de dispositivos cuando se elimina un dispositivo. (SCRNS-2653)

* Problema XSS en `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* Se reflejó XSS con el parámetro `item` en `/screens/register-device-wizard.html`. (SCRNS-2670)

* Se reflejó XSS en `screens/dashboard/device.html` mediante el parámetro `returnPage`. (SCRNS-3056)

* Abra Redirigir en assign-device-wizard.html. (SCRNS-3444)

* Abra Redireccionar en el panel del dispositivo. (SCRNS-3443)

* Problema XSS en `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Corregido, Faltan los botones de Programación de periodicidad y Agregar programación: Se detectó un problema en la programación del canal. (SCRNS-2739)
