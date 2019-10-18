---
title: Monitoreo de soporte
seo-title: Supervisión de la compatibilidad con AEM Screens
description: En la página se describe la Guía de prácticas recomendadas de supervisión de la compatibilidad con AEM Screens
seo-description: En la página se describe la Guía de prácticas recomendadas de supervisión de la compatibilidad con AEM Screens
translation-type: tm+mt
source-git-commit: 3c91e0ec80b29bebcc066f45a1eef1fd74e00a13

---


# Monitoreo de soporte {#support-monitoring}

En esta sección se proporcionan prácticas recomendadas relacionadas con la administración de anomalías de contenido y dispositivos en un proyecto de publicidad dinámica.

La supervisión de soporte incluye:

* **Supervisión de dispositivos**
* **Monitoreo del contenido**

## Monitoreo del contenido {#content-monitoring}

La supervisión del contenido le permite solucionar los problemas relacionados con el contenido que no se muestra correctamente en la pantalla:

1. Si se encuentra un problema con la pantalla en blanco:

   * Compruebe la *vista previa* para ver si el canal muestra una pantalla negra
   * Registre un reproductor *de cromo* local (como extensión) en su portátil para ver si se muestra una pantalla negra.
   * Haga clic con el botón derecho e inspeccione y compruebe los registros *aplicables*.
   Además, si esto no sucede en el reproductor local, sino solo en el dispositivo:

   * Compruebe el tipo *de* medios (en uso) que puede tener problemas en ese dispositivo y confirme también si el contenido se ha descargado localmente correctamente (IU de administración: caché de canal transparente).
   * Incluya todos los registros *de* dispositivos en el ticket para solucionar problemas rápidamente.
   * *Recopilar registros* desde el dispositivo desde AEM.


## Supervisión de dispositivos {#device-monitoring}

Monitoreo del dispositivo relacionado con la supervisión del dispositivo físico si se produce un problema con la pantalla en blanco:

1. Si se encuentra un problema con la pantalla en blanco:

   * Compruebe si la *pantalla* está encendida.
   * Compruebe si el *equipo* está encendido y está enviando una señal.
   * Haga clic con el botón derecho, inspeccione y compruebe los registros *aplicables*.

