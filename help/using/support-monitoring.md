---
title: Monitoreo de soporte
seo-title: Monitoreo de soporte para AEM Screens
description: La página describe la Guía de optimizaciones de supervisión de asistencia técnica para AEM Screens
seo-description: La página describe la Guía de optimizaciones de supervisión de asistencia técnica para AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Monitoreo de soporte {#support-monitoring}

En esta sección se proporcionan prácticas recomendadas relacionadas con la administración de anomalías de contenido y dispositivos en un proyecto de publicidad dinámica.

La supervisión de soporte incluye:

* **Supervisión de dispositivos**
* **Monitoreo del contenido**

## Monitoreo del contenido {#content-monitoring}

La supervisión del contenido le permite solucionar los problemas relacionados con el contenido que no se muestra correctamente en la pantalla:

1. Si se encuentra un problema con la pantalla en blanco:

   * Compruebe la *previsualización* para ver si el canal muestra una pantalla negra
   * Registre un reproductor *de cromo* local (como extensión) en su portátil para ver si se muestra una pantalla negra.
   * Haga clic con el botón derecho e inspeccione y compruebe los registros *aplicables*.

   Además, si esto no sucede en el reproductor local, sino solo en el dispositivo:

   * Compruebe el tipo *de* medios (en uso) que puede tener problemas en ese dispositivo y confirme también si el contenido se ha descargado localmente correctamente (IU de administración borrar caché de canal).
   * Incluya todos los registros *de* dispositivos en el ticket para solucionar problemas rápidamente.
   * *Recopilar registros* del dispositivo desde AEM.


## Supervisión de dispositivos {#device-monitoring}

Monitoreo del dispositivo relacionado con la supervisión del dispositivo físico si se produce un problema con la pantalla en blanco:

1. Si se encuentra un problema con la pantalla en blanco:

   * Compruebe si la *pantalla* está encendida.
   * Compruebe si el *equipo* está encendido y está enviando una señal.
   * Haga clic con el botón derecho, inspeccione y compruebe los registros *aplicables*.

