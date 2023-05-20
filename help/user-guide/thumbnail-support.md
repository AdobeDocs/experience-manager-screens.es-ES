---
title: Compatibilidad con miniaturas para vídeos en AEM Screens
description: Esta página describe cómo añadir compatibilidad con miniaturas para vídeos en Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: ec58cd9171e359b451eaad7015d42b41ef1bff3f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---

# Compatibilidad con miniaturas para vídeos {#thumbnail-support-videos}

## Introducción {#introduction}

Un autor de contenido puede definir una miniatura para los vídeos, de modo que la imagen pueda utilizarse como marcador de posición y probar correctamente la reproducción y la segmentación del contenido, mientras el equipo correspondiente finaliza el vídeo real. También se puede utilizar la imagen en caso de que falle la reproducción del vídeo.

Añadir la compatibilidad con una imagen en miniatura en el componente de vídeo permite al cliente añadir correctamente un componente válido en el canal, con contenido real, y realizar cualquier configuración de segmentación antes de que se envíe el vídeo.

>[!NOTE]
>La imagen en miniatura, si se configura en el componente de vídeo, se reproduce en caso de que falle la reproducción del vídeo en el reproductor. Esto le permite enviar el mensaje deseado a la audiencia (reproduciendo contenido) en lugar de omitirlo por completo.

La compatibilidad con miniaturas le permite:

* Prepare una experiencia de canal cuando los vídeos aún no estén listos o cuando no desee probar necesariamente una descarga de recursos grande en los reproductores

* Establezca un mecanismo de reserva en caso de que haya problemas de reproducción en el dispositivo.

## Uso de miniaturas en vídeos {#using-thumbnails}

Siga los pasos a continuación para utilizar las miniaturas en los vídeos:

1. Vaya a un canal de Screens existente o cree un canal nuevo.

1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Añada o edite un componente de vídeo existente, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Seleccione el vídeo y haga clic en el icono *llave* para abrir las propiedades del vídeo.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. El **Vídeo** se abre el cuadro de diálogo, donde verá el **Miniatura** zona de colocación.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Arrastre y suelte una imagen desde el selector de recursos hasta el **Miniatura** zona de colocación y haga clic en **Listo**.

   ![imagen](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Haga clic en **Previsualizar**.

1. Si se establece un vídeo en el componente, se reproducirá el vídeo. Si no es así, y la miniatura está configurada, la miniatura se reproducirá. De lo contrario, el componente se considera no configurado y se omitirá.

## Casos de uso admitidos al usar la miniatura en vídeos {#understand-use-case}

La miniatura en vídeos admite los siguientes casos de uso:

* Se omitirá un componente de vídeo sin configurar nada.

* Un componente de vídeo solo con el conjunto de miniaturas reproducirá la miniatura.

* Un componente de vídeo con el vídeo (si el vídeo tiene la representación correcta) y el conjunto de miniaturas reproducirán el vídeo.

* Un componente de vídeo con el conjunto de vídeos reproducirá la miniatura, en caso de error de reproducción, o simplemente pasará al siguiente elemento en caso de que la miniatura no esté configurada.
