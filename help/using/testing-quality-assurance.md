---
title: Pruebas y control de calidad
seo-title: Comprobación y garantía de calidad para AEM Screens
description: La página describe la Guía de optimizaciones de prueba y garantía de calidad para AEM Screens
seo-description: La página describe la Guía de optimizaciones de prueba y garantía de calidad para AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# Pruebas y control de calidad {#testing-quality}

>[!NOTE]
>El accionista típico de esta actividad es un integrador A/V.

A medida que nos acercamos a la implementación real de la red de publicidad dinámica, debemos crear un plan de pruebas y control de calidad que aborde todos los elementos de la red, incluidos todos los componentes de hardware, todos los componentes de software y todos los componentes de red.
En la fase, deben construirse y probarse todos los sistemas de ensayo.

Debe crearse una lista de comprobación que identifique todos los KPI definidos previamente y que mida la entrega en relación con ellos.

>[!NOTE]
>
>Esta fase también debería utilizarse como herramienta para crear una instalación y una guía del usuario que posteriormente se pueda enviar con el equipo y mantener in situ para consulta futura.

Deben considerarse los siguientes elementos:

## 1. Consideraciones mecánicas {#mechanical-considerations}

Se recomiendan las siguientes consideraciones mecánicas:

* montaje en pantalla
* montaje del reproductor
* ventilación
* anexos periféricos
* administración de cables
* red de dispositivos

## 2. Consideraciones de software {#software-considerations}

Se recomiendan las siguientes consideraciones de software:

* registro del dispositivo
* publicación de medios
* reproducción
* dependencias de base de datos (definidas previamente)


## 3. Consideraciones de administración de dispositivos {#device-management-considerations}

AEM Screens incluye un módulo de Device Control Center que permite la administración de los puntos finales de la aplicación del reproductor de pantallas.

Esto hace referencia a cualquier dispositivo de hardware *reproductor* que tenga instalada la aplicación de reproductor de Pantallas y esté registrado en una instancia de AEM.
Este módulo le permite:

1. Monitorear registros de errores de la aplicación del reproductor
1. Administrar capturas de pantalla remotas
1. Administrar descargas de contenido
1. Administrar problemas de reinicio de la aplicación

Para obtener información detallada sobre ***Device Control Center***, consulte [Resolución de problemas del Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) en **Guía del usuario de AEM Screens**.

>[!CAUTION]
>
> No debe utilizar el Centro de control de dispositivos para:
> 1. Instalar nuevas versiones de la aplicación del reproductor
> 1. Supervisar los recursos de nivel del sistema
> 1. Solucionar errores de nivel de sistema
> 1. Permitir la intervención en equipos de escritorio remotos



>[!NOTE]
>
> Adobe recomienda que las plataformas de administración de dispositivos de terceros dedicadas se utilicen en todas las implementaciones.

La plataforma específica elegida depende de una serie de factores, como el ***sistema operativo destinatario***, los ***requisitos del proyecto*** y el ***número de puntos finales***.

Algunos ejemplos son:

* Administración de dispositivos de Google Chrome
* TeamViewer
* AirWatch
* 42 engranajes
* Portátil de integración de AV propietario
