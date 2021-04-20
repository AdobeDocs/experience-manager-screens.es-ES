---
title: Informe de asignación de contenido
description: En esta página se describe la descarga y el uso del informe de asignación de contenido.
feature: Authoring Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 7%

---


# Informe de asignación de contenido {#content-assignment-report}

La función Informe de asignación de contenido permite a un administrador de AEM Screens o a un autor exportar un *informe de asignación de contenido* en formato de hoja de cálculo.

## Uso del informe de asignación de contenido {#using-content-assignment-report}

El informe de asignación de contenido permite a un autor de AEM Screens o a un administrador descargar el informe que contiene todos los recursos, como imágenes o vídeos, en todos los canales creados en un proyecto de AEM Screens. Además, incluye la información de todos los canales asignados a todas las visualizaciones designadas y, a partir de entonces, todos los dispositivos asignados a sus visualizaciones designadas.

El informe de asignación de contenido no solo permite obtener una vista previa de todos los canales, recursos, pantallas y dispositivos del proyecto de AEM Screens seleccionado, sino que también proporciona una estructura de alto nivel del proyecto.


### Requisitos previos {#pre-reqs}

Antes de descargar el informe de asignación de contenido, asegúrese de que ha configurado un proyecto de AEM Screens con canales, ubicaciones y dispositivos.
Consulte los siguientes recursos para obtener más información:

1. [Creación y administración de proyectos](/help/user-guide/creating-a-screens-project.md)
1. [Crear y administrar canales](/help/user-guide/managing-channels.md)
1. [Crear y administrar ubicaciones](/help/user-guide/managing-locations.md)
1. [Crear y administrar visualizaciones](/help/user-guide/managing-displays.md)
1. [Creación de dispositivos](/help/user-guide/managing-devices.md)
1. [Asignar canales](/help/user-guide/channel-assignment-latest-fp.md) 


## Descarga del informe de asignación de contenido {#downloading-content-assignment-report-fp}

Una vez que haya configurado el proyecto de AEM Screens y haya asignado visualizaciones a cada una de las ubicaciones como se muestra en los pasos anteriores, estará listo para descargar el informe de asignación de contenido.

>[!NOTE]
>Solo se puede acceder a la función Informe de asignación de contenido en el nivel de proyecto.

Siga las instrucciones que se indican a continuación para descargar el informe de asignación de contenido:

1. Vaya al proyecto de AEM Screens y seleccione el proyecto **DemoScreens**.

1. Haga clic en **Content Assignment Report** en la barra de acciones.

   ![image](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >La hoja de cálculo descargada consta de cuatro columnas, como **Channels**, **Assets**, **Display** y **Devices**, que pueden utilizarse para investigar más a fondo estas cuatro entidades pertenecientes a su proyecto de AEM Screens.

1. Se descarga una hoja de Excel al equipo local con el nombre idéntico al nombre del proyecto de AEM Screens con el prefijo . Por ejemplo, si el nombre del proyecto es **DemoScreens**, el nombre de archivo descargado será **demoscreens-content-assign-report.xlxs**.

   ![image](/help/user-guide/assets/content-assignment-report/car-download1.png)

