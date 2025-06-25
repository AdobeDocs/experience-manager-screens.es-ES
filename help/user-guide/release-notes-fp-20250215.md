---
title: Notas de la versión de Feature Pack 20250327 de Screens
description: Obtenga más información acerca del paquete de funciones 20250327 de AEM Screens lanzado el 27 de marzo de 2025.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
source-git-commit: 6cdf350fa4e45b816d50b64252b8ed6d5e0904d0
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 3%

---

# Notas de la versión del paquete de funciones 20250327 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe recomienda actualizar a la última versión de 6.5 Adobe Experience Manager (AEM 6.5). Puede obtener la información de la versión más reciente de [aquí](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/release-notes/release-notes).
>&#x200B;>Adobe recomienda utilizar FP11.6 con SP(servicepack) >= 21.

## Disponibilidad {#availability}

AEM Screens ha lanzado el paquete de funciones 11.6 de AEM 6.5.

Puede descargar el paquete de funciones más reciente para la versión de AEM Screens 6.5.11.6 desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último paquete de funciones titulado **AEM 6.5 Screens FP11.6**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del AEM Screens Feature Pack 20250327 es el 27 de marzo de 2025.

### Novedades {#what-is-new}

* Esta versión corrige el conflicto de paquetes que los usuarios afrontan con Service Pack 21 y versiones posteriores.

* Esta versión corrige el problema con la vista de tarjetas con SP22 y versiones posteriores.

* **Actualización de AEM Screens Players**
   * El reproductor AEM Screens basado en Linux está oficialmente obsoleto. Se aconseja a los usuarios migrar a otro sistema operativo compatible con AEM Screens.
   * No se realizan más actualizaciones ni mejoras en el Reproductor de AEM Screens basado en Android. Se recomienda a los usuarios migrar a un sistema operativo alternativo compatible con AEM Screens.

### Correcciones de errores {#bug-fixes}

* Conflicto de paquetes con Service Pack 21 y Feature Pack de Screens. (SCRNS-4638)

* El panel de Screens no funciona. (SCRNS-4749)

* Problema XSS en /libs/screens/dcc/components/dashboard/clientlibs/device-clear-cache.js (SCRNS-4761)
