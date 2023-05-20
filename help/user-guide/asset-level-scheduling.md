---
title: Activación de nivel de recurso
seo-title: Asset Level Activation
description: Siga esta página para aprender a activar un recurso específico en un canal durante un lapso de tiempo programado en la zona horaria local del reproductor.
seo-description: Follow this page to learn how to activate a specific asset in a channel for a scheduled time frame in the player's local timezone.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: 939d078def133e0db0e61ec80167f496c65ade46
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 1%

---

# Activación de nivel de recurso {#asset-level-scheduling}

Esta página describe la activación a nivel de recurso para los recursos utilizados en los canales.

En esta sección se tratan los siguientes temas:

* Información general
* Ventana de activación
* Reproducción de un solo evento
* Administrar la periodicidad en Assets
   * DayParting
   * WeekParting
   * MonthParting
   * Combinación de Particiones
* Activación de varios recursos
* Sustitución Global Para La Hora De Inicio Universal

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens AEM AEM solo está disponible si ha instalado el paquete de funciones 3 de 6.3 o el paquete de funciones 1 de Screens de 6.3 o de 6.4.
>
>Para obtener acceso a este paquete de funciones, debe ponerse en contacto con el Soporte técnico de Adobe y solicitar acceso. Una vez que tenga los permisos necesarios, puede descargarlo desde Package Share.

## Información general {#overview}

***Activación de nivel de recurso***, permite activar un recurso específico en un canal durante un lapso de tiempo programado en la zona horaria local del reproductor. Está disponible para imágenes, vídeos, transiciones, páginas y canales incrustados (dinámicos o estáticos).

*Por ejemplo*, desea que una promoción especial se muestre solo durante la hora feliz (de 2 p. m. a 5 p. m.) los lunes y miércoles.

Con esta función, no solo se puede especificar la fecha y la hora de inicio y finalización, sino también un patrón de periodicidad.

## Ventana de activación {#single-event-playback}

La activación a nivel de recurso se realiza configurando **Activation** al acceder a las propiedades de un recurso.

Siga los pasos a continuación para realizar la programación de nivel de recurso:

1. Seleccione cualquier canal y haga clic en **Editar** en la barra de acciones para añadir o editar contenido en el canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Para obtener información detallada sobre cómo
   >
   >* Creación de un proyecto, consulte [Creación de un nuevo proyecto](creating-a-screens-project.md).
   >* Creación y adición de contenido a un canal, consulte [Administración de canales](managing-channels.md).


