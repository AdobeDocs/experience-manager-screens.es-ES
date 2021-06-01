---
title: Crear y administrar canales
seo-title: Administrar canales
description: Siga esta página para obtener más información sobre la creación y administración de canales. También explica el portal del canal y el contenido de edición de un canal.
seo-description: Siga esta página para obtener más información sobre la creación y administración de canales. También explica el portal del canal y el contenido de edición de un canal.
feature: Creación en Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 42%

---


# Crear y administrar canales {#creating-and-managing-channels}

Un canal muestra una secuencia de contenido (imágenes y vídeos) y también muestra un sitio web o una aplicación de una sola página.

En esta página se muestra la creación y administración de canales para AEM Screens.

**Requisitos previos**:

* [Configurar e implementar Screens](configuring-screens-introduction.md)
* [Crear y administrar proyecto de Screens](creating-a-screens-project.md)

## Crear un nuevo canal {#creating-a-new-channel}

Una vez que haya creado el proyecto para AEM Screens, siga los pasos a continuación para crear un nuevo canal para el proyecto:

1. Seleccione el vínculo de Adobe Experience Manager (parte superior izquierda) y luego seleccione Screens. Alternativamente, puede navegar directamente a `https://localhost:4502/screens.html/content/screens`.

1. Vaya al proyecto Screens y seleccione la carpeta **Channels** .

1. Haga clic en **Crear** en la barra de acciones.

   ![demochannel](assets/create-channel1.png)

1. Seleccione la plantilla **Sequence Channel** del asistente **Create** y haga clic en **Next**.

   ![demochannel](assets/create-channel2.png)

1. Introduzca el Título como **ScreensChannel** y haga clic en **Crear**.

   ![demochannel](assets/create-project4.png)

1. Ahora se agrega un canal de secuencia a la carpeta **Channels**.

### Tipos de canales {#channel-types}

Las opciones de plantilla siguientes están disponibles mientras utiliza el asistente, por ejemplo:

| **Opción de plantilla** | **Descripción** |
|---|---|
| Carpeta de canales | Permite crear una carpeta para almacenar la colección de canales. |
| Canal de secuencia | Permite crear un canal que reproduzca los componentes de forma secuencial (uno por uno en una presentación con diapositivas). |
| Canal de aplicaciones | Permite mostrar la aplicación web personalizada en el reproductor Screens. |
| Canal de pantalla dividida 1x1 | Permite ver el componente en una sola zona. |
| Canal de pantalla dividida 1x2 | Permite ver los recursos en dos zonas (divididos horizontalmente). |
| Canal de pantalla dividida 2X1 | Permite ver los recursos en dos zonas (divididos verticalmente). |
| Canal de pantalla dividida 2x2 | Permite ver los recursos en cuatro zonas (divididos horizontal y verticalmente en una matriz). |
| Canal de pantalla dividida 2 a 3 | Permite ver los recursos en dos zonas (divididas horizontalmente), siendo una de ellas más grande que la otra. |
| Canal de pantalla dividida de barras L izquierda o derecha | Permite a los autores de contenido ver diferentes tipos de recursos en zonas de tamaño adecuado. |

>[!NOTE]
>
>Los canales Dividir pantalla dividen la visualización en varias zonas para que pueda reproducir varias experiencias al mismo tiempo, en paralelo. Las experiencias pueden ser recursos estáticos/texto o secuencias incrustadas.

>[!IMPORTANT]
>
> Una vez que cree y añada contenido al canal, el siguiente paso es crear una ubicación seguida de una visualización. Además, debe asignar ese canal a una pantalla. Consulte los siguientes recursos que se encuentran al final de la sección para obtener más información.

## Uso de canales {#working-with-channels}

