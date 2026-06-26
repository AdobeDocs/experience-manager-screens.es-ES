---
title: Déclencheur de datos
description: Obtenga información sobre los déclencheur de datos en AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 0%

---

# Optimizaciones dinámicas de Creative {#dynamic-creative}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>
>Una parte interesada típica de esta actividad es un implementador de AEM.

**Dynamic Creative Optimization**, o DCO, se usa para crear experiencias de señalización digital que reflejen las circunstancias únicas de cualquier ubicación en un momento dado y para cualquier usuario dado.

Este uso también se denomina aplanamiento del contenido en el lado del cliente.

El razonamiento es garantizar que cada dispositivo de reproducción o punto final pueda utilizar conjuntos de datos para determinar el mejor contenido para reproducir automáticamente en función de varios factores diferentes.

Esta funcionalidad elimina la necesidad de una intervención humana constante al crear contenido. También ayuda a reducir el coste total de propiedad para operar la red y hace que las experiencias digitales sean más relevantes, contextuales y efectivas.

Algunos ejemplos son:

* uso del nivel de inventario actual de productos de funciones
* temperatura exterior o tiempo
* la presencia de una campaña de anuncios en los medios locales
* tráfico web e incluso eventos locales como cuando un cliente recoge un producto para examinarlo

Todos estos ejemplos y más se pueden utilizar para proporcionar un nivel más alto de contexto y personalización.

Tener una estrategia de comercialización visual que incluya DCO puede aumentar considerablemente la visibilidad en la red.

Existen dos tipos principales de déclencheur de datos:

* **Déclencheur de datos locales**: estos déclencheur de datos son locales en el dispositivo. Por ejemplo, si toca la pantalla, se activa un sensor que déclencheur un recurso de datos local o un conmutador de canal.
* **Déclencheur de datos remotos**: esto implicó un cambio de canal activado por datos o un cambio de recurso basado en los valores devueltos por una API de servicio web.

