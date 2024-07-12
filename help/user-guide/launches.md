---
title: Actualización de contenido con Screens Launch
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
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---

# Actualización de contenido con Screens Launch {#launches}

Los autores de contenido pueden crear una versión futura de los canales y establecer la fecha de lanzamiento. Esta capacidad permite que el contenido esté activo en dispositivos o reproductores en la fecha en directo especificada.

Con la ayuda de ***Screens Launch***, los autores pueden obtener una vista previa de cada canal en el lanzamiento y deben poder iniciar una solicitud de revisión. El grupo de aprobadores recibe una notificación y puede aprobar o rechazar la solicitud. Cuando se llega a la fecha de lanzamiento, el contenido se reproduce en los dispositivos.

Por ejemplo, si el autor desea crear versiones futuras de c1, c2 (canales), se crea un lanzamiento y se establece una fecha de lanzamiento (por ejemplo, 10 de noviembre a las 8:00 a.m.). Cualquier otra actualización del contenido se envía para su revisión.

Después de la aprobación y en la fecha de lanzamiento (10 de noviembre a las 8:00 a.m.), este lanzamiento reproduce el contenido en los dispositivos o reproductores.

## Requisitos  {#requirements}

Antes de empezar a usar *Screens Launch* en un proyecto de AEM Screens, asegúrese de comprender el concepto de período de gracia y su relevancia.

La ejecución de una experiencia en la fecha en directo establecida en el reproductor implica:

* Promoción del lanzamiento (normalmente tarda unos segundos).

* La publicación de los recursos en instancias de publicación (normalmente tarda unos minutos, depende del tamaño de los canales o recursos que se deban publicar).

* Tiempo que tarda en completarse la actualización del contenido sin conexión (normalmente tarda unos minutos).

* Tiempo que tardan los reproductores en descargar el contenido de la instancia de publicación (normalmente tarda minutos en función del ancho de banda y el tamaño de los recursos que se deben descargar).

* Diferencias en cualquier momento entre el servidor y el reproductor.

### Comprender el período de gracia {#understanding-grace-period}

Para que el reproductor pueda empezar a reproducir el contenido en la fecha en directo establecida, inicie las actividades anteriores a la fecha en directo.

Si la fecha de activación es el *24 de noviembre a las 9:00 a.m.* y *24 horas* es el período de gracia, la secuencia de acciones anterior comienza en (fecha de activación - período de gracia), es decir, el 23 de noviembre a las 9:00 a.m. hora del servidor. Esta configuración proporciona 24 horas para completar todas las acciones mencionadas anteriormente para que el contenido llegue a los reproductores. Los jugadores entienden que este periodo es un contenido de lanzamiento. Como tal, el contenido no se reproduce inmediatamente, pero los reproductores pueden almacenar este contenido como una versión futura y hacer que comience a reproducirse exactamente en la fecha en directo establecida en la zona horaria del reproductor.

Por ejemplo, el servidor está en PST y los dispositivos en EST. La diferencia de tiempo máxima es de tres horas. Supone que la promoción tarda 1 minuto y la publicación del autor a la publicación tarda 10 minutos y que el reproductor puede descargar los recursos normalmente en 10-15 minutos. A continuación, el periodo de gracia = diferencia horaria (tres horas):

* Más tiempo para promocionar el lanzamiento (1 minuto)
* Más tiempo para publicar el lanzamiento (10 minutos)
* Más tiempo para descargar en el reproductor (10-15 minutos)
* Más búfer (30 minutos)

Por lo tanto, 3 horas y 56 minutos (14160 segundos).

Por lo tanto, cada vez que se programa un lanzamiento activo, la promoción comienza antes teniendo en cuenta este desplazamiento. En la ecuación anterior, la mayoría de los elementos no tardan mucho tiempo. Puede utilizar una suposición decente para este desplazamiento cuando conozca la diferencia de tiempo máxima entre el servidor y cualquier reproductor.

>[!NOTE]
>
>De forma predeterminada, el período de gracia de Screens Launch se establece en 24 horas. Esto significa que cuando establece una fecha de lanzamiento para cualquier lanzamiento de los recursos en */content/screens*, la promoción comienza con este desplazamiento.

