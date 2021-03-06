---
title: Notas de la versión para Feature Pack 202103
description: La página resalta las notas de la versión del Feature Pack 202103.
translation-type: tm+mt
source-git-commit: dfbf904c1f23f7e41a9d65a270c5ca667ddcdb31
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---


# Notas de la versión para Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Se recomienda actualizar a la versión más reciente de Adobe Experience Manager (AEM). Screens proporciona compatibilidad con el mantenimiento de la plataforma AEM 6.3 Screens.

## Disponibilidad {#availability}

AEM Screens ha lanzado AEM 6.5 Feature Pack 7.

Puede descargar el último paquete de funciones para la versión 6.5.7 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último feature pack titulado como **AEM 6.5 Screens FP7**.

## Fecha de la versión {#release-date}

La fecha de versión del paquete de funciones 202103 de AEM Screens es el 5 de marzo de 2021.

### Novedades {#what-is-new}

* **Registro automático de reproductores en AEM Screens**

   El registro masivo de miles de jugadores manualmente es muy complicado y añade tiempo y costo. Para simplificar este proceso, la función Registro automático de reproductores permite especificar una clave previamente compartida en AEM que se puede aprovisionar en un reproductor a través de un archivo de configuración o una solución de Administración de dispositivos móviles (MDM).

   Consulte [Registro automático de reproductores](/help/user-guide/auto-registration-players.md) para obtener más información.


* **Aprovisionamiento masivo de Android Player mediante Enterprise Mobility Management**

   Al implementar el reproductor de Android de forma masiva, resulta tedioso registrar manualmente cada reproductor con AEM. Es muy recomendable utilizar una solución EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron o Samsung Knox para aprovisionar y administrar su implementación de forma remota. El reproductor de Android de AEM Screens es compatible con el estándar del sector EMM AppConfig para permitir el aprovisionamiento remoto.

   Consulte [Aprovisionamiento masivo de Reproductor de Android mediante Enterprise Mobility Management](/help/user-guide/using-emm-bulkprovision-android-player.md) para obtener más información.


### Corrección de errores {#bug-fixes}

* Se ha mejorado el rendimiento para la computación `clientlib` y `asset hashes`.

* La migración de SmartSync dañaría el reproductor si la caché no se invalida.

* No se crearon cachés sin conexión si la asignación tenía *OfflineConfig*.

* Actualizaciones en el reproductor Tizen que se han interrumpido porque no se admite la directiva de referente &quot;origen estricto cuando origen cruzado&quot;.

* El cambio del campo *Repeats* de programación del canal asignado dañaba la interfaz de usuario.

* La actualización del contenido sin conexión fallaba con excepciones de consulta.

* El lapso de tiempo entre transiciones durante la interacción en la experiencia interactiva ahora está fijo.

* El error en la solicitud de actualización de configuración causaba la pantalla en blanco.

### Reproductores de AEM Screens publicados {#released-aem-screens-players}

Los siguientes reproductores de AEM Screens están disponibles para AEM 6.5 Feature Pack 7:

* Sistema operativo Chrome
* Windows
* Linux

#### Descargas del reproductor de AEM Screens {#aem-screens-player-downloads}

Para descargar el último reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.
