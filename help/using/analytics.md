---
title: Analytics con AEM Screens
seo-title: Analytics con AEM Screens
description: En la página se describe Analytics con AEM Screens
seo-description: La página describe los análisis con AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Las partes interesadas habituales de esta actividad son los especialistas en marketing/estrategias empresariales.

AEM Screens ofrece la capacidad de capturar localmente cada evento rastreable que se ejecute en cada dispositivo de reproductor. Estos datos se almacenan localmente hasta que se puedan cargar en la nube para su procesamiento. Además de todos los datos de evento, también se añaden deviceID y una marca de tiempo. Esto garantiza que los datos de un reproductor se puedan distinguir de otro y que los datos ejecutados en diferentes momentos del día se puedan evaluar por separado si lo desea.

Existen dos razones fundamentales por las que es posible que deseemos capturar estos datos.

El primero implica **bucles de comentarios y aprendizaje automático** mientras que el segundo implica la **creación de gráficos, tableros e informes** que están destinados al consumo humano.

En el caso de uso del bucle de comentarios, no nos preocupan los informes visuales o los paneles, sino que queremos definir reglas en las que AEM ejecutar para la modificación de contenido. Al consumir y procesar todos los datos de evento del reproductor Screens desde un período de tiempo determinado, podemos definir una regla que evalúe la eficacia de image1 frente a image2. Al combinar los datos de ventas con los datos de reproducción, AEM puede determinar que image1 tiene un impacto muy bueno en las ventas y automáticamente ordena a todos los reproductores que utilicen image1.

El segundo caso de uso que utiliza analytics es el de procesar eventos de reproducción y datos de uso para consumo humano mediante informes y paneles.
Podemos usar estos datos para crear un mapa de calor de una experiencia interactiva para determinar el mapa de recorrido preferido a través de nuestra aplicación. También podemos elegir crear un panel que proporcione una interpretación gráfica de cuántas veces los consumidores interactúan con nuestra aplicación.

