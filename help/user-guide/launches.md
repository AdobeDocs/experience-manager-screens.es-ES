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
source-git-commit: 14a45b58862477ec6be082ab1c059f991b086755

---


# Actualización de contenido con Screens Launch {#launches}

Los autores de contenido pueden crear versiones futuras de los canales, conocidas como **Pantallas** , y establecer la fecha de lanzamiento de este lanzamiento. Esto permite que el contenido esté activo en dispositivos o reproductores en la fecha de lanzamiento especificada.

Con la ayuda de **Screens Launches**, los autores pueden realizar previsualizaciones de cada canal en el lanzamiento y deben poder iniciar una solicitud de revisión. El grupo Aprobadores recibirá una notificación y puede aprobar o rechazar la solicitud. Cuando se alcanza la fecha de lanzamiento, el contenido se reproduce en los dispositivos.

Por ejemplo, si el autor desea crear versiones futuras de c1, c2 (canales), se crea un lanzamiento y se establece una fecha de lanzamiento (por ejemplo, 10 de noviembre a las 8:00 a.m.). Cualquier otra actualización del contenido se envía para su revisión. Una vez aprobado y en fecha de lanzamiento (10 de noviembre, 8:00 AM), este lanzamiento reproduce el contenido en los dispositivos o reproductores.

## Requisitos {#requirements}

Antes de inicio de aprovechar Screens Launches en un proyecto de AEM Screens, asegúrese de comprender el concepto de período de gracia y su importancia.

La ejecución de una experiencia en la fecha de lanzamiento establecida en el reproductor implica:

* promoción del lanzamiento (normalmente tarda unos segundos)

* publicar los recursos para publicar instancias (normalmente tarda unos minutos, depende del tamaño de los canales o recursos que deban publicarse)

* tiempo que tarda la actualización en completarse (suele tardar unos minutos)

* tiempo que tardan los reproductores en descargar el contenido de la instancia de publicación (normalmente tarda minutos en función del ancho de banda n/w y del tamaño de los recursos que deben descargarse)

* diferencias de tiempo del servidor y del reproductor

### Explicación del período de gracia {#understanding-grace-period}

Para que el reproductor pueda reproducir en inicio el contenido en la fecha de lanzamiento establecida, necesitamos inicios de las actividades antes mencionadas antes de la fecha de lanzamiento.

Si la fecha de lanzamiento es *24 de noviembre, 9:00 AM* y el período de gracia es de *24 horas*, la secuencia de acciones anterior tendrá un inicio en (fecha de lanzamiento - período de gracia), es decir, 23 de noviembre, 9:00 AM hora del servidor. Esto da 24 horas de tiempo para completar todas las acciones mencionadas anteriormente y el contenido llegará a los jugadores. Los jugadores comprenderán que se trata de un contenido de inicio, por lo que el contenido no se reproducirá inmediatamente, pero los reproductores almacenarán este contenido como una versión futura y tendrán el inicio de reproducirse exactamente en la fecha de lanzamiento establecida en el huso horario del reproductor.

Por ejemplo: supongamos que el servidor está en PST y que los dispositivos están en EST, la diferencia máxima de tiempo es de 3 horas en este caso y supongamos que la promoción tardará 1 minuto y que la publicación del autor tarda 10 minutos y que el reproductor puede descargar los recursos normalmente en 10-15 minutos. Entonces período de gracia = diferencia de tiempo (3 horas) + tiempo para promocionar el lanzamiento (1 min) + tiempo para publicar el lanzamiento (10 min) + tiempo para descargar en el reproductor (10-15 min) + buffer (para ser seguro, digamos 30 min) = 3 horas 56 min = 14160 segundos. Así que, cuando programemos cualquier lanzamiento en directo, la promoción se inicio temprano con este desplazamiento. En la ecuación anterior, la mayoría de los elementos no toma mucho tiempo, podemos usar una estimación decente para este desplazamiento una vez que sepamos la diferencia de tiempo máxima por parte del servidor y de cualquier reproductor.

>[!NOTE]
>De forma predeterminada, el período de gracia para los inicios de pantallas se establece en 24 horas, lo que significa que cuando se establece la fecha de lanzamiento de cualquier lanzamiento para los recursos en */contenido/pantallas*, la promoción se inicio con este desplazamiento.

