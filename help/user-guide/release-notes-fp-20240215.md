---
title: Notas de la versión de Feature Pack 20240215 de Screens
description: Obtenga más información acerca del paquete de funciones 20240215 de AEM Screens lanzado el 15 de febrero de 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e4149f5b-42c0-43c8-b275-ecbe90104a98
TQID: https://experienceleague.adobe.com/yasPGCEV-9sw-TNqKeF0NJo6p1UKi2JvfYyR4D4ID-g
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
    internal-label: Experience Manager Screens
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 6ecc9375c5ddbc8c0aea5f267fdd4596dcfdec6f
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 15%
---
# Notas de la versión del paquete de funciones 20240215 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>
>Adobe recomienda actualizar a la última versión de 6.5 Adobe Experience Manager (AEM 6.5). Puede obtener la información de la versión más reciente de [aquí](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/release-notes/release-notes).

## Disponibilidad {#availability}

AEM Screens ha lanzado AEM 6.5 Feature Pack 11.3.

Puede descargar el paquete de funciones más reciente para la versión de AEM Screens 6.5.11.3 desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último paquete de funciones titulado **AEM 6.5 Screens FP11.3**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del AEM Screens Feature Pack 20240215 es el 15 de febrero de 2024.

### Novedades {#what-is-new}

Esta versión solo incluye correcciones de seguridad.

### Correcciones de errores {#bug-fixes}

* Se ha eliminado la comprobación de alternancia de la corrección proporcionada anteriormente en FP11.1 para XSS en `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Problema XSS en `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js`. (SCRNS-3973)
