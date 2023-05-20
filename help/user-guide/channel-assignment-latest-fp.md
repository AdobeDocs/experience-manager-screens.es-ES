---
title: Asignación de canales - Último FP
seo-title: Channel Assignment - Latest FP
description: Siga esta página para obtener más información sobre la asignación de canales y la partición por día.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1467'
ht-degree: 3%

---

# Asignación de canales {#channel-assignment}

>[!IMPORTANT]
>
>AEM En esta sección se destaca la asignación de canales y la programación de canales para el paquete de funciones de Screens 6.5.5 y versiones posteriores, respectivamente.

Una vez configurada una pantalla, debe asignar un canal a una pantalla para ver el contenido.

En esta página se muestra la asignación de un canal a la pantalla, cómo comprender las propiedades del canal y DayParting.

>[!NOTE]
>
>Puede asignar varios canales a una visualización.


## Asignación de un canal {#assign-a-channel-new-release}

Siga las secciones a continuación para crear un proyecto de AEM Screens y asignar un canal a una visualización.

### Creación de un proyecto de AEM Screens y canales {#creating-project}

Siga los pasos a continuación para configurar un proyecto y un canal:

1. Cree un proyecto de AEM Screens con el título **Demostraciones**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consulte [Creación y administración de proyectos](creating-a-screens-project.md) para aprender a crear un proyecto de AEM Screens.

1. Cree un canal de secuencia titulado como **Cafetería** en el **Canales** carpeta.

