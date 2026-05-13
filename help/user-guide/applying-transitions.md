---
title: Aplicación de transiciones
description: Aprenda a aplicar transiciones a sus proyectos de AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
TQID: https://experienceleague.adobe.com/t4JTCyQhe7kb5v-dveK4Np9dAAGLBeatCN2kyTM6ELc
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: e8696a6a-4caa-4059-b0b2-3fbb66f5ab7e
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 276
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
