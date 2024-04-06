---
title: 'Activación a nivel de canal: reproducción de un solo evento'
seo-title: Channel Level Activation - Single Event Playback
description: Siga esta guía para comprender la activación a nivel de canal mediante la reproducción de un solo evento.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1792'
ht-degree: 1%

---

# Activación de nivel de canal {#channel-level-activation-single-event-playback}

Esta página describe la activación a nivel de canal para los recursos utilizados en Canales.

En esta sección se tratan los siguientes temas:

* Información general
* Ventana de activación
* Uso de la activación a nivel de canal como reproducción de evento único
* Administrar la periodicidad de los recursos de un canal
   * DayParting
   * WeekParting
   * MonthParting
   * Combinación de Particiones
* Uso de la activación a nivel de canal como reproducción de evento único

## Información general {#overview}

***Activación de nivel de canal*** permite que los canales cambien después de una programación determinada. El canal de evento único reemplaza al canal principal después de una programación establecida y se reproduce durante un tiempo determinado, hasta que el canal principal vuelva a reproducir su contenido.

En el ejemplo siguiente se proporciona una solución centrándose en los términos clave siguientes:

* a ***canal de secuencia principal*** para la secuencia global
* a ***canal de evento único*** que se ejecuta solo una vez a la hora establecida
* a ***establecer programación y prioridad*** para el evento de reproducción única que se produce dentro del canal de secuencia principal

## Ventana de activación {#using-channel-level-activation}

En la siguiente sección se explica la creación de una única reproducción de evento dentro de un canal para un proyecto de AEM Screens.

### Requisitos previos {#prerequisites}

Antes de comenzar a implementar esta funcionalidad, asegúrese de que tiene los siguientes requisitos previos listos para comenzar a implementar la activación a nivel de canal:

* Cree un proyecto de AEM Screens, en este ejemplo, **Activación de nivel de canal**

* Crear un canal como **MainAdChannel** bajo **Canales** carpeta

* Crear otro canal como **TargetedSinglePlay** bajo **Canales** carpeta

* Añadir los recursos relevantes a ambos canales

La siguiente imagen muestra el **Activación de nivel de canal** proyecto con **MainAdChannel** y **TargetedSinglePlay** canales en **Canales** carpeta.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obtener información adicional sobre cómo crear un proyecto y cómo crear un canal de secuencia, consulte los recursos a continuación:
>
>* [Creación y administración de proyectos](creating-a-screens-project.md)
>
>* [Administración de un canal](managing-channels.md)
>

### Implementación {#implementation}

La implementación de la activación a nivel de canal en un proyecto de AEM Screens implica tres tareas principales:

1. **Configuración de la taxonomía de proyecto, incluidos canales, ubicaciones y pantallas**
1. **Asignación de canales a la visualización**
1. **Configuración de un horario y una prioridad**

Siga los pasos a continuación para implementar la funcionalidad:

1. **Crear una ubicación**

   Navegue hasta su **Ubicaciones** en el proyecto de AEM Screens y cree una ubicación como **Región**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para aprender a crear una ubicación, consulte **[Creación y administración de ubicaciones](managing-locations.md)**.

