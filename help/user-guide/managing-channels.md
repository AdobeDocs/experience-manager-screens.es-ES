---
title: Creación y administración de canales
description: Obtenga información sobre la creación y administración de canales. También se explica el tablero de canales y la edición de contenido para un canal.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 7bbd211a-f54f-42b9-a1b3-516efe6fb579
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 2%

---

# Creación y administración de canales {#creating-and-managing-channels}

Un canal muestra una secuencia de contenido (imágenes y vídeos) y también muestra un sitio web o una aplicación de una sola página.

Esta página muestra la creación y administración de canales para AEM Screens.

**Requisitos previos**:

* [Configuración e implementación de Screens](configuring-screens-introduction.md)
* [Crear y administrar un proyecto de Screens](creating-a-screens-project.md)

## Creación de un nuevo canal {#creating-a-new-channel}

Después de crear el proyecto para AEM Screens, siga los pasos a continuación para crear un canal para el proyecto:

1. Haga clic en el vínculo Adobe Experience Manager (parte superior izquierda) y, a continuación, en Screens. También puede navegar directamente a `https://localhost:4502/screens.html/content/screens`.

1. Vaya al proyecto de Screens y haga clic en la carpeta **Canales**.

1. Haga clic en **Crear** en la barra de acciones.

   ![demochannel](assets/create-channel1.png)

1. Haga clic en la plantilla **Canal de secuencia** del asistente **Crear** y luego haga clic en **Siguiente**.

   ![demochannel](assets/create-channel2.png)

1. Escriba el título como **ScreensChannel** y haga clic en **Crear**.

   ![demochannel](assets/create-project4.png)

1. Ahora se agrega un canal de secuencia a la carpeta **Canales**.

### Tipos de canales {#channel-types}

Las siguientes opciones de plantilla están disponibles mientras se utiliza el asistente:

| **Opción de plantilla** | **Descripción** |
|---|---|
| Carpeta de canales | Cree una carpeta para almacenar una colección de canales. |
| Canal de secuencia | Cree un canal que reproduzca los componentes secuencialmente (uno a uno en una presentación con diapositivas). |
| Canal de aplicaciones | Muestre la aplicación web personalizada en el reproductor de Screens. |
| Canal de pantalla dividida 1x1 | Ver un componente en una sola zona. |
| Canal de pantalla dividida 1x2 | Visualice los recursos en dos zonas (divididas horizontalmente). |
| Canal De Pantalla Dividida 2X1 | Vea los recursos en dos zonas (divididas verticalmente). |
| Canal de pantalla dividida 2x2 | Visualice los recursos en cuatro zonas (divididas horizontal y verticalmente en una matriz). |
| Canal de pantalla dividida 2 a 3 | Vea los recursos en dos zonas (divididas horizontalmente): una de las zonas es más grande que la otra. |
| Canal de pantalla dividida de barra en L izquierda o derecha | Los autores de contenido pueden ver diferentes tipos de recursos en zonas de tamaño adecuado. |

>[!NOTE]
>
>Los canales de pantalla dividida dividen la pantalla en varias zonas para que pueda reproducir varias experiencias al mismo tiempo, una al lado de la otra. Las experiencias pueden ser recursos estáticos/texto o secuencias incrustadas.

>[!IMPORTANT]
>
>Después de crear y añadir contenido al canal, el siguiente paso es crear una ubicación y, a continuación, una pantalla. Además, asigne ese canal a una pantalla. Consulte los recursos que aparecen a continuación al final de la sección.

## Uso de canales {#working-with-channels}

