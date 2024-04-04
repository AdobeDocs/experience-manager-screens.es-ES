---
title: Asignación de canales
seo-title: Channel Assignment
description: Siga esta página para obtener más información sobre la asignación de canales y la partición del día.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 3%

---

# Asignación de canales {#channel-assignment}

>[!IMPORTANT]
>AEM En esta sección se destaca la asignación de canales y la programación de canales para paquetes de funciones anteriores a la versión de Screens de la versión 6.5.5 de la versión de.

Una vez configurada una pantalla, debe asignar un canal a una pantalla para ver el contenido.

Esta página muestra la asignación de un canal a la visualización.

>[!NOTE]
>Puede asignar varios canales a una visualización.

## Asignación de un canal {#assign-a-channel}

Siga los pasos a continuación para asignar un canal a una visualización:

1. Navegue hasta la visualización requerida, por ejemplo, **DemoProject** —> **Ubicaciones** —> **San José** —> **StoreDisplay**.

   ![imagen](assets/screen_shot_2018-08-23at25359pm.png)

1. Pulse o haga clic en **Asignar canal** en la barra de acciones

   O bien,

   Pulse o haga clic en **Tablero** y haga clic en **+Asignar canal** desde el **CANALES ASIGNADOS** panel para abrir **Asignación de canales** Cuadro de diálogo.

   ![imagen](/help/user-guide/assets/channel-assign1.png)

   Puede configurar las propiedades desde el **Asignación de canales** Cuadro de diálogo de la sección siguiente. Consulte [Propiedades de canal](#channel-properties) para obtener más información sobre las propiedades del canal.


## Explicación de las propiedades de canal de la asignación de canal {#channel-properties}

### Canal de referencia {#ref-channel}

El canal de referencia permite proporcionar una referencia al canal deseado, ya sea por nombre de canal o por ruta de canal.

* **por ruta**: proporciona una referencia explícita utilizando la ruta absoluta del canal.

* **por nombre**: Introduzca el nombre del canal que se resolverá en un canal real por contexto. Esta función le permite crear la versión local de un canal para resolver de forma dinámica contenido específico de la ubicación. Por ejemplo, un canal con el nombre *ofertas del día*, donde el contenido real sería diferente en dos ciudades, pero el canal sigue teniendo una función sensata en todas las pantallas.

### Función del canal {#role-channel}

La función Canal define el contexto de la visualización. La función está dirigida por varias acciones y es independiente del canal real que cumple la función.

### Prioridad {#priority-channel}

La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tenga el valor más alto siempre tendrá prioridad sobre los valores más bajos. Por ejemplo, si hay dos canales, A y B. A tiene una prioridad de 1 y B tiene una prioridad de 2. A continuación, se muestra el canal B, ya que tiene una prioridad mayor que A.

>[!NOTE]
>La prioridad de un canal se establece como un número (1 como mínimo) en la variable **Asignación de canales** , como se ha mencionado anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

### Eventos admitidos {#supported-events-channel}

* **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales en combinación con la programación
* **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales en combinación con la programación
* **Temporizador**: debe configurarse cuando se proporciona una programación
* **Interacción del usuario**: el reproductor cambiará al canal especificado si hay una interacción del usuario en la pantalla (táctil) en un canal inactivo y se cargará cuando se toque la pantalla

### Método de interrupción {#interruption-method-channel}

>[!IMPORTANT]
>
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

### Programación {#schedule-channel}

Programación le permite proporcionar una descripción en texto cuando el canal debe aparecer. También permite definir una fecha de inicio (**activo desde**) y una fecha de finalización (**activo hasta**) para que se muestre el canal.

**Mostrar información de atracción**:

Mostrar información sobre la atracción define si la información sobre la atracción (&quot;*Toque en cualquier lugar para empezar*&quot;) se debe mostrar o no mientras se ejecuta el canal.

### DayParting {#dayparting}

Programaciones cuando se combinan con **DayParting**, permite establecer una programación global con varios canales en ejecución a horas específicas del día y reutilizar esa configuración para todas las pantallas a la vez.

DayParting se refiere a dividir un día en espacios de tiempo y especificar qué contenido se reproduce a la hora deseada. AEM Screens le permite programar canales en términos de partición de día en un día, una semana o un mes según sea necesario.

Los siguientes ejemplos explican la partición del día en canales en tres escenarios diferentes:

#### Reproducción de contenido en un solo día dividido en varias franjas horarias {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este ejemplo muestra cómo un restaurante utiliza la partición del día para mostrar su menú de desayuno, almuerzo y cena.

Aquí, dividiremos cada día en tres franjas horarias diferentes, de modo que el contenido del canal se reproduzca a la hora especificada del día:

| **Canal** | **Función** | **Prioridad** | **Programación** |
|---|---|---|---|
| Menú_A | Desayuno |  | después de las 6:00 y antes de las 11:00 |
| Menu_B | Almuerzo |  | después de las 11:00 y antes de las 15:00 |
| Menu_C | Cena |  | después de las 15:00 y antes de las 20:00 |

#### Reproducción de contenido en un día de la semana concreto {#playing-content-on-a-particular-day-of-the-week}

Este ejemplo muestra el dayParting logrado en un casino donde el evento en vivo ocurre todos los fines de semana de 8:00 pm hasta 10:00 pm y los especiales están disponibles para el menú de cena después de las 10:00 pm hasta la 1:00 am

<table>
 <tbody>
  <tr>
   <td><strong>Canal</strong></td>
   <td><strong>Función</strong></td>
   <td><strong>Prioridad</strong></td>
   <td><strong>Programación</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>Weekend</td>
   <td> </td>
   <td>21 de octubre de 2017 - 22 de octubre de 2017 <br /> después de las 20:00 antes de las 22:00</td>
  </tr>
  <tr>
   <td>SpecialsDinner</td>
   <td>Weekend</td>
   <td> </td>
   <td>21 de octubre de 2017 - 22 de octubre de 2017 <br /> después de las 22:00 antes de la 1:00</td>
  </tr>
 </tbody>
</table>

#### Reproducción de contenido durante un mes o meses determinados {#playing-content-for-a-particular-month-months}

En este ejemplo se muestra el DayParting de una tienda que muestra su colección de verano de los meses de junio a agosto y la colección de otoño de septiembre a finales de octubre.

Aquí puede crear la partición de día según los meses, de modo que el contenido del canal se reproduzca según los meses del año especificados.

| **Canal** | **Función** | **Prioridad** | **Programación** |
|---|---|---|---|
| SummerCollection | Verano |  | 1 de junio de 2017 - 31 de agosto de 2017 |
| FallCollection | Otoño |  | 1 de septiembre de 2017 - 30 de octubre de 2017 |

>[!NOTE]
>
>Además, puede definir lo siguiente ***Prioridad*** para cada uno de los canales. Por ejemplo, si se establecen dos canales para el mismo día y hora o para el mismo mes, el canal con mayor prioridad se reproduce primero. El valor mínimo de prioridad puede establecerse como 0.

#### Reproducción de contenido para canales con la misma prioridad {#playing-content-for-channels-with-same-priority}

En este ejemplo se muestra el DayParting de una tienda que muestra su colección de invierno con la misma programación en el mes de diciembre. Pero dado que el Canal B tiene la prioridad establecida como 2, durante esa semana; el Canal B reproduce su contenido en lugar del Canal A.

| **Canal** | **Función** | **Prioridad** | **Programación** |
|---|---|---|---|
| A | Invierno | 1 | 1 de diciembre de 2017 - 31 de diciembre de 2017 |
| B | Navidad | 2 | 24 de diciembre de 2017 - 31 de diciembre de 2017 |


>[!NOTE]
>
> Para obtener más información sobre DayParting, consulte las secciones siguientes:
>
>* [Administrar la periodicidad en Assets](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [Administrar la periodicidad de los recursos de un canal](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)
