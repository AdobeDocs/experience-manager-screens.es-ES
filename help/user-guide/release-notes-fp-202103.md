---
title: Notas de la versión del paquete de funciones 202103
description: Obtenga más información acerca del paquete de funciones 202103 de AEM Screens lanzado el 5 de marzo de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---

# Notas de la versión del paquete de funciones 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>El Adobe recomienda actualizar a la última versión de Adobe Experience Manager AEM (). AEM Screens AEM proporciona compatibilidad de mantenimiento para la plataforma Screens de la versión 6.3 de la plataforma de la.

## Disponibilidad {#availability}

AEM Screens AEM ha lanzado el paquete de funciones 7 de la versión 6.5.

Puede descargar el paquete de funciones más reciente para la versión 6.5.7 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens AEM** para obtener el último paquete de funciones con el título **6.5 Screens FP7**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202103 de AEM Screens es el 5 de marzo de 2021.

### Novedades {#what-is-new}

* **Registro automático de reproductores en AEM Screens**

  El registro masivo de miles de jugadores manualmente es engorroso y añade tiempo y costo. AEM Para simplificar este proceso, la función Registro automático de reproductores le permite especificar una clave previamente compartida en la. Esta clave se puede aprovisionar en un reproductor mediante un archivo de configuración o una solución de administración de dispositivos móviles (MDM).

  Consulte [Registro automático de jugadores](/help/user-guide/auto-registration-players.md) para obtener más información.


* **Aprovisionamiento masivo del reproductor Android™ mediante Enterprise Mobility Management**

  Al implementar el reproductor de AndroidAEM ™ de forma masiva, resulta tedioso registrar cada reproductor manualmente con la opción de configuración de la aplicación de forma manual Se recomienda encarecidamente usar una solución de EMM (Enterprise Mobility Management) como `VMWare Airwatch`, `MobileIron` o `Samsung Knox` para aprovisionar y administrar la implementación de forma remota. El reproductor AEM Screens Android™ es compatible con el estándar del sector EMM AppConfig para permitir el aprovisionamiento remoto.

  Consulte [Aprovisionamiento masivo del reproductor Android™ mediante Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) para obtener más información.


### Correcciones de errores {#bug-fixes}

* Rendimiento mejorado para calcular `clientlib` y `asset hashes`.

* La migración a SmartSync dañaría el reproductor si la caché no se invalidara.

* No se crearon cachés sin conexión si la asignación tenía *OfflineConfig*.

* Actualizaciones en el reproductor `Tizen` que se interrumpió porque no se admite la directiva de referente strict-origin-when-cross-origin.

* Al cambiar la programación del canal asignado *Repeticiones*, el campo dañaba la interfaz de usuario.

* La actualización del contenido sin conexión fallaba con excepciones de consulta.

* El lapso de tiempo entre transiciones durante la interacción en una experiencia interactiva ya es fijo.

* Una solicitud de actualización de configuración errónea provocaba pantallas en blanco.

### Reproductores de AEM Screens publicados

Los siguientes reproductores de AEM Screens AEM se incluyen en el paquete de funciones 7 de la versión 6.5 de:

* SO CHROME
* Windows
* Linux®

#### Descargas del reproductor AEM Screens

Para descargar el último Reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del Reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.
