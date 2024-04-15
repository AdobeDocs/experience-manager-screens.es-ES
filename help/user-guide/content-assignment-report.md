---
title: Informe de asignación de contenido
description: Conozca la descarga y el uso del informe de asignación de contenido en relación con AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 2%

---

# Informe de asignación de contenido {#content-assignment-report}

La función Informe de asignación de contenido permite a un administrador de AEM Screens o a un autor exportar un *Informe de asignación de contenido* en formato de hoja de cálculo.

## Uso del informe de asignación de contenido {#using-content-assignment-report}

El informe de asignación de contenido permite a un autor o a un administrador de AEM Screens descargar el informe que contiene todos los recursos, como imágenes y vídeos, en todos los canales creados en un proyecto de AEM Screens. Además, incluye la información de todos los canales asignados a todas las pantallas designadas y, en adelante, de todos los dispositivos asignados a sus pantallas designadas.

El informe de asignación de contenido no solo permite obtener una vista previa de todos los canales, activos, pantallas y dispositivos del proyecto de AEM Screens seleccionado, sino que también proporciona una estructura de alto nivel del proyecto.


### Requisitos previos {#pre-reqs}

Antes de descargar el informe de asignación de contenido, asegúrese de haber configurado un proyecto de AEM Screens con canales, ubicaciones y dispositivos.
Consulte los siguientes recursos para obtener más información:

1. [Creación y administración de proyectos](/help/user-guide/creating-a-screens-project.md)
1. [Creación y administración de canales](/help/user-guide/managing-channels.md)
1. [Creación y administración de ubicaciones](/help/user-guide/managing-locations.md)
1. [Creación y administración de pantallas](/help/user-guide/managing-displays.md)
1. [Creación de dispositivos](/help/user-guide/managing-devices.md)
1. [Asignación de canales](/help/user-guide/channel-assignment-latest-fp.md)


## Descarga del informe de asignación de contenido {#downloading-content-assignment-report-fp}

Cuando haya configurado el proyecto de AEM Screens y haya asignado pantallas a cada una de las ubicaciones, como se muestra en los pasos anteriores, descargue el informe de asignación de contenido.

>[!NOTE]
>Solo se puede acceder a la función Informe de asignación de contenido en el nivel de proyecto.

Siga las instrucciones a continuación para descargar el informe de asignación de contenido:

1. Vaya al proyecto de AEM Screens y seleccione el proyecto **Demostraciones**.

1. Clic **Informe de asignación de contenido** de la barra de acciones.

   ![imagen](/help/user-guide/assets/content-assignment-report/can-download.png)

1. La hoja de cálculo descargada consta de dos pestañas, como **Ubicaciones** y **Contenido**. La pestaña Ubicación muestra cuatro columnas, como **Ubicaciones**, **Visualizaciones**, **Canales**, y **Dispositivos** que se puede utilizar para investigar más a fondo estas cuatro entidades pertenecientes a su proyecto de AEM Screens.

   ![imagen](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Los datos mostrados en la hoja de cálculo se ordenan alfabéticamente en un formato fácil de leer.

1. Al hacer clic en cualquiera de los canales de **Canales** abre la columna **Contenido** pestaña. A su vez, le desplaza directamente a ese canal y le proporciona información sobre los recursos (imágenes y vídeos) asociados a ese canal específico.

   ![imagen](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
