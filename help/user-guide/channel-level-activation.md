---
title: 'Activación a nivel de canal: reproducción de un solo evento'
seo-title: 'Activación a nivel de canal: reproducción de un solo evento'
description: Siga esta guía para comprender la activación a nivel de canal mediante la reproducción de un solo evento.
seo-description: Siga esta guía para comprender la activación a nivel de canal mediante la reproducción de un solo evento.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
feature: Authoring Screens, Channel Level Activation
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 0%

---


# Activación a nivel de canal {#channel-level-activation-single-event-playback}

En esta página se describe la activación a nivel de canal para los recursos utilizados en los canales.

En esta sección se tratan los temas siguientes:

* Información general
* Ventana de activación
* Uso de la activación de nivel de canal como una reproducción de evento único
* Gestión de la periodicidad para los recursos de un canal
   * Partición de día
   * División Semana
   * MonthParting
   * Combinación de asociaciones
* Uso de la activación de nivel de canal como una reproducción de evento único

## Información general {#overview}

***La*** activación a nivel de canal permite que los canales cambien después de una programación establecida concreta. El canal de evento único reemplaza al canal principal después de una programación establecida y se reproduce durante un tiempo concreto, hasta que el canal principal vuelva a reproducir su contenido.

El siguiente ejemplo proporciona una solución centrándose en los siguientes términos clave:

* a ***canal de secuencia principal*** para la secuencia global
* un ***canal de evento único*** que se ejecuta una sola vez a la hora establecida
* una ***programación establecida y prioridad*** para el evento de reproducción única que se produce dentro del canal de secuencia principal

## Ventana de activación {#using-channel-level-activation}

En la siguiente sección se explica la creación de una sola reproducción de evento dentro de un canal para un proyecto de AEM Screens.

### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de que tiene los siguientes requisitos previos listos para empezar a implementar la activación a nivel de canal:

* Cree un proyecto de AEM Screens, en este ejemplo **Activación a nivel de canal**

* Cree un canal como **MainAdChannel** en la carpeta **Channels**

* Cree otro canal como **TargetedSinglePlay** en la carpeta **Channels**

* Agregar recursos relevantes a ambos canales

La imagen siguiente muestra el proyecto **Channel Level Activation** con los canales **MainAdChannel** y **TargetedSinglePlay** en la carpeta **Channels**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obtener información adicional sobre cómo crear un proyecto y cómo crear un canal de secuencia, consulte los recursos a continuación:
>
>* [Creación y administración de proyectos](creating-a-screens-project.md)
   >
   >
* [Administración de un canal](managing-channels.md)

>



### Implementación {#implementation}

La implementación de la activación a nivel de canal en un proyecto de AEM Screens implica tres tareas principales:

1. **Configuración de la taxonomía del proyecto, incluidos Canales, Ubicaciones y Visualizaciones**
1. **Asignación de canales para mostrar**
1. **Configuración de una programación y una prioridad**

Siga los pasos a continuación para implementar la funcionalidad:

1. **Crear una ubicación**

   Vaya a la carpeta **Ubicaciones** del proyecto de AEM Screens y cree una ubicación como **Región**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para aprender a crear una ubicación, consulte **[Creación y administración de ubicaciones](managing-locations.md)**.

1. **Crear visualización en Ubicación**

   1. Vaya a **Channel Level Activation** > **Ubicaciones** > **Región**.
   1. Seleccione **Región** y haga clic en **+ Crear** en la barra de acciones.
   1. Seleccione **Display** del asistente y cree una visualización con el título **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Asignar canales a la visualización**

   Para **MainAdChannel:**

   1. Vaya a **Channel Level Activation** > **Ubicaciones** > **Región** > **RegionDisplay** y haga clic en **Asignar canal** en la barra de acciones.
   1. **Se abre el cuadro de diálogo** Asignación de canales .
   1. Seleccione **Canal de referencia**.. por ruta.
   1. Seleccione **Ruta del canal** como **Activación a nivel de canal** —> ***Canales*** —> ***CanalAdChannel***.
   1. El **Rol del canal** se rellena como **mainadchannel**.
   1. Seleccione **Priority** como **1**.
   1. Seleccione **Eventos admitidos** como **Carga inicial** y **Pantalla inactiva**.
   1. Haga clic en **Guardar**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >También puede asignar canales desde el panel de visualización navegando a **Activación de nivel de canal** —> **Ubicaciones** —> **Región** —> **Visualización de región** y haciendo clic en **Panel** en la barra de acciones. Haga clic en **+ Asignar canal** en el panel **CANALES Y PROGRAMAS ASIGNADOS**.

   Del mismo modo, asigne el canal **TargetedSinglePlay** para la visualización**:

   1. Vaya a **Channel Level Activation** —> **Ubicaciones** —> **Región** —> **RegionDisplay** y haga clic en **Asignar canal** en la barra de acciones.
   1. **Se abre el cuadro de diálogo** Asignación de canales .
   1. Seleccione **Canal de referencia**.. por ruta.
   1. Seleccione la **Ruta del canal** como **Activación a nivel de canal*** —> ***Canales*** —> ***TargetedSinglePlay***.
   1. El **Rol del canal** se rellena como **targetedsingleplay**.
   1. Establezca la **Prioridad** como **2**.
   1. Seleccione **Eventos admitidos** como **Carga inicial**, **Pantalla inactiva** y **Temporizador**, *como se muestra en la figura siguiente.
   1. Elija la fecha en **activo desde** como 27 de noviembre de 2018 a las 11:59 y en **activo hasta** como 28 de noviembre de 2018 a las 12:05.
   1. Haga clic en **Guardar**.

   >[!CAUTION]
   Debe establecer la prioridad para el canal **TargetedSinglePlay** más alto que el canal **MainAdSegment**.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Para elegir el mismo día, debe seleccionar el día siguiente y editar la fecha manualmente al mismo día pero para más tarde. Esto impide que el usuario seleccione una fecha anterior. Consulte el ejemplo siguiente:

   ![new1](assets/new1.gif)

