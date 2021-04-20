---
title: Actualización de contenido con Screens Launch
seo-title: Actualización de contenido con Screens Launch
description: Los autores de contenido pueden crear una versión futura de los canales, conocidos como Launch, y una fecha de lanzamiento posterior permite que el contenido esté activo en dispositivos o reproductores.
seo-description: Los autores de contenido pueden crear una versión futura de los canales, conocidos como Launch, y una fecha de lanzamiento posterior permite que el contenido esté activo en dispositivos o reproductores.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: Authoring Screens, Launches
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 0%

---


# Actualización de contenido con Screens Launch {#launches}

Los autores de contenido pueden crear una versión futura de los canales, conocidos como **Screens Launch**, y además establecer la fecha de lanzamiento para este lanzamiento. Esto permite que el contenido esté activo en dispositivos o reproductores en la fecha de lanzamiento especificada.

Con la ayuda de ***Screens Launch***, los autores pueden obtener una vista previa de cada canal en el lanzamiento y deben poder iniciar una solicitud de revisión. El grupo de aprobadores recibe una notificación y puede aprobar o rechazar la solicitud. Cuando se llega a la fecha de lanzamiento, el contenido se reproduce en los dispositivos.

Por ejemplo, si el autor desea crear versiones futuras de c1, c2 (canales), se crea un lanzamiento y se establece una fecha de lanzamiento (por ejemplo, el 10 de noviembre a las 8:00 a. m.). Cualquier otra actualización en el contenido se envía para su revisión.

Una vez aprobado y en fecha de lanzamiento (10 de noviembre a las 8:00 a.m.), este lanzamiento reproduce el contenido en los dispositivos o reproductores.

## Requisitos {#requirements}

Antes de comenzar a aprovechar *Screens Launch* en un proyecto de AEM Screens, asegúrese de comprender el concepto de período de gracia y su relevancia.

La ejecución de una experiencia en la fecha de lanzamiento establecida en el reproductor implica:

* promoción del lanzamiento (suele tardar unos segundos)

* publicación de los recursos para publicar instancias (generalmente, tarda unos minutos, depende del tamaño de los canales o recursos que deben publicarse)

* tiempo que tarda la actualización en completarse (normalmente tarda unos minutos)

* tiempo que tardan los reproductores en descargar el contenido de la instancia de publicación (normalmente tardan minutos en depender del ancho de banda y el tamaño de los recursos que deben descargarse)

* diferencias temporales entre el servidor y el reproductor

### Explicación del período de gracia {#understanding-grace-period}

Para que el reproductor pueda comenzar a reproducir el contenido en la fecha de lanzamiento establecida, debemos iniciar las actividades anteriores antes de la fecha de lanzamiento.

Si la fecha de lanzamiento es *24 de noviembre, 9:00 AM* y el período de gracia es *24 horas*, la secuencia de acciones anterior comenzará en (fecha de lanzamiento - período de gracia), es decir, 23 de noviembre, 9:00 AM, hora del servidor. Esto da 24 horas de tiempo para completar todas las acciones mencionadas anteriormente y el contenido llegará a los jugadores. Los reproductores entenderán que se trata de un contenido de lanzamiento, por lo que el contenido no se reproducirá inmediatamente, pero los reproductores almacenarán este contenido como una versión futura y empezarán a reproducirse exactamente en la fecha de lanzamiento establecida en la zona horaria del reproductor.

Por ejemplo, supongamos que el servidor está en PST y que los dispositivos están en EST, la diferencia de tiempo máxima es de 3 horas en este caso y supongamos que la promoción tardará 1 minuto y la publicación de un autor tarda 10 minutos y que el reproductor puede descargar los recursos normalmente en 10-15 minutos. Entonces, período de gracia = diferencia de tiempo (3 horas) + tiempo para promocionar el lanzamiento (1 min) + tiempo para publicar el lanzamiento (10 min) + tiempo para descargar en el reproductor (10-15 min) + búfer (para estar seguro, digamos 30 min) = 3 horas 56 min = 14160 segundos.

