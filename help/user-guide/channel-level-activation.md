---
title: 'Activación de nivel de Canal: reproducción de un solo Evento'
seo-title: 'Activación de nivel de Canal: reproducción de un solo Evento'
description: Siga esta guía para comprender la activación a nivel de canal mediante la reproducción de un solo evento.
seo-description: Siga esta guía para comprender la activación a nivel de canal mediante la reproducción de un solo evento.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '1809'
ht-degree: 0%

---


# Activación de nivel de Canal {#channel-level-activation-single-event-playback}

En esta página se describe la activación de nivel de canal de los recursos utilizados en los Canales.

En esta sección se tratan los siguientes temas:

* Información general
* Ventana de activación
* Uso de la Activación de nivel de Canal como una única reproducción de Evento
* Gestión de periodicidad para recursos en un Canal
   * Partición de días
   * Partición de semana
   * Partición de mes
   * Combinación de asociaciones
* Uso de la Activación de nivel de Canal como una única reproducción de Evento

## Información general {#overview}

***La Activación*** de nivel de Canal permite que los canales cambien después de una programación establecida en particular. El canal de evento único reemplaza al canal principal después de una programación establecida y se reproduce durante un tiempo determinado, hasta que el canal principal vuelve a reproducir su contenido.

El siguiente ejemplo proporciona una solución centrándose en los siguientes términos clave:

* un canal ***de secuencia*** principal para la secuencia global
* un ***único canal*** de evento que se ejecuta una sola vez a la hora establecida
* un programa ***establecido y una prioridad*** para el evento de reproducción único que se produce dentro del canal de secuencia principal

## Ventana de activación {#using-channel-level-activation}

En la siguiente sección se explica la creación de una sola reproducción de evento dentro de un canal para un proyecto de AEM Screens.

### Requisitos previos {#prerequisites}

Antes de implementar esta funcionalidad en inicio, asegúrese de tener los siguientes requisitos previos listos para inicio para implementar la activación de nivel de canal:

* Crear un proyecto de AEM Screens, en este ejemplo, Activación de nivel de **Canal**

* Crear un canal como **MainAdChannel** en la carpeta **Canales**

* Crear otro canal como **TargetedSinglePlay** en la carpeta **Canales**

* Añadir los activos pertinentes a ambos canales

La siguiente imagen muestra el proyecto de Activación **de nivel de** Canal con los canales **MainAdChannel** y **TargetedSinglePlay** en la carpeta **Canales** .

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obtener información adicional sobre cómo crear un proyecto y cómo crear un canal de secuencia, consulte los recursos siguientes:
>
>* [Creación y administración de proyectos](creating-a-screens-project.md)
   >
   >
* [Administración de un Canal](managing-channels.md)

>



### Implementación {#implementation}

La implementación de la Activación del nivel de Canal en un proyecto de AEM Screens implica tres tareas principales:

1. **Configuración de la taxonomía del proyecto, incluidos Canales, ubicaciones y pantallas**
1. **Asignación de Canales para mostrar**
1. **Configuración de una programación y una prioridad**

Siga los pasos a continuación para implementar la funcionalidad:

1. **Crear una ubicación**

   Vaya a la carpeta **Ubicaciones** del proyecto AEM Screens y cree una ubicación como **Región**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo crear una ubicación, consulte **[Creación y administración de ubicaciones](managing-locations.md)**.

