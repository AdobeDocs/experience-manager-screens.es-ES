---
title: Instalación del reproductor de Screens
seo-title: Installing Screens Player
description: Siga esta página para obtener más información acerca de la instalación del Reproductor de AEM Screens disponible.
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 1%

---

# Instalación del reproductor de AEM Screens {#installing-player}

En esta página se describe cómo instalar el reproductor AEM Screens.

## Reproductor de pantallas disponible {#available-players}

El reproductor AEM Screens está disponible para Android, Chrome OS y Windows.

Para descargar **Reproductor de AEM Screens**, visite la [AEM Descargas del reproductor de 6.5 en](https://download.macromedia.com/screens/) página.

>[!NOTE]
>
>Una vez descargado el último reproductor (*.exe*), siga los pasos en el reproductor para completar la instalación ad-hoc:
>
>1. Pulse durante mucho tiempo en la esquina superior izquierda para abrir el panel de administración.
>1. Vaya a **Configuración** AEM en el menú de acción de la izquierda e introduzca la dirección de ubicación de la instancia de en **Servidor** y haga clic en **Guardar**.
>1. Haga clic en **Registro** desde el menú de acción de la izquierda y los pasos a continuación para completar el proceso de registro del dispositivo.

## Monitorización de reproducción básica {#playback-monitoring}

El reproductor informa de varias métricas de reproducción con cada una `ping` el valor predeterminado es de 30 segundos. En función de estas métricas, podemos detectar varios casos extremos, como experiencias atascadas, pantallas en blanco y problemas de programación. Esto nos permite comprender y solucionar problemas en el dispositivo y, por lo tanto, acelerar una investigación y medidas correctivas con usted.

La monitorización de la reproducción básica en un reproductor AEM Screens nos permite:

* Monitorice de forma remota si un reproductor está reproduciendo el contenido correctamente.

* Mejore la reacción a pantallas en blanco o experiencias rotas en el campo.

* Reduce el riesgo de mostrar una experiencia rota al usuario final.

### Explicación de propiedades {#understand-properties}

Las siguientes propiedades se incluyen en cada `ping`:

| Propiedad | Descripción |
|---|---|
| id {string} | el identificador del reproductor |
| activeChannel {string} | ruta de canal en reproducción, o nulo si no hay nada programado |
| activeElements {string} | cadena separada por comas, elementos visibles actualmente en todos los canales de secuencia de reproducción (varios en el caso de un diseño de varias zonas) |
| isDefaultContent {boolean} | true si el canal de reproducción se considera un canal predeterminado o de reserva (es decir, tiene prioridad 1 y no hay programación) |
| hasContentChanged {boolean} | true si el contenido ha cambiado en los últimos 5 minutos, false en caso contrario |
| lastContentChange {string} | marca de tiempo del último cambio de contenido |

>[!NOTE]
>De forma opcional, se puede activar una propiedad más avanzada en las preferencias del reproductor (Activar monitorización de reproducción), que puede ser:
>|Propiedad|Descripción|
>|—|—|
>|isContentRendering {boolean}|true si la GPU puede confirmar que está reproduciendo contenido real (según el análisis de píxeles)|

### Restricciones {#limitations}

A continuación se enumeran algunas limitaciones de la monitorización básica de la reproducción:

* El reproductor informa de su propio estado de reproducción al servidor, por lo que requiere una conexión activa.

* El `isContentRendering` La propiedad de que comprueba la GPU consume demasiados recursos como para habilitarla de forma predeterminada y requiere la inclusión explícita en las preferencias del reproductor. Se recomienda no utilizarlo junto con los vídeos en producción.

* SPA Esta función solo se admite para canales de secuencia y aún no cubre el caso de uso de canales interactivos ().

* Las métricas aún no están completamente expuestas a nuestros clientes. Estamos trabajando duro para habilitar un mecanismo de creación de informes y alertas similar a un panel en un futuro próximo.

### Recursos adicionales {#additional-resources}

Consulte los siguientes temas para obtener información detallada:

* Para descargar el reproductor de Android, visite **Google Play**. Para obtener más información sobre la implementación de Android Watchdog, consulte [Implementación del reproductor Android](implementing-android-player.md).

* Para implementar el reproductor Chrome OS, consulte [Consola de administración de Chrome](implementing-chrome-os-player.md) para obtener más información.

* Para configurar el reproductor de Windows de AEM Screens, consulte [Implementación del Reproductor de Windows](implementing-windows-player.md).
