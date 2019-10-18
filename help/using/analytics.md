---
title: Analytics con AEM Screens
seo-title: Analytics con AEM Screens
description: La página describe Analytics con AEM Screens
seo-description: La página describe los análisis con AEM Screens
translation-type: tm+mt
source-git-commit: f01b69b860a3862e2b46f11b2d9b95dede742d9c

---


# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Las partes interesadas habituales de esta actividad son los especialistas en marketing y estrategias empresariales.

AEM Screens ofrece la posibilidad de capturar localmente todos los eventos rastreables que ejecuta cada dispositivo de reproductor. Estos datos se almacenarán localmente hasta que se puedan cargar en la nube para su procesamiento. Además de todos los datos del evento, también se agregan un deviceID y una marca de hora. Esto garantiza que los datos de un reproductor se puedan distinguir de otro reproductor y que los datos ejecutados en distintas horas del día se puedan evaluar por separado si se desea.

Existen dos razones fundamentales por las que es posible que deseemos capturar estos datos.

El primero incluye **circuitos de retroalimentación y aprendizaje** automático, mientras que el segundo incluye la **creación de gráficos, tableros e informes** destinados al consumo humano.

En el caso de uso del bucle de retroalimentación, no nos preocupan los informes visuales o los tableros, sino que queremos definir las reglas en las que AEM puede ejecutar para la modificación de contenido. Al consumir y procesar todos los datos de eventos del reproductor de pantallas desde un período de tiempo determinado, podemos definir una regla que evalúe la eficacia de image1 frente a image2. Al combinar los datos de ventas con los datos de reproducción, AEM puede determinar que image1 tiene un impacto mucho mayor en las ventas e indicar automáticamente a todos los reproductores que utilicen image1.

El segundo caso de uso que utiliza Analytics es procesar eventos de reproducción y datos de uso para consumo humano mediante informes y tableros.
Podemos utilizar estos datos para crear un mapa de calor de una experiencia interactiva para determinar el mapa de viaje preferido a través de nuestra aplicación. También podemos elegir crear un tablero que proporcione una interpretación gráfica de cuántas veces los consumidores interactúan con nuestra aplicación.