### Actualización del periodo de gracia predeterminado {#updating-out-of-the-box-grace-period}

En esta sección se explica cómo actualizar un periodo de gracia predeterminado a 10 minutos.

1. Vaya al CRXDE Lite y luego a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Haga clic con el botón derecho y copie el archivo.
1. Vaya a `/apps/system/config`, haga clic con el botón derecho y pegue.
1. Haga doble clic en `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para poder abrir el archivo en el editor en CRXDE Lite. Debe mostrar el período de gracia para la ruta de acceso */content/screens/* como **86400**. Cambie ese valor a **600**.

Ahora, el contenido del archivo de texto debería tener un aspecto similar al siguiente:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

El período de gracia se establece en 10 minutos en el ejemplo anterior. Por lo tanto, cuando establece una fecha de lanzamiento para cualquier lanzamiento de recursos en */content/screens*, la promoción comienza con este desplazamiento.

Por ejemplo, si la fecha de lanzamiento se establece en 24 de noviembre a las 9:00 a.m. y el período de gracia es de 600 segundos, el trabajo de promoción se iniciará el 24 de noviembre a las 8:50 a.m.

## Uso de Screens Launch {#using-launches}

Esta sección muestra cómo implementar Screens Launch en un proyecto de AEM Screens.

### Creación de un lanzamiento de Screens {#creating-a-launch}

Siga los pasos a continuación para implementar la funcionalidad de Screens Launch en su proyecto de AEM Screens:

1. Cree un canal de secuencia en su proyecto de AEM Screens, por ejemplo **LaunchesDemo** > **Canales** > **FutureLaunch**, como se muestra a continuación.

   >[!CAUTION]
   >
   >Cree un lanzamiento a partir de un canal preexistente en su proyecto de AEM Screens.

   ![Imagen](/help/user-guide/assets/launches-images/launches-11.png)

1. Haga clic en el canal **FutureLaunch** y luego haga clic en **Crear lanzamiento** en la barra de acciones.

   ![Imagen](/help/user-guide/assets/launches-images/launches-12.png)

1. Se abre el asistente **Crear lanzamiento**. Puede hacer clic en el canal que ya está visible en el asistente o hacer clic en **+ Agregar canales** para agregar el canal para el que desea crear el lanzamiento.

1. Haga clic en **Siguiente** en el asistente para **Crear lanzamiento**. La opción **Incluir subpáginas** está seleccionada de forma predeterminada.

   ![imagen](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Puede usar la opción **+ Agregar canales** para agregar otro canal para el que desee crear el lanzamiento.

   Para usar la opción **Agregar canales**, vaya al canal para el que desea crear el lanzamiento y haga clic en **Seleccionar**.

   La opción **Select** está deshabilitada si intenta hacer clic en varios canales o en una carpeta para agregar el lanzamiento.

   ![imagen](/help/user-guide/assets/launches-images/launches-14.png)

   Después de hacer clic en el canal o canales, haga clic en **Siguiente**.


1. Escriba **Launch Title** como **SummerPromotions** y no necesita establecer la **fecha de lanzamiento**, como se muestra en la figura siguiente. Haga clic en **Crear**.

   >[!NOTE]
   >
   >*Habilitar o comprobar* la opción **Heredar datos activos de la página de origen** permite crear los canales como Live Copies en el lanzamiento. Si se realizan cambios en el canal original, estos se aplican automáticamente a los canales de lanzamiento.
   >
   >
   >*Deshabilitar o desmarcar* **Heredar datos activos de la página de origen** permite que los canales se copien sin ninguna relación activa en el lanzamiento. Por lo tanto, si se realizan cambios en el canal original, estos cambios no se aplican a los canales de lanzamiento.

   ![Imagen](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puede establecer la fecha de lanzamiento activo en este paso o puede configurarla más adelante mientras edita las propiedades del lanzamiento una vez que ya se ha creado.

   **Explicación del ámbito de la promoción de lanzamiento**

   * **Promocionar lanzamiento completo**: todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocionar páginas modificadas**: solo se promocionan los recursos de lanzamiento modificados. Utilice esta opción cuando no sea necesario realizar una revisión del lanzamiento.
   * **Promocionar páginas aprobadas**: esta opción requiere que el flujo de trabajo de aprobación del inicio se ejecute en los canales de lanzamiento. Solo las páginas aprobadas se promocionan en la fecha de activación establecida.

     >[!CAUTION]
     >
     >La fecha de lanzamiento respeta la zona horaria del reproductor/dispositivo en lugar de los servidores.

1. Verá que el lanzamiento se ha creado. Puede hacer clic en **Abrir** para ver las páginas en el editor o hacer clic en **Listo** para regresar a su proyecto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Si seleccionas **Listo**, podrás volver a tu canal de **FutureLaunch**.

   ![Imagen](/help/user-guide/assets/launches-images/launches-16.png)


### Edición de las propiedades de Launch para establecer la fecha de lanzamiento y el ámbito {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Una vez creado el lanzamiento, puede actualizar las propiedades como la fecha de lanzamiento, el título del lanzamiento y el ámbito de la promoción mediante **Propiedades del lanzamiento**.

* **Fecha de lanzamiento** - La fecha en vivo, es decir, la fecha o la hora en que se reproduce el contenido en el reproductor Screens según la zona horaria del reproductor.
* **Listo para la producción**: después de la promoción, permite que se publiquen los canales y está habilitado de forma predeterminada, por lo que no es necesario cambiarlo.
* **Ámbito**: decide qué canales se promocionan durante la promoción de lanzamiento.

Siga los pasos a continuación para editar las propiedades de Launch:

1. Vaya al canal **FutureLaunch** *(el lanzamiento pendiente)* y haga clic en el canal como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/launches-images/launches-17.png)

1. Haga clic en **Tablero** en la barra de acciones y verá el panel **LANZAMIENTOS PENDIENTES** desde el tablero del canal.

   ![imagen](/help/user-guide/assets/launches-images/launches-18.png)

1. Haga clic en el lanzamiento y luego en **Propiedades del lanzamiento** en el panel **LANZAMIENTOS PENDIENTES**.

   ![imagen](/help/user-guide/assets/launches-images/launches-19.png)

### Edición del lanzamiento de Screens para añadir o quitar canales {#editing-the-screens-launch-to-add-or-remove-channels}

Una vez creado el lanzamiento, puede agregar o quitar canales al lanzamiento existente mediante la opción **Editar lanzamiento**.

Cuando haya terminado, haga clic en **Guardar** para volver al canal **FutureLaunch**.

### Promoción manual del lanzamiento de Screens{#promote-the-screens-launch-manually}

Puede promocionar el lanzamiento manualmente mediante la opción **`Promote Launch`** desde el panel **LANZAMIENTOS PENDIENTES**.

Puede elegir los recursos que desea promocionar como parte de esta promoción manual en el **Asistente para iniciar promoción**.

![imagen](/help/user-guide/assets/launches-images/launches-e.png)

1. Puede activar o desactivar la opción para eliminar el lanzamiento después de la producción.
1. Puede establecer el **ámbito** del lanzamiento con las siguientes opciones:
   * **Promocionar lanzamiento completo**: todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocionar páginas modificadas**: solo se promocionan los recursos de lanzamiento modificados. Utilice esta opción cuando no sea necesario realizar una revisión del lanzamiento.
   * **Promocionar páginas aprobadas**: esta opción requiere que el flujo de trabajo de aprobación del inicio se ejecute en los canales de lanzamiento. Solo las páginas aprobadas se promocionan en la fecha de activación establecida.
   * **Promocionar página actual**: esta opción requiere que el flujo de trabajo de aprobación de lanzamiento se ejecute solamente para la página actual.
1. Haga clic en **Siguiente** en el asistente de **Promocionar lanzamiento**.
1. Haga clic en **Promocionar** para promocionar el lanzamiento.

### Eliminación de Screens Launch

Puede eliminar el lanzamiento con la opción **Eliminar lanzamiento** del panel **LANZAMIENTOS PENDIENTES**.

>[!CAUTION]
>
>Esta acción también elimina todos los descendientes (lanzamientos anidados).
