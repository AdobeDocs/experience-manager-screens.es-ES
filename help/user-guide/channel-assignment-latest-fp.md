---
title: Asignación de canales - Último FP
description: Obtenga información acerca de la asignación de canales y la partición por día.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 2%

---

# Asignación de canales {#channel-assignment}

>[!IMPORTANT]
>
>AEM En esta sección se destaca la asignación de canales y la programación de canales para el paquete de funciones de Screens 6.5.5 y versiones posteriores, así como para los canales de.

Cuando haya configurado una pantalla, asigne un canal a una pantalla para ver el contenido.

En esta página se muestra la asignación de un canal a la pantalla, cómo comprender las propiedades del canal y DayParting.

>[!NOTE]
>
>Puede asignar varios canales a una visualización.


## Asignación de un canal {#assign-a-channel-new-release}

Siga las secciones a continuación para crear un proyecto de AEM Screens y asignar un canal a una visualización.

### Creación de un proyecto de AEM Screens y canales {#creating-project}

Siga los pasos a continuación para configurar un proyecto y un canal:

1. Cree un proyecto de AEM Screens titulado **DemoScreens**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Para aprender a crear un proyecto de AEM Screens, vea [Crear y administrar proyectos](creating-a-screens-project.md).

1. Cree un canal de secuencia con el título **Cafetería** en la carpeta **Canales**.

