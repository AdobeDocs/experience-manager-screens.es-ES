---
title: Instalación del reproductor Screens
seo-title: Installing Screens Player
description: Siga esta página para obtener más información sobre la instalación del reproductor AEM Screens disponible.
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Instalación de AEM Screens Player {#installing-player}

En esta página se describe cómo instalar el reproductor AEM Screens.

## Reproductor de Screens disponible {#available-players}

El reproductor AEM Screens está disponible para Android, Chrome OS y Windows.

Para descargar **AEM Screens Player**, visite la página [AEM 6.5 Descargas del reproductor](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Una vez que descargue el último reproductor (*.exe*), siga los pasos del reproductor para completar la instalación ad hoc:
>
>1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
>1. Vaya a **Configuration** en el menú de acción de la izquierda, introduzca la dirección de ubicación de la instancia de AEM en **Server** y haga clic en **Save**.
>1. Haga clic en el enlace **Registration** del menú de acción de la izquierda y en los pasos siguientes para completar el proceso de registro del dispositivo.


## Monitorización de reproducción básica {#playback-monitoring}

El reproductor informa de varias métricas de reproducción con cada `ping` cuyo valor predeterminado es de 30 segundos. En función de estas métricas, podemos detectar varios casos extremos, como experiencia atascada, pantalla en blanco y problemas de programación. Esto nos permite comprender y solucionar problemas en el dispositivo y, por lo tanto, acelera la investigación y las medidas correctivas con usted.

La monitorización de reproducción básica en un reproductor AEM Screens permite:

* Monitorice de forma remota si un reproductor reproduce contenido correctamente.

* Mejore la reacción a pantallas en blanco o experiencias rotas en el campo .

* Reduce el riesgo de mostrar una experiencia rota al usuario final.

### Explicación de las propiedades {#understand-properties}

En cada `ping` se incluyen las siguientes propiedades:

| Propiedad | Descripción |
|---|---|
| id {string} | el identificador del reproductor |
| activeChannel {string} | ruta de canal en reproducción o nulo si no hay nada programado |
| activeElements {string} | cadena separada por comas, elementos visibles actualmente en todos los canales de secuencias de reproducción (varios en caso de un diseño de varias zonas) |
| isDefaultContent {boolean} | true si el canal de reproducción se considera un canal predeterminado o de reserva (es decir, tiene prioridad 1 y no hay programación) |
| hasContentChanged {boolean} | true si el contenido ha cambiado en los últimos 5 minutos, false en caso contrario |
| lastContentChange {string} | marca de tiempo del último cambio de contenido |

>[!NOTE]
>De forma opcional, se puede activar una propiedad más avanzada desde las preferencias del reproductor (Activar monitorización de reproducción), es decir:
>|Propiedad|Descripción|
>|—|—|
>|isContentRendering {boolean}|true si la GPU puede confirmar que está reproduciendo contenido real (basado en el análisis de píxeles)|

### Restricciones     {#limitations}

A continuación se enumeran algunas limitaciones de la monitorización de reproducción básica:

* El reproductor informa de su propio estado de reproducción al servidor, por lo que requiere una conexión activa.

* La propiedad `isContentRendering` que comprueba la GPU consume actualmente demasiados recursos para poder habilitarla de forma predeterminada y requiere la inclusión explícita de las preferencias del reproductor. Se recomienda no utilizarlo junto con los vídeos en producción.

* Esta función solo se admite para canales de secuencia y aún no cubre el caso de uso de canales interactivos (SPA).

* Las métricas aún no están completamente expuestas a nuestros clientes, por lo que estamos trabajando duro en habilitar un mecanismo de alerta e informes similar al panel en un futuro próximo.

### Recursos adicionales {#additional-resources}

Consulte los siguientes temas para obtener información detallada:

* Para descargar el Reproductor de Android, visite **Google Play**. Para obtener más información sobre la implementación de Android Watchdog, consulte [Implementación del reproductor Android](implementing-android-player.md).

* Para implementar el Reproductor de Chrome OS, consulte [Consola de administración de Chrome](implementing-chrome-os-player.md) para obtener más información.

* Para configurar el reproductor AEM Screens Windows, consulte [Implementación del reproductor Windows](implementing-windows-player.md).
