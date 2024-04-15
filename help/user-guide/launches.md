---
title: Actualización de contenido mediante Screens Launch
description: Aprenda a crear una versión futura de los canales, conocida como Launch, y a establecer una fecha de lanzamiento para que el contenido se publique en dispositivos o reproductores.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 0%

---

# Actualización de contenido mediante Screens Launch {#launches}

Los autores de contenido pueden crear una versión futura de los canales, conocida como **Lanzamiento de Screens** y establezca la fecha de lanzamiento de este lanzamiento. Esto permite que el contenido esté activo en dispositivos o reproductores en la fecha de lanzamiento especificada.

Con la ayuda de ***Lanzamiento de Screens*** Por lo tanto, los autores pueden obtener una vista previa de cada canal en el lanzamiento y deben poder iniciar una solicitud de revisión. El grupo de aprobadores recibe una notificación y puede aprobar o rechazar la solicitud. Cuando se llega a la fecha de lanzamiento, el contenido se reproduce en los dispositivos.

Por ejemplo, si el autor desea crear versiones futuras de c1, c2 (canales), se crea un lanzamiento y se establece una fecha de lanzamiento (por ejemplo, 10 de noviembre a las 8:00 a.m.). Cualquier otra actualización del contenido se envía para su revisión.

Después de la aprobación y en la fecha de lanzamiento (10 de noviembre a las 8:00 a.m.), este lanzamiento reproduce el contenido en los dispositivos o reproductores.

## Requisitos  {#requirements}

Antes de empezar a usar *Lanzamiento de Screens* en un proyecto de AEM Screens, asegúrese de comprender el concepto de Período de gracia y su importancia.

La ejecución de una experiencia en la fecha en directo establecida en el reproductor implica:

* Promoción del lanzamiento (normalmente tarda unos segundos).

* La publicación de los recursos en instancias de publicación (normalmente tarda unos minutos, depende del tamaño de los canales o recursos que se deban publicar).

* Tiempo que tarda la actualización en completarse el contenido sin conexión (normalmente tarda unos minutos).

* Tiempo que tardan los reproductores en descargar el contenido de la instancia de publicación (normalmente tarda minutos en función del ancho de banda y el tamaño de los recursos que se deben descargar).

* Diferencias en cualquier momento entre el servidor y el reproductor.

### Comprender el período de gracia {#understanding-grace-period}

Para que el reproductor pueda empezar a reproducir el contenido en la fecha en directo establecida, inicie las actividades anteriores a la fecha en directo.

Si la fecha de lanzamiento es *24 de noviembre, 9:00 a.m.* y el periodo de gracia es *24 horas*, la secuencia de acciones anterior comenzará a las (fecha de lanzamiento - período de gracia), es decir, el 23 de noviembre a las 9:00 a.m. hora del servidor. Esto da 24 horas para completar todas las acciones mencionadas anteriormente para que el contenido llegue a los reproductores. Los reproductores entienden que se trata de un contenido de lanzamiento. Como tal, el contenido no se reproduce inmediatamente, pero los reproductores pueden almacenar este contenido como una versión futura y hacer que comience a reproducirse exactamente en la fecha en directo establecida en la zona horaria del reproductor.

Por ejemplo, el servidor está en PST y los dispositivos en EST. La diferencia de tiempo máxima es de tres horas en este caso y supone que la promoción tarda 1 minuto y la publicación del autor a la publicación tarda 10 minutos y que el reproductor puede descargar los recursos normalmente en 10-15 minutos. A continuación, el periodo de gracia = diferencia horaria (tres horas):

* Más tiempo para promocionar el lanzamiento (1 minuto)
* Más tiempo para publicar el lanzamiento (10 minutos)
* Más tiempo para descargar en el reproductor (10-15 minutos)
* Más búfer (30 minutos)

Es igual a 3 horas 56 minutos (14160 segundos).

Por lo tanto, cada vez que programe un lanzamiento en directo, la promoción comienza antes por este desplazamiento. En la ecuación anterior, la mayoría de los elementos no tardan mucho tiempo. Puede utilizar una suposición decente para este desplazamiento cuando conozca la diferencia de tiempo máxima entre el servidor y cualquier reproductor.