Puede editar, ver las propiedades y el panel, copiar, previsualizar y eliminar un canal.


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Adición o edición de contenido en un canal {#adding-editing-content-to-a-channel}

Para añadir o editar contenido en un canal, siga los pasos a continuación:

1. Haga clic en el canal que desee editar (como se muestra en la figura anterior).
1. Haga clic en **Editar** en la esquina superior izquierda de la barra de acciones para poder editar las propiedades del canal. Se abre el editor, que le permite agregar recursos o componentes al canal que desee publicar.

>[!NOTE]
>Puede añadir componentes al canal. Consulte **[Agregar componentes a un canal](adding-components-to-a-channel.md)** para obtener más información.

![demochannel1](assets/demochannel1.gif)

**Cargando vídeos en el canal**

Siga los pasos a continuación para cargar vídeos en su canal:

1. Haga clic en el canal en el que desee cargar el vídeo.
1. Haga clic en **Editar** en la barra de acciones.
1. En el editor, haga clic en **Vídeos** en Assets y arrastre y suelte los vídeos necesarios.

>[!NOTE]
>Si tienes problemas al cargar videos en tu canal, consulta [Vídeos para solucionar problemas](troubleshoot-videos.md).

### Visualización o edición de las propiedades de un canal {#viewing-properties}

1. Haga clic en el canal que desee editar.
1. Haga clic en **Propiedades** en la barra de acciones para ver o editar las propiedades del canal. La siguiente pestaña permite cambiar las opciones.

![propiedades](assets/properties.gif)

### Visualización del panel {#viewing-dashboard}

1. Haga clic en el canal que desee editar.
1. Haga clic en **Tablero** en la barra de acciones.

![tablero](assets/dashboard.gif)

### Información del canal {#channel-information}

El panel Información del canal describe las propiedades del canal, junto con la vista previa del canal. Además, le proporciona información sobre si el canal está sin conexión o en línea.

Haga clic en (**...**) en la barra de acciones **INFORMACIÓN DEL CANAL** para que pueda ver las propiedades, editar el contenido o actualizar la caché (contenido sin conexión) del canal.

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### Visualización del manifiesto {#view-manifest}

Puede ver el manifiesto desde el panel de canales.

>[!IMPORTANT]
>AEM AEM Esta opción solo está disponible con el paquete de funciones 8 o 4 del paquete de funciones 4 de la versión 6.4 de la o con el paquete de funciones 4 de la versión 6.5.

Siga estos pasos para poder habilitar esta opción desde el panel de canales:

1. **Establecer el canal sin conexión**
   1. Haga clic en el canal y luego en **Propiedades** en la barra de acciones
   1. Vaya a la pestaña **Canal** y asegúrese de desactivar la opción **Modo de desarrollador (forzar al canal a estar en línea)**
   1. Haga clic en **Guardar y cerrar**
1. **Actualizar contenido sin conexión**
   1. Haga clic en el canal y luego en **Panel** en la barra de acciones
   1. Vaya al panel **INFORMACIÓN DE CANAL** y haga clic en *...*
   1. Haga clic en **Actualizar contenido sin conexión**

Debería ver la opción **Ver manifiesto** del panel **INFORMACIÓN DE CANAL** en el panel Canal.

![imagen1](assets/channel-one.png)


### Canales en línea y sin conexión {#online-and-offline-channels}

>[!NOTE]
>De forma predeterminada, al crear un canal, está Sin conexión.

Al crear un canal, puede definirse como un canal en línea o sin conexión.

Un ***canal en línea*** muestra el contenido actualizado en tiempo real, mientras que un ***canal sin conexión*** muestra el contenido almacenado en caché.

Siga los pasos a continuación para hacer el canal en línea:

1. Vaya al canal como **TestProject** > **Canales** > **TestChannel**.

   Haga clic en el canal.

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Haga clic en **Tablero** en la barra de acciones para que pueda ver el estado del reproductor. El panel **INFORMACIÓN DE CANAL** proporciona información sobre si el canal está en línea o sin conexión.

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Haga clic en **Propiedades** en la barra de acciones y vaya a la pestaña **Canal**, como se muestra a continuación:

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Marque el modo **Desarrollador** **para hacer que el canal esté en línea** para que el canal esté en línea.

   Haga clic en **Guardar y cerrar** para guardar la opción.

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Vuelva al panel del canal y ahora el panel **INFORMACIÓN DEL CANAL** mostrará el estado en línea del reproductor.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>Para volver a configurar el canal como sin conexión, anule la selección de la opción Modo de desarrollador en la pestaña **Propiedades** (como se muestra en el paso (3)). A continuación, en el panel **INFORMACIÓN DEL CANAL**, haga clic en **Actualizar contenido sin conexión**, como se muestra en la figura siguiente.

![tablero2](assets/dashboard2.gif)

#### Actualizaciones automáticas y manuales desde el panel de dispositivos {#automatic-versus-manual-updates-from-the-device-dashboard}

La siguiente tabla resume los eventos asociados con las actualizaciones automáticas y manuales desde el panel del dispositivo.

<table>
 <tbody>
  <tr>
   <td><strong>Evento</strong></td>
   <td><strong>Actualización automática del dispositivo</strong></td>
   <td><strong>Actualización manual del dispositivo</strong></td>
  </tr>
  <tr>
   <td>Cambio en el canal en línea</td>
   <td>El contenido se actualiza automáticamente</td>
   <td><p>Contenido actualizado en "Dispositivo: configuración push"</p> <p>O bien,</p> <p>Contenido actualizado en <strong><i>Dispositivo: Restart</i></strong></p> </td>
  </tr>
  <tr>
   <td>Cambio en el canal sin conexión, pero NO se activa "Contenido push" de canal (sin recreación de paquetes sin conexión)</td>
   <td>Sin actualización de contenido</td>
   <td>Sin actualización de contenido</td>
  </tr>
  <tr>
   <td>Cambio en el canal sin conexión y se activa el canal "Contenido push" (nuevo paquete sin conexión)</td>
   <td>El contenido se actualiza automáticamente</td>
   <td><p>Contenido actualizado en <strong><i>Dispositivo: configuración push</i></strong></p> <p>O bien,</p> <p>Contenido actualizado en <strong><i>Dispositivo: Restart</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>Cambiar en la configuración</p>
    <ul>
     <li>Pantalla (canal forzado)</li>
     <li>Dispositivo</li>
     <li>Asignaciones de canales (canal nuevo, canal eliminado)</li>
     <li>Asignación de canal (función, evento, programación)</li>
    </ul> </td>
   <td>La configuración se actualiza automáticamente</td>
   <td><p>La configuración se ha actualizado en <strong><i>Dispositivo: Configuración push</i></strong></p> <p>O bien,</p> <p>Configuración actualizada en <strong><i>Dispositivo: Restart</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Muestras asignadas {#assigned-displays}

El panel **Pantallas asignadas** muestra la pantalla asociada con el canal. Proporciona una instantánea de la visualización asignada junto con la resolución.

Las pantallas asociadas se enumeran en el panel **Pantallas asignadas**, como se muestra a continuación:

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>Para obtener más información sobre la creación de una visualización en una ubicación, consulte:
>
>* [Crear y administrar ubicaciones](managing-locations.md)
>* [Crear y administrar pantallas](managing-displays.md)
>

Además, haga clic en la pantalla del panel **PANTALLAS ASIGNADAS** para ver la información de visualización, como se muestra a continuación:

![chlimage_1-28](assets/chlimage_1-28.png)

### Pasos siguientes {#the-next-steps}

El siguiente paso después de crear un canal y añadir/editar contenido en él es aprender a crear una ubicación y a mostrar. Además, asigne un canal a esa visualización.

Consulte los siguientes recursos para ver los pasos siguientes:

* [Crear y administrar canales](managing-channels.md)
* [Crear y administrar ubicaciones](managing-locations.md)
* [Creación y administración de pantallas](managing-displays.md)
