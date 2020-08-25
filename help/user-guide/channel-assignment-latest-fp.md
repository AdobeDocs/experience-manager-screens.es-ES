---
title: Asignación de canales - Última publicación
seo-title: Asignación de canales - Última publicación
description: Siga esta página para conocer la asignación de Canales y la partición de días.
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 31%

---


# Asignación de canales {#channel-assignment}

>[!IMPORTANT]
>Esta sección resalta la asignación de Canales y la programación de canales para AEM 6.5.5 Screens Feature Pack y versiones posteriores.

Una vez configurada la visualización, debe asignar un canal a una pantalla para la vista del contenido.

Esta página muestra cómo asignar un canal a la pantalla.

>[!NOTE]
>Puede asignar varios canales a una pantalla.


## Assigning a Channel {#assign-a-channel-new-release}

Siga las secciones a continuación para crear un proyecto de AEM Screens y asignar un canal a una pantalla.

### Creación de un proyecto y Canales de AEM Screens {#creating-project}

Siga los pasos a continuación para configurar un proyecto y un canal:

1. Cree un proyecto de AEM Screens denominado **DemoScreens**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consulte [Creación y administración de proyectos](creating-a-screens-project.md) para obtener información sobre cómo crear un proyecto de AEM Screens.

1. Cree un canal de secuencia denominado **Cafeteria** en la carpeta **Canales** .

1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para agregar contenido al canal.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por ejemplo, el canal **Cafeteria** ahora muestra las siguientes imágenes:

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Cree una ubicación titulada **SanJosé** y una visualización como **Punto de encuentro**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Asignación de Canales a una visualización {#assigning-channel-to-display}

Una vez que se haya completado la configuración del proyecto, debe asignar el canal a una pantalla para la vista del contenido.

1. Vaya a la pantalla requerida, por ejemplo, **DemoScreens** —> **Ubicaciones** —> **SanJosé** —> **Punto de encuentro**.

1. Tap/click **Assign Channel** from the action bar.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   O bien,

   Toque o haga clic en **Panel** y haga clic en **+Asignar Canal** en el panel CANALES y PROGRAMAS **** ASIGNADOS.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. En la opción **Configuración** , puede elegir el canal por ruta o por nombre, introducir la función de canal, la prioridad, los eventos admitidos y los métodos de interrupción. Además, puede activar la opción de información sobre herramientas de atracción desde este cuadro de diálogo.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Consulte la sección Propiedades del [Canal](#channel-properties) para obtener más información sobre las propiedades del canal.

1. En la opción **Programaciones** , seleccione la Zona horaria **de** referencia, la Ventana **de** Activación y la Programación **de** periodicidad.

1. Haga clic en **Guardar** una vez que haya configurado las preferencias.

### Visualización del contenido en Chrome Player {#viewing-content-output}

### Explicación de las propiedades de Canal de la asignación de Canales {#channel-properties}

### Canal de referencia {#ref-channel}

El canal de referencia le permite proporcionar una referencia al canal deseado, ya sea según el nombre del canal o según la ruta de acceso al canal.

* **por ruta de acceso**: proporcione una referencia explícita mediante la ruta de acceso absoluta del canal.

* **por nombre**: Escriba el nombre del canal que se resolverá en un canal real por contexto. Esta característica le permite crear la versión local de un canal, para así resolver de forma dinámica el contenido de una ubicación específica. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

### Rol del canal {#role-channel}

El rol de canal define el contexto de la visualización. Varias acciones dirigen la función y es independiente del canal que cumple esa función.

### Prioridad {#priority-channel}

La prioridad se utiliza para solicitar las asignaciones en caso de que varias de ellas coincidan con los criterios de reproducción. Aquel elemento que tenga el valor más alto siempre tendrá prioridad sobre otros valores más bajos. Por ejemplo, si hay dos canales A y B, y A tiene una prioridad de 1 y B tiene una prioridad de 2, se muestra el canal B ya que tiene mayor prioridad que A.

>[!NOTE]
>La prioridad de un canal se establece como un número (1 para indicar el mínimo) en el cuadro de diálogo **Asignación de canales**, tal como se mencionó anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

### Eventos admitidos {#supported-events-channel}

* **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales junto con la programación
* **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales junto con la programación
* **Temporizador:** se debe establecer al proporcionar una programación
* **Interacción del usuario**: el reproductor cambiará al canal determinado si el usuario toca la pantalla que está visualizando un canal inactivo, y se cargará al tocar la pantalla

### Método de interrupción {#interruption-method-channel}

>[!IMPORTANT]
>
> Esta opción solo está disponible con AEM 6.4 Feature Pack 8 o AEM 6.5 Feature Pack 4.

Como autor de contenido, debe poder especificar cuándo se interrumpe un canal para que pueda optar por cortar el contenido no crítico, pero tener la opción de permitir que el contenido importante se reproduzca completamente antes de cortar la reproducción debido a la programación.

Seleccione una de las siguientes opciones disponibles para establecer el método de interrupción en el cuadro de diálogo Asignación de **Canal** :

* **Inmediatamente**: cada vez que se activa la programación o se recibe una actualización, puede cortar la reproducción y actualizar o reproducir inmediatamente el nuevo contenido
* **Al final del elemento** actual: cuando se activa una nueva programación o se recibe una actualización, tiene la opción de esperar a que el elemento actual de la secuencia termine de reproducirse y solo después de que actualice o reproduzca el nuevo contenido
   >[!NOTE]
   >Esta opción está seleccionada de forma predeterminada.
* **Al final de la secuencia**: cuando se activa una nueva programación o se recibe una actualización, tiene la opción de esperar a que toda la secuencia llegue a su final y, justo antes de la secuencia deseada, vuelva al primer elemento para actualizar o reproducir el nuevo contenido

   >[!NOTE]
   >El uso de la segunda o tercera opción puede hacer que los tiempos de programación definidos en la asignación se pospongan ligeramente, ya que el reproductor esperará el final del elemento o secuencia (después del tiempo especificado) antes de la actualización. El retraso dependerá de la duración de reproducción del elemento.