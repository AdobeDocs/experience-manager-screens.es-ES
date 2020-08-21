---
title: Asignación de canales
seo-title: Asignación de canales
description: Siga esta página para conocer la asignación de Canales y la partición de días.
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 42%

---


# Asignación de canales {#channel-assignment}

Una vez que haya definido una visualización, deberá asignar un canal a una pantalla.

Esta página muestra cómo asignar un canal a la pantalla.

>[!NOTE]
>Puede asignar varios canales a una pantalla.

## Assigning a Channel {#assign-a-channel}

Siga los pasos a continuación para asignar un canal a una visualización:

>[!Iimportante]
>El siguiente cuadro de diálogo para la asignación de canales es diferente para la versión de Adobe Experience 6.5.5 Screens Feature Pack y versiones posteriores. Consulte Asignación de [Canales](/help/user-guide/channel-assignment.md#assign-a-channel-new-release) para obtener más detalles.

1. Vaya a la pantalla requerida, por ejemplo, **DemoProject** —> **Ubicaciones** —> **SanJosé** —> **StoreDisplay**.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Tap/click **Assign Channel** in the action bar

   O bien,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![image](/help/user-guide/assets/channel-assign1.png)

   Puede configurar las propiedades desde el cuadro de diálogo Asignación **de** Canal en la sección siguiente. Consulte la sección Propiedades del [Canal](#channel-properties) para obtener más información sobre las propiedades del canal.

## Asignación de un Canal para la versión del paquete de funciones de las pantallas de AEM 6.5.5 {#assign-a-channel-new-release}

Siga los pasos a continuación para asignar un canal a una visualización:

1. Vaya a la pantalla requerida, por ejemplo, **DemoProject** —> **Ubicaciones** —> **SanJosé** —> **StoreDisplay**.


1. Tap/click **Assign Channel** from the action bar

   O bien,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS &amp; SCHEDULES** panel to open the **Channel Assignment** dialog box.

1. En la opción Configuración, puede elegir el canal por ruta o por nombre, introducir la función de canal, la prioridad y los Eventos admitidos.

   >[!NOTE]
   >Consulte la sección Propiedades del [Canal](#channel-properties) para obtener más información sobre las propiedades del canal.

1. En la opción **Programaciones** , seleccione la Zona horaria **de** referencia, la Ventana **de** Activación y la Programación **de** periodicidad.

1. Haga clic en **Guardar** una vez que haya configurado las preferencias.

### Explicación de las propiedades de Canal de la asignación de Canales {#channel-properties}

#### Canal de referencia {#ref-channel}

El canal de referencia le permite proporcionar una referencia al canal deseado, ya sea según el nombre del canal o según la ruta de acceso al canal.

* **por ruta de acceso**: proporcione una referencia explícita mediante la ruta de acceso absoluta del canal.

* **por nombre**: Escriba el nombre del canal que se resolverá en un canal real por contexto. Esta característica le permite crear la versión local de un canal, para así resolver de forma dinámica el contenido de una ubicación específica. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

#### Rol del canal {#role-channel}

El rol de canal define el contexto de la visualización. Varias acciones dirigen la función y es independiente del canal que cumple esa función.

#### Prioridad {#priority-channel}

La prioridad se utiliza para solicitar las asignaciones en caso de que varias de ellas coincidan con los criterios de reproducción. Aquel elemento que tenga el valor más alto siempre tendrá prioridad sobre otros valores más bajos. Por ejemplo, si hay dos canales A y B, y A tiene una prioridad de 1 y B tiene una prioridad de 2, se muestra el canal B ya que tiene mayor prioridad que A.

>[!NOTE]
>La prioridad de un canal se establece como un número (1 para indicar el mínimo) en el cuadro de diálogo **Asignación de canales**, tal como se mencionó anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

#### Eventos admitidos {#supported-events-channel}

* **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales junto con la programación
* **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales junto con la programación
* **Temporizador:** se debe establecer al proporcionar una programación
* **Interacción del usuario**: el reproductor cambiará al canal determinado si el usuario toca la pantalla que está visualizando un canal inactivo, y se cargará al tocar la pantalla

#### Método de interrupción {#interruption-method-channel}

>[IMPORTANTE]
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

#### Programa {#schedule-channel}

La programación le permite proporcionar una descripción de texto que indique cuándo debe aparecer el canal. También permite definir una fecha de inicio (**activo desde**) y una fecha de finalización (**activo hasta**) para que el canal se muestre.

**Mostrar información de herramientas de atracción**:

La opción de mostrar la información sobre herramientas de atracción define si esta opción (&quot;*Pulse donde quiera para comenzar*&quot;) debe mostrarse (o no) no mientras el canal se está ejecutando.

### Partición de día {#dayparting}

Schedules when combined with **Day-parting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

La parrilla de programación es el proceso de dividir un día en franjas horarias y especificar qué tipo de contenido se reproducirá en una hora concreta. AEM Screens le permite programar canales en términos de partición de día dentro de un día, una semana o un mes según lo requiera.

Los siguientes ejemplos explican la partición de día en canales en tres escenarios diferentes:

#### Reproducir contenido en un único día que esté dividido en varias franjas horarias {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este ejemplo muestra cómo un restaurante utiliza la partición de día para mostrar su menú de desayuno, almuerzo y cena.

Aquí dividiremos cada día en tres franjas de tiempo diferentes, para que el contenido de los canales se reproduzca según la hora del día:

| **Canal** | **Función** | **Prioridad** | **Programa** |
|---|---|---|---|
| Menu_A | Desayuno |  | después de las 6:00 y antes de las 11:00 |
| Menu_B | Almuerzo |  | después de las 11:00 y antes de las 15:00 |
| Menu_C | Cena |  | después de las 15:00 y antes de las 20:00 |

#### Reproducir contenido en un día específico de la semana {#playing-content-on-a-particular-day-of-the-week}

En este ejemplo se muestra la parrilla de programación de un casino donde se visualiza un evento en directo todos los fines de semana desde las 20:00 hasta las 22:00, y donde también se muestran los platos especiales del menú que estarán disponibles durante la cena después de las 22:00 hasta la 1:00 de la madrugada.

<table>
 <tbody>
  <tr>
   <td><strong>Canal</strong></td>
   <td><strong>Función</strong></td>
   <td><strong>Prioridad</strong></td>
   <td><strong>Programa</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>Fin de semana</td>
   <td> </td>
   <td>21 de octubre de 2017 - 22 de octubre de 2017 <br /> después de las 20:00 antes de las 22:00</td>
  </tr>
  <tr>
   <td>Ofertas especialesCena</td>
   <td>Fin de semana</td>
   <td> </td>
   <td>21 de octubre de 2017 - 22 de octubre de 2017 <br /> después de las 22:00 antes de la 1:00</td>
  </tr>
 </tbody>
</table>

#### Reproducir contenido para un mes o meses en particular {#playing-content-for-a-particular-month-months}

En este ejemplo se muestra la partición de día de una tienda que muestra su colección de verano de los meses de junio a agosto y de otoño de septiembre a finales de octubre.

Aquí, creará partición de día según los meses para que el contenido del canal se reproduzca según los meses especificados del año.

| **Canal** | **Función** | **Prioridad** | **Programa** |
|---|---|---|---|
| SummerCollection | Verano |  | 1 de junio de 2017 - 31 de agosto de 2017 |
| FallCollection | Otoño |  | 01 de septiembre de 2017 - 30 de octubre de 2017 |

>[!NOTE]
>
>Además, puede definir la ***Prioridad*** de cada uno de los canales. Por ejemplo, si dos canales están establecidos para el mismo día y hora o para ese mismo mes, el canal con mayor prioridad se reproduce en primer lugar. El valor mínimo de la prioridad se puede establecer en 0.

#### Reproducir contenido de canales con la misma prioridad {#playing-content-for-channels-with-same-priority}

Este ejemplo muestra la partición de día de una tienda que muestra su colección de invierno con la misma programación en el mes de diciembre. Pero, dado que el canal B tiene un conjunto de prioridad como 2, durante esa semana el canal B reproduce su contenido en lugar del canal A.

| **Canal** | **Función** | **Prioridad** | **Programa** |
|---|---|---|---|
| A | Invierno | 1 | 01 de diciembre de 2017 - 31 de diciembre de 2017 |
| B | Navidad | 2 | 24 de diciembre de 2017 - 31 de diciembre de 2017 |


>[!IMPORTANT]
>
> Para obtener más información sobre la partición de día, consulte las secciones siguientes:
>
>* [Gestión de periodicidad en recursos](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [Gestión de periodicidad para recursos en un Canal](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


