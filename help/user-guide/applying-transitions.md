---
title: Aplicación de transiciones
seo-title: Applying Transitions
description: Siga esta página para aprender a aplicar transiciones a sus proyectos de Screens.
seo-description: Follow this page to learn how to apply transitions to your Screens projects.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Aplicación de transiciones {#applying-transitions}

En esta sección se describe cómo se puede aplicar el **Transición** componente entre diferentes recursos (imágenes y vídeos) y secuencias incrustadas en un canal.


>[!CAUTION]
>
>Para obtener información detallada sobre las propiedades de **Transición** componente, consulte [Transiciones](adding-components-to-a-channel.md#transition).

## Adición de un componente de transición a los recursos de un canal {#adding-transition}

Siga los pasos a continuación para agregar un componente de transición al proyecto de AEM Screens:

>[!NOTE]
>
>**Requisitos previos**
>
>Creación de un proyecto de AEM Screens **TestProject** con un canal **TestTransition**. Además, configure una ubicación y una pantalla para ver el resultado.

1. Navegar al canal **TestTransition** y haga clic en **Editar** de la barra de acciones.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >El **TestTransition** El canal ya tiene pocos recursos (imágenes y vídeos). Por ejemplo, la variable **TestTransition** El canal incluye tres imágenes y dos vídeos, como se muestra a continuación:

   ![image2](assets/transitions2.png)


1. Arrastre y suelte el **Transición** al editor.
   >[!CAUTION]
   >
   >Antes de añadir la transición a los recursos del canal, asegúrese de no añadir la transición antes del primer recurso en el canal secuencial. El primer elemento del canal debe ser un recurso y no una transición.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >De forma predeterminada, las propiedades del componente de transición como **Tipo** se establece en **Atenuación** y el **Duración** se establece en *1600 ms*.  Además, no es aconsejable establecer un tiempo de duración de transición mayor que el recurso al que se está aplicando.

1. Además, si agrega un **Secuencia incrustada** componente (que incluye un canal de secuencia) a este editor de canales, puede añadir un componente de transición al final, para que el contenido se reproduzca en orden, como se muestra en la figura siguiente:

   ![image3](assets/transitions5.png)
