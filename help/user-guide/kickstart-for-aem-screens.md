---
title: Guía de inicio rápido
seo-title: Guía de inicio rápido
description: Siga esta página para crear un proyecto de demostración de AEM Screens. Le ayuda a crear una experiencia de señalización digital desde la instalación y la configuración de un nuevo proyecto hasta la visualización del contenido en el reproductor de AEM Screens.
translation-type: tm+mt
source-git-commit: f2fef18cc73825b3f062a79c560097e8fd00ac9f
workflow-type: tm+mt
source-wordcount: '1080'
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

### Creating a new AEM Screens Project {#creating-project}

El primer paso es crear un nuevo proyecto de AEM Screens.

1. Vaya a la instancia de Adobe Experience Manager (AEM) y haga clic en **Pantallas**. También puede desplazarse directamente desde `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![image](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Una vez creado el proyecto, vuelve a la página de inicio del proyecto Screens. Puede seleccionar el proyecto. En un proyecto, hay cinco carpetas diferentes tituladas **Aplicaciones**, **Canales**, **Dispositivos**, **Ubicaciones** y **Programaciones**.


### Crear un nuevo canal {#creating-channel}

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

1. Navigate to the *Test_Project* you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the *TestChannel* opens.

1. Haga clic en el icono que alterna el panel lateral del lado izquierdo de la barra de acciones para abrir los recursos y componentes.

1. Arrastre los componentes que quiera añadir y colóquelos en el canal.

   ![chlimage_1-8](assets/chlimage_1-8.png)

En este ejemplo, el editor muestra una imagen agregada al canal.

![chlimage_1-9](assets/chlimage_1-9.png)

### Crear una nueva ubicación {#creating-location}

Una vez que haya colocado el canal, deberá crear su ubicación.

***Las ubicaciones*** compartimentan las distintas experiencias de señalización digital y contienen las configuraciones de las pantallas según dónde estén las distintas pantallas.

Siga los pasos a continuación para crear una nueva ubicación para el proyecto:

1. Navigate to the *Test_Project* you created and select the **Locations** folder.

1. Haga clic en **Crear** junto al icono del signo más en la barra de acciones (consulte la figura siguiente). Se abrirá un asistente.
1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** and **Title** for your location (enter the title as *TestLocation*) and click **Create**.

   ![chlimage_1-10](assets/chlimage_1-10.png)

Se crea *TestLocation* y se agrega a la carpeta **Locations** .

![chlimage_1-11](assets/chlimage_1-11.png)

### Creación de una nueva visualización para TestLocation {#creating-display}

Una vez que haya creado una ubicación, deberá crear una nueva pantalla para la ubicación.

***Las pantallas*** representan la experiencia digital que se ejecuta en una o varias pantallas.

1. Vaya a la ubicación en la que desea crear la visualización (*Test_* Project —> **Ubicaciones** —> *TestLocation)* como se muestra en la figura de arriba y seleccione *TestLocation*.

1. Haga clic en **Crear** en la barra de acciones.
1. Select **Display** from the **Create** wizard and click **Next**.

1. Introduzca **Nombre** y **Título** para la ubicación de visualización (introduzca el título como *TestDisplay*).

1. Under the **Display** tab, choose the details of the Layout.

   1. Choose the **Resolution** as **Full HD**.

   1. Choose the **Number of Devices Horizontally** as 1.

   1. Choose the **Number of Devices Vertically** as 1.

   1. Haga clic en **Crear**.

Se agrega una nueva pantalla (*TestDisplay*) a su ubicación *TestLocation)*, como se muestra en la figura siguiente.

![chlimage_1-12](assets/chlimage_1-12.png)

### Asignación de un canal {#assigning-channel}

1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.

1. Select *TestDisplay* and tap/click **Assign Channel **from the action bar, *Or*,

1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **Se abre el cuadro de diálogo Asignación** de canal.

1. Select **Reference Channel** by **path**

1. Enter the **Channel Role** as *LiveStream*.

1. Seleccione la ruta **de** Canal (*Test_Project* —> *Canales* —> *TestChannel* ) en el **Canal**.

1. Select the **Priority** for this channel as *1*.

1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.

1. Introduzca **Programar** y seleccione las fechas **activas desde** y **activas hasta**.

1. Haga clic en **Guardar**.

El canal se crea y se agrega al panel.

![chlimage_1-15](assets/chlimage_1-15.png)

### Registro de un dispositivo {#registering-device}

Debe registrar el dispositivo mediante el panel de AEM.

>[!NOTE]
>Puede abrir el reproductor de pantallas con la aplicación de AEM Screens que ha descargado o con el navegador web.



### Viewing the content in AEM Screens Player {#viewing-the-content-in-screens-player}

Una vez que haya agregado las configuraciones anteriores, el reproductor debería mostrar automáticamente el canal predeterminado para la visualización en el dispositivo.

![chlimage_1-23](assets/chlimage_1-23.png)

Consulte [AEM Screens Player](working-with-screens-player.md) para obtener información más detallada sobre AEM Screens Player.
