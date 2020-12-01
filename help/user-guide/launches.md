---
title: Actualización de contenido con Screens Launch
seo-title: Actualización de contenido con Screens Launch
description: Los creadores de contenido pueden crear versiones futuras de los canales, conocidas como Launch, y una fecha de lanzamiento posterior para este lanzamiento permite que el contenido esté activo en dispositivos o reproductores.
seo-description: Los creadores de contenido pueden crear versiones futuras de los canales, conocidas como Launch, y una fecha de lanzamiento posterior para este lanzamiento permite que el contenido esté activo en dispositivos o reproductores.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---


# Actualización de contenido mediante Screens Launch {#launches}

Los autores de contenido pueden crear versiones futuras de los canales, conocidas como **Screens Launch** y establecer la fecha de lanzamiento para este lanzamiento. Esto permite que el contenido esté activo en dispositivos o reproductores en la fecha de lanzamiento especificada.

Con la ayuda de ***Screens Launch***, los autores pueden realizar previsualizaciones de cada canal en el lanzamiento y deben poder iniciar una solicitud de revisión. El grupo Aprobadores recibirá una notificación y puede aprobar o rechazar la solicitud. Cuando se alcanza la fecha de lanzamiento, el contenido se reproduce en los dispositivos.

Por ejemplo, si el autor desea crear versiones futuras de c1, c2 (canales), se crea un lanzamiento y se establece una fecha de lanzamiento (por ejemplo, 10 de noviembre a las 8:00 a.m.). Cualquier otra actualización del contenido se envía para su revisión.

Una vez aprobado y en fecha de lanzamiento (10 de noviembre, 8:00 AM), este lanzamiento reproduce el contenido en los dispositivos o reproductores.

## Requisitos {#requirements}

Antes de inicio de aprovechar *Screens Launch* en un proyecto de AEM Screens, asegúrese de comprender el concepto de período de gracia y su relevancia.

La ejecución de una experiencia en la fecha de lanzamiento establecida en el reproductor implica:

* promoción del lanzamiento (normalmente tarda unos segundos)

* publicar los recursos para publicar instancias (normalmente tarda unos minutos, depende del tamaño de los canales o recursos que deban publicarse)

* tiempo que tarda la actualización en completarse (suele tardar unos minutos)

* el tiempo que tardan los reproductores en descargar el contenido de la instancia de publicación (normalmente tarda unos minutos en función del ancho de banda y el tamaño de los recursos que deben descargarse)

* diferencias de tiempo del servidor y del reproductor

### Explicación del período de gracia {#understanding-grace-period}

Para que el reproductor pueda reproducir en inicio el contenido en la fecha de lanzamiento establecida, necesitamos inicios de las actividades anteriores antes de la fecha de lanzamiento.

Si la fecha de lanzamiento es *24 de noviembre, 9:00 AM* y el período de gracia es *24 horas*, la secuencia de acciones anterior se inicio en (fecha de lanzamiento - período de gracia), es decir, 23 de noviembre, 9:00 AM hora del servidor. Esto da 24 horas de tiempo para completar todas las acciones mencionadas anteriormente y el contenido llegará a los jugadores. Los jugadores comprenderán que se trata de un contenido de inicio, por lo que el contenido no se reproducirá inmediatamente, pero los reproductores almacenarán este contenido como una versión futura y tendrán el inicio de reproducirse exactamente en la fecha de lanzamiento establecida en el huso horario del reproductor.

Por ejemplo: supongamos que el servidor está en PST y que los dispositivos están en EST, la diferencia máxima de tiempo es de 3 horas en este caso y supongamos que la promoción tardará 1 minuto y que la publicación del autor tarda 10 minutos y que el reproductor puede descargar los recursos normalmente en 10-15 minutos. Entonces período de gracia = diferencia de tiempo (3 horas) + tiempo para promocionar el lanzamiento (1 min) + tiempo para publicar el lanzamiento (10 min) + tiempo para descargar en el reproductor (10-15 min) + buffer (para ser seguro, digamos 30 min) = 3 horas 56 min = 14160 segundos.

