---
title: Diseño de varias zonas
seo-title: Multi-zone Layout
description: El diseño de varias zonas le permite crear contenido de varias zonas y utilizar varios recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Siga esta página para obtener más información.
seo-description: Multi-zone Layout allows you to create multiple zone content and use a variety of assets such as videos, images and text that can be combined in a single screen. Follow this page to learn more.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---

# Diseño de varias zonas {#multi-zone-layout}

En la siguiente página se describe el uso del diseño de varias zonas y se tratan los siguientes temas:

* Información general
* Creación de diseños de varias zonas
* Requisitos previos
* Uso de recursos únicos en una o más zonas
* Uso de contenido secuenciado en una o varias zonas

## Información general {#overview}

***Diseño de varias zonas*** le permite crear contenido de varias zonas y utilizar varios recursos, como vídeos, imágenes y texto, que se pueden combinar en una sola pantalla. Puede extraer imágenes, vídeos y texto, lo que le permite fusionarse y crear una experiencia digital intuitiva.

Según los requisitos del proyecto, a veces necesita varias zonas en un canal y editarlas como una unidad completa. Por ejemplo, una secuencia de productos con una fuente de medios sociales relacionada que se ejecuta en tres zonas independientes en un solo canal.


### Requisitos previos {#prerequisites}

Antes de comenzar a implementar esta funcionalidad, asegúrese de tener los conocimientos conceptuales sobre:

* [Creación de un proyecto de AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Creación de una visualización](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Asignación de un canal a una pantalla](/help/user-guide/channel-assignment.md)

## Creación de diseños de varias zonas {#creating-multi-zone-layout}

Al crear un canal, puede utilizar diferentes plantillas para crear zonas en el canal. Puede añadir una sola imagen, vídeo o un canal incrustado que permita que se muestren varios recursos en una secuencia.

**Creación de un canal**

1. Seleccione el vínculo de Adobe Experience Manager (parte superior izquierda) y, a continuación, **Screens**. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.
1. Vaya a **Canales** y haga clic en **Crear** de la barra de acciones.

1. Seleccionar **Canal de pantalla dividida 1x2** desde el **Crear** asistente.

1. Clic **Siguiente** e introduzca la variable **title** as **MultiZone**.

1. Clic **Crear** para completar la creación del canal.

### Uso de recursos únicos en una o más zonas {#using-single-assets-in-one-or-more-zones}

Puede utilizar recursos únicos, como una imagen o un vídeo, en todas las zonas individuales. Siga los pasos a continuación para la implementación:

1. **Adición de contenido al canal**

   1. Vaya a **Zonas** —> **Canales**—> **MultiZone**.
   1. Seleccione el **MultiZone** y haga clic en **Editar** en la barra de acciones para abrir el editor.

