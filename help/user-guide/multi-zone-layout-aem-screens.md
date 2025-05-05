---
title: Diseño de varias zonas
description: Obtenga información sobre cómo crear contenido de varias zonas y utilizar varios recursos, como vídeos, imágenes y texto, que se combinan en una sola pantalla en AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Diseño de varias zonas {#multi-zone-layout}

En la siguiente página se describe el uso del diseño de varias zonas y se tratan los siguientes temas:

* Información general
* Creación de diseños de varias zonas
* Requisitos previos
* Uso de un solo Assets en una o varias zonas
* Uso de contenido secuenciado en una o varias zonas

## Información general {#overview}

***Diseño de varias zonas*** le permite crear contenido de varias zonas y utilizar varios recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Puede extraer imágenes, vídeos y texto, lo que le permite fusionarse y crear una experiencia digital intuitiva.

Según los requisitos del proyecto, a veces necesita varias zonas en un canal y editarlas como una unidad completa. Por ejemplo, una secuencia de productos con una fuente de medios sociales relacionada que se ejecuta en tres zonas independientes en un solo canal.

>[!NOTE]
>En canales de varias zonas, no se recomienda la programación en el nivel de recurso debido a posibles conflictos y a un comportamiento no deseado. Si es necesaria la programación a nivel de recurso, cree un canal de secuencia independiente y aplique la lógica de programación dentro de ese canal. A continuación, incruste el canal de secuencia en el canal de varias zonas.

### Requisitos previos {#prerequisites}

Antes de comenzar a implementar esta funcionalidad, asegúrese de tener los conocimientos conceptuales sobre lo siguiente:

* [Creando un proyecto de AEM Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Creando una pantalla](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Asignación de un canal a una pantalla](/help/user-guide/channel-assignment.md)

## Creación de diseños de varias zonas {#creating-multi-zone-layout}

Al crear un canal, puede utilizar diferentes plantillas para crear zonas en el canal. Puede añadir una sola imagen, vídeo o un canal incrustado que permita que se muestren varios recursos en una secuencia.

**Creando un canal**

1. Haga clic en el vínculo Adobe Experience Manager (parte superior izquierda) y, a continuación, **Screens**. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.
1. Vaya a la carpeta **Canales** y haga clic en **Crear** desde la barra de acciones.

1. Haga clic en **Canal de pantalla dividida 1x2** del asistente **Crear**.

1. Haga clic en **Siguiente** e introduzca el **título** como **MultiZone**.

1. Haga clic en **Crear** para completar la creación del canal.

### Uso de un solo Assets en una o varias zonas {#using-single-assets-in-one-or-more-zones}

Puede utilizar recursos únicos, como una imagen o un vídeo, en todas las zonas individuales. Siga los pasos a continuación para la implementación:

1. **Agregando contenido al canal**

   1. Vaya a **Zonas** > **Canales**> **MultiZone**.
   1. Haga clic en el canal **MultiZone** y luego en **Editar** en la barra de acciones.

1. **Agregando imágenes al canal**

   Para reproducir una sola imagen o un vídeo en dos zonas, simplemente arrastre y suelte una imagen en cada zona del editor de canales, como se muestra en la figura siguiente:

   ![imagen](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de contenido secuenciado en una o varias zonas {#using-sequenced-content-in-one-or-more-zones}

Si desea que las zonas muestren una secuencia de imágenes y un vídeo en las diferentes zonas, siga los pasos a continuación para obtener más información.

1. **Creando una carpeta de canal**

   1. Vaya a **Zonas** > **MultiZone** > **Canales** y haga clic en **Crear** desde la barra de acciones.
   1. Haga clic en la carpeta **Canales** del asistente **Crear** y luego haga clic en **Siguiente**.
   1. Escriba el título como **EmbeddedChannels** y haga clic en **Crear**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Agregando dos canales más a la carpeta del canal**

   1. Vaya a **Zonas** > **Canales** > **Canales incrustados** y haga clic en **Crear** en la barra de acciones.
   1. Haga clic en **Canal de secuencia** del asistente **Crear** para crear un canal con el título **`Zone1`**.
   1. Haga clic en **`Zone1`** y luego en **Editar** en la barra de acciones.
   1. Arrastre y suelte algunas imágenes en este canal.
   1. Del mismo modo, cree otro canal de secuencia denominado **`Zone2`** en la carpeta **EmbeddedChannels**.
   1. Arrastre y suelte un vídeo en este canal.

   La siguiente figura muestra los canales **`Zone1`** y **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Las imágenes agregadas al editor del canal de secuencia **`Zone1`** se muestran a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   El vídeo agregado al editor del canal de secuencia **`Zone2`** se muestra a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Agregar secuencias incrustadas (componente) al canal principal (MultiZone)**

   1. Vaya a **Zonas** > **Canales** > **MultiZone**.
   1. Haga clic en **Editar** en la barra de acciones.
   1. Arrastre y suelte el componente **Secuencia incrustada** en ambas zonas.
   1. Haga clic en la secuencia incrustada en una de las zonas.
   1. Haga clic en el icono **Configurar** (llave inglesa) para añadir una de las secuencias incrustadas en el editor.
   1. Haga clic en la ruta de acceso al canal como **Zonas** > **Canales** > **Canales incrustados** > **`Zone1`**, como se muestra en la figura siguiente.
   1. Del mismo modo, agregue **`Zone2`** a otro componente de secuencia incrustado en el editor.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creación de una ubicación y una visualización {#creating-location}

Cree una ubicación y una pantalla para poder ver el contenido en el Reproductor de AEM Screens.

1. **Creando una ubicación**

   1. Vaya a la carpeta **Zonas** > **Ubicaciones**.
   1. Haga clic en la carpeta **Ubicaciones** y luego en **Crear** en la barra de acciones.
   1. Haga clic en **Ubicación** en el asistente de **Crear** y luego en **Siguiente**.
   1. Escriba **Title** como **SanJose** y haga clic en **Crear**.

1. **Creando una pantalla**

   1. Vaya a la carpeta **Zonas** > **Ubicaciones**.
   1. Haga clic en la ubicación **SanJose** y luego en **Crear** en la barra de acciones.
   1. Haga clic en **Mostrar** en el asistente de **Crear** y luego haga clic en **Siguiente**.
   1. Escriba **Title** como **Lobby** y haga clic en **Crear**.

### Asignación de canales a la pantalla {#channel-channel}

Asigne los canales a la pantalla para ver el contenido. Siga los pasos a continuación para asignar el canal a la pantalla.

1. **Asignando canal a la pantalla**

   1. Vaya a **Zonas** > **Ubicaciones** > **SanJose**> **Vestíbulo**.
   1. Haga clic en la pantalla **Lobby** y luego en **Asignar canal** en la barra de acciones.
   1. Escriba la ruta al canal **MultiZone** en **Ruta del canal**.
   1. Establezca los **Eventos admitidos** como **Carga inicial**, **Pantalla inactiva** y **Temporizador**.
   1. Haga clic en **Guardar**.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Del mismo modo, asigne los otros dos canales incrustados (**`Zone1`** y **`Zone2`**) a esta pantalla.
   1. Después de asignar los tres canales a la pantalla **Lobby**, debería poder ver los canales asignados desde el panel de visualización.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >Después de asignar el canal principal (en este caso, **MultiZone**) a la pantalla, es obligatorio asignar los otros dos canales incrustados **`Zone1`** y **`Zone2`** también a la misma pantalla.

### Registro del dispositivo {#registering-device}

Cuando haya configurado una ubicación y una pantalla, siga los pasos a continuación para registrar el dispositivo y asignar la pantalla al dispositivo.

1. **Registrando el dispositivo**

   1. Vaya a la carpeta **Zonas** > **Dispositivos**.
   1. Haga clic en la carpeta **Dispositivos** y luego en **Administrador de dispositivos** en la barra de acciones.
   1. Haga clic en **Registro de dispositivo** y haga clic en el dispositivo pendiente de la lista.

      >[!NOTE]
      > El título del dispositivo debe coincidir con el token del dispositivo (campo **Token**) mostrado en la ficha **Registro de dispositivo**.

   1. Si el título coincide con el token del dispositivo, haz clic en el dispositivo y haz clic en **Registrar dispositivo** en la barra de acciones.
   1. Si el código de registro coincide con el código de la ficha **Registro de dispositivo** del reproductor de Screens, haga clic en **Validar** en la barra de acciones.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Escriba **Title** como **`Chrome-Device1`** y haga clic en **Registrar**.
   1. Haga clic en **Asignar pantalla** y haga clic en la ruta de acceso a la configuración del dispositivo.

   >[!NOTE]
   >Si intenta ver el contenido en el reproductor de Screens, asegúrese de hacer clic en **Actualizar contenido sin conexión** en el panel de canales para cada uno de los canales asignados a la pantalla.

### Visualización del resultado {#viewing-the-result}

Cuando se implementan diseños de varias zonas siguiendo los pasos anteriores, se muestra el siguiente resultado.

Compruebe el reproductor Screens para poder ver la salida que muestra el contenido en dos zonas diferentes. Las zonas izquierda y derecha (ambas utilizan una secuencia incrustada como componente).

La zona izquierda es un canal de secuencia y la zona derecha incluye un vídeo.

![nuevo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