Puede editar, ver las propiedades y el panel, y copiar, acceder a la vista previa y eliminar un canal.


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Añadir/editar el contenido de un canal {#adding-editing-content-to-a-channel}

Para añadir o editar contenido en un canal, siga los pasos que se indican a continuación:

1. Seleccione el canal que desee editar (como se muestra en la figura anterior).
1. Haga clic en **Editar** en la esquina superior izquierda de la barra de acciones para editar las propiedades del canal. El editor que se abra le permitirá añadir recursos o componentes al canal que quiera publicar.

>[!NOTE]
>Puede añadir componentes al canal. Consulte **[Añadir componentes a un canal](adding-components-to-a-channel.md)** para obtener más información.

![demochannel1](assets/demochannel1.gif)

**Cargar vídeos al canal**

Siga los pasos a continuación para cargar los vídeos en el canal:

1. Seleccione el canal en el que desee cargar el vídeo.
1. Haga clic en **Editar** en la barra de acciones para abrir el editor.
1. Seleccione los **vídeos** en la opción Recursos y arrastre y suelte los vídeos necesarios.

>[!NOTE]
>Si tiene problemas al cargar vídeos en el canal, consulte [Solución de problemas con los vídeos](troubleshoot-videos.md).

### Visualizar propiedades {#viewing-properties}

Para ver o editar las propiedades de un canal, siga los pasos que se indican a continuación:

1. Haga clic en el canal que desee editar.
1. Haga clic en **Properties** en la barra de acciones para ver o editar las propiedades del canal. Las fichas siguientes le permiten cambiar las opciones.

![propiedades](assets/properties.gif)

### Visualización del tablero {#viewing-dashboard}

Para ver el panel de un canal, siga los pasos que se indican a continuación:

1. Seleccione el canal que desee editar.
1. Haga clic en **Tablero** en la barra de acciones para ver el tablero. Se abre el panel **CHANNEL INFORMATION**,**ASSIGNED DISPLAYS** y **PENDING LAUNCHES**, como se muestra en la figura siguiente:

![tablero](assets/dashboard.gif)

### Información del canal {#channel-information}

El panel Información de canal describe las propiedades del canal, junto con la vista previa del canal. Asimismo, proporciona información sobre si el canal está en línea o sin conexión.

Haga clic en (**...**) de la barra de acciones **INFORMACIÓN DEL CANAL** para ver las propiedades, editar el contenido o actualizar la caché (contenido sin conexión) del canal.

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### Visualización del manifiesto {#view-manifest}

Puede ver el manifiesto desde el panel del canal.

>[!IMPORTANT]
>Esta opción solo está disponible con AEM 6.4 Feature Pack 8 o AEM 6.5 Feature Pack 4.

Siga estos pasos para habilitar esta opción desde el panel del canal:

1. **Definir el canal como sin conexión**
   1. Seleccione el canal y seleccione **Properties** en la barra de acciones
   1. Vaya a la pestaña **Channel** y asegúrese de desmarcar la opción **Developer Mode (force channel to be online)**
   1. Haga clic en **Guardar y cerrar**
1. **Actualizar contenido sin conexión**
   1. Seleccione el canal y seleccione **Dashboard** en la barra de acciones
   1. Vaya al panel **CHANNEL INFORMATION** y haga clic en *...*
   1. Haga clic en **Actualizar contenido sin conexión**

Debería ver la opción **Ver manifiesto** del panel **INFORMACIÓN DEL CANAL** en el panel del canal.

![image1](assets/channel-one.png)


### Canales en línea y sin conexión {#online-and-offline-channels}

>[!NOTE]
>De forma predeterminada, cuando se crea un canal, se encuentra sin conexión.

Cuando cree un canal, podrá definirlo como un canal en línea o sin conexión.

Un ***canal en línea*** mostrará el contenido actualizado en el entorno en tiempo real, mientras que ***un canal sin conexión*** muestra el contenido almacenado en caché.

Siga los pasos que se describen para crear el canal en línea:

1. Desplácese al canal denominado **TestProject** --> **Canales** --> **TestChannel**.

   Seleccione el canal.

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Haga clic en **Dashboard** en la barra de acciones para ver el estado del reproductor. El panel **INFORMACIÓN DE CANAL** proporciona información sobre si el canal está en línea o sin conexión.

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Haga clic en **Propiedades** en la barra de acciones y desplácese a la ficha **Canal** tal como se muestra a continuación:

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Compruebe el modo **Developer** **(forzar el canal a estar en línea)** para que el canal esté en línea.

   Haga clic en **Guardar y cerrar** para guardar su elección.

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Vuelva al panel del canal y ahora el panel **CHANNEL INFORMATION** muestra el estado en línea del reproductor.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>Si desea configurar el canal de nuevo como sin conexión, desmarque la opción Modo de desarrollador en la pestaña **Properties** (como se muestra en el paso (3)) y luego en el panel **CHANNEL INFORMATION** haga clic en **Actualizar contenido sin conexión**, como se muestra en la figura siguiente.

![panel2](assets/dashboard2.gif)

#### Actualizaciones automáticas frente a manuales del panel del dispositivo {#automatic-versus-manual-updates-from-the-device-dashboard}

En la tabla siguiente se resumen los eventos asociados a las actualizaciones automáticas y manuales del panel del dispositivo.

<table>
 <tbody>
  <tr>
   <td><strong>Evento</strong></td>
   <td><strong>Actualización automática de dispositivos</strong></td>
   <td><strong>Actualización manual del dispositivo</strong></td>
  </tr>
  <tr>
   <td>Cambio en el canal en línea</td>
   <td>El contenido se actualiza automáticamente</td>
   <td><p>Contenido actualizado en "Dispositivo: Configuración push"</p> <p>O bien,</p> <p>Contenido actualizado en <strong><i>Dispositivo: Reiniciar</i></strong></p> </td>
  </tr>
  <tr>
   <td>El cambio en el canal sin conexión, pero el "contenido push" del canal NO se activa (no se vuelve a crear el paquete sin conexión)</td>
   <td>Sin actualización de contenido</td>
   <td>Sin actualización de contenido</td>
  </tr>
  <tr>
   <td>Se activa el cambio en el canal sin conexión y el canal "Contenido push" (nuevo paquete sin conexión)</td>
   <td>El contenido se actualiza automáticamente</td>
   <td><p>Contenido actualizado en <strong><i>Dispositivo: Configuración push</i></strong></p> <p>O bien,</p> <p>Contenido actualizado en <strong><i>Dispositivo: Reiniciar</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>Cambio en la configuración</p>
    <ul>
     <li>Visualización (canal forzado)</li>
     <li>Dispositivo</li>
     <li>Asignaciones de canales (canal nuevo, canal eliminado)</li>
     <li>Asignación de canales (función, evento, programación)</li>
    </ul> </td>
   <td>La configuración se actualizó automáticamente</td>
   <td><p>Configuración actualizada en <strong><i>Dispositivo: Configuración push</i></strong></p> <p>O bien,</p> <p>Configuración actualizada en <strong><i>Dispositivo: Reiniciar</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Visualizaciones asignadas {#assigned-displays}

El panel de visualizaciones asignado muestra la visualización asociada al canal. Proporciona una instantánea de la visualización asignada junto con la resolución.

Las visualizaciones asociadas se incluirán en el panel **Visualizaciones asignadas**, tal como se muestra a continuación:

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>Para obtener más información sobre la creación de una visualización en una ubicación, consulte:
>
>* [Crear y administrar ubicaciones](managing-locations.md)
* [Crear y administrar visualizaciones](managing-displays.md)



Además, haga clic en la visualización del panel **VISUALIZACIONES ASIGNADAS**, para ver la información que se visualizará, tal y como se muestra a continuación:

![chlimage_1-28](assets/chlimage_1-28.png)

### Pasos siguientes {#the-next-steps}

El siguiente paso después de crear un canal y añadir o editar el contenido del canal es aprender a crear una ubicación y una visualización. Además, debe asignar un canal a esa pantalla. 

Consulte los recursos siguientes para ver los pasos siguientes:

* [Crear y administrar canales](managing-channels.md)
* [Crear y administrar ubicaciones](managing-locations.md)
* [Crear y administrar visualizaciones](managing-displays.md)

