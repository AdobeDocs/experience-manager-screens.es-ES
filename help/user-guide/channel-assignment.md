---
title: Asignación de canales
seo-title: Asignación de canales
description: Vaya a esta página para obtener más información sobre la asignación y la parrilla de programación del canal.
seo-description: Vaya a esta página para obtener más información sobre la asignación y la parrilla de programación del canal.
uuid: fe429485-dcc9-4507-864c-b04393cedeee
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 212adcd1-835b-453d-9d3e-775366abf181
docset: aem65
translation-type: tm+mt
source-git-commit: f8d4b612d9c10d3f9f43ff4792ca48a1bf9407d0

---


# Asignación de canales {#channel-assignment}

Esta sección abarca los siguientes temas:

* **Asignación de un canal**
* **Descripción de las propiedades de la asignación de canal, cuadro de diálogo**
* **Parrilla de programación**

Una vez que haya definido una visualización, debe asignar un canal a una de las visualizaciones.

En esta página se muestra la asignación del canal a las visualizaciones.

**Requisitos previos**:

* [Configurar e implementar Screens](configuring-screens-introduction.md)
* [Crear y gestionar proyecto de pantallas](creating-a-screens-project.md)
* [Crear y administrar canales](managing-channels.md)
* [Crear y administrar ubicaciones](managing-locations.md)
* [Crear y administrar pantallas](managing-displays.md)

## Asignar un canal {#assign-a-channel}

Siga los pasos a continuación para asignar un canal a una visualización:

1. Vaya a la pantalla requerida, por ejemplo, **DemoProject** —> **Ubicaciones** —> **SanJosé** —> **StoreDisplay**.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Toque o haga clic en **Asignar canal **en la barra de acciones

   O bien,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![screen_shot_2018-08-23at25938pm](assets/screen_shot_2018-08-23at25938pm.png)

   Puede configurar las siguientes propiedades en el cuadro de diálogo **Asignación de canales**:

   **Rol del canal**:

   El rol de canal define el contexto de la visualización. Varias acciones dirigen la función y es independiente del canal que cumple esa función.

   **Canal de referencia**:

   El canal de referencia le permite proporcionar una referencia al canal deseado, ya sea según el nombre del canal o según la ruta de acceso al canal.

   * **por ruta de acceso**: proporcione una referencia explícita mediante la ruta de acceso absoluta del canal.
   * **por nombre**: Escriba el nombre del canal que se resolverá en un canal real por contexto. Esta característica le permite crear la versión local de un canal, para así resolver de forma dinámica el contenido de una ubicación específica. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.
   **Prioridad:**

   La prioridad se utiliza para solicitar las asignaciones en caso de que varias de ellas coincidan con los criterios de reproducción. Aquel elemento que tenga el valor más alto siempre tendrá prioridad sobre otros valores más bajos. Por ejemplo, si hay dos canales A y B, y A tiene una prioridad de 1 y B tiene una prioridad de 2, se muestra el canal B ya que tiene mayor prioridad que A.

   La prioridad de un canal se establece como un número (1 para indicar el mínimo) en el cuadro de diálogo **Asignación de canales**, tal como se mencionó anteriormente. Además, los canales asignados se ordenan según la prioridad descendente.

   **Eventos admitidos**:

   * **Carga inicial**: carga el canal cuando se inicia el reproductor. Se puede asignar a varios canales junto con la programación
   * **Pantalla inactiva**: se carga cuando la pantalla está inactiva. Se puede asignar a varios canales junto con la programación
   * **Temporizador:** se debe establecer al proporcionar una programación
   * **Interacción del usuario**: el reproductor cambiará al canal determinado si el usuario toca la pantalla que está visualizando un canal inactivo, y se cargará al tocar la pantalla
   **Programa**:

   La programación le permite proporcionar una descripción de texto que indique cuándo debe aparecer el canal. También permite definir una fecha de inicio (**activo desde**) y una fecha de finalización (**activo hasta**) para que el canal se muestre. La sintaxis de la expresión de programación se basa en el texto de later.js y la sintaxis cron:

   * [https://bunkat.github.io/later/parsers.html#text](https://bunkat.github.io/later/parsers.html#text)
   * [https://bunkat.github.io/later/parsers.html#cron](https://bunkat.github.io/later/parsers.html#cron)
   **Mostrar información de herramientas de atracción**:

   La opción de mostrar la información sobre herramientas de atracción define si esta opción (&quot;*Pulse donde quiera para comenzar*&quot;) debe mostrarse (o no) no mientras el canal se está ejecutando.

1. Haga clic en **Guardar** para asignar el canal creado a una pantalla.

### Parrilla de programación {#dayparting}

Schedules when combined with **Dayparting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

La parrilla de programación es el proceso de dividir un día en franjas horarias y especificar qué tipo de contenido se reproducirá en una hora concreta. AEM Screens le permite programar los canales en una parrilla de programación en un día, semana o mes según sea necesario.

En los siguientes ejemplos se explica la parrilla de programación de los canales en tres contextos distintos:

#### Reproducir contenido en un único día que esté dividido en varias franjas horarias {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

En este ejemplo se muestra cómo un restaurante utiliza la parrilla de programación para mostrar los menús del desayuno, comida y cena.

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

En este ejemplo se muestra la parrilla de programación de una tienda que muestra su colección de verano desde los meses de junio hasta agosto, y su colección de otoño desde septiembre hasta finales de octubre.

Aquí se creará la parrilla de programación según los meses, de modo que el contenido del canal se reproduzca según los meses especificados del año.

| **Canal** | **Función** | **Prioridad** | **Programa** |
|---|---|---|---|
| SummerCollection | Verano |  | 1 de junio de 2017 - 31 de agosto de 2017 |
| FallCollection | Otoño |  | 01 de septiembre de 2017 - 30 de octubre de 2017 |

>[!NOTE]
>
>Además, puede definir la ***Prioridad*** de cada uno de los canales. Por ejemplo, si dos canales están establecidos para el mismo día y hora o para ese mismo mes, el canal con mayor prioridad se reproduce en primer lugar. El valor mínimo de la prioridad se puede establecer en 0.

#### Reproducir contenido de canales con la misma prioridad {#playing-content-for-channels-with-same-priority}

En este ejemplo se muestra la parrilla de programación de una tienda que muestra su colección de invierno con el mismo programa para el mes de diciembre. Pero, dado que el canal B tiene un conjunto de prioridad como 2, durante esa semana el canal B reproduce su contenido en lugar del canal A.

| **Canal** | **Función** | **Prioridad** | **Programa** |
|---|---|---|---|
| A | Invierno | 1 | 01 de diciembre de 2017 - 31 de diciembre de 2017 |
| B | Navidad | 2 | 24 de diciembre de 2017 - 31 de diciembre de 2017 |

