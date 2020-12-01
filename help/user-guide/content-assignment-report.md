---
title: Informe de asignación de contenido
description: Esta página describe la descarga y el uso del informe de asignación de contenido.
translation-type: tm+mt
source-git-commit: b9091708221f92b11e859f0da8a7080b31b0af77
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 1%

---


# Informe de asignación de contenido {#content-assignment-report}

La función Informe de asignación de contenido permite a un administrador de AEM Screens o a un autor exportar un informe *de asignación de* contenido que puede tener formato de hoja de cálculo.

## Uso del informe Asignación de contenido {#using-content-assignment-report}

El informe Asignación de contenido permite a un autor o administrador de AEM Screens descargar el informe que contiene todos los recursos, como imágenes o vídeos, en todos los Canales creados en un proyecto de AEM Screens. Además, incluye la información de todos los canales asignados a todas las pantallas designadas y, en adelante, todos los dispositivos asignados a las pantallas designadas.

### Uso de la función de informe Asignación de contenido{#downloading-content-assignment-report-fp}

#### Configuración del proyecto {#setting-up-project}

Siga los pasos a continuación para descargar el informe de asignación de contenido de un proyecto de AEM Screens:

1. Cree un AEM Screens denominado **DemoScreens**.

1. Cree dos canales de secuencia en **DemoScreens** como **ChannelOne** y **ChannelTwo**.

1. Seleccione **ChannelOne** y haga clic en **Editar** en la barra de acciones. Añada algunos recursos (imágenes/vídeos) en este canal. Del mismo modo, agregue recursos a **ChannelTwo**.

1. Vaya a la carpeta Locations desde **DemoScreens** —> **Ubicaciones** y cree tres ubicaciones diferentes denominadas **SanJosé**, **Dublín** y **SanFrancisco**.

1. Navegue hasta cada una de las ubicaciones y cree una visualización para cada ubicación, como **SanJoséMain** en **SanJosé** , **DublínMain** en **Dublín** y **SanFranciscoMain** **** en la ubicación de SanFrancisco.

1. Asigne un dispositivo a cada una de las pantallas.

#### Descarga del informe Asignación de contenido {#downloading-content-assignment-report}

Una vez que haya configurado el proyecto de AEM Screens y haya asignado pantallas a cada una de las ubicaciones, como se muestra en los pasos anteriores.

>[!NOTE]
>Solo se puede acceder a la función Informe de asignación de contenido en el nivel de proyecto.

Siga las instrucciones siguientes para descargar el informe Asignación de contenido:

1. Vaya a su proyecto de AEM Screens y seleccione el proyecto **DemoScreens**.

1. Haga clic en Informe de asignación de contenido en la barra de acciones. Se debe descargar una hoja de Excel en el equipo local.

   >[!NOTE]
   >La hoja de Excel descargada consta de cuatro columnas, como **Canales**, **Recursos**, **Pantallas** y **Dispositivos** , que pueden utilizarse para investigar más a fondo las cuatro entidades.