Así que, cada vez que programemos un lanzamiento en vivo, la promoción comenzará temprano con este desplazamiento. En la ecuación anterior, la mayoría de los elementos no tardan mucho tiempo, podemos usar una suposición decente para este desplazamiento una vez que sepamos la máxima diferencia de tiempo entre el servidor y cualquier reproductor.

>[!NOTE]
>
>De forma predeterminada, el período de gracia para Screens Launch se establece en 24 horas, lo que significa que, cuando establecemos la fecha de lanzamiento para cualquier lanzamiento de los recursos en */content/screens*, la promoción comenzará con este desplazamiento.

### Actualización del período de gracia predeterminado {#updating-out-of-the-box-grace-period}

En esta sección se explica cómo actualizar un período de gracia predeterminado a 10 minutos.

1. Vaya al CRXDE Lite y, a continuación, a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Haga clic con el botón derecho y copie el archivo.
3. Vaya a `/apps/system/config` y haga clic con el botón derecho y pegue.
4. Haga doble clic en `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir el archivo en el editor del CRXDE Lite. Debe mostrar el período de gracia de la ruta */content/screens/* como **86400**. Cambie ese valor a **600**.

Ahora el contenido del archivo de texto debería tener un aspecto similar al siguiente:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Como en el ejemplo anterior ha establecido el período de gracia en 10 minutos, cuando establece la fecha de lanzamiento para cualquier lanzamiento de los recursos en */content/screens*, la promoción comenzará con este desplazamiento.

Por ejemplo, si la fecha de lanzamiento se establece en 24 de noviembre a las 9:00 a. m. y el período de gracia es de 600 segundos, el trabajo de promoción comenzará el 24 de noviembre a las 8:50 a. m.

## Uso de Screens Launch {#using-launches}

En esta sección se explica cómo implementar Screens Launch en el proyecto de AEM Screens.

### Creación de un lanzamiento de Screens {#creating-a-launch}

Siga los pasos a continuación para implementar la funcionalidad de Screens Launch en su proyecto de AEM Screens:

1. Cree un canal de secuencia en su proyecto de AEM Screens, por ejemplo **LaunchesDemo** —> **Channels** —> **FutureLaunch**, como se muestra a continuación.

   >[!CAUTION]
   >
   >Debe crear un lanzamiento a partir de un canal preexistente en el proyecto de AEM Screens.

   ![Imagen](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleccione el canal **FutureLaunch** y haga clic en **Crear lanzamiento** en la barra de acciones.

   ![Imagen](/help/user-guide/assets/launches-images/launches-12.png)

1. Se abre el asistente **Crear lanzamiento**. Puede seleccionar el canal que ya está visible en el asistente o hacer clic en **+ Añadir canales** para añadir el canal para el que desea crear el lanzamiento.

1. Haga clic en **Siguiente** en el asistente **Crear lanzamiento**. La opción **Include subpages** está seleccionada de forma predeterminada.

   ![image](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Puede utilizar la opción **+ Agregar canales** para agregar otro canal para el que desee crear el lanzamiento.

   Para utilizar la opción **Add Channels**, vaya al canal para el que desee crear el lanzamiento y haga clic en **Select**.

   La opción **Select** se desactivará si intenta seleccionar varios canales o una carpeta para agregar el lanzamiento.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

   Una vez seleccionados los canales, haga clic en **Next**.


1. Introduzca **Launch Title** como **SummerPromotions** y no es necesario configurar la **Fecha de lanzamiento**, como se muestra en la figura siguiente. Haga clic en **Crear**.

   >[!NOTE]
   >
   >*Al habilitar o* marcar la opción  **Heredar datos activos de la página de origen,** los canales se pueden crear como Live Copies en el lanzamiento. Si se realizan cambios en el canal original, esos cambios se aplican automáticamente a los canales de lanzamiento.
   >
   >
   >*Desactivar o* **desmarcarHeredar datos activos de la página de origen** permite copiar los canales sin ninguna relación activa en el lanzamiento. Por lo tanto, si se realizan cambios en el canal original, esos cambios no se aplican a los canales de lanzamiento.

   ![Imagen](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puede establecer la fecha de lanzamiento en directo en este paso o puede configurarla más adelante mientras edita las propiedades del lanzamiento una vez que ya se ha creado.

   **Explicación del ámbito de promoción de Launch**

   * **Promocionar lanzamiento** completo: Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocionar páginas** modificadas: Solo se promoverán los recursos de lanzamiento modificados. Se recomienda utilizar esta opción cuando no sea necesaria la revisión del lanzamiento.
   * **Promocionar páginas** aprobadas: Esta opción requiere que el flujo de trabajo de aprobación del lanzamiento se ejecute en los canales de lanzamiento. Solo se promocionarán las páginas aprobadas en la fecha de lanzamiento establecida.

      >[!CAUTION]
      >
      >La fecha de lanzamiento respeta la zona horaria del reproductor/dispositivo en lugar de la del servidor.

1. Verá que se ha creado el lanzamiento. Puede hacer clic en **Abrir** para ver las páginas en el editor o hacer clic en **Listo** para volver al proyecto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Al hacer clic en **Listo** puede volver al canal **FutureLaunch**.

   ![Imagen](/help/user-guide/assets/launches-images/launches-16.png)


### Edición de las propiedades de Launch para establecer la fecha de lanzamiento y el ámbito {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Una vez creado el lanzamiento, puede actualizar las propiedades como la fecha de lanzamiento, el título del lanzamiento y el ámbito de promoción mediante **Propiedades de lanzamiento**.

* **Fecha de lanzamiento**, hace referencia a la fecha de lanzamiento, es decir, la fecha u hora en que se reproducirá el contenido en el reproductor Screens según la zona horaria del reproductor.
* **Listo para producción**, permite publicar los canales después de promoverlos ya que está habilitado, por lo que no es necesario cambiarlos.
* **Ámbito**, decide qué canales se promocionarán durante la promoción del lanzamiento.


Siga los pasos a continuación para editar las propiedades del lanzamiento:

1. Vaya al canal **FutureLaunch**, *(que es el lanzamiento pendiente)* y seleccione el canal, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Haga clic en **Dashboard** en la barra de acciones y verá el panel **PENDING LAUNCHES** en el panel del canal.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleccione el lanzamiento y haga clic en **Launch Properties** en el panel **PENDING LAUNCHES**.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

### Edición del lanzamiento de Screens para añadir o eliminar canales {#editing-the-screens-launch-to-add-or-remove-channels}

Después de crear el lanzamiento, puede agregar o quitar canales al lanzamiento existente mediante la opción **Editar lanzamiento**.

Una vez finalizado, haga clic en **Save** para volver al canal **FutureLaunch**.

### Promocionar el lanzamiento de Screens manualmente{#promote-the-screens-launch-manually}

Puede promocionar el lanzamiento manualmente con la opción **Promocionar lanzamiento** del panel **PENDING LAUNCHES**.

Puede elegir los recursos que desea promocionar como parte de esta promoción manual en el **Asistente para promociones de Launch**.

![image](/help/user-guide/assets/launches-images/launches-e.png)

1. Puede activar o desactivar la opción para eliminar el lanzamiento después de la producción.
1. Puede configurar el **Scope** del lanzamiento con las siguientes opciones:
   1. **Promocionar lanzamiento** completo: Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   1. **Promocionar páginas** modificadas: Solo se promoverán los recursos de lanzamiento modificados. Se recomienda utilizar esta opción cuando no sea necesaria la revisión del lanzamiento.
   1. **Promocionar páginas** aprobadas: Esta opción requiere que el flujo de trabajo de aprobación del lanzamiento se ejecute en los canales de lanzamiento. Solo se promocionarán las páginas aprobadas en la fecha de lanzamiento establecida.
   1. **Promocionar página** actual: Esta opción requiere que el flujo de trabajo de aprobación de lanzamiento se ejecute únicamente para la página actual.
1. Haga clic en **Siguiente** en el asistente **Promocionar lanzamiento**.
1. Haga clic en **Promocionar** para promocionar el lanzamiento.

### Eliminación de Screens Launch {#deleting-the-screens-launch}

Puede eliminar el lanzamiento utilizando la opción **Delete Launch** del panel **PENDING LAUNCHES**.

>[!CAUTION]
>
>Esta acción también elimina todos los descendientes (lanzamientos anidados).

