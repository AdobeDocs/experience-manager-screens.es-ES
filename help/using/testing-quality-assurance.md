---
title: Pruebas y control de calidad
description: Obtenga información acerca de las pruebas y la garantía de calidad para AEM Screens en la Guía de prácticas recomendadas.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Pruebas y control de calidad {#testing-quality}

>[!NOTE]
>Una de las partes interesadas habituales en esta actividad es un integrador de audio y vídeo.

A medida que se acerca la implementación de la red de publicidad dinámica, cree un plan de pruebas y control de calidad que aborde todos los elementos de la red, incluidos todos los componentes de hardware, todos los componentes de software y todos los componentes de red.
En esta fase, deben construirse y probarse completamente todos los sistemas de ensayo.

Se debe crear una lista de comprobación que identifique todos los KPI definidos anteriormente y mida las entregas con respecto a ellos.

>[!NOTE]
>
>Esta fase también debe utilizarse como herramienta para crear una instalación y una guía del usuario. Ambos pueden enviarse posteriormente con el equipo y mantenerse en el sitio para referencia futura.

Deben tenerse en cuenta los siguientes elementos:

## 1. Consideraciones mecánicas {#mechanical-considerations}

Se recomiendan las siguientes consideraciones mecánicas:

* montaje en pantalla
* montaje del reproductor
* ventilación
* accesorios periféricos
* tendido de cables
* redes de dispositivos

## 2. Consideraciones de software {#software-considerations}

Se recomiendan las siguientes consideraciones de software:

* registro de dispositivo
* publicación de medios
* reproducción
* dependencias de base de datos (previamente definidas)


## 3. Consideraciones de administración de dispositivos {#device-management-considerations}

AEM Screens incluye un módulo del Centro de control de dispositivos que permite administrar los extremos de la aplicación del reproductor de Screens.

Hace referencia a cualquier dispositivo de hardware *player* que tenga instalada la aplicación Screens AEM player y esté registrado en una instancia de.
Este módulo le permite:

1. Monitorizar registros de errores de aplicaciones del reproductor
1. Administrar capturas de pantalla remotas
1. Administrar descargas de contenido
1. Administrar problemas de reinicio de aplicaciones

Para obtener información detallada sobre el ***Centro de control de dispositivos***, consulte [Solución de problemas del Centro de control de dispositivos](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) en la **Guía del usuario de AEM Screens**.

>[!CAUTION]
>
>No utilice el Centro de control de dispositivos para:
>
>* Instalación de nuevas versiones de la aplicación de reproducción
>* Monitorización de recursos de nivel de sistema
>* Solucionar errores de nivel del sistema
>* Permitir la intervención del escritorio remoto


>[!NOTE]
>
> El Adobe recomienda utilizar plataformas de administración de dispositivos de terceros para todas las implementaciones.

La plataforma específica elegida depende de varios factores, entre ellos ***sistema operativo de destino***, ***requisitos del proyecto*** y ***número de puntos finales***.

Algunos ejemplos son los siguientes:

* Google Chrome Device Management
* TeamViewer
* AirWatch
* `42Gears`
* Middleware de integrador de audio y vídeo patentado