1. Haga clic en el canal y luego en **Editar** en la barra de acciones.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por ejemplo, el canal **Cafetería** ahora muestra las siguientes imágenes:

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Cree una ubicación con el título **SanJose** y una pantalla como **Lobby**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Asignación de canales a una pantalla {#assigning-channel-to-display}

Cuando finalice la configuración del proyecto, asigne el canal a una pantalla para ver el contenido.

1. Vaya a la pantalla que desee, por ejemplo, **DemoScreens** > **Ubicaciones** > **SanJose** > **Vestíbulo**.

1. Haga clic en **Asignar canal** en la barra de acciones.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   O bien,

   Haga clic en **Tablero** de la barra de acciones y, a continuación, haga clic en **+Asignar canal** en el panel **CANALES Y PROGRAMACIONES ASIGNADOS**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Se abre el cuadro de diálogo **Asignación de canal**.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. En la opción **Settings**, puede elegir el canal **por ruta** o **por nombre**, escribir el **Rol del canal**, **Prioridad**, **Eventos compatibles** y **Métodos de interrupción**. Además, se puede activar la información de objeto de atracción desde este cuadro de diálogo.

   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Para obtener más información acerca de las propiedades de asignación de canal, consulte la sección [Propiedades de canal](#channel-properties).

1. En la opción **Programar**, haga clic en **Ventana de activación** y **Programación de periodicidad**.
   ![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Para obtener más información acerca de las propiedades de asignación de canal, consulte la sección [Propiedades de canal](#channel-properties).

1. Haz clic en **Guardar** una vez que hayas configurado tus preferencias.

### Visualización del contenido en el reproductor de Chrome {#viewing-content-output}

Este ejemplo muestra la salida en un reproductor de Chrome. Cuando haya asignado el canal a la pantalla, registre el dispositivo en un reproductor.

Para obtener información sobre cómo registrar un dispositivo en un reproductor de AEM Screens, consulte [Registro de dispositivos](device-registration.md).

Puede ver el siguiente resultado a su elección de reproductor:

![nuevo1](assets/channel-assignment/channel-assign-output.gif)

## Vista Cronología {#timeline-view}

Cuando haya asignado un canal a una pantalla y haya configurado un horario de periodicidad, podrá ver la cronología desde el panel **CANALES Y HORARIOS ASIGNADOS**.

Siga los pasos a continuación para navegar a la vista de cronología:

1. Vaya a la pantalla que desee, por ejemplo, **DemoScreens** > **Ubicaciones** > **SanJose** > **Vestíbulo**.

1. Haga clic en **Asignar canal** en la barra de acciones.

   O bien,

   Haga clic en **Panel** y luego en **Cronología** en el panel **CANALES Y PROGRAMACIONES ASIGNADOS**.

   ![imagen](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Explicación de las propiedades de canal del cuadro de diálogo Asignación de canal {#channel-properties}

Las siguientes propiedades se establecen desde la opción **Configuración** del cuadro de diálogo **Asignación de canal**.

![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleccionar un canal {#select-channel}

La selección de un canal permite proporcionar una referencia al canal deseado, ya sea por nombre de canal o por ruta de canal.

* **Por ruta de acceso**: se proporciona una referencia explícita mediante la ruta de acceso absoluta del canal.
* **Por nombre**: escribe el nombre del canal que se resuelve en un canal real por contexto. Esta función permite crear una versión local de un canal para poder resolver de forma dinámica contenido específico de la ubicación. Por ejemplo, un canal con el nombre *ofertas del día*, donde el contenido real sería diferente en dos ciudades, pero aún tiene el rol de canal simulado en todas las pantallas.

### Función del canal {#role-channel}

La función Canal define el contexto de la visualización. Varias acciones se dirigen a la función. Es independiente del canal real que cumple la función.

### Prioridad {#priority-channel}

La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tiene el valor más alto siempre tiene prioridad sobre los valores más bajos. Por ejemplo, si hay dos canales, A y B. A tiene una prioridad de 1 y B tiene una prioridad de 2. A continuación, se muestra el canal B, ya que tiene una prioridad mayor que A.

>[!NOTE]
>
>La prioridad de un canal se establece como un número (1 como mínimo) en el cuadro de diálogo **Asignación de canal**, como se mencionó anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

### Eventos admitidos {#supported-events-channel}

* **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales con una programación.
* **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales con una programación.
* **Temporizador**: debe establecerse cuando se proporcione una programación.
* **Interacción de usuario**: el reproductor cambia al canal especificado si hay una interacción de usuario en la pantalla (táctil) en un canal inactivo y se carga cuando se toca la pantalla.

### Método de interrupción {#interruption-method-channel}

>[!IMPORTANT]
> AEM Esta opción solo está disponible con <!--AEM 6.4 Feature Pack 8 or-->Paquete de funciones 4 de 6.5 de.

Como autor de contenido, puede especificar cuándo se interrumpe un canal. Al hacerlo, puede optar por cortar el contenido no crítico. Pero también le ofrece la opción de permitir que el contenido importante se reproduzca por completo antes de acortarlo debido a la programación.

Seleccione una de las siguientes opciones disponibles para establecer el método de interrupción en el cuadro de diálogo **Asignación de canal**:

* **Inmediatamente**: cada vez que se active la programación o se reciba una actualización, puede interrumpir la reproducción y actualizar o reproducir inmediatamente el nuevo contenido
* **Fin del elemento actual**: cuando se activa una nueva programación o se recibe una actualización, puede esperar opcionalmente a que el elemento actual de la secuencia termine de reproducirse. A continuación, solo después de eso, puede actualizar o reproducir el nuevo contenido.

  >[!NOTE]
  >Esta opción está seleccionada de forma predeterminada.

* **Al final de la secuencia**: cuando se activa una nueva programación o se recibe una actualización, puede esperar opcionalmente a que toda la secuencia llegue a su final. A continuación, justo antes de la secuencia deseada, puede volver al primer elemento, actualizar o reproducir el nuevo contenido.

  >[!NOTE]
  >El uso de la segunda o tercera opción puede hacer que los tiempos de programación definidos en la asignación se difieran ligeramente. El motivo es que el reproductor espera el final del elemento o la secuencia (después del tiempo especificado) antes de actualizar. El retraso depende de la duración de reproducción del elemento.

Las siguientes propiedades se establecen desde la opción **Programar** del cuadro de diálogo **Asignación de canal**.

![imagen](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Ventana de activación {#activation-window}

La ventana de activación le permite seleccionar una **fecha de inicio** y una **fecha de finalización** para mostrar el contenido.

### Programación de repetición {#recurrence-schedule}

El Horario de periodicidad le permite establecer una programación recurrente para el contenido. Haz clic en **+ Agregar horario** para agregar un horario de periodicidad a tu canal.

>[!NOTE]
>Puede agregar varias programaciones recurrentes al canal.
>Los horarios de periodicidad presentan *DayParting*. Se establece una programación global con varios canales en ejecución a horas específicas del día y se reutiliza esa configuración para todas las pantallas a la vez.

Puede establecer las siguientes opciones:

* **Nombre** - Título de su horario de periodicidad.
* **Repetir** - Elija si la programación se ejecuta **diariamente**, **semanalmente**, **mensualmente** o **anualmente**.
* **Inicio**: la hora de inicio de su programación.
* **Fin**: la hora de finalización de su programación. Puede establecerlo por tiempo o duración.
   * **Hora**: la programación finaliza a una hora especificada.
   * **Duración**: la programación se ejecuta durante un período de tiempo determinado en horas o minutos.

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
>Además, puede definir ***Prioridad*** para cada uno de los canales. Por ejemplo, si se establecen dos canales para el mismo día y hora o para el mismo mes, el canal con mayor prioridad se reproduce primero. El valor mínimo de prioridad puede establecerse como 0.
