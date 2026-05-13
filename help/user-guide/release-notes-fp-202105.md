---
title: Notas de la versión del paquete de funciones 202105
description: Obtenga información acerca del paquete de funciones 202105 de AEM Screens lanzado el 4 de junio de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
TQID: https://experienceleague.adobe.com/lm2FhBZ2X-GzGoCRrsUuAKmC7vPfyaPXwYXSTxxOBJg
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 415
ht-degree: 5%

---

# Notas de la versión del paquete de funciones 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe recomienda actualizar a la última versión de Adobe Experience Manager (AEM). AEM Screens proporciona compatibilidad de mantenimiento para la plataforma Screens de AEM 6.3.

## Disponibilidad {#availability}

AEM Screens ha lanzado AEM 6.5 Feature Pack 8.

Puede descargar el paquete de funciones más reciente para la versión 6.5.8 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último paquete de funciones titulado **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Instale la versión mínima del paquete de funciones 8 de AEM 6.5 para que el conector de AMS funcione después de instalar los paquetes `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` y `screens core bundles`.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202105 de AEM Screens es el 4 de junio de 2021.

### Novedades {#what-is-new}

* **Bloqueando página en un canal de AEM Screens**

  AEM Screens ahora admite *Bloquear una página*, como ya se implementó en AEM Sites. Adobe Experience Manager (AEM) permite bloquear páginas para que nadie más pueda editar su contenido. Esta función es útil cuando realiza varias ediciones en una página específica o cuando debe congelar una página durante un corto tiempo.

* **Nombrar el dispositivo del reproductor de AEM Screens**

  Los reproductores de AEM Screens ahora incluyen la capacidad de enviar un nombre de dispositivo a Adobe Experience Manager (AEM).
De forma predeterminada, cuando se utiliza el registro masivo para registrar un dispositivo, se introduce un nombre de usuario generado por el sistema en el campo de título. Como alternativa, un cliente puede utilizar una etiqueta de recursos u otro nombre descriptivo para que sea visible en AEM y fácil de asignar el contenido adecuado.

  Consulte la siguiente documentación para obtener información sobre cómo configurar el nombre en cada sistema operativo admitido:

   * [Android™](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [SO CHROME](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generación de manifiesto**

  Generación de manifiestos de canal más rápida con un rendimiento mejorado, como la asignación de menos recursos en el servidor.

### Correcciones de errores {#bug-fixes}

* El reproductor mostraba una pantalla en negro al cambiar a un canal que contenía una secuencia incrustada dinámica.
* Los reproductores de Screens ahora bloquean el cambio a cualquier canal roto que evita aún más un error 404 o una página con un mensaje de error.

### Reproductores de AEM Screens publicados

Los siguientes reproductores AEM Screens se incluyen en el paquete de funciones 8 de AEM 6.5:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Descargas del reproductor AEM Screens

Para descargar el último Reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del Reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.