### Actualización del período de gracia listo para usar {#updating-out-of-the-box-grace-period}

En esta sección se explica cómo puede actualizar un período de gracia predeterminado a 10 minutos:

1. Vaya a CRXDE Lite y, a continuación, a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Haga clic con el botón derecho y copie el archivo.
3. Vaya a `/apps/system/config` y haga clic con el botón secundario y péguelo.
4. Haga clic en el Doble `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir el archivo en el editor de CRXDE Lite. Debe mostrar el período de gracia para la ruta */contenido/pantallas/* como 86400. Cambie ese valor a **600**.

Ahora, el contenido del archivo de texto debe tener un aspecto similar a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Dado que el período de gracia se ha establecido en 10 minutos en el ejemplo anterior, cuando se establece la fecha de lanzamiento de cualquier inicio para los recursos en */contenido/pantallas*, la promoción contraerá este inicio.

Por ejemplo, si la fecha de lanzamiento se establece como 24 de noviembre, 9:00 AM y el período de gracia es de 600 segundos, el trabajo de promoción se inicio el 24 de noviembre a las 8:50 AM.

## Uso de Screens Launch {#using-launches}

Siga la sección siguiente para implementar inicios en su proyecto de AEM Screens. Esta sección cubre estos temas:

1. **Creación de un lanzamiento de pantalla**
1. **Edición de un lanzamiento de pantallas para establecer la fecha y el ámbito de lanzamiento**

### Creación de un lanzamiento de pantalla {#creating-a-launch}

Siga los pasos a continuación para implementar la funcionalidad de inicios en su proyecto de AEM Screens:

1. Cree un canal de secuencia en su proyecto de AEM Screens, por ejemplo, **LaunchesDemo** —> **Canales** —> **FutureLaunch**, como se muestra a continuación.

   >[!CAUTION]
   >
   >Debe crear un inicio a partir de un canal preexistente en el proyecto de AEM Screens.

   ![Imagen](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleccione canal **FutureLaunch** y haga clic en **Crear lanzamiento** en la barra de acciones.

   ![Imagen](/help/user-guide/assets/launches-images/launches-12.png)

1. Se abre el asistente **Crear inicio** . Puede seleccionar el canal que ya está visible en el asistente o hacer clic en **+ Añadir Canales** para agregar el canal para el que desea crear el lanzamiento.


#### Uso del Canal existente {#existing-channel-launch}

1. Seleccione el canal que ya existe en el asistente **Crear inicio** y haga clic en **Siguiente**.

   ![image](/help/user-guide/assets/launches-images/launches-b.png)

1. Seleccione el canal y haga clic en **Siguiente** en la barra de acciones.

   >[!NOTE]
   >**La opción Incluir subpáginas** está seleccionada de forma predeterminada.

   ![Imagen](/help/user-guide/assets/launches-images/launches-b.png)

1. Introduzca el título **de** lanzamiento como **promociones** de verano y no necesita establecer la fecha **de** lanzamiento, como se muestra en la figura siguiente. Haga clic en **Crear**.

   >[!NOTE]
   >
   >*Al habilitar o comprobar* la opción **Heredar datos** activos de la página de origen, los canales se pueden crear como copias en directo en el lanzamiento. Si se realizan cambios en el canal original, dichos cambios se aplican automáticamente a los canales de inicio.
   >
   >
   >*Al deshabilitar o desmarcar* **Heredar datos** activos de la página de origen, los canales se pueden copiar sin ninguna relación activa durante el lanzamiento. Por lo tanto, si se realizan cambios en el canal original, esos cambios no se aplican a los canales de inicio.

   ![Imagen](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puede establecer la fecha de lanzamiento activo en este paso o puede configurarla más tarde mientras edita las propiedades del lanzamiento una vez que ya se ha creado.

1. Verá que se ha creado el lanzamiento. Puede hacer clic en **Abrir** para vista de las páginas en el editor o en **Hecho** para volver al proyecto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Al hacer clic en **Listo** , podrá volver al canal **FutureLaunch** .

   ![Imagen](/help/user-guide/assets/launches-images/launches-16.png)


#### Uso de la opción Añadir Canales {#add-channel-launch}

1. Haga clic en **+ Añadir Canales** para agregar el canal para el que desea crear el lanzamiento.

   ![image](/help/user-guide/assets/launches-images/launches-13.png)

   >[!NOTE]
   >La opción **Seleccionar** se desactivará si intenta seleccionar varios canales o una carpeta para agregar el lanzamiento.

1. Vaya al canal para el que desea crear el lanzamiento y haga clic en **Seleccionar**.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

1. Ahora puede seleccionar el canal que ha agregado para crear un lanzamiento y hacer clic en **Siguiente**.

   ![image](/help/user-guide/assets/launches-images/launches-15.png)

1. Introduzca el título **de** lanzamiento como **promociones** de verano y no necesita establecer la fecha **de** lanzamiento, como se muestra en la figura siguiente. Haga clic en **Crear**.

   >[!NOTE]
   >
   >*Al habilitar o comprobar* la opción **Heredar datos** activos de la página de origen, los canales se pueden crear como copias en directo en el lanzamiento. Si se realizan cambios en el canal original, dichos cambios se aplican automáticamente a los canales de inicio.
   >
   >
   >*Al deshabilitar o desmarcar* **Heredar datos** activos de la página de origen, los canales se pueden copiar sin ninguna relación activa durante el lanzamiento. Por lo tanto, si se realizan cambios en el canal original, esos cambios no se aplican a los canales de inicio.

   ![Imagen](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puede establecer la fecha de lanzamiento activo en este paso o puede configurarla más tarde mientras edita las propiedades del lanzamiento una vez que ya se ha creado.

1. Verá que se ha creado el lanzamiento. Puede hacer clic en **Abrir** para vista de las páginas en el editor o en **Hecho** para volver al proyecto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Al hacer clic en **Listo** , podrá volver al canal **FutureLaunch** .

   ![Imagen](/help/user-guide/assets/launches-images/launches-16.png)

### Edición de las propiedades de inicio para establecer la fecha de lanzamiento y el ámbito {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Una vez creado el lanzamiento, debe editar las propiedades de inicio para establecer la fecha de lanzamiento como el ámbito del lanzamiento.

Siga los pasos a continuación para editar las propiedades de inicio:

1. Vaya a canal **FutureLaunch***(es decir, el lanzamiento pendiente)* y seleccione el canal, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Haga clic en el **Panel** en la barra de acciones y verá el panel **PENDIENTES LAUNCHES** desde el panel canal.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleccione el inicio y haga clic en cualquiera de las acciones deseadas en el panel INICIOS **PENDIENTES** .

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

1. Por ejemplo, haga clic en **Iniciar propiedades** para editar las propiedades del lanzamiento **SummerPromotions**.

   ![image](/help/user-guide/assets/launches-images/launches-20.png)

1. Puede editar el título **de** la presentación y rellenar los campos siguientes:

   * Seleccione la fecha de **inicio**
   * Comprobar **producción lista**
   * Seleccione **Promocionar páginas** aprobadas desde el **ámbito**
   **Explicación de las entradas Lanzamientos en Promoción automática:**

   * **Fecha** de lanzamiento, hace referencia a la fecha de lanzamiento, es decir, la fecha y hora en que el contenido se reproducirá en el reproductor de pantallas según la zona horaria del reproductor.
   * **Listo** para la producción, permite promocionar los canales y significa que el lanzamiento está listo para ser utilizado.
   * **Ámbito**, se refiere a los canales que pueden promoverse durante un lanzamiento.
   Existen las tres opciones siguientes para configurar el ámbito:

   * **Promocione el lanzamiento** completo: Todos los canales del lanzamiento se promocionan en la fecha de lanzamiento establecida.
   * **Promocione las páginas** modificadas: Solo se promocionarán los recursos de lanzamiento editados. Se recomienda utilizar esta opción cuando no se requiera la revisión del inicio. Permite promover las modificaciones en los canales de lanzamiento.
   * **Promocione las páginas** aprobadas: Solo se promocionan las páginas aprobadas en la fecha de lanzamiento establecida.

      >[!CAUTION]
      >
      >La promoción de inicio respeta la zona horaria del reproductor/dispositivo en lugar de la del servidor.



1. Haga clic en **Guardar y cerrar** para volver al canal **FutureLaunch** .

