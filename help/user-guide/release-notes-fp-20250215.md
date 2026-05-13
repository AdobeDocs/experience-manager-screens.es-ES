---
title: Notas de la versión de Feature Pack 20250327 de Screens
description: Obtenga más información acerca del paquete de funciones 20250327 de AEM Screens lanzado el 27 de marzo de 2025.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
TQID: https://experienceleague.adobe.com/q6KAClMHbAULOEumQlx5-FdaaVmAcMOCL8m6KWIB458
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 10%

---

# Notas de la versión del paquete de funciones 20250327 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe recomienda actualizar a la última versión de 6.5 Adobe Experience Manager (AEM 6.5). Puede obtener la información de la versión más reciente de [aquí](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/release-notes/release-notes).
>Adobe recomienda utilizar FP11.6 con SP(servicepack) >= 21.

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