1. **Crear pantalla en Ubicación**

   1. Vaya a **Activación de nivel de canal** > **Ubicaciones** > **Región**.
   1. Seleccionar **Región** y haga clic en **+ Crear** de la barra de acciones.
   1. Seleccionar **Mostrar** en el asistente y cree una pantalla con el título **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Asignar canales a la pantalla**

   Para **MainAdChannel:**

   1. Vaya a **Activación de nivel de canal** > **Ubicaciones** > **Región** > **RegionDisplay** y haga clic en **Asignar canal** de la barra de acciones.
   1. **Asignación de canales** se abre el cuadro de diálogo.
   1. Seleccionar **Canal de referencia**.. por ruta.
   1. Seleccione el **Ruta de canal** as **Activación de nivel de canal** > ***Canales*** > ***MainAdChannel***.
   1. El **Función del canal** se rellena como **mainadchannel**.
   1. Seleccione el **Prioridad** as **1**.
   1. Seleccione el **Eventos admitidos** as **Carga inicial** y **Pantalla inactiva**.
   1. Haga clic en **Guardar**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >También puede asignar un canal desde el panel de visualización navegando hasta **Activación de nivel de canal** > **Ubicaciones** > **Región** > **RegionDisplay** y haciendo clic en **Tablero** de la barra de acciones. Clic **+ Asignar canal** desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel.

   Del mismo modo, asignar canal **TargetedSinglePlay** para visualización**:

   1. Vaya a **Activación de nivel de canal** > **Ubicaciones** > **Región** > **RegionDisplay** y haga clic en **Asignar canal** de la barra de acciones.
   1. **Asignación de canales** se abre el cuadro de diálogo.
   1. Seleccionar **Canal de referencia**.. por ruta.
   1. Seleccione el **Ruta de canal** as **Activación de nivel de canal*** > ***Canales*** > ***TargetedSinglePlay***.
   1. El **Función del canal** se rellena como **targetedsingleplay**.
   1. Configure las variables **Prioridad** as **2**.
   1. Seleccione el **Eventos admitidos** as **Carga inicial**, **Pantalla inactiva** y **Temporizador**, *como se muestra en la figura siguiente.
   1. Elija la fecha en **activo desde** como 27 de noviembre de 2018 23:59 h y en **activo hasta** as 28 de noviembre de 2018 12:05 am
   1. Haga clic en **Guardar**.

   >[!CAUTION]
   >
   >Debe establecer la prioridad de **TargetedSinglePlay** canal superior a **MainAdSegment** canal.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Para elegir el mismo día, debe seleccionar el día siguiente y editar manualmente la fecha en el mismo día, pero para una hora posterior. Esto restringe al usuario de la selección de una fecha pasada. Consulte el ejemplo siguiente:

   ![new1](assets/new1.gif)

## Visualización de los resultados {#viewing-the-results}

Una vez que haya completado la configuración de los canales y la visualización, inicie el reproductor de AEM Screens para ver el contenido.

El reproductor muestra el contenido de **MainAdChannel** y exactamente a las 23:59 (como se establece en el horario), el **TargetedSinglePlay** El canal mostrará su contenido hasta las 12:05 y, a continuación, el **MainAdChannel** reanudará la reproducción de su contenido.

>[!NOTE]
>
>AEM Para obtener más información sobre el Reproductor de pantalla de la pantalla de la aplicación, consulte los siguientes recursos:
>[Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/)
>[Uso del Reproductor de AEM Screens](working-with-screens-player.md)


## Administrar la periodicidad de los recursos de un canal {#handling-recurrence-in-assets}

Puede programar los recursos de un canal para que se repitan a intervalos específicos diariamente, semanalmente o mensualmente, según sus necesidades.

Supongamos que desea mostrar el contenido de un canal solo los viernes de 1:00 p.m. a 10:00 p.m. Puede usar el complemento **Activation** para establecer el intervalo recurrente deseado para el recurso.

### División por día {#day-parting}

1. Seleccione el canal y haga clic en **Tablero** en la barra de acciones para abrir el panel de canales.

1. Después de introducir la fecha/hora de inicio y la fecha/hora de finalización desde el **Asignación de canales** , puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   >
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules, según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo particular de día y hora.

#### Expresiones de ejemplo para la partición por día {#example-one}

La siguiente tabla resume algunas expresiones de ejemplo que se pueden agregar a la programación al asignar un canal a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 | el recurso del canal se reproduce antes de las 8:00 a. m. todos los días |
| después de las 14:00 | el recurso del canal se reproduce después de las 2 de la tarde todos los días |
| después de las 12:15 y antes de las 12:45 | el recurso del canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el recurso en el canal se reproduce antes de las 12:15 todos los días y luego también después de las 12:45 |
| Lun, Mar, Mié o Lun-Mié | el recurso se reproduce en el recurso del canal de lunes a miércoles |
| el 1 de enero después de las 14:00 h también el 2 de enero también el 3 de enero antes de las 3:00 h | el recurso del canal comienza a reproducirse después de las 2 de la tarde del 1 de enero y continúa reproduciendo durante todo el día del 2 de enero hasta las 3 de la madrugada del 3 de enero |
| el 1-2 día de enero después de las 2:00 pm también el 2-3 día de enero antes de las 3:00 am | el recurso del canal inicia el reproductor después de las 2:00 p.m. del 1 de enero, continúa reproduciendo hasta las 3:00 a.m. del 2 de enero, luego comienza nuevamente el 2 de enero a las 2:00 p.m. y continúa reproduciendo hasta las 3:00 a.m. del 3 de enero |

