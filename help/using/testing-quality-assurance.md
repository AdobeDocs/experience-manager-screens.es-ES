---
title: Pruebas y control de calidad
seo-title: Pruebas y control de calidad para AEM Screens
description: En la página se describe la Guía de prácticas recomendadas de Pruebas y control de calidad para AEM Screens
seo-description: En la página se describe la Guía de prácticas recomendadas de Pruebas y control de calidad para AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# Pruebas y control de calidad {#testing-quality}

>[!NOTE]
>El accionista típico de esta actividad es un integrador A/V.

A medida que nos acercamos a la implementación real de la red de publicidad dinámica, debemos crear un plan de pruebas y control de calidad que aborde todos los elementos de la red, incluidos todos los componentes de hardware, todos los componentes de software y todos los componentes de red.
En esta fase, se deben crear y probar todos los sistemas de ensayo.

Se debe crear una lista de comprobación que identifique todos los KPI definidos anteriormente y que mida el envío en relación con ellos.

>[!NOTE]
>
>Esta fase también debe utilizarse como herramienta para la creación de una instalación y guía de usuario que luego pueda enviarse con el equipo y mantenerse en el sitio para referencia futura.

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

* registro de dispositivos
* publicación de medios
* reproducción
* dependencias de base de datos (definidas anteriormente)


## 3. Consideraciones de administración de dispositivos {#device-management-considerations}

AEM Screens incluye un módulo Device Control Center que permite la administración de puntos finales de aplicación del reproductor Screens.

Esto hace referencia a cualquier dispositivo de hardware *player* que tenga instalada la aplicación de reproductor Screens y esté registrado en una instancia de AEM.
Este módulo le permite:

1. Registros de errores de la aplicación del reproductor
1. Administrar capturas de pantalla remotas
1. Administrar descargas de contenido
1. Administrar problemas de reinicio de aplicaciones

Para obtener más información sobre ***Device Control Center***, consulte [Resolución de problemas del centro de control de dispositivos](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) en la **Guía del usuario de AEM Screens**.

>[!CAUTION]
>
> No debe utilizar el Centro de control de dispositivos para:
> 1. Instalar nuevas versiones de la aplicación del reproductor
> 1. Monitorizar los recursos de nivel del sistema
> 1. Resolución de problemas de errores de nivel del sistema
> 1. Permitir la intervención del escritorio remoto



>[!NOTE]
>
> Adobe recomienda utilizar plataformas de administración de dispositivos de terceros dedicadas para todas las implementaciones.

La plataforma específica elegida depende de una serie de factores, incluidos el ***sistema operativo de destino***, los ***requisitos del proyecto*** y el ***número de puntos finales***.

Algunos ejemplos son:

* Administración de dispositivos de Google Chrome
* Visor de equipos
* AirWatch
* 42Engranajes
* Programación automática para integradores