1. **Adición de imágenes al canal**

   Para reproducir una sola imagen o un vídeo en dos zonas, simplemente arrastre y suelte una imagen en cada zona del editor de canales, como se muestra en la figura siguiente:

   ![imagen](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de contenido secuenciado en una o varias zonas {#using-sequenced-content-in-one-or-more-zones}

Si desea que las zonas muestren una secuencia de imágenes y un vídeo en las diferentes zonas, siga los pasos a continuación para obtener más información.

1. **Creación de una carpeta de canales**

   1. Vaya a **Zonas** —> **MultiZone** —> **Canales** y haga clic en **Crear** de la barra de acciones.
   1. Seleccionar **Carpeta de canales** desde el **Crear** y haga clic en **Siguiente**.
   1. Escriba el título como **EmbeddedChannels** y haga clic en **Crear**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adición de dos canales más a la carpeta del canal**

   1. Vaya a **Zonas** —> **Canales** —> **EmbeddedChannels** y haga clic en **Crear** de la barra de acciones.
   1. Seleccionar **Canal de secuencia** desde el **Crear** asistente para crear un canal con el título **Zona1**.
   1. Seleccionar **Zona1** y haga clic en **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte algunas imágenes en este canal.
   1. Del mismo modo, cree otro canal de secuencia llamado **Zona2** in **EmbeddedChannels** carpeta.
   1. Arrastre y suelte un vídeo en este canal.

   La siguiente figura muestra los canales **Zona1** y **Zona2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Las imágenes añadidas al editor de **Zona1** canal de secuencia se muestra a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   El vídeo añadido al editor de **Zona2** canal de secuencia se muestra a continuación:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adición de secuencias incrustadas (componente) al canal principal (MultiZone)**

   1. Vaya a **Zonas** —> **Canales** —> **MultiZone**.
   1. Clic **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte el **Secuencia incrustada** a ambas zonas.
   1. Seleccione la secuencia incrustada en una de las zonas.
   1. Haga clic en **Configurar** Icono (llave inglesa) a una de las secuencias incrustadas en el editor.
   1. Seleccione la ruta del canal como **Zonas** —> **Canales** —> **EmbeddedChannels** —> **Zona1**, como se muestra en la figura siguiente.
   1. Del mismo modo, agregue **Zona2** a otro componente de secuencia incrustado en el editor.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creación de una ubicación y una visualización {#creating-location}

Cree una ubicación y una pantalla para ver el contenido en el reproductor Screens.

1. **Creación de una ubicación**

   1. Vaya a **Zonas** —> **Ubicaciones** carpeta.
   1. Seleccione el **Ubicaciones** y haga clic en **Crear** de la barra de acciones.
   1. Seleccionar **Ubicación** desde el **Crear** y haga clic en **Siguiente**.
   1. Introduzca el **Título** as **San José** y haga clic en **Crear**.

1. **Creación de una visualización**

   1. Vaya a **Zonas** —> **Ubicaciones** carpeta.
   1. Seleccione el **San José** ubicación y haga clic en **Crear** de la barra de acciones.
   1. Seleccionar **Mostrar** desde el **Crear** y haga clic en **Siguiente**.
   1. Introduzca el **Título** as **Vestíbulo** y haga clic en **Crear**.

### Asignación de canales a la pantalla {#channel-channel}

Asigne los canales a la pantalla para ver el contenido. Siga los pasos a continuación para asignar el canal a la pantalla.

1. **Asignación de canales a la pantalla**

   1. Vaya a **Zonas** —> **Ubicaciones** —> **San José**—> **Vestíbulo**.
   1. Seleccione el **Vestíbulo** mostrar y hacer clic en **Asignar canal** de la barra de acciones.
   1. Introduzca la ruta al **MultiZone** entrada de canal **Ruta de canal**.
   1. Configure las variables **Eventos admitidos** as **Carga inicial**, **Pantalla inactiva**, y **Temporizador**.
   1. Haga clic en **Guardar**.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Del mismo modo, debe asignar los otros dos canales incrustados (**Zona1** y **Zona2**) a esta pantalla.
   1. Una vez que asigne los tres canales a **Vestíbulo** para mostrar, debería poder ver los canales asignados desde el panel de visualización.

      ![imagen](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Una vez asignado el canal principal (en este caso, **MultiZone**) a la pantalla, es obligatorio asignar los otros dos canales incrustados **Zona1** y **Zona2** también en la misma pantalla.

### Registro del dispositivo {#registering-device}

Una vez que haya configurado una ubicación y una pantalla, siga los pasos a continuación para registrar el dispositivo y asignarle una pantalla.

1. **Registro del dispositivo**

   1. Vaya a **Zonas** —> **Dispositivos** carpeta.
   1. Seleccione el **Dispositivos** y haga clic en **Administrador de dispositivos** de la barra de acciones.
   1. Clic **Registro de dispositivos** y seleccione el dispositivo pendiente de la lista.

      >[!NOTE]
      > El título del dispositivo debe coincidir con el token del dispositivo (**Token** ) se muestra en la **Registro de dispositivos** pestaña.
   1. Si el título coincide con el token del dispositivo, seleccione el dispositivo y haga clic en **Registrar dispositivo** de la barra de acciones.
   1. Si el código de registro coincide con el código del reproductor de Screens **Registro de dispositivos** pestaña, haga clic en **Validate** de la barra de acciones.
      ![imagen](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Introduzca el **Título** as **Chrome-Device1** y haga clic en **Registrar**.
   1. Seleccionar **Asignar visualización** y seleccione la ruta a la configuración del dispositivo.

   >[!NOTE]
   >Si intenta ver el contenido en el reproductor Screens, asegúrese de hacer clic en **Actualizar contenido sin conexión** del panel de canales para cada uno de los canales asignados a la visualización.

### Visualización del resultado {#viewing-the-result}

Una vez implementados los diseños de varias zonas siguiendo los pasos anteriores, se muestra el siguiente resultado.

Compruebe el reproductor Screens para ver la salida que muestra el contenido en dos zonas diferentes. Las zonas izquierda y derecha (ambas utilizan una secuencia incrustada como componente).

La zona izquierda es un canal de secuencia y la zona derecha incluye un vídeo.

![nuevo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
