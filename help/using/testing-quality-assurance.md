---
title: Pruebas y control de calidad
seo-title: Testing and Quality Assurance for AEM Screens
description: En la página se describe la Guía de prácticas recomendadas de Testing and Quality Assurance para AEM Screens
seo-description: The page describes Testing and Quality Assurance for AEM Screens Best Practices Guide
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# Pruebas y control de calidad {#testing-quality}

>[!NOTE]
>La parte interesada habitual de esta actividad es un integrador A/V.

A medida que nos acercamos a la implementación real de la red de publicidad dinámica, debemos crear un plan de pruebas y control de calidad que aborde todos los elementos de la red, incluidos todos los componentes de hardware, todos los componentes de software y todos los componentes de red.
En esta fase, deben construirse y probarse completamente todos los sistemas de ensayo.

Se debe crear una lista de comprobación que identifique todos los KPI definidos anteriormente y mida la entrega con ellos.

>[!NOTE]
>
>Esta fase también debe utilizarse como herramienta para crear una guía de instalación y usuario que posteriormente puede enviarse con el equipo y mantenerse en el sitio para referencia futura.

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

AEM Screens incluye un módulo de Centro de control de dispositivos que permite administrar los puntos finales de la aplicación del reproductor Screens.

Esto hace referencia a cualquier *jugador* AEM dispositivo de hardware que tiene instalada la aplicación de reproducción Screens y está registrado en una instancia de, así como una instancia de, que tiene la función de reproducción de la aplicación de software de la aplicación de reproducción de pantalla.
Este módulo le permite:

1. Monitorizar registros de errores de aplicaciones del reproductor
1. Administrar capturas de pantalla remotas
1. Administrar descargas de contenido
1. Administrar problemas de reinicio de aplicaciones

Para obtener información detallada sobre ***Centro de control de dispositivos***, consulte [Solución de problemas del Centro de control de dispositivos](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) in **Guía del usuario de AEM Screens**.

>[!CAUTION]
>
> No debe usar el Centro de control de dispositivos para lo siguiente:
> 1. Instalación de nuevas versiones de la aplicación de reproducción
> 1. Monitorización de recursos de nivel de sistema
> 1. Solucionar errores de nivel del sistema
> 1. Permitir la intervención del escritorio remoto



>[!NOTE]
>
> El Adobe recomienda que se utilicen plataformas de administración de dispositivos de terceros específicas para todas las implementaciones.

La plataforma específica elegida depende de una serie de factores, incluidos los siguientes ***sistema operativo de destino***, ***requisitos del proyecto*** y ***número de puntos finales***.

Algunos ejemplos son:

* Google Chrome Device Management
* TeamViewer
* AirWatch
* 42Gears
* Middleware exclusivo integrador AV
