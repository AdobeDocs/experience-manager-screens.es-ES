---
title: Aplicación de transiciones
seo-title: Aplicación de transiciones
description: Siga esta página para aprender a aplicar transiciones a sus proyectos de Screens.
seo-description: Siga esta página para aprender a aplicar transiciones a sus proyectos de Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 2%

---


# Aplicación de transiciones {#applying-transitions}

En esta sección se describe cómo aplicar el componente **Transición** entre distintos recursos (imágenes y vídeos) y secuencias incrustadas en un canal.


>[!CAUTION]
>
>Para obtener más información sobre las propiedades del componente **Transición**, consulte [Transiciones](adding-components-to-a-channel.md#transition).

## Adición de un componente de transición a los recursos en un canal {#adding-transition}

Siga los pasos a continuación para añadir un componente de transición al proyecto de AEM Screens:

>[!NOTE]
>
>**Requisitos previos**
>
>Cree un proyecto de AEM Screens **TestProject** con un canal **TestTransition**. Además, configure una ubicación y una visualización para ver el resultado.

1. Vaya al Canal **TestTransition** y haga clic **Edit** en la barra de acciones.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >El canal **TestTransition** ya contiene pocos recursos (imágenes y vídeos). Por ejemplo, el canal **TestTransition** incluye tres imágenes y dos vídeos, como se muestra a continuación:

   ![image2](assets/transitions2.png)


1. Arrastre y suelte el componente **Transición** en el editor.
   >[!CAUTION]
   >
   >Antes de añadir la transición a los recursos en el canal , asegúrese de no añadir transición antes del primer recurso en el canal secuencial. El primer elemento del canal debe ser un recurso y no una transición.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >De forma predeterminada, las propiedades del componente de transición como **Type** se establecen en **Fade** y **Duration** se establecen en *1600 ms*.  Además, no es aconsejable establecer un tiempo de duración de transición mayor que el recurso al que se aplica.

1. Además, si agrega un componente **Secuencia integrada** (que incluye un canal de secuencia) a este editor de canales, puede agregar un componente de transición al final, de modo que el contenido se reproduzca en orden, como se muestra en la figura siguiente:

   ![image3](assets/transitions5.png)

