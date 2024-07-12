---
title: Aplicación de transiciones
description: Aprenda a aplicar transiciones a sus proyectos de AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Aplicación de transiciones {#applying-transitions}

En esta sección se describe cómo se puede aplicar el componente **Transición** entre distintos recursos (imágenes y vídeos) y secuencias incrustadas en un canal.

>[!CAUTION]
>
>Para obtener información detallada sobre las propiedades del componente **Transition**, consulte [Transiciones](adding-components-to-a-channel.md#transition).

## Adición del componente Transición a Assets en un canal {#adding-transition}

Siga los pasos a continuación para agregar un componente de transición al proyecto de AEM Screens:

>[!NOTE]
>
>**Requisitos previos**
>
>Cree un proyecto de AEM Screens **TestProject** con un canal **TestTransition**. Asimismo, configure una ubicación y una pantalla para ver el resultado.

1. Vaya al canal **TestTransition** y haga clic en **Editar** en la barra de acciones.

   ![imagen1](assets/transitions1.png)

   >[!NOTE]
   >
   >El canal **TestTransition** ya contiene algunos recursos (imágenes y vídeos). Por ejemplo, el canal **TestTransition** incluye tres imágenes y dos vídeos, como se muestra a continuación:

   ![imagen2](assets/transitions2.png)


1. Arrastre y suelte el componente **Transition** en su editor.

   >[!CAUTION]
   >
   >Antes de añadir la transición a los recursos del canal, asegúrese de no agregar la transición antes del primer recurso en el canal secuencial. El primer elemento del canal debe ser un recurso y no una transición.

   ![imagen3](assets/transitions3.png)

   >[!NOTE]
   >
   >De manera predeterminada, las propiedades del componente de transición como **Type** se establecen en **Fade** y **Duration** se establece en *1600 milisegundos*. Además, no es aconsejable establecer un tiempo de duración de transición mayor que el recurso al que se está aplicando.

1. Además, si agrega un componente **Secuencia incrustada** (que incluye un canal de secuencia) a este editor de canales, puede agregar un componente de transición al final. Al hacerlo, se garantiza que el contenido se reproduzca en el orden correcto, como se ve en la siguiente imagen:

   ![imagen3](assets/transitions5.png)
