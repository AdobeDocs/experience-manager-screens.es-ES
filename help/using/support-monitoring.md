---
title: Monitorización de soporte
description: Obtenga información acerca de la supervisión de soporte para la Guía de prácticas recomendadas de AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Monitorización de soporte {#support-monitoring}

En esta sección se describen las prácticas recomendadas relacionadas con la administración de anomalías de dispositivos y contenido en un proyecto de señalización digital.

La monitorización de soporte incluye:

* **Monitorización de dispositivos**
* **Monitorización de contenido**

## Monitorización de contenido {#content-monitoring}

La monitorización de contenido le permite solucionar los problemas relacionados con el contenido que no se muestra correctamente en la pantalla:

1. Si se encuentra un problema de pantalla en blanco:

   * Compruebe la *previsualización* para que puedan ver si el canal muestra una pantalla en negro.
   * Registre un *reproductor local de chrome* (como extensión) en su portátil a esa pantalla y ver si se muestra una pantalla en negro.
   * Haga clic con el botón derecho, inspeccione y compruebe *registros aplicables*.

   Además, si el problema no se produce en el reproductor local, sino solo en el dispositivo:

   * Compruebe la *tipo de medios* (en uso) que pueden tener problemas en ese dispositivo y también confirmar si el contenido se descargó correctamente localmente (IU del administrador borra la caché del canal).
   * Incluir cualquiera *registros de dispositivo* en el ticket para una solución rápida de problemas.
   * *Recopilar registros* AEM desde el dispositivo desde el punto de vista de la.

## Monitorización de dispositivos {#device-monitoring}

Monitorización del dispositivo relacionada con la monitorización del dispositivo físico si se produce un problema de pantalla en blanco:

1. Si se encuentra un problema de pantalla en blanco:

   * Compruebe si la variable *exhibición* está encendido.
   * Compruebe si la variable *ordenador* está encendido y está enviando una señal.
   * Haga clic con el botón derecho, inspeccione y compruebe *registros aplicables*.
