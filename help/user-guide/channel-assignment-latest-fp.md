---
title: Asignación de canales - Último FP
description: Obtenga información acerca de la asignación de canales y la partición por día.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '1454'
ht-degree: 2%

---

# Asignación de canales {#channel-assignment}

>[!IMPORTANT]
>
>AEM En esta sección se destaca la asignación de canales y la programación de canales para el paquete de funciones de Screens 6.5.5 y versiones posteriores, respectivamente.

Cuando haya configurado una pantalla, asigne un canal a una pantalla para ver el contenido.

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
   >Para obtener información sobre cómo crear un proyecto de AEM Screens, consulte [Creación y administración de proyectos](creating-a-screens-project.md).

1. Cree un canal de secuencia titulado como **Cafetería** en el **Canales** carpeta.

1. Seleccione el canal y luego seleccione **Editar** de la barra de acciones.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por ejemplo, la variable **Cafetería** El canal ahora muestra las siguientes imágenes:

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Cree una ubicación con el título **San José** y una pantalla como **Vestíbulo**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Asignación de canales a una pantalla {#assigning-channel-to-display}

Cuando se complete la configuración del proyecto, debe asignar el canal a una pantalla para ver el contenido.

1. Navegue hasta la visualización requerida, por ejemplo, **Demostraciones** > **Ubicaciones** > **San José** > **Vestíbulo**.

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
   >Para obtener más información sobre las propiedades de asignación de canales, consulte [Propiedades de canal](#channel-properties) sección.

1. Desde el **Programación** , seleccione la opción **Ventana de activación** y **Horario de periodicidad**.
   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Para obtener más información sobre las propiedades de asignación de canales, consulte [Propiedades de canal](#channel-properties) sección.

1. Clic **Guardar** una vez configuradas las preferencias.

### Visualización del contenido en Chrome Player {#viewing-content-output}

Este ejemplo muestra la salida en un reproductor Chrome. Cuando haya asignado el canal a la pantalla, registre el dispositivo en un reproductor.

Para obtener información sobre cómo registrar un dispositivo en un reproductor AEM Screens, consulte [Registro de dispositivos](device-registration.md).

Puede ver el siguiente resultado a su elección de reproductor:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Vista Cronología {#timeline-view}

Una vez que haya asignado un canal a una pantalla y haya configurado un programa de periodicidad, puede ver la cronología desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel.

Siga los pasos a continuación para navegar a la vista de cronología:

1. Navegue hasta la visualización requerida, por ejemplo, **Demostraciones** > **Ubicaciones** > **San José** > **Vestíbulo**.

1. Pulse o haga clic en **Asignar canal** de la barra de acciones.

   O bien,

   Pulse o haga clic en **Tablero** y haga clic en **Cronología** desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel.

   ![imagen](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Explicación de las propiedades de canal del cuadro de diálogo Asignación de canal {#channel-properties}

Las siguientes propiedades se establecen desde la variable **Configuración** en la opción **Asignación de canales** Cuadro de diálogo.

![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleccionar un canal {#select-channel}

La selección de un canal permite proporcionar una referencia al canal deseado, ya sea por nombre de canal o por ruta de canal.

* **Por ruta** : Se proporciona una referencia explícita utilizando la ruta absoluta del canal.
* **Por nombre** : Introduzca el nombre del canal que se resuelve en un canal real por contexto. Esta función permite crear una versión local de un canal para poder resolver de forma dinámica contenido específico de la ubicación. Por ejemplo, un canal con el nombre *ofertas del día*, donde el contenido real sería diferente en dos ciudades, pero el canal sigue teniendo una función sensata en todas las pantallas.

### Función del canal {#role-channel}

La función Canal define el contexto de la visualización. La función está dirigida por varias acciones y es independiente del canal real que cumple la función.

### Prioridad {#priority-channel}

La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tiene el valor más alto siempre tiene prioridad sobre los valores más bajos. Por ejemplo, si hay dos canales, A y B. A tiene una prioridad de 1 y B tiene una prioridad de 2. A continuación, se muestra el canal B, ya que tiene una prioridad mayor que A.

>[!NOTE]
>
>La prioridad de un canal se establece como un número (1 como mínimo) en la variable **Asignación de canales** , como se ha mencionado anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

### Eventos admitidos {#supported-events-channel}

* **Carga inicial** - Carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales con una programación.
* **Pantalla inactiva** - Se carga cuando la pantalla está inactiva. Se puede asignar a varios canales con una programación.
* **Temporizador** - Debe configurarse cuando se proporciona una programación.
* **Interacción del usuario** - El reproductor cambia al canal especificado si hay una interacción del usuario en la pantalla (táctil) en un canal inactivo y se carga cuando se toca la pantalla.

### Método de interrupción {#interruption-method-channel}

>[!IMPORTANT]
> Esta opción solo está disponible con <!--AEM 6.4 Feature Pack 8 or-->AEM Paquete de funciones 4 para.5.

Como autor de contenido, puede especificar cuándo se interrumpe un canal. Al hacerlo, puede optar por cortar el contenido no crítico. Pero también le ofrece la opción de permitir que el contenido importante se reproduzca por completo antes de acortarlo debido a la programación.

Seleccione una de las siguientes opciones disponibles para establecer el método de interrupción desde el **Asignación de canales** Cuadro de diálogo:

* **Inmediata** : Siempre que se active la programación o se reciba una actualización, puede interrumpir la reproducción y actualizar o reproducir inmediatamente el nuevo contenido
* **Fin del elemento actual** : Cuando se activa una nueva programación o se recibe una actualización, puede esperar opcionalmente a que el elemento actual de la secuencia termine de reproducirse. A continuación, solo después de eso, puede actualizar o reproducir el nuevo contenido.

  >[!NOTE]
  >Esta opción está seleccionada de forma predeterminada.

* **Al final de la secuencia** : Cuando se activa una nueva programación o se recibe una actualización, puede esperar opcionalmente a que toda la secuencia llegue a su final. A continuación, justo antes de la secuencia deseada, puede volver al primer elemento, actualizar o reproducir el nuevo contenido.

  >[!NOTE]
  >El uso de la segunda o tercera opción puede hacer que los tiempos de programación definidos en la asignación se difieran ligeramente. El motivo es que el reproductor espera el final del elemento o la secuencia (después del tiempo especificado) antes de actualizar. El retraso depende de la duración de reproducción del elemento.

Las siguientes propiedades se establecen desde la variable **Programación** en la opción **Asignación de canales** Cuadro de diálogo.

![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Ventana de activación {#activation-window}

La ventana de activación permite seleccionar una **Fecha de inicio** y un **Fecha de finalización** para mostrar el contenido.

### Programación de repetición {#recurrence-schedule}

El Horario de periodicidad le permite establecer una programación recurrente para el contenido. Seleccionar **+ Agregar programación** para añadir una programación de periodicidad al canal.

>[!NOTE]
>Puede agregar varias programaciones recurrentes al canal.
>Los horarios de periodicidad presentan *DayParting* esto le permite establecer una programación global con varios canales en ejecución a horas específicas del día y reutilizar esa configuración para todas las pantallas a la vez.

Puede establecer las siguientes opciones:

* **Nombre** - Título de su horario de periodicidad.
* **Repetir** - Elija si la programación se ejecuta **Diario**, **Semanalmente**, **Mensual**, o **Anual**.
* **Inicio** - La hora de inicio de su programación.
* **Fin** - La hora de finalización de la programación. Puede establecerlo por tiempo o duración.
   * **Hora** - La programación finaliza a una hora especificada.
   * **Duración** : La programación se ejecuta durante un período de tiempo determinado en horas o minutos.

### DayParting {#dayparting}

La partición por día hace referencia a la división de un día en espacios de tiempo y a la especificación de qué contenido se reproduce a la hora deseada. AEM Screens permite programar canales según DayParting en un día, una semana o un mes, según sea necesario.

Los siguientes ejemplos explican DayParting en los canales en tres escenarios diferentes:

#### Reproducción de contenido en un solo día dividido en varias franjas horarias {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este ejemplo muestra cómo un restaurante utiliza DayParting para mostrar su menú de desayuno, almuerzo y cena todos los días.

En este caso, cada día se divide en diferentes franjas horarias, de modo que el contenido del canal se reproduce a la hora especificada del día. Establezca las siguientes propiedades del Horario de periodicidad para que su canal reproduzca el contenido según este caso de uso.

| **Nombre** | **Repeticiones** | **Inicial** | **Fin** |
|---|---|---|---|
| Desayuno | Cada día | 06:00 | 11:00 |
| Almuerzo | Cada día | 11:00 | 15:00 |
| Cena | Cada día | 15:00 | 20:00 |

#### Reproducción de contenido en un día de la semana concreto {#playing-content-on-a-particular-day-of-the-week}

En este ejemplo se muestra el DayParting implementado en un casino en el que los eventos en directo tienen lugar todos los fines de semana de 20:00 a 22:00 y los especiales están disponibles para el menú de la cena después de las 22:00 y hasta la 01:00.

| **Nombre** | **Repeticiones** | **Inicial** | **Fin** |
|---|---|---|---|
| Weekend | Semanal: sábado y domingo | 20:00 | 22:00 |
| Especiales | Diario: de lunes a viernes | 22:00 | 01:00 |

>[!NOTE]
>
>Además, puede definir lo siguiente ***Prioridad*** para cada uno de los canales. Por ejemplo, si se establecen dos canales para el mismo día y hora o para el mismo mes, el canal con mayor prioridad se reproduce primero. El valor mínimo de prioridad puede establecerse como 0.
