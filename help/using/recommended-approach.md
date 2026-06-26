---
title: Enfoque recomendado
description: Obtenga información acerca del enfoque recomendado en un proyecto de AEM Screens.
exl-id: 28aacffa-e9c9-4ccb-8038-720bb3e02a3f
TQID: https://experienceleague.adobe.com/r0WE0DQZx3dtGGlNaX9DUX3ckvu2ZdseJLy8-sDJZXQ
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ae478996-b206-4712-9b0c-dc78a2644453
  - id: f18e6c98-d21a-4444-b84b-f327ce464de4
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 482
ht-degree: 0%

---

# Enfoque recomendado {#recommended-approach}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Es una práctica recomendada pensar en cualquier proyecto de AEM Screens a nivel empresarial como una empresa a largo plazo. Es probable que la duración de un proyecto sea de uno o más años, especialmente si la solución permite una interacción compleja del usuario o se implementa en varios dispositivos y ubicaciones.

## Directrices para el desarrollo de una estrategia de publicidad dinámica {#signage-strategy}

Consulte las siguientes recomendaciones antes de desarrollar e implementar un proyecto de señalización digital:

* **Control de ámbito**:
Si la solución deseada es ambiciosa, se recomienda dividir los entregables en fases discretas para controlar el ámbito del proyecto.

* **Casos de uso definidos**:
Las fases del proyecto deben ofrecer casos de uso bien definidos con criterios de éxito claramente identificados.

* **Entregables incrementales**:
Céntrese en ofrecer funciones de forma gradual.

* **Calcular el resultado deseado**:
Comience con las funciones integradas de AEM Screens antes de crear componentes e integraciones personalizados. Tenga siempre en cuenta si se puede alcanzar el resultado deseado mediante los componentes y las funciones que se incluyen de serie en AEM Screens.

* **Definición de programas piloto, despliegues y POC**:
Desarrolle una prueba de concepto (POC) y adáptela según sea necesario mediante un programa piloto y un despliegue.

* **Estrategia de predefinición de contenido**:
Establezca una estrategia de contenido, que incluya objetivos a corto y largo plazo. Además, alinee los objetivos/KPI de la marca con las mejoras de las funciones.

  >[!NOTE]
  >
  > Los costes iniciales suelen ser más elevados en un proyecto de AEM Screens debido a la necesidad de invertir en hardware, accesorios y diseños de sitios. Por lo tanto, mantener las soluciones de contenido inicial más sencillas puede ayudar a administrar las expectativas presupuestarias.

* **Cálculo De Entregables A Gran Escala**:
Si la solución se suministra a gran escala, implemente los componentes de la aplicación en ubicaciones piloto cuidadosamente seleccionadas para su uso de prueba. Envío a nuevas ubicaciones y dispositivos a medida que la aplicación pasa la validación.

  >[!NOTE]
  >
  > Comience a recopilar análisis durante la prueba piloto para que los equipos empresariales puedan validar el éxito de la solución con las métricas específicas que intentan lograr. Saber el rendimiento de la prueba piloto ayuda al equipo empresarial a determinar qué mejoras se deben realizar.

* **División de entregas en tareas mensurables**:
Dividir la entrega de funciones en tareas mensurables permite recibir comentarios, proporciona objetivos más alcanzables y reduce los riesgos generales del proyecto.

* **Desarrollo de una hoja de ruta**:
Si su cliente desea un producto con numerosas funciones, envíe una parte de la funcionalidad planificada al principio del proyecto y programe otras funciones para fases futuras. Una primera entrega con muchas funciones conlleva un mayor riesgo y es más difícil de validar con el cliente.

* **Explicación del ámbito de las integraciones personalizadas**:
Los componentes interactivos con interacción de pantalla táctil, sensor de movimiento o RFID requieren un desarrollo personalizado significativo en el método de implementación. Las presentaciones de diapositivas, los anuncios de vídeo o los menús estáticos se pueden entregar como contenido gráfico o HTML en un canal de Screens.

