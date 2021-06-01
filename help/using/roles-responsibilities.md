---
title: Funciones y responsabilidades del proyecto de AEM Screens
seo-title: Funciones y responsabilidades del proyecto de AEM Screens
description: La página describe las funciones y responsabilidades del proyecto de AEM Screens
seo-description: La página describe las funciones y responsabilidades del proyecto de AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 11%

---


# Funciones y responsabilidades del proyecto {#roles-responsibilities}

Como implementador experimentado de AEM, probablemente habrá visto las funcionalidades a las que se hace referencia como *Autores*, *Desarrolladores* y *Técnicos/TI*.

En un proyecto típico de AEM Screens, las funciones se refinan aún más, ya que cada una de ellas cumple un objetivo importante en el proyecto.

El diagrama siguiente muestra las funciones a las que nos referiremos a través de la guía.

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> Muchas de estas funciones pueden ser internas o externas, según la configuración de cada proyecto.

## Definición de funciones {#roles}

En la siguiente sección se proporciona información general sobre la audiencia de destino:

### Adobe {#adobe-audience}

Adobe incluye recursos de Adobe Managed Services como CSE (ingeniero de éxito del cliente) y Soporte de Adobe.

### Implementadores de AEM {#aem-implementors}

AEM Implementadores son responsables de realizar tareas de desarrollo e integración para desarrollar la experiencia del usuario, las plantillas personalizadas y las integraciones back-end para AEM.

Las funciones personalizadas necesarias para abordar los parámetros de experiencia del usuario (experiencia del usuario) del cliente final también se capturan y se entregan mediante este proceso.

Los implementadores de AEM suelen implementar la funcionalidad personalizada por fases a lo largo del tiempo en las ubicaciones. Por ejemplo, en primer lugar podrían establecer la compatibilidad con la reproducción de vídeo básico en bucle o contenido gráfico estático. La siguiente fase podría incluir permitir la reproducción de contenido localizado mediante plantillas dinámicas y etiquetas de metadatos, con fases adicionales que incorporen compatibilidad con elementos interactivos mediante pantallas táctiles, sensores, déclencheur dinámicos, etc.

### Integradores audiovisuales {#av-integrators}

El integrador A/V es el proveedor/socio de hardware. Esta es la parte que se ocupa del diseño minorista y la preparación del sitio, incluida la adquisición, configuración e implementación de hardware. Normalmente es un tercero contratado que tiene acceso a un Centro de operaciones de red (NOC). En muchos casos, el integrador A/V es el propietario del proyecto debido a su participación continua después del inicio.

Un integrador de AV es responsable de realizar descubrimientos con los clientes finales para definir los requisitos que determinan el alcance del proyecto para diseñar, crear y administrar de forma eficaz las implementaciones en torno al hardware de señalización digital.

#### Consideración del Partner de Hardware {#selecting-hardware-partner}

Es crucial seleccionar el Partner de hardware adecuado. Deben tenerse en cuenta las siguientes cuestiones:

1. ¿Cuáles son los términos del contrato de nivel de servicio?

1. ¿Qué es la cobertura global?

1. ¿Es soporte las 24 horas?

1. ¿Cómo se administrarán los dispositivos?

1. ¿Cuáles son los sistemas activos de vigilancia y alerta?

### Encargados de estrategias comerciales {#business-strategist}

Los estrategas empresariales representan a quienes toman decisiones en la empresa. Esta función está muy involucrada en las etapas de descubrimiento y requerimientos y es el principal motor del proyecto.

Son los que definen los requisitos y configuran las métricas de KPI. La estrategia empresarial podría ser la siguiente:

* Marketing o
* Administrador de ventas Digital Strategy Manager Creativos / Administración de contenido.

El equipo de Creative y Gestión de contenido trabaja en estrecha colaboración con el equipo de Estrategia y convierte los requisitos en experiencias de cliente. Controlan el diseño de experiencia de usuario general y depuran el contenido que complementa la marca.

Los elementos creativos y la administración de contenido podrían ser los siguientes:

* Agencia creativa o
* Brand Manager

### Gestores de proyectos {#project-managers}

Los administradores de proyectos generalmente administran la implementación completa para su implementación de AEM Screens. Un director de proyecto es la persona encargada de toda la ejecución del proyecto designado y desempeña importantes funciones, como establecer plazos, atender las necesidades y comunicaciones de los equipos, hacer frente a los problemas y asegurar que se cumplan los objetivos.

>[!NOTE]
>
>Para obtener información detallada sobre las diferentes funciones y responsabilidades y la audiencia de destino de un proyecto de señalización digital, visite **[Funciones y responsabilidades del proyecto](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-roles-responsibilities.html)**.


## Etapas del proyecto {#project-stages}

Para admitir una implementación correcta de la señalización digital, es habitual segmentar el proyecto en 3 etapas.  Estas etapas suelen denominarse **Días**. No son días literales, sino designaciones para cada etapa principal del proyecto.

1. La primera etapa se denomina *Día cero*. Esta etapa incluye todos los esfuerzos de pre-ventas y descubrimiento necesarios para definir completamente el alcance del proyecto.
1. La segunda etapa, *Día uno*, hace referencia a todas las actividades incluidas en el esfuerzo de implementación.
1. La tercera y última etapa *Día dos* se refiere a todas las operaciones en curso y a los elementos de soporte como parte de la solución total.

