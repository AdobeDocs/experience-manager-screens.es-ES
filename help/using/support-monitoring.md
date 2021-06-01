---
title: Supervisión del soporte
seo-title: Supervisión de la compatibilidad con AEM Screens
description: En la página se describe la Guía de prácticas recomendadas de supervisión de la compatibilidad con AEM Screens
seo-description: En la página se describe la Guía de prácticas recomendadas de supervisión de la compatibilidad con AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Supervisión de soporte {#support-monitoring}

En esta sección se ofrecen prácticas recomendadas relacionadas con la administración de anomalías de contenido y dispositivos en un proyecto de publicidad dinámica.

La supervisión de la compatibilidad incluye:

* **Monitorización de dispositivos**
* **Supervisión del contenido**

## Supervisión de contenido {#content-monitoring}

La monitorización de contenido permite solucionar los problemas relacionados con el contenido que no se muestra correctamente en la pantalla:

1. Si se encuentra un problema con la pantalla en blanco:

   * Compruebe *preview* para ver si el canal está mostrando una pantalla negra
   * Registre un *reproductor local de Chrome* (como extensión) en su portátil en esa pantalla y compruebe si se muestra una pantalla negra.
   * Haga clic con el botón derecho, inspeccione y compruebe *registros aplicables*.

   Además, si esto no está ocurriendo en el reproductor local sino solo en el dispositivo:

   * Compruebe el *tipo de medio* (en uso) que pueda tener problemas en ese dispositivo y confirme también si el contenido se descargó localmente correctamente (interfaz de usuario de administración borra la caché del canal).
   * Incluya todos los *registros de dispositivo* en el ticket para una solución rápida de problemas.
   * *Recopile* registros del dispositivo desde AEM.


## Monitorización de dispositivos {#device-monitoring}

Monitorización de dispositivos relacionada con la monitorización del dispositivo físico si se produce un problema con la pantalla en blanco:

1. Si se encuentra un problema con la pantalla en blanco:

   * Compruebe si la *pantalla* está activada.
   * Compruebe si el *equipo* está encendido y está enviando una señal.
   * Haga clic con el botón derecho, inspeccione y compruebe *registros aplicables*.

