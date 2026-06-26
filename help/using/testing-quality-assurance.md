---
title: Pruebas y calidad de Assurance
description: Obtenga información acerca de las pruebas y la garantía de calidad para AEM Screens en la Guía de prácticas recomendadas.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
TQID: https://experienceleague.adobe.com/So83gHv7n21zhdoCdWHVf0yswyQuSr1hLWmCA7uHSiE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 392
ht-degree: 0%

---

# Pruebas y calidad de Assurance {#testing-quality}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>Una de las partes interesadas habituales en esta actividad es un integrador de audio y vídeo.

A medida que se acerca la implementación de la red de publicidad dinámica, cree un plan de pruebas y control de calidad que aborde todos los elementos de la red, incluidos todos los componentes de hardware, todos los componentes de software y todos los componentes de red.En esta fase, deben construirse y probarse completamente todos los sistemas de ensayo.

Se debe crear una lista de comprobación que identifique todos los KPI definidos anteriormente y mida las entregas con respecto a ellos.

>[!NOTE]
>
>Esta fase también debe utilizarse como herramienta para crear una instalación y una guía del usuario. Ambos pueden enviarse posteriormente con el equipo y mantenerse en el sitio para referencia futura.

Deben tenerse en cuenta los siguientes elementos:

## &#x200B;1. Consideraciones mecánicas {#mechanical-considerations}

Se recomiendan las siguientes consideraciones mecánicas:

* montaje en pantalla
* montaje del reproductor
* ventilación
* accesorios periféricos
* tendido de cables
* redes de dispositivos

## &#x200B;2. Consideraciones de software {#software-considerations}

Se recomiendan las siguientes consideraciones de software:

* registro de dispositivo
* publicación de medios
* reproducción
* dependencias de base de datos (previamente definidas)


## &#x200B;3. Consideraciones de administración de dispositivos {#device-management-considerations}

AEM Screens incluye un módulo del Centro de control de dispositivos que permite administrar los extremos de la aplicación del reproductor de Screens.

Hace referencia a cualquier dispositivo de hardware *player* que tenga instalada la aplicación Screens player y esté registrado en una instancia de AEM.Este módulo le permite:

1. Monitorizar registros de errores de aplicaciones del reproductor
1. Administrar capturas de pantalla remotas
1. Administrar descargas de contenido
1. Administrar problemas de reinicio de aplicaciones

Para obtener información detallada sobre el ***Centro de control de dispositivos***, consulte [Solución de problemas del Centro de control de dispositivos](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) en la **Guía del usuario de AEM Screens**.

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
> Adobe recomienda utilizar plataformas de administración de dispositivos de terceros dedicadas para todas las implementaciones.

La plataforma específica elegida depende de varios factores, entre ellos ***sistema operativo de destino***, ***requisitos del proyecto*** y ***número de puntos finales***.

Algunos ejemplos son los siguientes:

* Google Chrome Device Management
* TeamViewer
* AirWatch
* `42Gears`
* Middleware de integrador de audio y vídeo patentado