1. Clic **Editar** para abrir el editor de canales y seleccionar un recurso al que desee aplicar la programación.

   ![imagen](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Seleccione el recurso y haga clic en en la parte superior izquierda **Configurar** (icono de llave inglesa) para abrir las propiedades de la imagen.

   Haga clic en **Activation** pestaña.

   ![imagen](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Puede especificar la fecha desde el selector de fechas utilizando **Activo desde** y **Activo hasta** campos.

   Si selecciona la opción **Activo desde** y **Activo hasta** fecha y hora, el recurso solo se mostrará y se reproducirá entre esa fecha/hora de inicio y la fecha/hora de finalización respectivamente.

   ![imagen](/help/user-guide/assets/asset-activation/asset-level3.png)

## Administrar la periodicidad en Assets {#handling-recurrence-in-assets}

Puede programar la reaparición de recursos en determinados intervalos de forma diaria, semanal o mensual, según sus necesidades.

Supongamos que desea mostrar una imagen solo los viernes de 1:00 p.m. a 10:00 p.m. Puede usar el complemento **Activation** para establecer el intervalo recurrente deseado para el recurso.

### División por día {#day-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo propiedades.

1. Después de escribir la fecha/hora de inicio y la fecha/hora de finalización, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
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


>[!NOTE]
>
>También puede utilizar _hora militar_ (es decir, 14:00) en lugar de *am/pm* notación (es decir, 2:00 pm).

### WeekParting {#week-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo propiedades.

1. Después de escribir la fecha/hora de inicio y la fecha/hora de finalización, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules, según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo particular de día y hora.

#### Expresiones de ejemplo para WeekParting {#example-two}

La siguiente tabla resume algunas expresiones de ejemplo que se pueden agregar a la programación al asignar un canal a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| Lun, Mié, Vie | el recurso se reproduce en el canal los lunes, miércoles y viernes |
| Lun-Jue | el recurso se reproduce en el canal de lunes a jueves |

>[!NOTE]
>
>También puede utilizar _completo_ (lunes, miércoles, viernes) en lugar de _de mano corta_ (es decir, Lun,Mié,Vie).


### MonthParting {#month-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo propiedades.

1. Después de escribir la fecha/hora de inicio y la fecha/hora de finalización, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules, según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo particular de día y hora.

#### Expresiones de ejemplo para MonthParting {#example-three}

La siguiente tabla resume algunas expresiones de ejemplo que se pueden agregar a la programación al asignar un canal a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| de febrero, mayo, agosto, noviembre | el recurso se reproduce en el canal en febrero, mayo, agosto y noviembre |
| de febrero a julio | el recurso se reproduce en el canal desde febrero hasta finales de julio |

>[!NOTE]
>Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Lunes/Lunes y Enero/Enero.

### Combinación de Particiones {#combined-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo propiedades.

1. Después de escribir la fecha/hora de inicio y la fecha/hora de finalización, puede utilizar una expresión o una versión de texto natural para especificar la programación de periodicidad.

   >[!NOTE]
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
>Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Lunes/Lunes y Enero/Enero.  Además, también puede utilizar _hora militar_ (es decir, 14:00) en lugar de *am/pm* notación (es decir, 2:00 pm).


## Activación de varios recursos {#multi-asset-scheduling}

>[!CAUTION]
>
>El **Activación de varios recursos** AEM AEM Esta función solo está disponible si ha instalado el paquete de funciones 3 de 6.3 o 5 de la versión de 6.3 de la versión de, o bien si ha instalado el paquete de funciones 3 de la versión de 6.3 de la versión de 3.000.

***Activación de varios recursos*** permite al usuario seleccionar varios recursos y aplicar una programación de reproducción a todos los recursos seleccionados.

### Requisitos previos {#prerequisites}

Para utilizar la activación a nivel de varios recursos para sus recursos, cree un proyecto de AEM Screens con un canal de secuencia. Por ejemplo, el siguiente caso de uso muestra la implementación de la función:

* Cree un proyecto de AEM Screens titulado como **MultiAssetDemo**
* Cree un canal con el título **MultiAssetChannel** y añada contenido al canal, como se muestra en la figura siguiente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga los pasos a continuación para seleccionar varios recursos y programar su visualización en un proyecto de AEM Screens:

1. Seleccionar **MultiAssetChannel** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Seleccione varios recursos en el editor y haga clic en **Editar activación** (icono superior izquierdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Seleccione la fecha y la hora en **Activo desde** y **Activo hasta** desde el **Activación de componentes** Cuadro de diálogo. Haga clic en el icono de la marca de verificación cuando haya terminado de seleccionar las programaciones.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Haga clic en Actualizar para comprobar los recursos a los que se aplica la programación de varios recursos.

   >[!NOTE]
   >
   >El icono de programación se puede ver en la esquina superior derecha de los recursos que tienen activación de varios recursos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Sustitución Global Para La Hora De Inicio Universal {#global-override-scheduling}

***Sustitución global para la hora de inicio universal***, es una configuración que permite al autor del contenido definir la reproducción de una imagen o un recurso de vídeo en función de un tiempo específico. No se utiliza el ajuste de hora/zona horaria de ningún reproductor individual.

Normalmente, la reproducción se determina por la hora local de cualquier reproductor determinado, pero con la anulación global, se puede utilizar una hora de inicio universal específica para iniciar la reproducción del recurso.

Esto permite al autor del contenido designar la reproducción de un recurso específico en una fecha u hora específicas, independientemente del reloj local de cualquier reproductor que tenga el contenido asignado.

La anulación global para el tiempo de inicio universal se realiza configurando el **Activation** al acceder a las propiedades de un recurso. Siga los pasos a continuación para realizar una anulación global de la programación de recursos:

1. Seleccione cualquier canal y haga clic en **Editar** en la barra de acciones para añadir o editar contenido en el canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Clic **Editar** para abrir el editor de canales y seleccionar un recurso al que desee aplicar la programación.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Para una anulación global, introduzca la hora de activación en **Anulación de zona horaria** para el recurso. Si no introduce nada en esta área, la zona horaria aplicada será la del jugador.


