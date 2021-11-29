---
title: Notas de la versión para Feature Pack 202105
description: '"Siga esta página para obtener información sobre el Feature Pack 202105 de AEM Screens publicado el 4 de junio de 2021".'
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 02bc399d61f5666918caad9fce3d69d63f0782d7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 11%

---

# Notas de la versión para Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Se recomienda actualizar a la última versión de Adobe Experience Manager (AEM). Screens proporciona compatibilidad con el mantenimiento de AEM plataforma Screens 6.3.

## Disponibilidad {#availability}

AEM Screens ha lanzado AEM 6.5 Feature Pack 8.

Puede descargar el último paquete de funciones para la versión 6.5.8 de AEM Screens desde la [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) usar su Adobe ID. Vaya a **Adobe Experience Manager** y busque **Pantallas** para obtener el último feature pack titulado como **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Debe instalar una versión mínima del conector AEM 6.5 Feature Pack 8 para AMS para que funcione una vez que haya instalado los paquetes `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` y `screens core bundles`.

## Fecha de la versión {#release-date}

La fecha de versión del Feature Pack 202105 de AEM Screens es el 4 de junio de 2021.

### Novedades {#what-is-new}

* **Bloqueo de páginas en un canal de AEM Screens**

   AEM Screens ahora es compatible *Bloquear una página*, tal y como se ha implementado en AEM Sites. Adobe Experience Manager (AEM) le permite bloquear páginas para que nadie más pueda modificar su contenido. Esta función es útil cuando realice muchas ediciones en una página concreta o cuando tenga que congelar una página durante un rato.

* **Asignación de nombre al dispositivo del reproductor AEM Screens**

   Los reproductores de AEM Screens ahora incluyen la capacidad de enviar un nombre de dispositivo a Adobe Experience Manager (AEM).
De forma predeterminada, cuando se utiliza el registro masivo para registrar un dispositivo, se introduce un nombre de usuario generado por el sistema en el campo title . Como alternativa, un cliente puede utilizar una etiqueta de recurso u otro nombre descriptivo para que sea visible en AEM y más fácil asignar el contenido adecuado.

   Consulte la siguiente documentación para aprender a configurar el nombre en cada sistema operativo compatible:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Sistema operativo Chrome](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generación de manifiestos**

   Generación más rápida de manifiestos de canal con un rendimiento mejorado, como la asignación de menos recursos al servidor.

### Corrección de errores {#bug-fixes}

* El reproductor mostraba una pantalla negra al cambiar al canal que contenía una secuencia integrada dinámica.
* Los reproductores de Screens ahora bloquean el cambio a cualquier canal roto que evite aún más el error 404 o una página con un mensaje de error.

### Reproductores de AEM Screens publicados {#released-aem-screens-players}

Los siguientes reproductores de AEM Screens están disponibles para AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Descargas del reproductor de AEM Screens  {#aem-screens-player-downloads}

Para descargar el último reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.
