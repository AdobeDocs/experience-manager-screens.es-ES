---
title: Programación del nivel de recursos
seo-title: Programación del nivel de recursos
description: Siga esta página para aprender a activar un recurso específico en un canal durante un intervalo de tiempo programado en la zona horaria local del reproductor.
seo-description: Siga esta página para aprender a activar un recurso específico en un canal durante un intervalo de tiempo programado en la zona horaria local del reproductor.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: da25cdc7-c814-493e-8d8e-b6191fee2831
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Programación del nivel de recursos {#asset-level-scheduling}


En esta sección se describe la programación de nivel de recursos para los recursos utilizados en los canales.

En esta sección se tratan los siguientes temas:

* Información general
* Uso de la programación de nivel de recursos
* Gestión de periodicidad en recursos
* Programación de varios recursos


>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Información general {#overview}

***La programación*** de nivel de recursos le permite activar un recurso específico en un canal para un intervalo de tiempo programado en la zona horaria local del reproductor. Esta opción está disponible para imágenes, vídeos, transiciones, páginas y canales incrustados (dinámicos o estáticos).

*Por ejemplo*, desea que una promoción especial se muestre solamente durante la hora feliz (de 2pm a 5pm) los lunes y miércoles.

Con esta función, no sólo puede especificar la fecha y hora de inicio y finalización, sino también un patrón de periodicidad.

## Uso de la programación de nivel de recursos {#using-asset-level-scheduling}

La programación de nivel de recursos se realiza configurando la ficha **Activación** al acceder a las propiedades de un recurso.

Siga los pasos a continuación para realizar la programación de nivel de recursos:

1. Seleccione cualquier canal y haga clic en **Editar** en la barra de acciones para agregar o editar contenido en el canal.

   ![screen_shot_2018-04-23at111422am](assets/screen_shot_2018-04-23at111422am.png)

   >[!NOTE]
   >
   >Para aprender en detalle sobre cómo
   >
   >* Cree un proyecto, consulte [Creación de un nuevo proyecto](creating-a-screens-project.md).
   >* Cree y agregue contenido a un canal, consulte [Administración de canales](managing-channels.md).


1. Haga clic en **Editar** para abrir el editor de canales y seleccionar el recurso al que desee aplicar la programación.

   ![screen_shot_2018-04-24at90434pm](assets/screen_shot_2018-04-24at90434pm.png)

1. Seleccione el recurso y haga clic en el icono **Configurar** de la parte superior izquierda para abrir las propiedades de la imagen.

   Click the **Activation** tab.

   ![screen_shot_2018-04-23at112348am](assets/screen_shot_2018-04-23at112348am.png)

1. Puede especificar la fecha desde el selector de fechas desde los campos **Activo desde** y **Activo hasta** .

   Si selecciona **Activo desde** y **Activo hasta** la fecha y la hora, el recurso se mostrará y se reproducirá en bucle únicamente entre esa fecha y hora de inicio y la fecha y hora de finalización, respectivamente.

   ![screen_shot_2018-04-23at113545am](assets/screen_shot_2018-04-23at113545am.png)

## Gestión de periodicidad en recursos {#handling-recurrence-in-assets}

Puede programar los recursos para que se repitan a determinados intervalos de forma diaria, semanal o mensual, según sus necesidades.

Supongamos que desea mostrar una imagen sólo los viernes de 1:00 a 22:00. Puede utilizar la ficha Activación para establecer el intervalo recurrente deseado para el recurso.

### Adición de un evento recurrente para el recurso {#adding-a-recurring-event-for-your-asset}

1. Seleccione el recurso y haga clic en el icono **Configurar** para abrir el cuadro de diálogo de propiedades.
1. Después de introducir la fecha/hora de inicio y la hora de finalización/fecha, puede utilizar una expresión cron o una versión de texto natural para especificar la programación de periodicidad.

   Puede buscar en la web un generador de expresiones cron gratuitas y, a continuación, copiar y pegar la expresión cron en la **programación** y el recurso se mostrará para el intervalo de día y hora concreto.

   *Como alternativa*, en lugar de utilizar la expresión cron, también puede utilizar la versión de texto natural, como *después de las 6:00 y antes de las 18:00* del viernes, para realizar la tarea. Introduzca el texto en la **programación** para mostrar el recurso.

## Programación de varios recursos {#multi-asset-scheduling}

>[!CAUTION]
>
>La función de programación **de** varios recursos solo está disponible si ha instalado AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

***La programación*** de varios recursos permite al usuario seleccionar varios recursos y aplicar una programación de reproducción a todos los recursos seleccionados.

### Requisitos previos {#prerequisites}

Para utilizar la programación de varios recursos para sus recursos, cree un proyecto de AEM Screens con un canal de secuencia. Por ejemplo, el siguiente caso de uso muestra la implementación de la función:

* Creación de un proyecto de AEM Screens con el título **MultiAssetDemo**
* Cree un canal denominado **MultiAssetChannel** y agregue contenido al canal, como se muestra en la figura siguiente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga los pasos a continuación para seleccionar varios recursos y programar su visualización en un proyecto de AEM Screens:

1. Select **MultiAssetChannel** and click **Edit** from the action bar to open the editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Seleccione varios recursos en el editor y haga clic en **Editar activación** (icono superior izquierdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Seleccione la fecha y la hora en **Activo desde** y **Activo hasta** en el cuadro de diálogo Activación **de** componentes. Haga clic en el icono de marca de verificación cuando haya terminado de seleccionar los programas.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Haga clic en Actualizar para comprobar los recursos a los que se ha aplicado la programación de varios recursos.

   >[!NOTE]
   >
   >El icono de programación está visible en la esquina superior derecha para aquellos recursos que tienen una programación de varios recursos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

