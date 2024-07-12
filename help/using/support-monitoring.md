---
title: Monitorización de soporte
description: Obtenga información acerca de la supervisión de soporte para la Guía de prácticas recomendadas de AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Monitorización de soporte {#support-monitoring}

En esta sección se describen las prácticas recomendadas relacionadas con la administración de anomalías de dispositivos y contenido en un proyecto de señalización digital.

La monitorización de soporte incluye:

* **Supervisión de dispositivos**
* **Supervisión del contenido**

## Monitorización de contenido {#content-monitoring}

La monitorización de contenido le permite solucionar los problemas relacionados con el contenido que no se muestra correctamente en la pantalla:

1. Si se encuentra un problema de pantalla en blanco:

   * Comprueba la *vista previa* para ver si el canal muestra una pantalla en negro.
   * Registre un *reproductor local de Chrome* (como extensión) en su portátil para ver si muestra una pantalla en negro.
   * Haga clic con el botón derecho, inspeccione y compruebe los *registros aplicables*.

   Además, si el problema no se produce en el reproductor local, sino solo en el dispositivo:

   * Compruebe el *tipo de medio* (en uso) que puede tener problemas en ese dispositivo y también confirme si el contenido se descargó correctamente de manera local (IU del administrador borra la caché del canal).
   * Incluya *registros de dispositivo* en el ticket para una rápida solución de problemas.
   * AEM *Recopilar registros* del dispositivo desde el dispositivo de la cuenta de usuario de.

## Monitorización de dispositivos {#device-monitoring}

Monitorización del dispositivo relacionada con la monitorización del dispositivo físico si se produce un problema de pantalla en blanco:

1. Si se encuentra un problema de pantalla en blanco:

   * Comprueba si la *pantalla* está encendida.
   * Comprueba si el *equipo* está encendido y está enviando una señal.
   * Haga clic con el botón derecho, inspeccione y compruebe *registros aplicables*.
