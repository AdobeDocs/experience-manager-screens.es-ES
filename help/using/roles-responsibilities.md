---
title: Funciones y responsabilidades del proyecto AEM Screens
description: Obtenga información acerca de las funciones y responsabilidades del proyecto AEM Screens.
exl-id: 9377625b-529a-4b46-89d9-f526de398639
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Funciones y responsabilidades del proyecto {#roles-responsibilities}

Como implementador experimentado de AEM, es probable que haya visto que las funciones se denominan *Autores*, *Desarrolladores* y *Técnicos de TI*.

En un proyecto típico de AEM Screens, las funciones se refinan aún más, ya que cada una cumple un propósito importante en el proyecto.

En el diagrama siguiente se muestran las funciones que debería ver en toda la guía.

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> Muchas de estas funciones pueden ser internas o externas, según la configuración de cada proyecto.

## Definición de funciones {#roles}

La siguiente sección ofrece información general sobre la audiencia de destino:

### Adobe {#adobe-audience}

Adobe incluye recursos de Adobe Managed Services como el CSE (ingeniero de éxito del cliente) y la asistencia de Adobe.

### Implementadores de AEM {#aem-implementors}

Los implementadores de AEM son responsables de realizar tareas de desarrollo e integración para desarrollar la experiencia del usuario, las plantillas personalizadas y las integraciones back-end para AEM.

Las funciones personalizadas necesarias para abordar los parámetros de experiencia de usuario (UX) del cliente final también se capturan y entregan a través de este proceso.

Los implementadores de AEM generalmente implementan la funcionalidad personalizada por fases a lo largo del tiempo en las ubicaciones. Por ejemplo, pueden establecer primero una compatibilidad con la reproducción de vídeo en bucle básico o contenido gráfico estático. La siguiente fase incluye la posibilidad de admitir la reproducción de contenido localizado mediante plantillas dinámicas y etiquetas de metadatos. Otras fases incorporan la compatibilidad con elementos interactivos mediante pantallas táctiles, sensores, déclencheur dinámicos, etc.

### Integradores de audio y vídeo {#av-integrators}

El integrador de audio y vídeo es el proveedor-socio de hardware. Son la parte que se ocupa del diseño comercial y la preparación del sitio, incluida la adquisición, configuración e implementación de hardware. Suele ser un tercero contratado que tiene acceso a un centro de operaciones de red (NOC). A menudo, el integrador de audio y vídeo es el propietario del proyecto debido a su implicación continua después del lanzamiento.

Un integrador de audio y vídeo es responsable de llevar a cabo la detección con los clientes finales para definir los requisitos y determinar el ámbito del proyecto para diseñar, crear y administrar de forma eficaz las implementaciones en torno al hardware de señalización digital.

>[!NOTE]
>
> Debe tener un integrador de audio y vídeo como parte de la implementación de AEM Screens.

#### Considerar partner de hardware {#selecting-hardware-partner}

Es crucial hacer clic en el socio de hardware adecuado. Deben tenerse en cuenta las siguientes cuestiones:

1. ¿Cuáles son los términos de Service level agreement?

1. ¿Qué es la cobertura global?

1. ¿Es asistencia las 24 horas?

1. ¿Cómo se administran los dispositivos?

1. ¿Cuáles son los sistemas activos de monitoreo y advertencia?

### Estrategas empresariales {#business-strategist}

Los estrategas empresariales representan a los responsables de la toma de decisiones en la empresa. Esta función participa activamente en las fases de descubrimiento y requisitos, y es el principal motor del proyecto.

Son los que definen los requisitos y configuran las métricas de KPI. La estrategia empresarial podría ser la siguiente:

* Marketing o,
* Director de ventas Digital Strategy Manager Creativos / Gestión de contenido.

El equipo de creativos y gestión de contenido trabaja estrechamente con el equipo de estrategia y convierte los requisitos en experiencias del cliente. Impulsan el diseño general de la experiencia de usuario y depuran el contenido que complementa la marca.

La administración de contenido y creativos puede ser la siguiente:

* Agencia Creative o,
* Administrador de marca

### Gestores de proyecto {#project-managers}

Los jefes de proyecto suelen administrar toda la implementación para la implementación de AEM Screens. Un administrador de proyectos es la persona clave para toda la implementación del proyecto designado. Desempeñan importantes responsabilidades, como la fijación de plazos y la gestión de las necesidades del equipo. También afectan a las comunicaciones, abordan los desafíos y garantizan el cumplimiento de los objetivos.

>[!NOTE]
>
>Para obtener información detallada sobre las diferentes funciones y responsabilidades y la audiencia de destino de un proyecto de señalización digital, visite **[Funciones y responsabilidades del proyecto](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-roles-responsibilities)**.


## Fases del proyecto {#project-stages}

Para permitir una implementación correcta de la publicidad dinámica, es habitual segmentar el proyecto en tres fases. Estas etapas se denominan comúnmente **Días**. No son días literales, sino designaciones para cada etapa principal del proyecto.

1. La primera etapa se conoce como *Día cero*. Esta fase incluye todas las tareas de preventa y descubrimiento necesarias para definir el ámbito del proyecto.
1. La segunda fase, *Día uno*, se refiere a todas las actividades incluidas en el esfuerzo de implementación.
1. La tercera y última etapa es el *Día dos*. Hace referencia a todas las operaciones en curso y a los elementos de soporte como parte de la solución total.

>[!NOTE]
>
>Aunque esta guía pone énfasis principalmente en *Día uno* y *Día dos*, es necesario prestar atención a las tres etapas para ejecutar un proyecto de señalización digital exitoso.
>
>Para obtener información sobre la preproducción, el inicio y la progresión del proyecto, vea un vídeo sobre **[Administración e implementación del proyecto](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-management-and-deployment)**.

## Gráfico RACI {#raci-chart}

A continuación se muestra un ejemplo de gráfico RACI utilizando las definiciones de funciones.

>[!NOTE]
>
>No es necesario que siga el gráfico exactamente. En su lugar, se pretende proporcionar un ejemplo de las tareas y consideraciones comunes de un proyecto de AEM Screens.

### Definiciones de RACI {#raci-definitions}

* **Responsable**: realiza el trabajo para completar la tarea.

* **Responsable**: Los delegados trabajan y son la última parte en revisar la tarea antes de que se complete.

* **Consultado**: revisa la tarea o el envío para proporcionar datos.

* **Informado**: se mantiene informado del progreso de la tarea, pero no participa en los detalles de la entrega.

A continuación se muestra un ejemplo de gráfico RACI que utiliza las definiciones de funciones y proporciona un ejemplo de tareas y consideraciones comunes en un proyecto de AEM Screens.

La siguiente tabla resume el **día cero: consideraciones previas a la venta**:

| **Fase** | **Integrador de audio y vídeo** | **Implementador de AEM** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Formación del equipo y selección de proveedores | I | I | RA | RA |
| Acuerdo sobre Funciones y Responsabilidades | RA | RA | RA | RA |
| Alineación con los objetivos estratégicos | CI | I | RA | RA |
| Necesidades de informes e identificación de ROI | I | C | RA | C |
| Visitas al sitio y requisitos de hardware | RA | I | C | C |
| Definición del proceso de soporte | C | I | RA | I |
| Definir ámbito de trabajo y plan de proyecto | RA | RA | C | C |

La siguiente tabla resume el **Día uno: Implementación del proyecto (diseño de aplicación)**:

| **Fase** | **Integrador de audio y vídeo** | **Implementador de AEM** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Acuerdo sobre Funciones y Responsabilidades | RA | RA | RA | RA |
| Alineación en el plan y el horario del proyecto | RA | RA | C | C |
| Evaluar entornos de servidor actuales | I | RA | I | I |
| Requisitos de diseño de UX | I | RA | C | RA |
| Validación de requisitos técnicos | I | RA | RA | C |
| Diseño de arquitectura | I | RA | I | I |
| Validar la estructura de datos con el diseño de IU | I | RA | C | C |
| Desarrollo de aplicaciones | RA | RA | RA | RA |
| Configuración del proyecto de AEM Screens | I | RA | C | I |
| Implementación de Analytics | I | RA | C | - |
| Pruebas e implementación | RA | C | RA | I |
| Configuración del servidor | I | RA | I | I |
| Plan de actualización de contenido | I | RA | C | C |
| Plan para la transición de la fase piloto a la producción | RA | RA | I | I |
| Transferencia de conocimientos | RA | RA | I | I |

La siguiente tabla resume el **Día uno: Implementación del proyecto (preparación para la venta minorista)**:

| **Fase** | **Integrador de audio y vídeo** | **Implementador de AEM** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Pedidos y almacenamiento de hardware | RA | I | I | I |
| Horario de incorporación comercial | I | I | C | RA |
| Pruebas de aceptación de usuarios de ensayo | I | C | RA |   |
| Configuración masiva de hardware | RA | I | C | I |
| Acuerdo de asistencia posterior al lanzamiento | RA | C | RA | C |

La siguiente tabla resume el **Día uno: Día uno: Implementación del proyecto (hardware)**:

| **Fase** | **Integrador de audio y vídeo** | **Implementador de AEM** | **Estrategia empresarial** | **Administración de contenido** |
|---|---|---|---|---|
| Acuerdo sobre Funciones y Responsabilidades | RA | RA | RA | RA |
| El diseño comercial incluye operaciones de cableado | - | - | - | - |
| Selección de hardware del reproductor | RAC | - | - | - |
| Administración de dispositivos del principal | RA | I | - | - |
| Ordenación, almacenamiento y configuración de dispositivos | RA | CI | I | - |
| Definición del proceso de soporte | RA | I | RA | C |

>[!NOTE]
>
>Las funciones cambian durante el segundo día (compatibilidad posterior al inicio).

* **Autor**: Administración de contenido + Estrategia

* **Desarrollador**: Normalmente, es miembro del equipo de implementación de AEM Screens o se transfiere a un equipo de desarrollo interno

* **Técnico**: Es contratado por el Integrador de audio-vídeo o forma parte de la misma empresa.

La siguiente tabla resume el **Día dos: después del inicio admite el gráfico RACI**:

| **Fase** | **Autor** | **Desarrollador** | **Técnico** |
|---|---|---|---|
| *Día dos: soporte posterior al inicio* |
| Acuerdo sobre Funciones y Responsabilidades | RA | RA | RA |
| Compatibilidad de nivel 1 | I | I | RA |
| Compatibilidad de nivel 2 | I | C | RA |
| Compatibilidad de nivel 3 | I | RA | C |
| Actualización de contenido | RA | I | I |
| Evaluar el éxito de la experiencia de usuario e identificar áreas de mejora | RA | C | I |