>[!NOTE]
>
>También puede utilizar _hora militar_ (es decir, 14:00) en lugar de *am/pm* notación (es decir, 2:00 pm).

### WeekParting {#week-parting}

1. Seleccione el canal y haga clic en **Tablero** en la barra de acciones para abrir el panel de canales.

1. Después de introducir la fecha/hora de inicio y la fecha/hora de finalización desde el **Asignación de canales** , puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   >
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules, según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo particular de día y hora.

#### Expresiones de ejemplo para WeekParting {#example-two}

La siguiente tabla resume algunas expresiones de ejemplo que se pueden agregar a la programación al asignar un canal a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| Lun, Mar, Mié o Lun-Mié | el recurso se reproduce en el recurso del canal de lunes a miércoles |
| antes de las 8:00 | el recurso del canal se reproduce antes de las 8:00 a. m. todos los días |
| después de las 14:00 | el recurso del canal se reproduce después de las 2 de la tarde todos los días |
| después de las 12:15 y antes de las 12:45 | el recurso del canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el canal se reproduce antes de las 12:15 todos los días y luego también después de las 12:45 |

>[!NOTE]
>
>También puede utilizar _hora militar_ (es decir, 14:00) en lugar de *am/pm* notación (es decir, 2:00 pm).


### MonthParting {#month-parting}

1. Seleccione el canal y haga clic en **Tablero** en la barra de acciones para abrir el panel de canales.

1. Después de introducir la fecha/hora de inicio y la fecha/hora de finalización desde el **Asignación de canales** , puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   >
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules, según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo particular de día y hora.

#### Expresiones de ejemplo para MonthParting {#example-three}

La siguiente tabla resume algunas expresiones de ejemplo que se pueden agregar a la programación al asignar un canal a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| de febrero, mayo, agosto, noviembre | el recurso se reproduce en el canal en febrero, mayo, agosto y noviembre |

>[!NOTE]
>
>Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Lunes/Lunes y Enero/Enero.

>[!NOTE]
>
>También puede utilizar _hora militar_ (es decir, 14:00) en lugar de *am/pm* notación (es decir, 2:00 pm).

### Combinación de Particiones {#combined-parting}

1. Seleccione el canal y haga clic en **Tablero** en la barra de acciones para abrir el panel de canales.

1. Después de introducir la fecha/hora de inicio y la fecha/hora de finalización desde el **Asignación de canales** , puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   >
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules, según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo particular de día y hora.

#### Expresiones de ejemplo para combinación de particiones {#example-four}

La siguiente tabla resume algunas expresiones de ejemplo que se pueden agregar a la programación al asignar un canal a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| después de las 6:00 y antes de las 18:00 el lunes, miércoles de enero a marzo | el recurso se reproduce en el canal entre las 6:00 y las 18:00 los lunes y miércoles de enero a finales de marzo |
| el 1 de enero después de las 14:00 h también el 2 de enero también el 3 de enero antes de las 3:00 h | el recurso del canal comienza a reproducirse después de las 2 de la tarde del 1 de enero y continúa reproduciendo durante todo el día del 2 de enero hasta las 3 de la madrugada del 3 de enero |
| el 1-2 día de enero después de las 2:00 pm también el 2-3 día de enero antes de las 3:00 am | el recurso del canal inicia el reproductor después de las 2:00 p.m. del 1 de enero, continúa reproduciendo hasta las 3:00 a.m. del 2 de enero, luego comienza nuevamente el 2 de enero a las 2:00 p.m. y continúa reproduciendo hasta las 3:00 a.m. del 3 de enero |

>[!NOTE]
>
>Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Lunes/Lunes y Enero/Enero.  Además, también puede utilizar _hora militar_ (es decir, 14:00) en lugar de *am/pm* notación (es decir, 2:00 pm).