>[!NOTE]
>
>De forma predeterminada, el periodo de gracia de Screens Launch se establece en 24 horas. Esto significa que, cuando se establece la fecha de lanzamiento de cualquier recurso en */content/screens*, la promoción comienza con este desplazamiento.

### Actualización del período de gracia listo para usar {#updating-out-of-the-box-grace-period}

En esta sección se explica cómo actualizar un periodo de gracia predeterminado a 10 minutos.

1. Vaya a CRXDE Lite y, a continuación, a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Haga clic con el botón derecho y copie el archivo.
1. Vaya a `/apps/system/config` y haga clic con el botón derecho y pegue.
1. Doble clic `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para poder abrir el archivo en el editor en CRXDE Lite. Debe mostrar el periodo de gracia de la ruta */content/screens/* as **86400**. Cambie ese valor a **600**.

Ahora, el contenido del archivo de texto debería tener un aspecto similar al siguiente:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Puesto que en el ejemplo anterior había establecido el Período de gracia en 10 minutos, al establecer la fecha de lanzamiento de cualquier lanzamiento de los recursos en */content/screens*, la promoción comienza con este desplazamiento.

Por ejemplo, si la fecha de lanzamiento se establece en 24 de noviembre a las 9:00 a.m. y el periodo de gracia es de 600 segundos, el trabajo de promoción se iniciará el 24 de noviembre a las 8:50 a.m.

## Uso de Screens Launch {#using-launches}

Esta sección muestra cómo implementar Screens Launch en un proyecto de AEM Screens.

### Creación de un lanzamiento de Screens {#creating-a-launch}

Siga los pasos a continuación para implementar la funcionalidad de Screens Launch en su proyecto de AEM Screens:

1. Cree un canal de secuencia en su proyecto de AEM Screens, por ejemplo **LaunchesDemo** > **Canales** > **FutureLaunch**, como se muestra a continuación.

   >[!CAUTION]
   >
   >Cree un lanzamiento a partir de un canal preexistente en su proyecto de AEM Screens.

   ![Imagen](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleccione el canal **FutureLaunch** y haga clic en **Crear lanzamiento** de la barra de acciones.

   ![Imagen](/help/user-guide/assets/launches-images/launches-12.png)

1. El **Crear lanzamiento** se abre el asistente. Puede seleccionar el canal que ya está visible en el asistente o hacer clic en **+ Agregar canales** para añadir el canal para el que desea crear el lanzamiento.

1. Clic **Siguiente** desde el **Crear lanzamiento** asistente. El **Incluir subpáginas** está seleccionada de forma predeterminada.

   ![imagen](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Puede utilizar **+ Agregar canales** para añadir otro canal para el que desee crear el lanzamiento.

   Para usar **Agregar canales** , vaya al canal para el que desea crear el lanzamiento y haga clic en **Seleccionar**.

   El **Seleccionar** Esta opción está desactivada si intenta seleccionar varios canales o una carpeta para añadir el lanzamiento.

   ![imagen](/help/user-guide/assets/launches-images/launches-14.png)

   Después de seleccionar el canal o los canales, haga clic en **Siguiente**.


1. Introduzca el **Título del lanzamiento** as **SummerPromotions** y no es necesario configurar el **Fecha de lanzamiento**, como se muestra en la figura siguiente. Haga clic en **Crear**.

   >[!NOTE]
   >
   >*Activación o comprobación* la opción **Heredar datos activos de la página de origen** permite crear los canales como Live Copies en el lanzamiento. Si se realizan cambios en el canal original, estos se aplican automáticamente a los canales de lanzamiento.
   >
   >
   >*Desactivación o desactivación* **Heredar datos activos de la página de origen** permite copiar los canales sin ninguna relación activa en el lanzamiento. Por lo tanto, si se realizan cambios en el canal original, estos cambios no se aplican a los canales de lanzamiento.

   ![Imagen](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puede establecer la fecha de lanzamiento activo en este paso o puede configurarla más adelante mientras edita las propiedades del lanzamiento una vez que ya se ha creado.

   **Explicación del ámbito de promoción de Launch**

   * **Promocionar lanzamiento completo** - Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocionar páginas modificadas** - Solo se promocionan los recursos de lanzamiento modificados. Utilice esta opción cuando no sea necesario realizar una revisión del lanzamiento.
   * **Promocionar páginas aprobadas** : Esta opción requiere que el flujo de trabajo de aprobación del inicio se ejecute en los canales de inicio. Solo las páginas aprobadas se promocionan en la fecha de activación establecida.

     >[!CAUTION]
     >
     >La fecha de lanzamiento respeta la zona horaria del reproductor/dispositivo en lugar de la del servidor.

1. Verá que el lanzamiento se ha creado. Puede seleccionar **Abrir** para ver las páginas en el editor o seleccione **Listo** para volver al proyecto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Seleccionar **Listo** le permite volver a su **FutureLaunch** canal.

   ![Imagen](/help/user-guide/assets/launches-images/launches-16.png)


### Edición de las propiedades de Launch para establecer la fecha de lanzamiento y el ámbito {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Una vez creado el lanzamiento, puede actualizar las propiedades como la fecha de lanzamiento, el título del lanzamiento y el ámbito de la promoción utilizando **Propiedades del lanzamiento**.

* **Fecha de lanzamiento** : La fecha en directo, es decir, la fecha o la hora en que se reproduce el contenido en el reproductor de Screens según la zona horaria del reproductor.
* **Producción lista** : Permite que los canales se publiquen después de promocionarlos, ya que esta opción está habilitada, por lo que no es necesario cambiarla.
* **Ámbito** - Decide qué canales se promocionan durante la promoción de lanzamiento.

Siga los pasos a continuación para editar las propiedades de Launch:

1. Navegar al canal **FutureLaunch** *(el lanzamiento pendiente)* y seleccione el canal como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/launches-images/launches-17.png)

1. Seleccionar **Tablero** de la barra de acciones y verá el **INICIOS PENDIENTES** panel desde el panel de canal.

   ![imagen](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleccione el lanzamiento y haga clic en **Propiedades del lanzamiento** desde el **INICIOS PENDIENTES** panel.

   ![imagen](/help/user-guide/assets/launches-images/launches-19.png)

### Edición del lanzamiento de Screens para añadir o quitar canales  {#editing-the-screens-launch-to-add-or-remove-channels}

Una vez creado el lanzamiento, puede añadir o quitar canales al lanzamiento existente mediante **Editar lanzamiento** opción.

Cuando haya terminado, seleccione **Guardar** para volver a navegar a **FutureLaunch** canal.

### Promoción manual del lanzamiento de Screens{#promote-the-screens-launch-manually}

Puede promocionar el lanzamiento manualmente con la variable **`Promote Launch`** de la opción **INICIOS PENDIENTES** panel.

Puede elegir los recursos que desea promocionar como parte de esta promoción manual en la **Iniciar el Asistente para promociones**.

![imagen](/help/user-guide/assets/launches-images/launches-e.png)

1. Puede activar o desactivar la opción para eliminar el lanzamiento después de la producción.
1. Puede configurar las variables **Ámbito** del lanzamiento con las siguientes opciones:
   * **Promocionar lanzamiento completo** - Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocionar páginas modificadas** - Solo se promocionan los recursos de lanzamiento modificados. Utilice esta opción cuando no sea necesario realizar una revisión del lanzamiento.
   * **Promocionar páginas aprobadas** : Esta opción requiere que el flujo de trabajo de aprobación del inicio se ejecute en los canales de inicio. Solo las páginas aprobadas se promocionan en la fecha de activación establecida.
   * **Promocionar página actual** : Esta opción requiere que el flujo de trabajo de aprobación de lanzamiento se ejecute únicamente para la página actual.
1. Seleccionar **Siguiente** en el **Promocionar lanzamiento** asistente.
1. Seleccionar **Promocionar** para promocionar el lanzamiento.

### Eliminación del lanzamiento de Screens

Puede eliminar el lanzamiento mediante **Eliminar lanzamiento** de la opción **INICIOS PENDIENTES** panel.

>[!CAUTION]
>
>Esta acción también elimina todos los descendientes (lanzamientos anidados).
