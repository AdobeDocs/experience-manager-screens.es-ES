---
title: Creación y administración de pantallas
description: Obtenga información acerca de la creación de una pantalla y la configuración de dispositivos en AEM Screens. Además, obtenga información acerca del panel de visualización.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Creación y administración de pantallas {#creating-and-managing-displays}

Una visualización es una agrupación virtual de pantallas que se colocan una al lado de la otra. La pantalla es permanente con respecto a una instalación. Este es el objeto con el que trabajan los autores de contenido y al que siempre se hace referencia como visualización lógica en lugar de como partes de contador físicas.

Al crear una ubicación, debe crear una pantalla para la ubicación.

En esta página se muestra la creación y administración de pantallas.

**Requisitos previos**:

* [Configuración e implementación de Screens](configuring-screens-introduction.md)
* [Crear y administrar un proyecto de Screens](creating-a-screens-project.md)
* [Crear y administrar canales](managing-channels.md)
* [Crear y administrar ubicaciones](managing-locations.md)

## Creación de una nueva pantalla {#creating-a-new-display}

>[!NOTE]
>
>Cree una ubicación antes de crear una visualización. Consulte [Crear y administrar ubicaciones](managing-locations.md) para obtener más información.

1. Vaya a la ubicación adecuada, por ejemplo `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Seleccione la carpeta de ubicación y seleccione **Crear** que se encuentra junto al icono más en la barra de acciones.
1. Seleccionar **Mostrar** desde el **Crear** asistente, luego seleccione **Siguiente**.
1. Entrar **Nombre** y **Título** para la ubicación de visualización.
1. En el **Mostrar** pestaña, elija los detalles del diseño. Elija el que desee **Resolución**, como **HD completo**. Elija el número de dispositivos horizontal y verticalmente.
1. Seleccione **Crear**.

La pantalla (*StoreDisplay*) se crea y se agrega a la ubicación (*San José*).

![exhibición](assets/display.gif)

Cuando tenga la visualización en posición, el siguiente paso es crear una configuración de dispositivo para esa visualización en particular.

>[!NOTE]
>
>**El siguiente paso**:
>
>Cuando cree una pantalla para su ubicación, asigne un canal a la pantalla para utilizar el contenido.
>
>Consulte [Asignar canales](channel-assignment.md) para obtener información sobre cómo asignar un canal a la visualización.

## Creación de una nueva configuración de dispositivo {#creating-a-new-device-config}

Una configuración de dispositivo actúa como marcador de posición para un dispositivo de señalización digital real que aún no está instalado.

1. Vaya a la pantalla adecuada, por ejemplo, `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Seleccione la carpeta para mostrar y seleccione **Ver tablero** en la barra de acciones.
1. Seleccionar **+ Agregar configuración de dispositivo** en la parte superior derecha de la **Dispositivos** panel.

1. Seleccione el **Configuración del dispositivo** como la plantilla requerida y pulse o haga clic en **Siguiente**.

1. Introduzca las propiedades según sea necesario y pulse o haga clic en **Crear**.

La configuración del dispositivo se crea y se añade a la visualización actual (en la siguiente demostración, la nueva configuración del dispositivo es *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>Cuando se establece una configuración de dispositivo en la pantalla en la ubicación, el siguiente paso será asignar un canal a la pantalla.
>
>Como se muestra en la figura siguiente, si la configuración del dispositivo se muestra como sin asignar en la **DISPOSITIVOS** , si no se ha asignado ningún canal a esa configuración de dispositivo en particular.
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

Haga clic en (**...**), en la esquina superior derecha de la **MOSTRAR INFORMACIÓN** para poder ver las propiedades y previsualizar la visualización.


#### Visualización de propiedades {#viewing-properties}

Clic **Propiedades** para que pueda ver o cambiar las propiedades de la pantalla.

Además, puede ajustar el valor del temporizador de evento del canal interactivo en **Tiempo de espera inactivo** propiedad en **Mostrar** pestaña. El valor predeterminado se establece en *300 segundos*.

Uso **CRXDE Lite**, para acceder a **inactiveTimeout** propiedad, es decir, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Panel de canales asignados {#assigned-channels-panel}

El **CANALES ASIGNADOS** el panel muestra los canales asignados a este dispositivo.


### Panel Dispositivos {#devices-panel}

El **DISPOSITIVOS** El panel proporciona información sobre las configuraciones del dispositivo.

Seleccionar (**...**), en la esquina superior derecha de la **DISPOSITIVOS** para que pueda añadir configuraciones de dispositivo y actualizar dispositivos.

Además, haga clic en la configuración del dispositivo para ver las propiedades, asignar un dispositivo o eliminarlo por completo.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Pasos siguientes {#the-next-steps}

Cuando termine de crear una pantalla para su ubicación, asigne un canal para la pantalla.

Consulte [Asignar canales](channel-assignment.md) para obtener más información.