1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para añadir contenido al canal.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por ejemplo, la variable **Cafetería** El canal ahora muestra las siguientes imágenes:

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Cree una ubicación con el título **San José** y una pantalla como **Vestíbulo**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Asignación de canales a una pantalla {#assigning-channel-to-display}

Una vez completada la configuración del proyecto, debe asignar el canal a una pantalla para ver el contenido.

1. Navegue hasta la visualización requerida, por ejemplo, **Demostraciones** —> **Ubicaciones** —> **San José** —> **Vestíbulo**.

1. Pulse o haga clic en **Asignar canal** de la barra de acciones.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   O bien,

   Pulse o haga clic en **Tablero** en la barra de acciones y haga clic en **+Asignar canal** desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. El **Asignación de canales** se abre el cuadro de diálogo.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Desde el **Configuración** opción, puede elegir el canal **por ruta** o **por nombre**, introduzca la variable **Función del canal**, **Prioridad**, **Eventos admitidos**, y **Métodos de interrupción**. Además, se puede activar la información de objeto de atracción desde este cuadro de diálogo.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Consulte [Propiedades de canal](#channel-properties) para obtener más información sobre las propiedades de asignación de canal.

1. Desde el **Programación** opción seleccione la **Ventana de activación** y **Horario de periodicidad**.
   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Consulte [Propiedades de canal](#channel-properties) para obtener más información sobre las propiedades de asignación de canal.

1. Clic **Guardar** una vez configuradas las preferencias.

### Visualización del contenido en Chrome Player {#viewing-content-output}

Este ejemplo muestra la salida en un reproductor Chrome. Una vez asignado el canal a la pantalla, debe registrar el dispositivo en un reproductor.

Consulte [Registro de dispositivos](device-registration.md) para aprender a registrar un dispositivo en un reproductor de AEM Screens.

Verá el siguiente resultado a su elección de reproductor:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Vista Cronología {#timeline-view}

Una vez que haya asignado un canal a una pantalla y haya configurado un programa de periodicidad, puede ver la cronología desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel.

Siga los pasos a continuación para navegar a la vista de cronología:

1. Navegue hasta la visualización requerida, por ejemplo, **Demostraciones** —> **Ubicaciones** —> **San José** —> **Vestíbulo**.

1. Pulse o haga clic en **Asignar canal** de la barra de acciones.

   O bien,

   Pulse o haga clic en **Tablero** y haga clic en **Cronología** desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel.

   ![imagen](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Explicación de las propiedades de canal del cuadro de diálogo Asignación de canal {#channel-properties}

Las siguientes propiedades se establecen desde la variable **Configuración** en la opción **Asignación de canales** Cuadro de diálogo.

![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleccionar un canal {#select-channel}

La selección de un canal permite proporcionar una referencia al canal deseado, ya sea por nombre de canal o por ruta de canal.

* **por ruta**: proporciona una referencia explícita utilizando la ruta absoluta del canal.

* **por nombre**: Introduzca el nombre del canal que se resolverá en un canal real por contexto. Esta función le permite crear la versión local de un canal para resolver de forma dinámica contenido específico de la ubicación. Por ejemplo, un canal con el nombre *ofertas del día*, donde el contenido real sería diferente en dos ciudades, pero el canal sigue teniendo una función sensata en todas las pantallas.

### Función del canal {#role-channel}

La función Canal define el contexto de la visualización. La función está dirigida por varias acciones y es independiente del canal real que cumple la función.

### Prioridad {#priority-channel}

La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tenga el valor más alto siempre tendrá prioridad sobre los valores más bajos. Por ejemplo, si hay dos canales, A y B. A tiene una prioridad de 1 y B tiene una prioridad de 2. A continuación, se muestra el canal B, ya que tiene una prioridad mayor que A.

>[!NOTE]
>
>La prioridad de un canal se establece como un número (1 como mínimo) en la variable **Asignación de canales** , como se ha mencionado anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

### Eventos admitidos {#supported-events-channel}

* **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales en combinación con la programación
* **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales en combinación con la programación
* **Temporizador**: debe configurarse cuando se proporciona una programación
* **Interacción del usuario**: el reproductor cambiará al canal especificado si hay una interacción del usuario en la pantalla (táctil) en un canal inactivo y se cargará cuando se toque la pantalla

### Método de interrupción {#interruption-method-channel}

>[!IMPORTANT]
> AEM AEM Esta opción solo está disponible con el paquete de funciones 8 o 4 del paquete de funciones 4 de la versión 6.4 de la o con el paquete de funciones 4 de la versión 6.5.

Como autor de contenido, debe poder especificar cuándo se interrumpe un canal para que pueda optar por cortar contenido no crítico, pero tiene la opción de permitir que el contenido importante se reproduzca por completo antes de cortar la reproducción debido a la programación.

Seleccione una de las siguientes opciones disponibles para establecer el método de interrupción desde el **Asignación de canales** Cuadro de diálogo:

* **Inmediata**: cada vez que se activa la programación o se recibe una actualización, puede interrumpir la reproducción y actualizar o reproducir inmediatamente el nuevo contenido
* **Al final del elemento actual**: cuando se activa una nueva programación o se recibe una actualización, tiene la opción de esperar a que el elemento actual de la secuencia termine de reproducirse y solo después de ello actualice o reproduzca el nuevo contenido

   >[!NOTE]
   >Esta opción está seleccionada de forma predeterminada.

* **Al final de la secuencia**: cuando se activa una nueva programación o se recibe una actualización, tiene la opción de esperar a que toda la secuencia llegue a su final y, justo antes de la secuencia deseada, vuelve al primer elemento, actualiza o reproduce el nuevo contenido

   >[!NOTE]
   >El uso de la segunda o tercera opción puede provocar que los tiempos de programación definidos en la asignación se aplazen ligeramente, ya que el reproductor esperará al final del elemento o la secuencia (después del tiempo especificado) antes de actualizar. El retraso dependerá de la duración de reproducción del elemento.

Las siguientes propiedades se establecen desde la variable **Programación** en la opción **Asignación de canales** Cuadro de diálogo.

![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Ventana de activación {#activation-window}

La ventana de activación le permite seleccionar una **Fecha de inicio** y un **Fecha de finalización** para mostrar el contenido.

### Programación de repetición {#recurrence-schedule}

El Horario de periodicidad le permite establecer una programación recurrente para el contenido. Haga clic en **+ Agregar programación** para añadir una programación de periodicidad al canal.

>[!NOTE]
>Puede agregar varias programaciones recurrentes al canal.
>Los horarios de periodicidad presentan *DayParting*, que le permite establecer una programación global con varios canales en ejecución a horas específicas del día y reutilizar esa configuración para todas las pantallas a la vez.

Puede establecer las siguientes opciones:

* **Nombre**: Título de la programación de periodicidad.
* **Repetir**: elija si la programación se ejecuta **Diario**, **Semanalmente**, **Mensual**, o **Anual**.
* **Inicio**: la hora de inicio de la programación.
* **Fin**: la hora de finalización de la programación. Puede configurarlo por tiempo o duración.
   * **Hora**: la programación finalizará a una hora especificada.
   * **Duración**: la programación se ejecuta durante un período de tiempo determinado en horas o minutos.

### DayParting {#dayparting}

DayParting hace referencia a la división de un día en espacios de tiempo y a la especificación de qué contenido se reproduce a la hora deseada. AEM Screens le permite programar canales en términos de Partición del día en un día, una semana o un mes según sea necesario.

Los siguientes ejemplos explican DayParting en los canales en tres escenarios diferentes:

#### Reproducción de contenido en un solo día dividido en varias franjas horarias {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este ejemplo muestra cómo un restaurante utiliza DayParting para mostrar su menú de desayuno, almuerzo y cena todos los días.

Aquí, dividiremos cada día en diferentes franjas horarias, de modo que el contenido del canal se reproduzca a la hora especificada del día. Establezca las siguientes propiedades del Horario de periodicidad para que su canal reproduzca el contenido según este caso de uso.

| **Nombre** | **Repeticiones** | **Inicial** | **Finalizar** |
|---|---|---|---|
| Desayuno | Cada día | 6:00 | 11:00 |
| Almuerzo | Cada día | 11:00 | 15:00 |
| Cena | Cada día | 15:00 | 20:00 |

#### Reproducción de contenido en un día de la semana concreto {#playing-content-on-a-particular-day-of-the-week}

En este ejemplo se muestra la implementación de DayParting en un casino en el que los eventos en directo tienen lugar todos los fines de semana de 20:00 a 22:00 y los especiales están disponibles para el menú de cena después de las 22:00 y hasta la 01:00.

| **Nombre** | **Repeticiones** | **Inicial** | **Finalizar** |
|---|---|---|---|
| Weekend | Semanal: sábado, domingo | 20:00 | 22:00 |
| Especiales | Diario: lunes a viernes | 22:00 | 1:00 |

>[!NOTE]
>
>Además, puede definir lo siguiente ***Prioridad*** para cada uno de los canales. Por ejemplo, si se establecen dos canales para el mismo día y hora o para el mismo mes, el canal con mayor prioridad se reproduce primero. El valor mínimo de prioridad puede establecerse como 0.
