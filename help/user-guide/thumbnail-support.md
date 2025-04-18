---
title: Compatibilidad con miniaturas para vídeos en AEM Screens
description: Obtenga información sobre cómo añadir compatibilidad con miniaturas para vídeos en AEM Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 3%

---

# Compatibilidad con miniaturas para vídeos {#thumbnail-support-videos}

## Introducción {#introduction}

Un autor de contenido puede definir una miniatura para los vídeos, de modo que la imagen se utilice como marcador de posición. Puede probar correctamente la reproducción y la segmentación del contenido, mientras el equipo correspondiente finaliza el vídeo real. La imagen también se puede utilizar en caso de que falle la reproducción del vídeo.

Añadir la compatibilidad con una imagen en miniatura en el componente de vídeo permite al cliente añadir correctamente un componente válido en el canal, con contenido real, y realizar cualquier configuración de segmentación antes de que se envíe el vídeo.

>[!NOTE]
>La imagen en miniatura, si se establece en el componente de vídeo, se reproduce si hay un error de reproducción de vídeo en el reproductor. Esta reserva le permite enviar el mensaje deseado a la audiencia (reproduciendo contenido) en lugar de omitirlo por completo.

La compatibilidad con miniaturas le permite:

* Prepare una experiencia de canal cuando los vídeos aún no estén listos o cuando no desee probar necesariamente una descarga de recursos grande en los reproductores

* Establezca un mecanismo de reserva en caso de que haya problemas de reproducción en el dispositivo.

## Uso de miniaturas en vídeos {#using-thumbnails}

Siga los pasos a continuación para utilizar una miniatura en los vídeos:

1. Vaya a un canal de AEM Screens existente o cree un canal.

1. Haga clic en el canal y luego en **Editar** en la barra de acciones.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Añada o edite un componente de vídeo existente, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Haga clic en el vídeo y luego en el icono *llave inglesa*.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Se abre el cuadro de diálogo **Vídeo** en el que puede ver la zona de colocación de **Miniatura**.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Arrastre y suelte una imagen del selector de recursos en la zona de colocación de **Miniatura** y haga clic en **Listo**.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Haga clic en **Vista previa**.

1. Si se establece un vídeo en el componente, se reproduce el vídeo. Si no es así, y la miniatura está configurada, la miniatura se reproduce. De lo contrario, el componente se considera no configurado y se omite.

## Casos de uso admitidos al usar la miniatura en vídeos {#understand-use-case}

La miniatura en vídeos admite los siguientes casos de uso:

* Se omite un componente de vídeo sin ninguna configuración.

* Un componente de vídeo solo con el conjunto de miniaturas reproduce la miniatura.

* Un componente de vídeo con el vídeo (si el vídeo tiene la representación correcta) y el conjunto de miniaturas reproduce el vídeo.

* Un componente de vídeo con el conjunto de vídeos reproduce la miniatura, si hay un error de reproducción, o pasa al siguiente elemento en caso de que la miniatura no esté configurada.
