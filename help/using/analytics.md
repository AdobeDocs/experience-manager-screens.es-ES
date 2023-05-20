---
title: Analytics con AEM Screens
seo-title: Analytics with AEM Screens
description: La página describe Analytics con AEM Screens
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Las partes interesadas habituales de esta actividad son un estratega de marketing/empresarial.

AEM Screens ofrece la capacidad de capturar localmente cada evento rastreable que ejecuta cada dispositivo de reproducción. Estos datos se almacenarán localmente hasta que se puedan cargar en la nube para su procesamiento. Además de todos los datos de evento, también se agregan un ID de dispositivo y una marca de tiempo. Esto garantiza que los datos de un reproductor se puedan distinguir de otro y que los datos ejecutados en diferentes momentos del día se puedan evaluar por separado si lo desea.

Existen dos razones fundamentales por las que es posible que queramos capturar estos datos.

La primera implica **bucles de comentarios y aprendizaje automático** mientras que el segundo implica el **creación de gráficos, tableros e informes** destinados al consumo humano.

AEM En el caso de uso del bucle de comentarios, no nos interesan los informes visuales ni los paneles, sino que queremos definir reglas en las que se pueda ejecutar la modificación de contenido. Al consumir y procesar todos los datos de evento del reproductor Screens desde un período de tiempo determinado, podemos definir una regla que evalúe la eficacia de image1 frente a image2. AEM Al combinar los datos de ventas con los datos de reproducción, puede determinar que image1 tiene un impacto mucho bueno en las ventas e indica automáticamente a todos los reproductores que utilicen image1.

El segundo caso de uso con Analytics es para procesar eventos de reproducción y datos de uso para el consumo humano a través de informes y paneles.
Podemos usar estos datos para crear un mapa de calor de una experiencia interactiva y determinar el mapa de recorrido preferido a través de nuestra aplicación. También podemos elegir la creación de un panel que proporcione una interpretación gráfica de cuántas veces los consumidores interactúan con nuestra aplicación.
