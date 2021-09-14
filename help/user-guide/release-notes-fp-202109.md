---
title: Notas de la versión para Feature Pack 202109
description: '"Siga esta página para obtener información sobre el paquete de funciones 202105 de AEM Screens, publicado el 22 de septiembre de 2021".'
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: e96c314ea7487932d2ab994ffc41ca8d2af61c5c
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 10%

---

# Notas de la versión para Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Se recomienda actualizar a la última versión de Adobe Experience Manager (AEM). Screens proporciona compatibilidad con el mantenimiento de AEM plataforma Screens 6.3.

## Disponibilidad {#availability}

AEM Screens ha lanzado AEM 6.5 Feature Pack 9.

Puede descargar el último paquete de funciones para la versión 6.5.9 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último feature pack titulado como **AEM 6.5 Screens FP9**.

## Fecha de la versión {#release-date}

La fecha de versión del Feature Pack 202109 de AEM Screens es el 9 de septiembre de 2021.

### Novedades {#what-is-new}

* **Bloqueo de páginas en un canal de AEM Screens**

   AEM Screens ahora admite el *Bloqueo de una página*, como ya se ha implementado en AEM Sites. Adobe Experience Manager (AEM) le permite bloquear páginas para que nadie más pueda modificar su contenido. Esta función es útil cuando realice muchas ediciones en una página concreta o cuando tenga que congelar una página durante un rato.

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
