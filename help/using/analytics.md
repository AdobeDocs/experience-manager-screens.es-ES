---
title: Analytics con AEM Screens
description: Obtenga información sobre Adobe Analytics con Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Las partes interesadas habituales de esta actividad son los estrategas de marketing/empresariales.

AEM Screens puede capturar localmente cada evento rastreable que ejecuta cada dispositivo reproductor. Estos datos se almacenan localmente hasta que se pueden cargar en la nube para su procesamiento. Además de todos los datos de evento, también se agregan un ID de dispositivo y una marca de tiempo. Esta funcionalidad garantiza que los datos de un reproductor se puedan distinguir de otro reproductor. Además, los datos que se ejecutan en diferentes momentos del día se pueden evaluar por separado, si lo desea.

Existen dos razones fundamentales por las que es posible que desee capturar estos datos.

El primero implica **bucles de comentarios y aprendizaje automático**, mientras que el segundo implica la **creación de gráficos, paneles e informes** destinados al consumo humano.

AEM En el caso de uso del bucle de comentarios, no es necesario preocuparse por los informes visuales o los paneles, sino que desea definir reglas que se puedan ejecutar en para la modificación de contenido. Al consumir y procesar todos los datos de evento del reproductor de Screens de un periodo determinado, puede definir una regla que evalúe la eficacia de image1 frente a image2. AEM Al combinar los datos de ventas con los datos de reproducción, puede determinar que image1 tiene un mayor impacto en las ventas e indica automáticamente a todos los reproductores que utilicen image1.

El segundo caso de uso con Analytics es para procesar eventos de reproducción y datos de uso para el consumo humano mediante informes y paneles.
Puede utilizar estos datos para crear un mapa de calor de una experiencia interactiva y determinar el mapa de recorrido preferido mediante la aplicación. También puede crear un panel que proporcione una interpretación gráfica de cuántas veces interactúan los consumidores con la aplicación.
