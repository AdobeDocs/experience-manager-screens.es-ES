---
title: Analytics con AEM Screens
seo-title: Analytics con AEM Screens
description: La página describe Analytics con AEM Screens
seo-description: La página describe los análisis con AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Las partes interesadas típicas de esta actividad son los especialistas en marketing y estrategias empresariales.

AEM Screens oferta la capacidad de capturar localmente todos los eventos rastreables que ejecuta cada dispositivo de reproductor. Estos datos se almacenarán localmente hasta que se puedan cargar en la nube para su procesamiento. Además de todos los datos de evento, también se agregan un deviceID y una marca de hora. Esto garantiza que los datos de un reproductor se puedan distinguir de otro reproductor y que los datos ejecutados en distintas horas del día se puedan evaluar por separado si se desea.

Existen dos razones fundamentales por las que es posible que deseemos capturar estos datos.

La primera implica **bucles de retroalimentación y aprendizaje automático** mientras que la segunda implica la **creación de gráficos, paneles e informes** que están destinados al consumo humano.

En el caso de uso del bucle de retroalimentación, no nos preocupan los informes o paneles visuales, sino que queremos definir reglas en las que AEM ejecutar para la modificación de contenido. Al consumir y procesar todos los datos de evento del reproductor de Pantallas desde un período de tiempo determinado, podemos definir una regla que evalúe la efectividad de image1 frente a image2. Al combinar los datos de ventas con los datos de reproducción, AEM puede determinar que image1 tiene un impacto muy bueno en las ventas e indicar automáticamente a todos los reproductores que utilicen image1.

El segundo caso de uso que utiliza Analytics es procesar eventos de reproducción y datos de uso para consumo humano mediante informes y paneles.
Podemos usar estos datos para crear un mapa de calor de una experiencia interactiva para determinar el mapa de recorrido preferido a través de nuestra aplicación. También podemos elegir crear un panel que proporcione una interpretación gráfica de cuántas veces los consumidores interactúan con nuestra aplicación.

