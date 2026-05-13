---
title: Notas de la versión del paquete de funciones 202103
description: Obtenga más información acerca del paquete de funciones 202103 de AEM Screens lanzado el 5 de marzo de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
TQID: https://experienceleague.adobe.com/x7dgY8u-SdWo2JRK1W2uqRWtHy2wtXdAnIcS0gRoxiY
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 407
ht-degree: 4%

---

# Notas de la versión del paquete de funciones 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe recomienda actualizar a la última versión de Adobe Experience Manager (AEM). AEM Screens proporciona compatibilidad de mantenimiento para la plataforma Screens de AEM 6.3.

## Disponibilidad {#availability}

AEM Screens ha lanzado el paquete de funciones 7 de AEM 6.5.

Puede descargar el paquete de funciones más reciente para la versión 6.5.7 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último paquete de funciones titulado **AEM 6.5 Screens FP7**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 202103 de AEM Screens es el 5 de marzo de 2021.

### Novedades {#what-is-new}

* **Registro automático de reproductores en AEM Screens**

  El registro masivo de miles de jugadores manualmente es engorroso y añade tiempo y costo. Para simplificar este proceso, la función Registro automático de reproductores permite especificar una clave previamente compartida en AEM. Esta clave se puede aprovisionar en un reproductor mediante un archivo de configuración o una solución de administración de dispositivos móviles (MDM).

  Consulte [Registro automático de jugadores](/help/user-guide/auto-registration-players.md) para obtener más información.


* **Aprovisionamiento masivo del reproductor Android™ mediante Enterprise Mobility Management**

  Al implementar el reproductor Android™ de forma masiva, resulta tedioso registrar cada reproductor manualmente con AEM. Se recomienda encarecidamente usar una solución de EMM (Enterprise Mobility Management) como `VMWare Airwatch`, `MobileIron` o `Samsung Knox` para aprovisionar y administrar la implementación de forma remota. El reproductor AEM Screens Android™ es compatible con el estándar del sector EMM AppConfig para permitir el aprovisionamiento remoto.

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

Los siguientes reproductores AEM Screens se incluyen en el paquete de funciones 7 de AEM 6.5:

* SO CHROME
* Windows
* Linux®

#### Descargas del reproductor AEM Screens

Para descargar el último Reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del Reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.