1. **Crear visualización en Ubicación**

   1. Vaya a Activación **de nivel de** Canal > **Ubicaciones** > **Región**.
   1. Seleccione **Región** y haga clic en **+ Crear** en la barra de acciones.
   1. Seleccione **Mostrar** en el asistente y cree una pantalla con el título **RegiónMostrar.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Asignar Canales para mostrar**

   Para **MainAdChannel:**

   1. Vaya a Activación **de nivel de** Canal > **Ubicaciones** > **Región** > **RegiónVisualización** y haga clic en **Asignar Canal** en la barra de acciones.
   1. **Se abre el cuadro de diálogo Asignación** de Canal.
   1. Select **Reference Channel**.. by path.
   1. Seleccione la ruta **de** Canal como Activación **de nivel de** Canal —> ***Canales*** —> ***MainAdChannel***.
   1. La función **de** Canal se rellena como **mainadchannel**.
   1. Seleccione la **prioridad** como **1**.
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Haga clic en **Guardar**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >También puede asignar canales desde el panel de visualización navegando a la Activación **de nivel de** Canal —> **Ubicaciones** —> **Región** —> **RegiónVisualización** y haciendo clic en **Panel** en la barra de acciones. Haga clic en **+ Asignar Canal** en el panel CANALES y PROGRAMAS **** ASIGNADOS.

   Del mismo modo, asigne canal **TargetedSinglePlay** para la visualización**:

   1. Vaya a la Activación **de nivel de** Canal —> **Ubicaciones** —> **Región** —> **RegiónVisualización** y haga clic en **Asignar Canal** en la barra de acciones.
   1. **Se abre el cuadro de diálogo Asignación** de Canal.
   1. Select **Reference Channel**.. by path.
   1. Seleccione la ruta **de** Canal como Activación **de nivel de** Canal* —> ***Canales*** —> ***TargetedSinglePlay***.
   1. La función de **Canal** se rellena como **targetedsingleplay**.
   1. Establezca la **prioridad** como **2**.
   1. Seleccione los Eventos **** admitidos como Carga **** inicial, **Pantalla** inactiva y **Temporizador**, *como se muestra en la figura siguiente.
   1. Elija la fecha en **activo desde** el 27 de noviembre de 2018 a las 11:59 y en **activo hasta** el 28 de noviembre de 2018 a las 12:05.
   1. Haga clic en **Guardar**.

   >[!CAUTION]
   Debe establecer la prioridad para el canal **TargetedSinglePlay** más alto que el canal **MainAdSegment** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Para elegir el mismo día, debe seleccionar el día siguiente y editar la fecha manualmente hasta el mismo día, pero para más tarde. Esto impide que el usuario seleccione una fecha pasada. Consulte el ejemplo siguiente:

   ![new1](assets/new1.gif)

## Visualización de los resultados {#viewing-the-results}

Una vez que haya configurado los canales y se haya completado la visualización, inicie el reproductor de AEM Screens para la vista del contenido.

El reproductor muestra el contenido de **MainAdChannel** y exactamente a las 11:59 (según lo establecido en la programación), el canal **TargetedSinglePlay** mostrará su contenido hasta las 12:05 a.m. y, a continuación, **MainAdChannel** reanudará la reproducción de su contenido.