>[!NOTE]
>
>Aunque esta guía pone énfasis principalmente en el *Día uno* y el *Día dos*, es necesario prestar atención a las tres etapas para ejecutar un proyecto de publicidad dinámica exitoso.
>
>Siga un vídeo adicional sobre **[Administración e implementación de proyectos](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-management-and-deployment.html)** para obtener más información sobre la preproducción, el inicio del proyecto y el progreso del proyecto.

## Gráfico RACI {#raci-chart}

A continuación se muestra un gráfico RACI de muestra utilizando las definiciones de funciones.

>[!NOTE]
>
>El propósito de este gráfico no es que se siga exactamente, sino que proporcione un ejemplo de tareas comunes y consideraciones en un proyecto de AEM Screens.

### Definiciones de RACI {#raci-definitions}

* **Responsable**: Realiza el trabajo para completar la tarea.

* **Contable**: Los delegados trabajan y es la última parte en revisar la tarea antes de que se complete.

* **Consultado**: Revisa la tarea o la entrega para proporcionar información.

* **Informado**: Se ha mantenido informado del progreso de la tarea, pero no participa en los detalles del envío.

A continuación se muestra un gráfico RACI de muestra que utiliza las definiciones de funciones y proporciona un ejemplo de tareas y consideraciones comunes en un proyecto de AEM Screens.

La siguiente tabla resume el **Día cero: Consideraciones previas a la venta**:

| **Fase** | **Integrador A/V** | **AEM Implementador** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Formación del equipo y selección de proveedores | I | I | RA | RA |
| Acuerdo sobre funciones y responsabilidades | RA | RA | RA | RA |
| Alineación en los objetivos estratégicos | CI | I | RA | RA |
| Necesidades de informes e identificación de ROI | I | C | RA | C |
| Visitas al sitio y requisitos de hardware | RA | I | C | C |
| Definición del proceso de soporte | C | I | RA | I |
| Definir ámbito de trabajo y plan de proyecto | RA | RA | C | C |

La siguiente tabla resume el **Día uno: Implementación del proyecto (diseño de la aplicación)**:

| **Fase** | **Integrador A/V** | **AEM Implementador** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Acuerdo sobre funciones y responsabilidades | RA | RA | RA | RA |
| Alineación en el plan y la programación del proyecto | RA | RA | C | C |
| Evaluar Entornos de Servidor Actuales | I | RA | I | I |
| Requisitos de diseño de experiencia de usuario | I | RA | C | RA |
| Validación de requisitos técnicos | I | RA | RA | C |
| Diseño de arquitectura | I | RA | I | I |
| Validación de la estructura de datos con diseño de interfaz de usuario | I | RA | C | C |
| Desarrollo de aplicaciones | RA | RA | RA | RA |
| Configuración del proyecto de AEM Screens | I | RA | C | I |
| Implementación de Analytics | I | RA | C | - |
| Pruebas e implementación | RA | C | RA | I |
| Configuración del servidor | I | RA | I | I |
| Plan de actualización de contenido | I | RA | C | C |
| Plan de transición de la fase piloto a la producción | RA | RA | I | I |
| Transferencia de conocimientos | RA | RA | I | I |

La siguiente tabla resume el **Día uno: Implementación del proyecto (preparación para minoristas)**:

| **Fase** | **Integrador A/V** | **AEM Implementador** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Ordenación y almacenamiento de hardware | RA | I | I | I |
| Programa de incorporación al comercio minorista | I | I | C | RA |
| Ensayo de la prueba de aceptación del usuario | I | C | RA |  |
| Configuración masiva de hardware | RA | I | C | I |
| Acuerdo sobre la compatibilidad con el lanzamiento posterior | RA | C | RA | C |

La siguiente tabla resume el **Día uno: Día uno: Implementación del proyecto (hardware)**:

| **Fase** | **Integrador A/V** | **AEM Implementador** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Acuerdo sobre funciones y responsabilidades | RA | RA | RA | RA |
| Diseño comercial incluye operaciones de cableado | - | - | - | - |
| Selección de hardware del reproductor | RAC | - | - | - |
| Administración de dispositivos del maestro | RA | I | - | - |
| Ordenación y almacenamiento de dispositivos y configuración | RA | CI | I | - |
| Definición del proceso de soporte | RA | I | RA | C |

>[!NOTE]
>
>Las funciones cambian durante el día dos (compatibilidad con poslanzamiento).

* **Autor**: Gestión de contenido + Estrategia

* **Desarrollador**: Normalmente, es miembro del equipo de implementación de AEM Screens o se entrega al equipo de desarrollo interno

* **Técnico**: Ya sea contratado por el integrador AV o es parte de la misma compañía.

La siguiente tabla resume el **Día dos: Gráfico RACI de compatibilidad con poslanzamiento**:

| **Fase** | **Autor** | **Desarrollador** | **Técnico** |
|---|---|---|---|
| *Día dos: Compatibilidad con poslanzamiento* |
| Acuerdo sobre funciones y responsabilidades | RA | RA | RA |
| Asistencia de nivel 1 | I | I | RA |
| Compatibilidad con el nivel 2 | I | C | RA |
| Asistencia de nivel 3 | I | RA | C |
| Actualización de contenido | RA | I | I |
| Evaluar el éxito de experiencia de usuario e identificar áreas de mejoras | RA | C | I |
