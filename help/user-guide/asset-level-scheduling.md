---
title: Activación en el nivel de recurso
seo-title: Asset Level Activation
description: Siga esta página para aprender a activar un recurso específico en un canal durante un intervalo de tiempo programado en la zona horaria local del reproductor.
seo-description: Follow this page to learn how to activate a specific asset in a channel for a scheduled time frame in the player's local timezone.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: 939d078def133e0db0e61ec80167f496c65ade46
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 2%

---

# Activación en el nivel de recurso {#asset-level-scheduling}

Esta página describe la activación a nivel de recurso para los recursos utilizados en los canales.

En esta sección se tratan los temas siguientes:

* Información general
* Ventana de activación
* Reproducción de un solo evento
* Gestión de la periodicidad en Assets
   * Partición de día
   * División Semana
   * MonthParting
   * Combinación de asociaciones
* Activación de varios recursos
* Anulación Global Para La Hora De Inicio Universal

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Información general {#overview}

***Activación en el nivel de recurso***, le permite activar un recurso específico en un canal para un lapso de tiempo programado en la zona horaria local del reproductor. Esta opción está disponible para imágenes, vídeos, transiciones, páginas y canales incrustados (dinámicos o estáticos).

*Por ejemplo*, desea que una promoción especial se muestre solamente durante la hora feliz (de 2pm a 5pm) los lunes y miércoles.

Con esta función, no solo puede especificar la fecha y la hora de inicio y finalización, sino también un patrón de periodicidad.

## Ventana de activación {#single-event-playback}

La activación del nivel de recurso se realiza configurando la variable **Activation** al acceder a las propiedades de un recurso.

Siga los pasos a continuación para realizar la programación de nivel de recurso:

1. Seleccione cualquier canal y haga clic en **Editar** en la barra de acciones para añadir o editar contenido en el canal.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Para obtener información detallada sobre cómo
   >
   >* Crear un proyecto, consulte [Creación de un nuevo proyecto](creating-a-screens-project.md).
   >* Cree y añada contenido a un canal; consulte [Administración de canales](managing-channels.md).


1. Haga clic en **Editar** para abrir el editor de canales y seleccionar un recurso al que desee aplicar la programación.

   ![imagen](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Seleccione el recurso y haga clic en en la parte superior izquierda **Configurar** (icono de llave inglesa) para abrir las propiedades de la imagen.

   Haga clic en el **Activation** pestaña .

   ![imagen](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Puede especificar la fecha desde el selector de fechas utilizando **Activo desde** y **Activo hasta** campos.

   Si selecciona la opción **Activo desde** y **Activo hasta** fecha y hora, el recurso solo se mostrará y se reproducirá en bucle entre la fecha y la hora de inicio y la fecha y hora de finalización, respectivamente.

   ![imagen](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestión de la periodicidad en Assets {#handling-recurrence-in-assets}

Puede programar que los recursos se repitan a intervalos determinados de forma diaria, semanal o mensual, según sus necesidades.

Supongamos que desea mostrar una imagen solo los viernes de 13:00 a 22:00. Puede usar la variable **Activation** para establecer el intervalo recurrente deseado para el recurso.

### Partición de día {#day-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo de día y hora en particular.

#### Ejemplo de expresiones para partición de día {#example-one}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 am | el recurso del canal se reproduce antes de las 8:00 a. m. todos los días |
| después de las 2:00 pm | el recurso del canal se reproduce después de las 2:00 pm todos los días |
| después de las 12:15 y antes de las 12:45 | el recurso en el canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el recurso en el canal se reproduce antes de las 12:15 todos los días y después también después de las 12:45 |


>[!NOTE]
>
>También puede utilizar _hora militar_ notación (es decir, 14:00) en lugar de *am/pm* notación (es decir, a las 2 de la tarde).

### División Semana {#week-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo de día y hora en particular.

#### Ejemplo de expresiones para WeekParting {#example-two}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| Lun,Mié,Vie | el recurso se reproduce en el canal desde lunes, miércoles y viernes |
| Mon-Thu | el recurso se reproduce en el canal de los lunes a los jueves |

>[!NOTE]
>
>También puede utilizar _full_ notación (es decir, lunes, miércoles, viernes) en lugar de _mano corta_ notación (es decir, Mon, Wed, Fri).


### MonthParting {#month-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo de día y hora en particular.

#### Expresiones de ejemplo para MonthParting {#example-three}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| de febrero, mayo, agosto, noviembre | el recurso se reproduce en el canal en febrero, mayo, agosto y noviembre |
| de febrero a julio | el recurso se reproduce en el canal desde febrero hasta finales de julio |

>[!NOTE]
>Al definir los días de la semana y los meses, puede utilizar las anotaciones de nombre corto y completo, como Lunes/Lunes y Enero/Enero.

### Combinación de asociaciones {#combined-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir el **Activo desde** y **Activo hasta** y añada la expresión al campo Schedules según sus necesidades.

1. Introduzca la expresión en la variable **Programación** y el recurso se mostrará para el intervalo de día y hora en particular.

#### Ejemplos de expresiones para la combinación de elementos {#example-four}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| después de las 6:00 y antes de las 18:00 el lunes, miércoles de enero a marzo | el recurso se reproduce en el canal entre las 6:00 y las 6:00 h los lunes y miércoles de enero a finales de marzo |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el recurso en el canal comienza a reproducirse después de las 2:00 pm del 1 de enero y continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 am del 3 de enero |
| el día 1-2 de enero después de las 2:00 pm también el día 2-3 de enero antes de las 3:00 am | el recurso en el canal inicia el reproductor después de las 2:00 pm del 1 de enero, continúa reproduciendo hasta las 3:00 am del 2 de enero, y luego vuelve a empezar el 2 de enero a las 2:00 pm y continúa reproduciendo hasta las 3:00 am del 3 de enero |

>[!NOTE]
>Al definir los días de la semana y los meses, puede utilizar las anotaciones de nombre corto y completo, como Lunes/Lunes y Enero/Enero.  Además, también puede utilizar _hora militar_ notación (es decir, 14:00) en lugar de *am/pm* notación (es decir, a las 2 de la tarde).


## Activación de varios recursos {#multi-asset-scheduling}

>[!CAUTION]
>
>La variable **Activación de varios recursos** esta función solo está disponible si ha instalado AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

***Activación de varios recursos*** permite al usuario seleccionar varios recursos y aplicar una programación de reproducción a todos los recursos seleccionados.

### Requisitos previos {#prerequisites}

Para utilizar la activación a nivel de recursos múltiples para los recursos, cree un proyecto de AEM Screens con un canal de secuencia. Por ejemplo, el siguiente caso de uso muestra la implementación de la función:

* Crear un proyecto de AEM Screens con el título **MultiAssetDemo**
* Cree un canal con el título **MultiAssetChannel** y añada contenido al canal, como se muestra en la figura siguiente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga los pasos a continuación para seleccionar varios recursos y programar su visualización en un proyecto de AEM Screens:

1. Select **MultiAssetChannel** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Seleccione varios recursos en el editor y haga clic en **Editar activación** (icono superior izquierdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Seleccione la fecha y la hora en **Activo desde** y **Activo hasta** de la variable **Activación de componentes** para abrir el Navegador. Haga clic en el icono de marca de verificación cuando haya terminado de seleccionar las programaciones.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Haga clic en actualizar para comprobar los recursos a los que se aplica la programación de varios recursos.

   >[!NOTE]
   >
   >El icono de programación está visible en la esquina superior derecha de los recursos que tienen activación de varios recursos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Anulación Global Para La Hora De Inicio Universal {#global-override-scheduling}

***Anulación global para la hora de inicio universal***, es un ajuste que permite al autor del contenido definir la reproducción de una imagen o un recurso de vídeo en función de un tiempo específico. No se utiliza la configuración de zona horaria/horaria de ningún reproductor individual.

Normalmente, la reproducción está determinada por la hora local de un reproductor determinado, pero con la anulación global, se puede utilizar un tiempo de inicio universal específico para iniciar la reproducción del recurso.

Esto permite al autor del contenido designar la reproducción de un recurso específico como si se produjera en una fecha y hora específicas, independientemente del reloj local en cualquier reproductor que tenga asignado el contenido.

La anulación global del tiempo de inicio universal se realiza configurando la variable **Activation** al acceder a las propiedades de un recurso. Siga los pasos a continuación para realizar una anulación global de la programación de recursos:

1. Seleccione cualquier canal y haga clic en **Editar** en la barra de acciones para añadir o editar contenido en el canal.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Haga clic en **Editar** para abrir el editor de canales y seleccionar un recurso al que desee aplicar la programación.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Para una anulación global, introduzca el tiempo de activación en la variable **Anulación de zona horaria** para el recurso. Si no introduce nada en esta área, la zona horaria aplicada será la zona horaria del reproductor.


