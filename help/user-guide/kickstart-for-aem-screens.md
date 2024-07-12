---
title: Guía de KickStart
description: Obtenga información sobre cómo crear un proyecto de AEM Screens de demostración. Le ayuda a crear una experiencia de señalización digital que comienza desde la instalación y la configuración de un nuevo proyecto hasta la visualización del contenido en el Reproductor de AEM Screens.
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 2%

---

# Guía de KickStart {#kickstart-guide}

La introducción a AEM Screens muestra cómo configurar y ejecutar un proyecto de AEM Screens. Le guiará a través de la configuración de una experiencia de señalización digital básica y la adición de contenido como recursos o vídeos a cada canal, así como la publicación del contenido en un reproductor de AEM Screens.

>[!NOTE]
>Antes de trabajar en los detalles del proyecto, asegúrese de que ha instalado el último paquete de funciones para AEM Screens. Puede descargar el paquete de funciones más reciente del [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID.

## Requisitos previos {#prerequisites}

Siga los pasos a continuación para crear un proyecto de ejemplo para AEM Screens y publicar contenido en el reproductor de Screens.

>[!NOTE]
>El siguiente tutorial muestra la reproducción del contenido del canal en un reproductor del sistema operativo Chrome.

>[!IMPORTANT]
>**Ajustes de configuración de OSGi**
>Debe habilitar el referente vacío para permitir que el dispositivo publique datos en el servidor. Por ejemplo, si la propiedad referrer vacía está deshabilitada, el dispositivo no podrá devolver una captura de pantalla. Actualmente, algunas de estas funciones solo están disponibles si el Filtro de referente de Apache Sling Permitir vacío está habilitado en la configuración de OSGi. Es posible que el tablero muestre una advertencia indicando que la configuración de seguridad puede impedir que funcionen algunas de estas características.
>Siga los pasos a continuación para habilitar el ***Filtro de referente de Apache Sling Permitir vacío***:


## Permitir solicitudes de referente vacías {#allow-empty-referrer-requests}

1. Vaya a la **configuración de la consola web de Adobe Experience Manager AEM** mediante la instancia de la instancia de > icono de martillo > **Operaciones** > **Consola web**.

   ![imagen](assets/config/empty-ref1.png)

1. **Se abre la configuración de la consola web de Adobe Experience Manager**. Busque el referente de sling.

   Para buscar en la propiedad sling referrer, presione **Comando+F** para **Mac** y **Control+F** para **Windows**.

1. Marque la opción **Permitir vacío**, como se muestra en la figura siguiente.

   ![imagen](assets/config/empty-ref2.png)

1. Haga clic en **Guardar** para habilitar la opción Permitir filtro de referente de Apache Sling vacío.

## Creación de una experiencia de señalización digital en 5 minutos {#creating-a-digital-signage-experience-in-minutes}

### Creación de un proyecto de AEM Screens {#creating-project}

El primer paso es crear un proyecto de AEM Screens.

1. Vaya a la instancia de Adobe Experience Manager AEM () y haga clic en **Screens**. También puede navegar directamente desde `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Haga clic en **Crear proyecto de Screens** para poder crear un proyecto de Screens.
1. Escriba el título como **DemoScreens** y haga clic en **Guardar**.

   ![imagen](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Después de crear el proyecto, vuelve a la página principal del proyecto de AEM Screens. Ahora puede hacer clic en el proyecto. En un proyecto, hay cinco carpetas diferentes con los títulos **Aplicaciones**, **Canales**, **Dispositivos**, **Ubicaciones** y **Programas**.

### Creación de un canal {#creating-channel}

Una vez creado el proyecto de AEM Screens, cree un canal donde administre el contenido.

Siga los pasos a continuación para crear un canal para su proyecto:

1. Después de crear un proyecto, haz clic en el proyecto **DemoScreens** y luego haz clic en la carpeta **Canales**, como se muestra en la figura siguiente. Haga clic en **+ Crear** en la barra de acciones.

   ![imagen](assets/kickstart/demo-2.png)

1. Elija **Canal de secuencia** del asistente y haga clic en **Siguiente**.
   ![imagen](assets/kickstart/demo-3.png)

1. Escriba **Title** como **TestChannel** y haga clic en **Crear**.

   ![imagen](assets/kickstart/demo-4.png)

   **TestChannel** se agrega ahora a la carpeta de canales, como se muestra en la figura siguiente.

   ![imagen](assets/kickstart/demo-5.png)

### Adición de contenido a un canal {#adding-content}

Cuando tenga el canal configurado, agregue contenido al canal que el Reproductor de AEM Screens pueda mostrar.

Siga los pasos a continuación para agregar contenido al canal (**TestChannel**) en su proyecto:

1. Vaya al **DemoProject** que ha creado y haga clic en **TestChannel** desde la carpeta **Channels**.

1. Haga clic en **Editar** en la barra de acciones (vea la figura siguiente). Se abre el editor de **TestChannel**.

   ![imagen](assets/kickstart/demo-6.png)

1. Haga clic en el icono que conmuta el panel lateral del lado izquierdo de la barra de acciones para abrir los recursos y componentes.

1. Arrastre y suelte los componentes que desee añadir al canal.

   ![imagen](assets/kickstart/demo-7.png)

### Creación de una ubicación {#creating-location}

Cuando tenga el canal configurado, cree una ubicación.

>[!NOTE]
>***Ubicaciones*** divide en compartimentos las distintas experiencias de señalización digital y contiene las configuraciones de las pantallas según dónde se encuentren.

Siga los pasos a continuación para crear una ubicación para su proyecto:

1. Vaya al **DemoProject** que ha creado y haga clic en la carpeta **Ubicaciones**.
1. Haga clic en **+ Crear** en la barra de acciones.
1. Haga clic en **Ubicación** en el asistente y, a continuación, haga clic en **Siguiente**.
1. Escriba **Name** para su ubicación (escriba el título como **TestLocation**) y haga clic en **Crear**.

Se crea **TestLocation** y se agrega a la carpeta **Ubicaciones**.


### Creación de una visualización para la ubicación {#creating-display}

Cuando haya creado una ubicación, cree una pantalla para la ubicación.

>[!NOTE]
>***Pantalla*** representa la experiencia digital que se ejecuta en una o varias pantallas.

1. Vaya a **TestLocation** y haga clic en ella.
1. Haga clic en **Crear** en la barra de acciones.

   ![imagen](assets/kickstart/demo-disp1.png)

1. Haga clic en **Mostrar** en el asistente de **Crear** y luego haga clic en **Siguiente**.

   ![imagen](assets/kickstart/demo-disp2.png)

1. Escriba **Title** como **LobbyDisplay** y haga clic en **Crear**.

   ![imagen](assets/kickstart/demo-disp3.png)

   Ahora se agrega una nueva pantalla con el título **TestDisplay** a su ubicación **TestLocation**, como se muestra en la figura siguiente.

   ![imagen](assets/kickstart/demo-disp4.png)

### Asignación de un canal {#assigning-channel}

Cuando finalice la configuración del proyecto, asigne el canal a una pantalla para ver el contenido.

1. Vaya a la pantalla requerida en **DemoScreens** > **Ubicaciones** > **TestLocation** > **LobbyDisplay**.

1. Haga clic en **Asignar canal** en la barra de acciones.

   ![imagen](assets/kickstart/demo-assign1.png)

   O bien,

   Haga clic en **Tablero** de la barra de acciones y, a continuación, haga clic en **+Asignar canal** en el panel **CANALES Y PROGRAMACIONES ASIGNADOS**.

   ![imagen](assets/kickstart/demo-assign2.png)

1. Se abre el cuadro de diálogo **Asignación de canal**.

1. En la opción **Settings**, elija el canal **por ruta** y **Eventos compatibles** como **Carga inicial** y **Pantalla inactiva**.

   >[!NOTE]
   >
   >**El rol de canal**, **Prioridad** y **Métodos de interrupción** se rellenan de manera predeterminada. Consulte la sección [Propiedades del canal](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) para obtener más información sobre las propiedades de asignación de canal.

   ![imagen](assets/kickstart/demo-assign3.png)

   Además, puede hacer clic en **Ventana de activación** y **Programación de periodicidad**.

   >[!NOTE]
   >*Programación de periodicidad* le permite establecer una programación recurrente para su canal. Puede configurar varias programaciones de periodicidad para un canal.
   >Consulte [Programación de periodicidad](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) para obtener más información.

1. Haz clic en **Guardar** una vez que hayas configurado tus preferencias.

### Registro de un dispositivo y asignación de un dispositivo a una pantalla {#registering-device}

AEM Registre el dispositivo mediante el panel de control de.

>[!IMPORTANT]
>El reproductor Chrome OS se puede instalar como complemento del explorador de Chrome en modo de desarrollador sin necesidad de un dispositivo Chrome Player real. Para la instalación, siga los pasos a continuación:
>
>1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar el último reproductor de Chrome.
>1. Descomprima y guárdelo en el disco.
>1. Abra el explorador Chrome y haga clic en **Extensiones** en el menú o vaya directamente a ***chrome://extensions***.
>1. Encienda el **modo de desarrollador** desde la esquina superior derecha.
>1. Haga clic en **Cargar desempaquetado** en la esquina superior izquierda y cargue el reproductor de Chrome descomprimido.
>1. Compruebe el complemento **AEM Screens Chrome Player** si está disponible en la lista de extensiones.
>1. Abra una ficha nueva y haga clic en el icono **Aplicaciones** desde la esquina superior izquierda o navegue directamente a ***chrome://apps***.
>1. Haga clic en el complemento **AEM Screens** para iniciar el Reproductor de Chrome. De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **Esc** para salir del modo de pantalla completa.

Una vez que el reproductor del sistema operativo Chrome esté encendido, siga los pasos a continuación para registrar un dispositivo Chrome.

1. AEM Vaya a la carpeta **Dispositivos** de su proyecto desde la instancia de la.

1. Haga clic en **Administrador de dispositivos** en la barra de acciones.

   ![imagen](assets/kickstart/demo-register1.png)

1. Haga clic en **Registro de dispositivo** en la parte superior derecha.

1. Haga clic en el dispositivo requerido y luego en **Registrar dispositivo**.

   ![imagen](assets/kickstart/demo-register2.png)

1. Espere a que el dispositivo envíe su código de registro y compruebe simultáneamente el **código de registro** desde su dispositivo Chrome.
   ![imagen](assets/kickstart/demo-register3.png)

1. AEM Si el **código de registro** es el mismo en ambos equipos, haga clic en **Validar** en la.

1. Establezca el nombre deseado como **ChromeDeviceForDemo** para el dispositivo y haga clic en **Registrar**.

   ![imagen](assets/kickstart/demo-register4.png)

1. Haga clic en **Asignar pantalla** en el cuadro de diálogo **Registro de dispositivo correcto**.

   ![imagen](assets/kickstart/demo-register5.png)

1. Haga clic en la ruta de acceso a la pantalla como **DemoScreens** > **Ubicaciones** > **TestLocation** > **LobbyDisplay** y haga clic en **Asignar**.

   ![imagen](assets/kickstart/demo-device6.png)

1. Cuando el dispositivo se asigne correctamente, verá la siguiente confirmación.

   ![imagen](assets/kickstart/demo-register8.png)

1. Haga clic en **Finalizar** para completar el proceso de registro. Ahora puede ver el dispositivo registrado en el panel de visualización.

   ![imagen](assets/kickstart/demo-register9.png)

### Visualización del contenido en el reproductor de Chrome {#viewing-content-output}

Todos los recursos del canal se están reproduciendo en el reproductor del sistema operativo Chrome.

¡Felicidades por reproducir contenido en un canal de AEM Screens!

![imagen](assets/kickstart/demo-video-screens.gif)
