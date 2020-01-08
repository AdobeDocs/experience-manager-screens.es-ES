---
title: Uso de la sincronización de comandos
seo-title: Uso de la sincronización de comandos
description: Siga esta página para conocer cómo utilizar la sincronización de comandos.
seo-description: Siga esta página para conocer cómo utilizar la sincronización de comandos.
translation-type: tm+mt
source-git-commit: 8f9ede8681c8c23cefa66c1177e2761ed8aae2fd

---


# Uso de la sincronización de comandos {#using-command-sync}

En la página siguiente se describe cómo utilizar la sincronización de comandos. La sincronización de comandos permite la reproducción sincronizada entre distintos reproductores. Los reproductores pueden reproducir contenido diferente, pero cada recurso debe tener la misma duración.

## Información general {#overview}

Las soluciones de señalización digital necesitan admitir paredes de vídeo y reproducción sincronizada para admitir escenarios como las cuentas regresivas de Año Nuevo o los vídeos de gran tamaño divididos para reproducirse en varias pantallas, y es aquí donde entra en juego la sincronización de contenido.

Para utilizar la sincronización de contenido, un reproductor actúa como *maestro* y envía el comando y todos los demás reproductores actúan como *clientes* y se reproducen cuando reciben el comando. El *maestro* envía un comando a todos los clientes registrados cuando está a punto de iniciar la reproducción de un elemento. La carga útil de esto puede ser el índice del elemento que se va a reproducir y/o el HTML externo del elemento que se va a reproducir.



