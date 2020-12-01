---
title: Activación de nivel de recurso
seo-title: Activación de nivel de recurso
description: Siga esta página para aprender a activar un recurso específico en un canal para un intervalo de tiempo programado en la zona horaria local del reproductor.
seo-description: Siga esta página para aprender a activar un recurso específico en un canal para un intervalo de tiempo programado en la zona horaria local del reproductor.
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 2%

---


# Activación de nivel de recurso {#asset-level-scheduling}

En esta página se describe la activación de nivel de recurso para los recursos utilizados en los Canales.

En esta sección se tratan los siguientes temas:

* Información general
* Ventana de activación
* Reproducción de un solo Evento
* Gestión de periodicidad en recursos
   * Partición de día
   * Partición de semana
   * MonthParting
   * Combinación de asociaciones
* Activación de varios recursos

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Información general {#overview}

***La Activación*** de nivel de recurso le permite activar un recurso específico en un canal para un intervalo de tiempo programado en la zona horaria local del reproductor. Está disponible para imágenes, vídeos, transiciones, páginas y canales incrustados (dinámicos o estáticos).

*Por ejemplo*, desea que una promoción especial se muestre solamente durante la hora feliz (de 2pm a 5pm) los lunes y miércoles.

Con esta función, no sólo puede especificar el inicio y la fecha y hora de finalización, sino también un patrón de periodicidad.

## Ventana de activación {#single-event-playback}

La Activación del nivel de recurso se realiza configurando la ficha **Activación** al acceder a las propiedades de un recurso.

Siga los pasos a continuación para realizar la programación de nivel de recursos:

1. Seleccione cualquier canal y haga clic en **Editar** en la barra de acciones para agregar o editar contenido en el canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Para aprender en detalle sobre cómo
   >
   >* Cree un proyecto, consulte [Creación de un nuevo proyecto](creating-a-screens-project.md).
   >* Cree y agregue contenido a un canal, consulte [Administración de Canales](managing-channels.md).


1. Haga clic en **Editar** para abrir el editor de canal y seleccionar un recurso al que desee aplicar la programación.

   ![image](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Seleccione el recurso y haga clic en la parte superior izquierda **Configurar** (icono de llave inglesa) para abrir las propiedades de la imagen.

   Haga clic en la ficha **Activación**.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Puede especificar la fecha desde el selector de fechas mediante los campos **Activo desde** y **Activo hasta**.

   Si selecciona la fecha y hora **Activo desde** y **Activo hasta**, el recurso se mostrará y se reproducirá únicamente entre esa fecha y hora de inicio y la fecha y hora de finalización, respectivamente.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestión de la periodicidad en los recursos {#handling-recurrence-in-assets}

Puede programar los recursos para que se repitan a determinados intervalos de forma diaria, semanal o mensual, según sus necesidades.

Supongamos que desea mostrar una imagen sólo los viernes de 1:00 a 22:00. Puede utilizar la ficha **Activación** para establecer el intervalo recurrente deseado para el recurso.

### Partición de días {#day-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **Programación** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Ejemplo de Expresiones para partición de día {#example-one}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 am | el canal juega antes de las 8:00 todos los días |
| después de las 2:00 pm | el canal juega a partir de las 14:00 todos los días |
| después de las 12:15 y antes de las 12:45 | el canal juega cada día durante 30 minutos después de las 12:15 |
| antes de las 12:15 también después de las 12:45 | el punto fuerte del canal se juega antes de las 12:15 todos los días y después de las 12:45 |


>[!NOTE]
>
>También puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, a las 2:00 pm).

### Partición de semana {#week-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **Programación** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Ejemplo de Expresiones para WeekParting {#example-two}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| Lun,Wed,Fri | el recurso se reproduce en el canal los lunes, miércoles y viernes |
| Mon-Thu | el recurso se reproduce en el canal de los lunes a los jueves |

>[!NOTE]
>
>También puede utilizar la notación _completa_ (es decir, lunes, miércoles, viernes) en lugar de la notación _de mano corta_ (es decir, Mon,Wed,Fri).


### MonthParting {#month-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **Programación** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Ejemplo de Expresiones para MonthParting {#example-three}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| de febrero, mayo, agosto, noviembre | el recurso se reproduce en el canal en febrero, mayo, agosto y noviembre |
| de febrero a julio | el recurso se reproduce en el canal desde febrero hasta finales de julio |

>[!NOTE]
>Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Mon/Lunes y Ene/Enero.

### Combinación de elementos {#combined-parting}

1. Seleccione el recurso y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo de propiedades.

1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión o una versión de texto natural para especificar el programa de periodicidad.

   >[!NOTE]
   >Puede omitir o incluir los campos **Activo desde** y **Activo hasta** y agregar la expresión al campo Programaciones, según sus necesidades.

1. Introduzca la expresión en la **Programación** y el recurso se mostrará para el intervalo de día y hora concreto.

#### Expresiones de ejemplo para la combinación de elementos {#example-four}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| después de las 6:00 y antes de las 18:00 el lunes, miércoles de enero a marzo | el canal funciona de 6:00 a 18:00 los lunes y miércoles de enero a finales de marzo |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el recurso en los inicios de canal que se reproducen después de las 14:00 del 1 de enero continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 del 3 de enero |
| del 1 al 2 de enero después de las 2:00 pm también del 2 al 3 de enero antes de las 3:00 am | el recurso en el reproductor de inicios de canal después de las 2:00 pm del 1 de enero, continúa reproduciéndose hasta las 3:00 am del 2 de enero, luego vuelve a inicio el 2 de enero a las 2:00 pm y continúa reproduciéndose hasta las 3:00 am del 3 de enero |

>[!NOTE]
>Al definir los días de la semana y los meses, puede utilizar las notaciones de mano corta y nombre completo, como Mon/Lunes y Ene/Enero.  Además, también puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, a las 2:00 pm).


## Activación de varios recursos {#multi-asset-scheduling}

>[!CAUTION]
>
>La función **Activación de varios recursos** solo está disponible si ha instalado AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

***La*** activación de varios recursos permite al usuario seleccionar varios recursos y aplicar una programación de reproducción a todos los recursos seleccionados.

### Requisitos previos {#prerequisites}

Para utilizar la activación de varios recursos para los recursos, cree un proyecto de AEM Screens con un canal de secuencia. Por ejemplo, el siguiente caso de uso muestra la implementación de la función:

* Cree un proyecto de AEM Screens con el título **MultiAssetDemo**
* Cree un canal con el título **MultiAssetChannel** y agregue contenido al canal, como se muestra en la figura siguiente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga los pasos a continuación para seleccionar varios recursos y programar su visualización en un proyecto de AEM Screens:

1. Seleccione **MultiAssetChannel** y haga clic en **Editar** en la barra de acciones para abrir el editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Seleccione varios recursos del editor y haga clic en **Editar Activación** (icono superior izquierdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Seleccione la fecha y la hora en **Activo desde** y **Activo hasta** en el cuadro de diálogo **Activación de componentes**. Haga clic en el icono de marca de verificación cuando haya terminado de seleccionar los programas.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Haga clic en Actualizar para comprobar los recursos a los que se ha aplicado la programación de varios recursos.

   >[!NOTE]
   >
   >El icono de programación está visible en la esquina superior derecha para los recursos que tienen activación de varios recursos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

