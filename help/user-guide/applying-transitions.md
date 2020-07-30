---
title: Aplicación de Transiciones
seo-title: Aplicación de Transiciones
description: Siga esta página para conocer cómo aplicar transiciones a sus proyectos de Pantallas.
seo-description: Siga esta página para conocer cómo aplicar transiciones a sus proyectos de Pantallas.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# Aplicación de Transiciones {#applying-transitions}

En esta sección se describe cómo aplicar el componente de **Transición** entre distintos recursos (imágenes y vídeos) y secuencias incrustadas en un canal.


>[!CAUTION]
>
>Para obtener información detallada sobre las propiedades del componente de **Transición** , consulte [Transiciones](adding-components-to-a-channel.md#transition).

## Añadir componente de Transición a recursos en un Canal {#adding-transition}

Siga los pasos a continuación para agregar un componente de transición al proyecto de AEM Screens:

>[!NOTE]
>
>**Requisitos previos**
>
> Cree un proyecto de AEM Screens **TestProject** con un canal **TestTransition**. Además, configure una ubicación y una pantalla para la vista del resultado.

1. Vaya a Canal **TestTransition** y haga clic en **Editar** en la barra de acciones.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >El canal **TestTransition** ya tiene pocos recursos (imágenes y vídeos). Por ejemplo, el canal **TestTransition** incluye tres imágenes y dos vídeos, como se muestra a continuación:

   ![image2](assets/transitions2.png)


1. Arrastre y suelte el componente de **Transición** en el editor.
   >[!CAUTION]
   >
   >Antes de agregar la transición a los recursos del canal, asegúrese de no agregar transición antes del primer recurso del canal secuencial. El primer elemento del canal debe ser un recurso y no una transición.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >De forma predeterminada, las propiedades del componente de transición, como **Tipo** , se establecen en **Desvanecer** y la **Duración** se establece en *1600 ms*.  Además, no es aconsejable establecer un tiempo de duración de transición que sea más largo que el recurso al que se está aplicando.

1. Además, si agrega un componente Secuencia **** incrustada (que incluye un canal de secuencia) a este editor de canal, puede agregar un componente de transición al final para que el contenido se reproduzca en orden, como se muestra en la figura siguiente:

   ![image3](assets/transitions5.png)

