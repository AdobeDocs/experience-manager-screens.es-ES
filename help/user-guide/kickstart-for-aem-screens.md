---
title: Guía de inicio rápido
seo-title: Guía de inicio rápido
description: Siga esta página para crear un proyecto de demostración de AEM Screens. Le ayuda a crear una experiencia de señalización digital desde la instalación y la configuración de un nuevo proyecto hasta la visualización del contenido en el reproductor de AEM Screens.
translation-type: tm+mt
source-git-commit: 78ddd2b45f39d69b66f740910327eef475bcdcac
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 6%

---


# Guía de inicio rápido {#kickstart-guide}

Esta sección es un inicio rápido para AEM Screens y muestra cómo configurar y ejecutar un proyecto de AEM Screens. Le guiará a través de la configuración de una experiencia de señalización digital básica y la adición de contenido como recursos y/o vídeos a cada canal, y la posterior publicación del contenido en un reproductor de AEM Screens.

>[!NOTE]
>Antes de comenzar a trabajar con los detalles del proyecto, asegúrese de haber instalado el último Feature Pack. Puede descargar el paquete de funciones más reciente para AEM Screens 6.5.5 desde el portal [de distribución de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) software con su Adobe ID.

## Creación de una experiencia de señalización digital en 5 minutos {#creating-a-digital-signage-experience-in-minutes}

Siga los pasos a continuación para crear un proyecto de muestra para AEM Screens y publicar contenido en Screens Player.

>[!NOTE]
>El siguiente tutorial muestra cómo reproducir el contenido del canal en el reproductor de Chrome OS.

>[!IMPORTANT]
>**Configuración de OSGi**
>Debe habilitar el remitente del reenvío vacío para permitir que el dispositivo publique datos en el servidor. Por ejemplo, si la propiedad de remitente del reenvío vacía está deshabilitada, el dispositivo no puede publicar una captura de pantalla de nuevo. Actualmente, algunas de estas funciones solo están disponibles si el filtro Remitente del reenvío Sling de Apache Permitir vacío está habilitado en la configuración OSGi. El panel puede mostrar una advertencia de que la configuración de seguridad puede impedir que algunas de estas funciones funcionen.
>Siga los pasos a continuación para habilitar el filtro de Remitente del reenvío Sling de ***Apache para permitir que esté vacío***:


## Permitir solicitudes de Remitente del reenvío vacías {#allow-empty-referrer-requests}

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante AEM instancia —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![image](assets/config/empty-ref1.png)

1. **Se abre la Configuración** de Adobe Experience Manager Web Console. Buscar remitente del reenvío sling.

   Para buscar la propiedad de remitente del reenvío sling, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **Permitir vacío** , como se muestra en la figura siguiente.

   ![image](assets/config/empty-ref2.png)

1. Haga clic en **Guardar** para activar el filtro de Remitente del reenvío Sling de Apache Permitir vacío.


## Tutorial {#tutorial}

### Creating an AEM Screens Project {#creating-project}

El primer paso es crear un nuevo proyecto de AEM Screens.

1. Vaya a la instancia de Adobe Experience Manager (AEM) y haga clic en **Pantallas**. También puede desplazarse directamente desde `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![image](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Una vez creado el proyecto, vuelve a la página de inicio del proyecto Screens. Puede seleccionar el proyecto. En un proyecto, hay cinco carpetas diferentes tituladas **Aplicaciones**, **Canales**, **Dispositivos**, **Ubicaciones** y **Programaciones**.


### Crear un canal{#creating-channel} 

Una vez que haya implementado el proyecto, deberá crear un nuevo canal en el que administrar el contenido.

Siga los pasos a continuación para crear un nuevo canal para su proyecto:

1. Una vez creado un proyecto, seleccione el proyecto **DemoScreens** y seleccione la carpeta **** Canales, como se muestra en la figura siguiente. Click **+ Create** from the action bar.

   ![image](assets/kickstart/demo-2.png)

1. Elija el Canal **** Secuencia en el asistente y haga clic en **Siguiente**.
   ![image](assets/kickstart/demo-3.png)

1. Enter the **Title** as *TestChannel* and click **Create**.

   ![image](assets/kickstart/demo-4.png)

Se crea *TestChannel* y se agrega a la carpeta canales, como se muestra en la figura siguiente.

![image](assets/kickstart/demo-5.png)

### Adding Content to a Channel {#adding-content}

Una vez que haya colocado el canal, deberá añadir contenido al canal que mostrará el reproductor de Pantallas.

Siga los pasos a continuación para agregar contenido al canal (*TestChannel*) de su proyecto:

1. Navigate to the **DemoProject** you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the **TestChannel** opens.

   ![image](assets/kickstart/demo-6.png)

1. Haga clic en el icono que alterna el panel lateral del lado izquierdo de la barra de acciones para abrir los recursos y componentes.

1. Arrastre los componentes que quiera añadir y colóquelos en el canal.

   ![image](assets/kickstart/demo-7.png)

### Creación de una ubicación{#creating-location} 

Una vez que haya colocado el canal, debe crear una ubicación.

>[!NOTE]
>***Las ubicaciones*** compartimentan las distintas experiencias de señalización digital y contienen las configuraciones de las pantallas según dónde estén las distintas pantallas.

Siga los pasos a continuación para crear una nueva ubicación para el proyecto:

1. Navigate to the **DemoProject** you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

Se crea **TestLocation** y se agrega a la carpeta **Locations** .


### Creación de una visualización para una ubicación {#creating-display}

Una vez que haya creado una ubicación, deberá crear una nueva pantalla para la ubicación.

>[!NOTE]
>***Las pantallas*** representan la experiencia digital que se ejecuta en una o varias pantallas.

1. Vaya a **TestLocation** y selecciónelo.

1. Haga clic en **Crear** en la barra de acciones.

1. Select **Display** from the **Create** wizard and click **Next**.

1. Enter the **Title** as **LobbyDisplay** and click **Create**.

Ahora se agrega una nueva pantalla titulada **TestDisplay** a su ubicación **TestLocation**, como se muestra en la figura siguiente.

### Assigning a Channel {#assigning-channel}

Una vez que se haya completado la configuración del proyecto, debe asignar el canal a una pantalla para vista del contenido.

1. Navigate to the required display, for example, **DemoScreens** --> **Locations** --> **TestLocation** --> **LobbyDisplay**.

1. Tap/click **Assign Channel** from the action bar.

   O bien,

   Toque o haga clic en **Panel** en la barra de acciones y haga clic en **+Asignar Canal** en el panel CANALES y PROGRAMAS **ASIGNADOS** .

1. The **Channel Assignment** dialog box opens.

1. En la opción **Configuración** , puede elegir el canal **por ruta** o **por nombre**, introducir la función **de** Canal, la **prioridad**********, los Eventos compatiblesy los métodos de interrupción. Además, puede activar la información de objeto de atracción desde este cuadro de diálogo.


   >[!NOTE]
   >Consulte la sección Propiedades del [Canal](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) para obtener más información sobre las propiedades de asignación de canales.

1. En la opción **Programar** , seleccione la Ventana **de** Activación y la Programación **de** periodicidad.

1. Haga clic en **Guardar** una vez que haya configurado las preferencias.

### Registro de un dispositivo {#registering-device}

Debe registrar el dispositivo mediante el panel de AEM.

### Visualización del contenido en Chrome Player {#viewing-content-output}

Este ejemplo muestra la salida en un reproductor Chrome. Una vez que haya asignado el canal a la pantalla, debe registrar el dispositivo en un reproductor.