Así que, cada vez que programamos un lanzamiento en vivo, el inicio de la promoción se hará pronto con este desplazamiento. En la ecuación anterior, la mayoría de los elementos no toma mucho tiempo, podemos usar una estimación decente para este desplazamiento una vez que sepamos la máxima diferencia de tiempo entre el servidor y cualquier reproductor.

>[!NOTE]
>
>De forma predeterminada, el período de gracia para el lanzamiento de pantallas se establece en 24 horas, lo que significa que cuando se establece la fecha de lanzamiento para cualquier inicio de los recursos en */content/screen*, la promoción contraerá este inicio.

### Actualización del período de gracia predeterminado {#updating-out-of-the-box-grace-period}

En esta sección se explica cómo puede actualizar un período de gracia predeterminado a 10 minutos.

1. Vaya al CRXDE Lite y luego a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Haga clic con el botón derecho y copie el archivo.
3. Vaya a `/apps/system/config` y haga clic con el botón derecho y pegue.
4. Doble haga clic en `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir el archivo en el editor en CRXDE Lite. Debe mostrar el período de gracia para la ruta */content/screen/* como **86400**. Cambie ese valor a **600**.

Ahora, el contenido del archivo de texto debe tener un aspecto similar a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Dado que el período de gracia se ha establecido en 10 minutos en el ejemplo anterior, cuando se establece la fecha de lanzamiento para cualquier inicio de los recursos en */content/screen*, la promoción contraerá este desplazamiento.

Por ejemplo, si la fecha de lanzamiento se establece como 24 de noviembre, 9:00 AM y el período de gracia es de 600 segundos, el trabajo de promoción se inicio el 24 de noviembre a las 8:50 AM.

## Uso de Screens Launch {#using-launches}

Esta sección muestra cómo implementar Screens Launch en el proyecto de AEM Screens.

### Creación de un lanzamiento de pantalla {#creating-a-launch}

Siga los pasos que se describen a continuación para implementar la funcionalidad Screens Launch en el proyecto de AEM Screens:

1. Cree un canal de secuencia en su proyecto de AEM Screens, por ejemplo **LaunchesDemo** —> **Canales** —> **FutureLaunch**, como se muestra a continuación.

   >[!CAUTION]
   >
   >Debe crear un inicio a partir de un canal preexistente en el proyecto de AEM Screens.

   ![Imagen](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleccione el canal **FutureLaunch** y haga clic en **Crear lanzamiento** en la barra de acciones.

   ![Imagen](/help/user-guide/assets/launches-images/launches-12.png)

1. Se abre el asistente **Crear inicio**. Puede seleccionar el canal que ya está visible en el asistente o hacer clic en **+ Añadir Canales** para agregar el canal para el que desea crear el lanzamiento.

1. Haga clic en **Siguiente** desde el asistente **Crear inicio**. La opción **Incluir subpáginas** está seleccionada de forma predeterminada.

   ![image](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Puede utilizar la opción **+ Añadir Canales** para agregar otro canal para el cual desee crear el lanzamiento.

   Para utilizar la opción **Añadir Canales**, desplácese hasta el canal para el que desea crear el lanzamiento y haga clic en **Seleccionar**.

   La opción **Seleccionar** se desactivará si intenta seleccionar varios canales o una carpeta para agregar el lanzamiento.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

   Una vez que haya seleccionado el canal o los canales, haga clic en **Siguiente**.


1. Escriba el **Título de inicio** como **Promociones de verano** y no necesita establecer la **Fecha de inicio**, como se muestra en la figura siguiente. Haga clic en **Crear**.

   >[!NOTE]
   >
   >*Al habilitar o* comprobar la opción  **Heredar** datos activos de la página de origen, los canales se pueden crear como copias en vivo en el lanzamiento. Si se realizan cambios en el canal original, dichos cambios se aplican automáticamente a los canales de inicio.
   >
   >
   >*Deshabilitar o* **desmarcarHeredar** datos activos de la página de origen permite copiar los canales sin ninguna relación activa durante el lanzamiento. Por lo tanto, si se realizan cambios en el canal original, esos cambios no se aplican a los canales de inicio.

   ![Imagen](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puede establecer la fecha de lanzamiento activo en este paso o puede configurarla más tarde mientras edita las propiedades del lanzamiento una vez que ya se ha creado.

   **Explicación del ámbito de la promoción de lanzamiento**

   * **Promocione el lanzamiento** completo: Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocione las páginas** modificadas: Solo se promocionarán los recursos de inicio modificados. Se recomienda utilizar esta opción cuando no se requiera la revisión del inicio.
   * **Promocione las páginas** aprobadas: Esta opción requiere que el flujo de trabajo de aprobación de inicio se ejecute en los canales de inicio. Solo se promocionarán las páginas aprobadas en la fecha de lanzamiento establecida.

      >[!CAUTION]
      >
      >Iniciar la fecha de lanzamiento respeta la zona horaria del reproductor/dispositivo en lugar de la del servidor.

1. Verá que se ha creado el lanzamiento. Puede hacer clic en **Abrir** para vista de las páginas en el editor o en **Listo** para volver al proyecto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Al hacer clic en **Listo** puede volver al canal **FutureLaunch**.

   ![Imagen](/help/user-guide/assets/launches-images/launches-16.png)


### Edición de las propiedades de inicio para establecer la fecha de lanzamiento y el ámbito {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Una vez creado el lanzamiento, puede actualizar las propiedades como fecha de lanzamiento, título de inicio y ámbito de promoción mediante **Propiedades de inicio**.

* **Fecha** de lanzamiento, hace referencia a la fecha de lanzamiento, es decir, la fecha o hora en que el contenido se reproducirá en el reproductor de pantallas según la zona horaria del reproductor.
* **Listo** para producción, permite que los canales se publiquen después de promocionarlos, ya que está activado, por lo que no es necesario cambiarlos.
* **Ámbito**, decide qué canales se promoverán durante la promoción de lanzamiento.


Siga los pasos a continuación para editar las propiedades de inicio:

1. Vaya al canal **FutureLaunch**, *(que es el lanzamiento pendiente)* y seleccione el canal, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Haga clic en **Panel** desde la barra de acciones y verá el panel **INICIOS PENDIENTES** desde el panel de canal.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleccione el inicio y haga clic en **Propiedades de inicio** en el panel **INICIOS PENDIENTES**.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

### Edición del lanzamiento de pantallas para Añadir o eliminar Canales {#editing-the-screens-launch-to-add-or-remove-channels}

Después de crear el lanzamiento, puede agregar o quitar canales al inicio existente mediante la opción **Editar inicio**.

Una vez que haya terminado, haga clic en **Guardar** para volver al **canal de FutureLaunch**.

### Promoción manual del lanzamiento de pantallas{#promote-the-screens-launch-manually}

Puede promocionar el lanzamiento manualmente mediante la opción **Promote Launch** del panel **PENDING LAUNCHES**.

Puede elegir los recursos que desee promocionar como parte de esta promoción manual en el **Asistente para promoción de inicio**.

![image](/help/user-guide/assets/launches-images/launches-e.png)

1. Puede activar o desactivar la opción para eliminar el lanzamiento después de la producción.
1. Puede configurar el **Ámbito** del lanzamiento, con las siguientes opciones:
   1. **Promocione el lanzamiento** completo: Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   1. **Promocione las páginas** modificadas: Solo se promocionarán los recursos de inicio modificados. Se recomienda utilizar esta opción cuando no se requiera la revisión del inicio.
   1. **Promocione las páginas** aprobadas: Esta opción requiere que el flujo de trabajo de aprobación de inicio se ejecute en los canales de inicio. Solo se promocionarán las páginas aprobadas en la fecha de lanzamiento establecida.
   1. **Promocione la página** actual: Esta opción requiere que el flujo de trabajo de aprobación de inicio se ejecute solamente para la página actual.
1. Haga clic en **Siguiente** en el asistente **Promote Launch**.
1. Haga clic en **Promocionar** para promocionar el lanzamiento.

### Eliminación del lanzamiento de pantallas {#deleting-the-screens-launch}

Puede eliminar el lanzamiento mediante la opción **Eliminar inicio** del panel **INICIOS PENDIENTES**.

>[!CAUTION]
>
>Esta acción también eliminará todos los descendientes (inicios anidados).

