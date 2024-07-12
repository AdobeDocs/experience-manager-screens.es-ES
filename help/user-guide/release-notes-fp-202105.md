---
title: Notas de la versión del paquete de funciones 202105
description: Obtenga información acerca del paquete de funciones 202105 de AEM Screens lanzado el 4 de junio de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 3%

---

# Notas de la versión del paquete de funciones 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>El Adobe recomienda actualizar a la última versión de Adobe Experience Manager AEM (). AEM Screens AEM proporciona compatibilidad de mantenimiento para la plataforma Screens de la versión 6.3 de la plataforma de la.

## Disponibilidad {#availability}

AEM Screens AEM ha lanzado el paquete de funciones 8 de la versión 6.5.

Puede descargar el paquete de funciones más reciente para la versión 6.5.8 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens AEM** para obtener el último paquete de funciones con el título **6.5 Screens FP8**.

>[!IMPORTANT]
>AEM Instale la versión mínima del paquete de funciones 8 de 6.5 para que el conector AMS funcione después de instalar los paquetes `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` y `screens core bundles`.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202105 de AEM Screens es el 4 de junio de 2021.

### Novedades {#what-is-new}

* **Bloqueando página en un canal de AEM Screens**

  AEM Screens ahora admite *Bloquear una página*, como ya se implementó en AEM Sites. Adobe Experience Manager AEM () permite bloquear páginas para que nadie más pueda editar su contenido. Esta función es útil cuando realiza varias ediciones en una página específica o cuando debe congelar una página durante un corto tiempo.

* **Nombrar el dispositivo del reproductor de AEM Screens**

  Los reproductores de AEM Screens ahora incluyen la capacidad de enviar un nombre de dispositivo a Adobe Experience Manager AEM ().
De forma predeterminada, cuando se utiliza el registro masivo para registrar un dispositivo, se introduce un nombre de usuario generado por el sistema en el campo de título. AEM Como alternativa, un cliente puede utilizar una etiqueta de recursos u otro nombre descriptivo para que sea visible en los recursos y resulte más fácil asignar el contenido adecuado.

  Consulte la siguiente documentación para obtener información sobre cómo configurar el nombre en cada sistema operativo admitido:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [SO CHROME](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generación de manifiesto**

  Generación de manifiestos de canal más rápida con un rendimiento mejorado, como la asignación de menos recursos en el servidor.

### Correcciones de errores {#bug-fixes}

* El reproductor mostraba una pantalla en negro al cambiar a un canal que contenía una secuencia incrustada dinámica.
* Los reproductores de Screens ahora bloquean el cambio a cualquier canal roto que evita aún más un error 404 o una página con un mensaje de error.

### Reproductores de AEM Screens publicados

Los siguientes reproductores de AEM Screens AEM se incluyen en el paquete de funciones 8 de la versión 6.5 de:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Descargas del reproductor AEM Screens

Para descargar el último Reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del Reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.
