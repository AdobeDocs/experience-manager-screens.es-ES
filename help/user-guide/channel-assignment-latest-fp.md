---
title: 'Asignación de canales: última versión de FP'
seo-title: 'Asignación de canales: última versión de FP'
description: Siga esta página para obtener más información sobre Asignación de canales y Partición de días.
feature: Creación en Screens, asignación de canales
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 23%

---

# Asignación de canales {#channel-assignment}

>[!IMPORTANT]
>
>Esta sección resalta la asignación de canales y la programación de canales para AEM 6.5.5 Screens Feature Pack y posteriores.

Una vez configurada la visualización, debe asignar un canal a una pantalla para ver el contenido.

Esta página muestra la asignación de un canal a la visualización, la comprensión de las propiedades del canal y la partición de día.

>[!NOTE]
>
>Puede asignar varios canales a una pantalla.


## Asignación de un canal {#assign-a-channel-new-release}

Siga las secciones a continuación para crear un proyecto de AEM Screens y asignar un canal a una pantalla.

### Creación de un proyecto y canales de AEM Screens {#creating-project}

Siga los pasos a continuación para configurar un proyecto y un canal:

1. Cree un proyecto de AEM Screens con el título **DemoScreens**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consulte [Creación y administración de proyectos](creating-a-screens-project.md) para obtener información sobre cómo crear un proyecto de AEM Screens.

1. Cree un canal de secuencia denominado como **Cafeteria** en la carpeta **Channels**.