>[!NOTE]
Para obtener más información sobre AEM reproductor de pantalla, consulte los siguientes recursos:
* [Descargas de AEM Screens Player](https://download.macromedia.com/screens/)
* [Uso de AEM Screens Player](working-with-screens-player.md)



## Gestión de periodicidad para recursos en un Canal{#handling-recurrence-in-assets}

Puede programar los recursos de un canal para que se repitan en determinados intervalos, de forma diaria, semanal o mensual, según sus necesidades.

Supongamos que desea mostrar el contenido de un canal sólo los viernes de 1:00 a 22:00. Puede utilizar la ficha **Activación** para establecer el intervalo recurrente deseado para el recurso.

### Partición de días {#day-parting}

1. Seleccione el canal y haga clic en el **Panel** en la barra de acciones para abrir el panel de canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha desde el cuadro de diálogo Asignación **de** Canales, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **programación** y se mostrará el recurso para el intervalo de día y hora concreto.

#### Ejemplo de Expresiones para partición de día {#example-one}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 am | el canal juega antes de las 8:00 todos los días |
| después de las 2:00 pm | el canal juega a partir de las 14:00 todos los días |
| después de las 12:15 y antes de las 12:45 | el canal juega cada día durante 30 minutos después de las 12:15 |
| antes de las 12:15 también después de las 12:45 | el punto fuerte del canal se juega antes de las 12:15 todos los días y después de las 12:45 |
| Lun,Tue,Wed o Lun-Wed | el recurso se reproduce en el canal de lunes a miércoles |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el recurso en los inicios de canal que se reproducen después de las 14:00 del 1 de enero continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 del 3 de enero |
| del 1 al 2 de enero después de las 2:00 pm también del 2 al 3 de enero antes de las 3:00 am | el recurso en el reproductor de inicios de canal después de las 2:00 pm del 1 de enero, continúa reproduciéndose hasta las 3:00 am del 2 de enero, luego vuelve a inicio el 2 de enero a las 2:00 pm y continúa reproduciéndose hasta las 3:00 am del 3 de enero |

>[!NOTE]
También se puede utilizar la notación de hora __ militar (es decir, 14:00) en lugar de la notación de *am/pm* (es decir, 2:00 pm).

### Partición de semana {#week-parting}

1. Seleccione el canal y haga clic en el **Panel** en la barra de acciones para abrir el panel de canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha desde el cuadro de diálogo Asignación **de** Canales, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **programación** y se mostrará el recurso para el intervalo de día y hora concreto.

#### Ejemplo de Expresiones para partición de semana {#example-two}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| Lun,Tue,Wed o Lun-Wed | el recurso se reproduce en el canal de lunes a miércoles |
| antes de las 8:00 am | el canal juega antes de las 8:00 todos los días |
| después de las 2:00 pm | el canal juega a partir de las 14:00 todos los días |
| después de las 12:15 y antes de las 12:45 | el canal juega cada día durante 30 minutos después de las 12:15 |
| antes de las 12:15 también después de las 12:45 | el canal toca antes de las 12:15 todos los días y después de las 12:45 |

>[!NOTE]
También se puede utilizar la notación de hora __ militar (es decir, 14:00) en lugar de la notación de *am/pm* (es decir, 2:00 pm).


### Partición de mes {#month-parting}

1. Seleccione el canal y haga clic en el **Panel** en la barra de acciones para abrir el panel de canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha desde el cuadro de diálogo Asignación **de** Canales, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **programación** y se mostrará el recurso para el intervalo de día y hora concreto.

#### Ejemplo de Expresiones para partición mensual {#example-three}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| de febrero, mayo, agosto, noviembre | el recurso se reproduce en el canal en febrero, mayo, agosto y noviembre |

>[!NOTE]
Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Mon/Lunes y Ene/Enero.

>[!NOTE]
También se puede utilizar la notación de hora __ militar (es decir, 14:00) en lugar de la notación de *am/pm* (es decir, 2:00 pm).

### Combinación de asociaciones {#combined-parting}

1. Seleccione el canal y haga clic en el **Panel** en la barra de acciones para abrir el panel de canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha desde el cuadro de diálogo Asignación **de** Canales, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **programación** y se mostrará el recurso para el intervalo de día y hora concreto.

#### Expresiones de ejemplo para la combinación de elementos {#example-four}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| después de las 6:00 y antes de las 18:00 el lunes, miércoles de enero a marzo | el canal funciona de 6:00 a 18:00 los lunes y miércoles de enero a finales de marzo |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el recurso en los inicios de canal que se reproducen después de las 14:00 del 1 de enero continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 del 3 de enero |
| del 1 al 2 de enero después de las 2:00 pm también del 2 al 3 de enero antes de las 3:00 am | el recurso en el reproductor de inicios de canal después de las 2:00 pm del 1 de enero, continúa reproduciéndose hasta las 3:00 am del 2 de enero, luego vuelve a inicio el 2 de enero a las 2:00 pm y continúa reproduciéndose hasta las 3:00 am del 3 de enero |

>[!NOTE]
Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Mon/Lunes y Ene/Enero.  Además, también se puede utilizar la notación de hora __ militar (es decir, 14:00) en lugar de la notación de *am/pm* (es decir, 2:00 pm).

