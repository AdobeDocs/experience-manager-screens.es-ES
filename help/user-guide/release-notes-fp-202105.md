---
title: Notas de la versión del paquete de funciones 202105
description: '"Siga esta página para obtener información sobre el paquete de funciones de AEM Screens 202105 lanzado el 4 de junio de 2021".'
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 02bc399d61f5666918caad9fce3d69d63f0782d7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 11%

---

# Notas de la versión del paquete de funciones 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Se recomienda actualizar a la última versión de Adobe Experience Manager AEM (). AEM Screens proporciona soporte de mantenimiento para la plataforma de Screens de la versión 6.3 de.

## Disponibilidad {#availability}

AEM Screens AEM ha lanzado el paquete de funciones 8 de la versión 6.5.

Puede descargar el paquete de funciones más reciente para la versión 6.5.8 de AEM Screens en [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a **Adobe Experience Manager** pestaña y busque **Screens** para obtener el último paquete de funciones titulado **AEM Pantallas FP8 de 6,5**.

>[!IMPORTANT]
>AEM Debe instalar una versión mínima del paquete de funciones 8 de 6.5 para que el conector de AMS funcione una vez instalados los paquetes `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` y el `screens core bundles`.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202105 de AEM Screens es el 4 de junio de 2021.

### Novedades {#what-is-new}

* **Bloquear páginas en un canal de AEM Screens**

   AEM Screens ahora es compatible *Bloquear una página*, como ya se implementó en AEM Sites. Adobe Experience Manager AEM () permite bloquear páginas para que nadie más pueda modificar su contenido. Esta función es útil cuando realice muchas ediciones en una página concreta o cuando tenga que congelar una página durante un rato.

* **Nombrar el dispositivo del reproductor de AEM Screens**

   Los reproductores de AEM Screens ahora incluyen la capacidad de enviar un nombre de dispositivo a Adobe Experience Manager AEM ().
De forma predeterminada, cuando se utiliza el registro masivo para registrar un dispositivo, se introduce un nombre de usuario generado por el sistema en el campo de título. AEM Como alternativa, un cliente puede utilizar una etiqueta de recursos u otro nombre descriptivo para que sea visible en los recursos y resulte más fácil asignar el contenido adecuado.

   Consulte la siguiente documentación para aprender a configurar el nombre en cada sistema operativo admitido:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generación de manifiestos**

   Generación de manifiestos de canal más rápida con un rendimiento mejorado, como la asignación de menos recursos en el servidor.

### Correcciones de errores {#bug-fixes}

* El reproductor mostraba una pantalla en negro al cambiar al canal que contenía la secuencia incrustada dinámica.
* Los reproductores de Screens ahora bloquean el cambio a cualquier canal roto que evita aún más el error 404 o una página con un mensaje de error.

### Reproductores de AEM Screens publicados {#released-aem-screens-players}

Los siguientes reproductores de AEM Screens AEM se incluyen en el paquete de funciones 8 de la versión 6.5 de:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Descargas del reproductor AEM Screens  {#aem-screens-player-downloads}

Para descargar el reproductor de AEM Screens más reciente y obtener más información sobre las correcciones de errores, consulte **[Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/index.html)**.
