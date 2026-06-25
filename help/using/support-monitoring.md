---
title: Monitorización de soporte
description: Obtenga información acerca de la supervisión de soporte para la Guía de prácticas recomendadas de AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 0%

---

# Monitorización de soporte {#support-monitoring}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

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
   * *Recopilar registros* del dispositivo desde AEM.

## Monitorización de dispositivos {#device-monitoring}

Monitorización del dispositivo relacionada con la monitorización del dispositivo físico si se produce un problema de pantalla en blanco:

1. Si se encuentra un problema de pantalla en blanco:

   * Comprueba si la *pantalla* está encendida.
   * Comprueba si el *equipo* está encendido y está enviando una señal.
   * Haga clic con el botón derecho, inspeccione y compruebe *registros aplicables*.
