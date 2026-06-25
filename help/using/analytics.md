---
title: Analytics con AEM Screens
description: Obtenga información sobre Adobe Analytics con Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
TQID: https://experienceleague.adobe.com/i7B7E5Kyno2U-ZTxEOPfhrr9W7fqYTWTV5vvcteRicY
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---

# Analytics con AEM Screens {#analytics-screens}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>
>Las partes interesadas habituales de esta actividad son los estrategas de marketing/empresariales.

AEM Screens puede capturar localmente cada evento rastreable que ejecuta cada dispositivo reproductor. Estos datos se almacenan localmente hasta que se pueden cargar en la nube para su procesamiento. Además de todos los datos de evento, también se agregan un ID de dispositivo y una marca de tiempo. Esta funcionalidad garantiza que los datos de un reproductor se puedan distinguir de otro reproductor. Además, los datos que se ejecutan en diferentes momentos del día se pueden evaluar por separado, si lo desea.

Existen dos razones fundamentales por las que es posible que desee capturar estos datos.

El primero implica **bucles de comentarios y aprendizaje automático**, mientras que el segundo implica la **creación de gráficos, paneles e informes** destinados al consumo humano.

En el caso de uso del bucle de comentarios, no es necesario preocuparse por los informes visuales o los paneles, sino que desea definir reglas en las que AEM puede ejecutar la modificación de contenido. Al consumir y procesar todos los datos de evento del reproductor de Screens de un periodo determinado, puede definir una regla que evalúe la eficacia de image1 frente a image2. Al combinar los datos de ventas con los datos de reproducción, AEM puede determinar que image1 tiene un mayor impacto en las ventas e indicar automáticamente a todos los reproductores que utilicen image1.

El segundo caso de uso con Analytics es para procesar eventos de reproducción y datos de uso para el consumo humano mediante informes y paneles.
Puede utilizar estos datos para crear un mapa de calor de una experiencia interactiva y determinar el mapa de recorrido preferido mediante la aplicación. También puede crear un panel que proporcione una interpretación gráfica de cuántas veces interactúan los consumidores con la aplicación.