## Visualización de los resultados {#viewing-the-results}

Una vez que haya configurado los canales y se haya completado la visualización, inicie el reproductor AEM Screens para ver el contenido.

El reproductor muestra el contenido de **MainAdChannel** y exactamente a las 23:59 (como se establece en la programación), el canal **TargetedSinglePlay** mostrará su contenido hasta las 12:05 y luego el **MainAdChannel** reanudará la reproducción del contenido.

>[!NOTE]
Para obtener más información sobre AEM reproductor de pantalla, consulte los siguientes recursos:
[Descargas del Reproductor de AEM Screens](https://download.macromedia.com/screens/)
[Trabajo con AEM Screens Player](working-with-screens-player.md)


## Gestión de la periodicidad para los recursos en un canal {#handling-recurrence-in-assets}

Puede programar los recursos de un canal para que se repitan a intervalos determinados de forma diaria, semanal o mensual, según sus necesidades.

Supongamos que desea mostrar el contenido de un canal solo los viernes de 13:00 a 22:00. Puede utilizar la pestaña **Activation** para establecer el intervalo recurrente deseado para el recurso.

### Partición de día {#day-parting}

1. Seleccione el canal y haga clic en **Dashboard** en la barra de acciones para abrir el panel del canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha del cuadro de diálogo **Asignación de canal**, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programas según sus necesidades.

1. Introduzca la expresión en **Schedule** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Ejemplo de expresiones para partición de día {#example-one}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 am | el recurso del canal se reproduce antes de las 8:00 a. m. todos los días |
| después de las 2:00 pm | el recurso del canal se reproduce después de las 2:00 pm todos los días |
| después de las 12:15 y antes de las 12:45 | el recurso en el canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el recurso en el canal se reproduce antes de las 12:15 todos los días y después también después de las 12:45 |
| Lun,Tue,Wed o Lun-Wed | el recurso se reproduce en el canal de lunes a miércoles |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el recurso en el canal comienza a reproducirse después de las 2:00 pm del 1 de enero y continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 am del 3 de enero |
| el día 1-2 de enero después de las 2:00 pm también el día 2-3 de enero antes de las 3:00 am | el recurso en el canal inicia el reproductor después de las 2:00 pm del 1 de enero, continúa reproduciendo hasta las 3:00 am del 2 de enero, y luego vuelve a empezar el 2 de enero a las 2:00 pm y continúa reproduciendo hasta las 3:00 am del 3 de enero |

>[!NOTE]
También puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, las 2:00 pm).

### División por semana {#week-parting}

1. Seleccione el canal y haga clic en **Dashboard** en la barra de acciones para abrir el panel del canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha del cuadro de diálogo **Asignación de canal**, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programas según sus necesidades.

1. Introduzca la expresión en **Schedule** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Ejemplo de expresiones para WeekParting {#example-two}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| Lun,Tue,Wed o Lun-Wed | el recurso se reproduce en el canal de lunes a miércoles |
| antes de las 8:00 am | el recurso del canal se reproduce antes de las 8:00 a. m. todos los días |
| después de las 2:00 pm | el recurso del canal se reproduce después de las 2:00 pm todos los días |
| después de las 12:15 y antes de las 12:45 | el recurso en el canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el canal se reproduce antes de las 12:15 todos los días y después de las 12:45 |

>[!NOTE]
También puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, las 2:00 pm).


### MonthParting {#month-parting}

1. Seleccione el canal y haga clic en **Dashboard** en la barra de acciones para abrir el panel del canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha del cuadro de diálogo **Asignación de canal**, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programas según sus necesidades.

1. Introduzca la expresión en **Schedule** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Expresiones de ejemplo para MonthParting {#example-three}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| de febrero, mayo, agosto, noviembre | el recurso se reproduce en el canal en febrero, mayo, agosto y noviembre |

>[!NOTE]
Al definir los días de la semana y los meses, puede utilizar las anotaciones de nombre corto y completo, como Lunes/Lunes y Enero/Enero.

>[!NOTE]
También puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, las 2:00 pm).

### Combinación de elementos {#combined-parting}

1. Seleccione el canal y haga clic en **Dashboard** en la barra de acciones para abrir el panel del canal.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha del cuadro de diálogo **Asignación de canal**, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programas según sus necesidades.

1. Introduzca la expresión en **Schedule** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Expresiones de ejemplo para la combinación de elementos {#example-four}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| después de las 6:00 y antes de las 18:00 el lunes, miércoles de enero a marzo | el recurso se reproduce en el canal entre las 6:00 y las 6:00 h los lunes y miércoles de enero a finales de marzo |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el recurso en el canal comienza a reproducirse después de las 2:00 pm del 1 de enero y continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 am del 3 de enero |
| el día 1-2 de enero después de las 2:00 pm también el día 2-3 de enero antes de las 3:00 am | el recurso en el canal inicia el reproductor después de las 2:00 pm del 1 de enero, continúa reproduciendo hasta las 3:00 am del 2 de enero, y luego vuelve a empezar el 2 de enero a las 2:00 pm y continúa reproduciendo hasta las 3:00 am del 3 de enero |

>[!NOTE]
Al definir los días de la semana y los meses, puede utilizar las anotaciones de nombre corto y completo, como Lunes/Lunes y Enero/Enero.  Además, también puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, las 2:00 pm).

