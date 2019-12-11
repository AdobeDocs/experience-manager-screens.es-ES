---
title: Aplicación de transiciones
seo-title: Aplicación de transiciones
description: Siga esta página para aprender a aplicar transiciones a sus proyectos de Pantallas.
seo-description: Siga esta página para aprender a aplicar transiciones a sus proyectos de Pantallas.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 2708464222321fd138c986f19d8572c71f1dae75

---


# Aplicación de transiciones {#applying-transitions}

En esta sección se describe cómo un componente **Transición** le permite agregar una transición al proyecto Pantallas.


>[!CAUTION]
>
>Para obtener información detallada sobre las propiedades del componente Transición, consulte [Transiciones](adding-components-to-a-channel.md#transition)

## Adición de un componente de transición a recursos en un canal {#adding-transition}

Siga los pasos a continuación para añadir un componente de transición a su proyecto de AEM Screens:

>[!NOTE]
>
>**Requisitos previos**
> Cree un proyecto **TestProject** de AEM Screens con un canal **TestTransition**. Además, configure una ubicación y una pantalla para ver el resultado.

1. Vaya a Channel **TestTransition** y haga clic en **Editar** en la barra de acciones.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >El canal **TestTransition** ya tiene pocos recursos (imágenes y vídeos) en él. Por ejemplo, el canal **TestTransition** incluye tres imágenes y dos vídeos, como se muestra a continuación:

   ![image2](assets/transitions2.png)


1. Arrastre y suelte el componente **Transición** en el editor.
   >[!CAUTION]
   >
   >Antes de agregar la transición a los recursos del canal, asegúrese de:
No se agrega transición antes del primer recurso en el canal secuencial. El primer elemento del canal debe ser un recurso y no una transición.

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >De forma predeterminada, el componente de transición se establece en Tipo como **Normal** con **Duración** definida en *600 ms*.  Además, no es aconsejable establecer un tiempo de duración de transición más largo que el recurso al que se está aplicando.


## Adición de un componente de transición a vídeos en un canal {#adding-transition-videos}

Al aplicar el componente de transición entre vídeos, defina siempre el **tipo** en **Desvanecimiento** y la duración **de la** secuencia en **1600 ms**.

![image3](assets/transitions4.png)