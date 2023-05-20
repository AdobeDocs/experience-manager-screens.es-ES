---
title: Creación y administración de pantallas
seo-title: Managing Displays
description: Siga esta página para obtener más información sobre la creación de una nueva pantalla y configuración del dispositivo. Además, obtenga información acerca del panel de visualización.
seo-description: Follow this page to learn about creating a new display and device config. Additionally, learn about the display dashboard.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# Creación y administración de pantallas {#creating-and-managing-displays}

Una visualización es una agrupación virtual de pantallas que normalmente se colocan una al lado de la otra. La pantalla suele ser permanente con respecto a una instalación. Estos serán los objetos con los que los autores de contenido trabajarán y a los que siempre se hará referencia como visualización lógica en lugar de sus partes de contador físicas.

Una vez creada una ubicación, debe crear una nueva pantalla para la ubicación.

En esta página se muestra la creación y administración de pantallas.

**Requisitos previos**:

* [Configuración e implementación de Screens](configuring-screens-introduction.md)
* [Crear y administrar un proyecto de Screens](creating-a-screens-project.md)
* [Crear y administrar canales](managing-channels.md)
* [Crear y administrar ubicaciones](managing-locations.md)

## Creación de una nueva pantalla {#creating-a-new-display}

>[!NOTE]
>
>Debe crear una ubicación antes de crear una visualización. Para ver cómo crear una ubicación, consulte [Crear y administrar ubicaciones](managing-locations.md) para obtener más información.

Para crear una nueva pantalla en su ubicación, siga los pasos a continuación:

1. Vaya a la ubicación adecuada, por ejemplo `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Seleccione la carpeta de ubicación y pulse o haga clic en ella **Crear** situado junto al icono más en la barra de acciones. Se abrirá un asistente.
1. Seleccionar **Mostrar** desde el **Crear** y haga clic en **Siguiente**.

1. Entrar **Nombre** y **Título** para la ubicación de visualización.

1. En el **Mostrar** pestaña, elija los detalles del diseño. Elija el que desee **Resolución** (ejemplo: como, como **HD completo**). Además, puede elegir el número de dispositivos horizontal y verticalmente.

1. Haga clic en **Crear**.

La pantalla (*StoreDisplay*) se crea y se agrega a la ubicación (*San José*).

![exhibición](assets/display.gif)

Una vez que tenga la visualización en posición, el siguiente paso será crear una configuración de dispositivo para esa visualización en particular. Siga la sección siguiente para crear una nueva configuración de dispositivo.

>[!NOTE]
>
>**El siguiente paso**:
>
>Una vez creada una pantalla para la ubicación, debe asignar un canal a la pantalla para aprovechar el contenido.
>
>Consulte [Asignar canales](channel-assignment.md) para obtener información sobre cómo asignar un canal a la visualización.

## Creación de una nueva configuración de dispositivo {#creating-a-new-device-config}

Una configuración de dispositivo actúa como marcador de posición para un dispositivo de señalización digital real que aún no está instalado.

Siga los pasos a continuación para crear una nueva configuración de dispositivo:

1. Vaya a la pantalla adecuada, por ejemplo, `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Seleccione la carpeta de visualización y pulse o haga clic en ella **Ver tablero** en la barra de acciones.
1. Pulse o haga clic en **+ Agregar configuración de dispositivo** en la parte superior derecha de la **Dispositivos** panel.

1. Seleccione el **Configuración del dispositivo** como la plantilla requerida y pulse o haga clic en **Siguiente**.

1. Introduzca las propiedades según sea necesario y pulse o haga clic en **Crear**.

La configuración del dispositivo se crea y se añade a la visualización actual (en la siguiente demostración, la nueva configuración del dispositivo es *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Una vez que la configuración de un dispositivo esté configurada en su pantalla en la ubicación, el siguiente paso será asignar un canal a su pantalla.

>[!NOTE]
>
>Una vez que la configuración de un dispositivo esté configurada en su pantalla en la ubicación, el siguiente paso será asignar un canal a su pantalla.
>
>Como se muestra en la figura siguiente, si la configuración del dispositivo se muestra como sin asignar en la **DISPOSITIVOS** panel, si no se ha asignado ningún canal a esa configuración de dispositivo en particular.
>
>Debe tener conocimientos previos sobre la creación y administración de canales. Consulte [Crear y administrar canales](managing-channels.md) para obtener más información.

![chlimage_1-9](assets/chlimage_1-9.png)

## Tablero de visualización {#display-dashboard}

El panel de visualización le proporciona diferentes paneles para administrar los dispositivos de visualización y las configuraciones de dispositivo de su dispositivo.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Puede seleccionar las listas de tableros y las acciones masivas de déclencheur en los elementos, en lugar de pasar por cada elemento individualmente.
>
>Por ejemplo, la siguiente imagen muestra cómo se pueden seleccionar varios canales desde el panel de visualización.

![cqdoc9456](assets/cqdoc9456.gif)

### Mostrar panel de información {#display-information-panel}

El **MOSTRAR INFORMACIÓN** El panel proporciona las propiedades de visualización.

Haga clic en el icono (**...**), en la esquina superior derecha de la **MOSTRAR INFORMACIÓN** para ver las propiedades y previsualizar la visualización.


#### Visualización de propiedades {#viewing-properties}

Clic **Propiedades** para ver o cambiar las propiedades de la pantalla.

Además, puede ajustar el valor del temporizador de evento del canal interactivo en **Tiempo de espera inactivo** propiedad en **Mostrar** pestaña. El valor predeterminado se establece en *300 segundos*.

Uso **CRXDE Lite**, para acceder a **inactiveTimeout** propiedad, es decir, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Panel de canales asignados {#assigned-channels-panel}

El **CANALES ASIGNADOS** el panel muestra los canales asignados a este dispositivo.


### Panel Dispositivos {#devices-panel}

El **DISPOSITIVOS** El panel proporciona información sobre las configuraciones del dispositivo.

Haga clic en el icono (**...**), en la esquina superior derecha de la **DISPOSITIVOS** panel para añadir configuraciones de dispositivo y actualizar dispositivos.

Además, haga clic en la configuración del dispositivo para ver las propiedades, asignar un dispositivo o eliminarlo por completo.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Pasos siguientes {#the-next-steps}

Una vez que haya terminado de crear una pantalla para su ubicación, debe asignar un canal a la pantalla.

Consulte [Asignar canales](channel-assignment.md) para obtener más información.