1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para agregar contenido al canal.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por ejemplo, el canal **Cafeteria** ahora muestra las siguientes imágenes:

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Cree una ubicación titulada como **SanJosé** y una visualización como **Lobby**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Asignación de canales a una pantalla {#assigning-channel-to-display}

Una vez completada la configuración del proyecto, debe asignar el canal a una pantalla para ver el contenido.

1. Vaya a la visualización requerida, por ejemplo, **DemoScreens** —> **Ubicaciones** —> **SanJosé** —> **Vestíbulo**.

1. Toque o haga clic **Asignar canal** en la barra de acciones.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   O bien,

   Pulse o haga clic en **Panel** en la barra de acciones y haga clic en **+Asignar canal** en el panel **CANALES Y PROGRAMAS ASIGNADOS**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Se abre el cuadro de diálogo **Asignación de canales**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Desde la opción **Settings**, puede elegir el canal **por ruta** o **por nombre**, introducir el **Rol del canal**, **Prioridad**, **Eventos admitidos** y **>Métodos de interrupción**. Además, puede activar la información de objeto de atracción desde este cuadro de diálogo.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Consulte la sección [Propiedades del canal](#channel-properties) para obtener más información sobre las propiedades de asignación de canales.

1. En la opción **Schedule**, seleccione **Activation Window** y **Recurrence Schedule**.
   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Consulte la sección [Propiedades del canal](#channel-properties) para obtener más información sobre las propiedades de asignación de canales.

1. Haga clic en **Guardar** una vez que haya configurado las preferencias.

### Visualización del contenido en el reproductor Chrome {#viewing-content-output}

Este ejemplo muestra la salida en un reproductor Chrome. Una vez asignado el canal a la pantalla, debe registrar el dispositivo en un reproductor.

Consulte [Device Registration](device-registration.md) para obtener información sobre cómo registrar un dispositivo en un reproductor de AEM Screens.

Verá el siguiente resultado en su elección del reproductor:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Vista Cronología {#timeline-view}

Una vez asignado un canal a una pantalla y configurado un programa de periodicidad, puede ver la cronología desde el panel **CANALES ASIGNADOS y PROGRAMAS**.

Siga los pasos a continuación para navegar a la vista de línea de tiempo:

1. Vaya a la visualización requerida, por ejemplo, **DemoScreens** —> **Ubicaciones** —> **SanJosé** —> **Vestíbulo**.

1. Toque o haga clic **Asignar canal** en la barra de acciones.

   O bien,

   Pulse o haga clic en **Panel** y haga clic en **Línea de tiempo** en el panel **CANALES Y PROGRAMAS ASIGNADOS**.

   ![image](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Explicación de las propiedades de canal del cuadro de diálogo Asignación de canales {#channel-properties}

Las siguientes propiedades se establecen desde la opción **Settings** del cuadro de diálogo **Channel Assignment**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleccionar un canal {#select-channel}

La selección de un canal permite proporcionar una referencia al canal deseado, ya sea por nombre de canal o por ruta de acceso al canal.

* **por ruta de acceso**: proporcione una referencia explícita mediante la ruta de acceso absoluta del canal.

* **por nombre**: Introduzca el nombre del canal que se convertirá en un canal real por contexto. Esta característica le permite crear la versión local de un canal, para así resolver de forma dinámica el contenido de una ubicación específica. Por ejemplo, un canal con el nombre *ofertas del día*, donde el contenido real sería diferente en dos ciudades, pero aún así tendrá la función de canal en todas las pantallas.

### Rol del canal {#role-channel}

El rol de canal define el contexto de la visualización. Varias acciones dirigen la función y es independiente del canal que cumple esa función.

### Prioridad {#priority-channel}

La prioridad se utiliza para solicitar las asignaciones en caso de que varias de ellas coincidan con los criterios de reproducción. Aquel elemento que tenga el valor más alto siempre tendrá prioridad sobre otros valores más bajos. Por ejemplo, si hay dos canales A y B, y A tiene una prioridad de 1 y B tiene una prioridad de 2, se muestra el canal B ya que tiene mayor prioridad que A.

>[!NOTE]
>
>La prioridad de un canal se establece como un número (1 para indicar el mínimo) en el cuadro de diálogo **Asignación de canales**, tal como se mencionó anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

### Eventos admitidos {#supported-events-channel}

* **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales junto con la programación
* **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales junto con la programación
* **Temporizador:** se debe establecer al proporcionar una programación
* **Interacción del usuario**: el reproductor cambiará al canal determinado si el usuario toca la pantalla que está visualizando un canal inactivo, y se cargará al tocar la pantalla

### Método de interrupción {#interruption-method-channel}

>[!IMPORTANT]
> Esta opción solo está disponible con AEM 6.4 Feature Pack 8 o AEM 6.5 Feature Pack 4.

Como autor de contenido, debería poder especificar cuándo se interrumpe un canal para que pueda optar por cortar contenido no crítico, pero tenga la opción de permitir que el contenido importante se reproduzca completamente antes de interrumpir la reproducción debido a la programación.

Seleccione una de las siguientes opciones disponibles para configurar el método de interrupción en el cuadro de diálogo **Asignación de canales**:

* **Inmediatamente**: cuando la programación se activa o se recibe una actualización, puede cortar la reproducción y actualizar o reproducir inmediatamente el nuevo contenido
* **Al final del elemento** actual: cuando se activa una nueva programación o se recibe una actualización, tiene la opción de esperar a que el elemento actual de la secuencia termine de reproducirse y solo después de que actualice o reproduzca el nuevo contenido

   >[!NOTE]
   >Esta opción está seleccionada de forma predeterminada.

* **Al final de la secuencia**: cuando se activa una nueva programación o se recibe una actualización, tiene la opción de esperar a que toda la secuencia llegue a su final y justo antes de la secuencia deseada, vuelve al primer elemento para actualizar o reproducir el nuevo contenido

   >[!NOTE]
   >El uso de la segunda o tercera opción puede hacer que los tiempos de programación definidos en la asignación se posterguen ligeramente, ya que el reproductor esperará el final del elemento o secuencia (después del tiempo especificado) antes de la actualización. El retraso dependerá de la duración de reproducción del elemento.

Las siguientes propiedades se establecen desde la opción **Schedule** del cuadro de diálogo **Channel Assignment**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Ventana de activación {#activation-window}

La ventana de activación permite seleccionar una **Fecha de inicio** y una **Fecha de finalización** para mostrar el contenido.

### Programación de repetición {#recurrence-schedule}

La programación de periodicidad le permite establecer una programación recurrente para el contenido. Haga clic en **+ Agregar programación** para agregar una programación de periodicidad al canal.

>[!NOTE]
>Puede agregar varias programaciones recurrentes al canal.
>Las programaciones de periodicidad introducen *DayParting*, que le permite establecer una programación global con varios canales que se ejecutan en momentos específicos del día y reutilizar esa configuración para todas las visualizaciones a la vez.

Puede establecer las siguientes opciones:

* **Nombre**: Título de la programación de periodicidad.
* **Repetir**: Elija si la programación se ejecuta  **Diariamente**,  **Semanal**,  **Mensual** o  **Anualmente**.
* **Inicio**: La hora de inicio de la programación.
* **Fin**: La hora de finalización de la programación. Puede configurarlo por tiempo o duración.
   * **Tiempo**: La programación finalizará a una hora especificada.
   * **Duración**: La programación se ejecuta durante un tiempo determinado en horas o minutos.

### Partición de día {#dayparting}

DayParting hace referencia a dividir un día en franjas horarias y a especificar qué contenido se reproduce a la hora deseada. AEM Screens le permite programar canales en términos de partición de día dentro de un día, una semana o un mes según sea necesario.

En los siguientes ejemplos se explica DayParting en los canales en tres escenarios diferentes:

#### Reproducir contenido en un único día que esté dividido en varias franjas horarias {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este ejemplo muestra cómo un restaurante utiliza DayParting para mostrar su menú de desayuno, almuerzo y cena todos los días.

Aquí, dividiremos cada día en diferentes franjas horarias, de modo que el contenido del canal se reproduzca según la hora especificada del día. Establezca las siguientes propiedades de la programación de periodicidad para que su canal reproduzca el contenido según este caso de uso.

| **Nombre** | **Repeticiones** | **Inicial** | **Fin** |
|---|---|---|---|
| Desayuno | Cada día | 6:00 AM | 11:00 |
| Almuerzo | Cada día | 11:00 | 3:00 PM |
| Cena | Cada día | 3:00 PM | 8:00 PM |

#### Reproducir contenido en un día específico de la semana {#playing-content-on-a-particular-day-of-the-week}

En este ejemplo se muestra la DayParting implementada en un casino donde el evento en directo se produce todos los fines de semana desde las 20:00 hasta las 22:00 y hay disponibles especiales para el menú de la cena después de las 22:00 hasta la 01:00.

| **Nombre** | **Repeticiones** | **Inicial** | **Fin** |
|---|---|---|---|
| Fin de semana | Semanal: Sábado,domingo | 8:00 PM | 10:00 PM |
| Ofertas especiales | Diario: Lunes a viernes | 10:00 PM | 1:00 AM |

>[!NOTE]
>
>Además, puede definir la ***Prioridad*** de cada uno de los canales. Por ejemplo, si dos canales están establecidos para el mismo día y hora o para ese mismo mes, el canal con mayor prioridad se reproduce en primer lugar. El valor mínimo de la prioridad se puede establecer en 0.
