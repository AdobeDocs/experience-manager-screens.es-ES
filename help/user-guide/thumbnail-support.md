---
title: Compatibilidad con miniaturas para vídeos en AEM Screens
description: En esta página se describe cómo agregar compatibilidad con miniaturas para vídeos en Screens.
index: false
source-git-commit: e1f46a908a10bdf08985c857fb9302d3e111e9a1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Compatibilidad con miniaturas para vídeos {#thumbnail-support-videos}

## Introducción {#introduction}

Un autor de contenido puede definir una miniatura para los vídeos, de modo que la imagen pueda utilizarse como marcador de posición y probar correctamente la reproducción y el destino del contenido, mientras el equipo adecuado está finalizando el vídeo en sí. También se puede utilizar la imagen en caso de que falle la reproducción del vídeo.

La adición de compatibilidad con una imagen en miniatura en el componente de vídeo permite al cliente añadir correctamente un componente válido en el canal, con contenido real, y realizar cualquier configuración de destino antes de que el vídeo se entregue.

>[!NOTE]
>La imagen en miniatura, si se establece en el componente de vídeo, se reproduce en caso de que falle la reproducción del vídeo en el reproductor. Esto le permite enviar el mensaje deseado a la audiencia (reproduciendo contenido) en lugar de omitirlo completamente.

La compatibilidad con miniaturas le permite:

* Prepare una experiencia de canal cuando los vídeos aún no estén listos, o cuando no necesariamente desee probar una descarga de recursos de gran tamaño en los reproductores

* Establezca un mecanismo de reserva, en caso de que haya problemas de reproducción en el dispositivo.

## Uso de miniaturas en vídeos {#using-thumbnails}

Siga los pasos a continuación para usar miniaturas en vídeos:

1. Vaya a un canal Screens existente o cree un canal nuevo.


1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para abrir el editor.

1. Añada o edite un componente de vídeo existente, como se muestra en la figura siguiente.

1. Seleccione el vídeo y haga clic en el icono *llave inglesa* para abrir las propiedades del vídeo.

1. Se abre el cuadro de diálogo **Vídeo** donde verá la zona de colocación **Miniatura**.

1. Arrastre y suelte una imagen del selector de recursos en la zona de colocación **Miniatura** y haga clic en **Listo**.

1. Haga clic en **Preview**.

1. Si se establece un vídeo en el componente, se reproducirá el vídeo. Si no es así, y la miniatura está configurada, entonces se reproducirá la miniatura. De lo contrario, el componente se considera no configurado y se omitirá.

## Casos de uso compatibles con el uso de miniaturas en vídeos {#understand-use-case}

Las miniaturas de los vídeos son compatibles con los siguientes casos de uso:

* Se omitirá un componente de vídeo sin configurar nada.

* Un componente de vídeo con solo el conjunto de miniaturas reproducirá la miniatura.

* Un componente de vídeo con el vídeo (si el vídeo tiene la representación correcta) y el conjunto de miniaturas reproducirán el vídeo.

* Un componente de vídeo con el conjunto de vídeo reproducirá la miniatura, en caso de error de reproducción, o simplemente se saltará al siguiente elemento en caso de que la miniatura no esté configurada.
