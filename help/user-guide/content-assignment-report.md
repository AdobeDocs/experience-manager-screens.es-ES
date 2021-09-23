---
title: Informe de asignación de contenido
description: En esta página se describe la descarga y el uso del informe de asignación de contenido.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 6%

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
1. [Asignar canales ](/help/user-guide/channel-assignment-latest-fp.md)


## Descarga del informe de asignación de contenido {#downloading-content-assignment-report-fp}

Una vez que haya configurado el proyecto de AEM Screens y haya asignado visualizaciones a cada una de las ubicaciones como se muestra en los pasos anteriores, estará listo para descargar el informe de asignación de contenido.

>[!NOTE]
>Solo se puede acceder a la función Informe de asignación de contenido en el nivel de proyecto.

Siga las instrucciones que se indican a continuación para descargar el informe de asignación de contenido:

1. Vaya al proyecto de AEM Screens y seleccione el proyecto **DemoScreens**.

1. Haga clic en **Content Assignment Report** en la barra de acciones.

   ![image](/help/user-guide/assets/content-assignment-report/can-download.png)

1. La hoja de cálculo descargada consta de dos fichas, como **Ubicaciones** y **Contenido**. La ficha Ubicación muestra cuatro columnas, como **Ubicaciones**, **Muestra**, **Canales** y **Dispositivos**, que pueden utilizarse para investigar más a fondo estas cuatro entidades pertenecientes a su proyecto de AEM Screens.

   ![image](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Los datos mostrados en la hoja de cálculo se ordenan alfabéticamente en un formato fácil de leer.

1. Puede hacer clic en cualquiera de los canales en la columna **Channels** para abrir la pestaña **Content** que le conducirá directamente a ese canal y también le proporcionará información sobre los recursos (imágenes y vídeos) asociados a ese canal específico, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
