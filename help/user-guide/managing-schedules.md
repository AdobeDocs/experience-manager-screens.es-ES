---
title: Creación y administración de programas
description: Obtenga información sobre los Programas que permiten organizar los canales en grupos reutilizables para no tener que repetir su asignación individualmente.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Creación y administración de programas {#creating-and-managing-schedules}

Los **horarios** de AEM Screens le permiten organizar canales en grupos reutilizables. Hacerlo significa que no tiene que repetir su asignación individualmente para cada pantalla en la que desee mostrar el contenido.

Programaciones, cuando se combina con ***DayParting***, le permite establecer una programación global con varios canales que se ejecutan a horas específicas del día y reutilizar esa configuración para todas las pantallas a la vez.

>[!NOTE]
>
>Esta funcionalidad de AEM Screens AEM solo está disponible si ha instalado el paquete de funciones 1 de Sites de la versión 6.3 de. Para obtener acceso a este paquete de funciones, póngase en contacto con el Soporte técnico de Adobe y solicite acceso. Una vez que tenga los permisos necesarios, puede descargarlo desde Package Share.

## Creación de una programación {#creating-a-schedule}

Puede crear una programación para su proyecto de Screens que pueda administrar todas las actividades de su caso de uso.

Siga los pasos a continuación para crear una programación para su canal:

1. Haga clic en el vínculo Adobe Experience Manager (parte superior izquierda) y, a continuación, en Screens. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.
1. Vaya al proyecto de Screens y haga clic en **Horarios**.
1. Haga clic en **Crear** en la barra de acciones.
1. Haga clic en **Programar** en el asistente **Crear** y luego haga clic en **Siguiente**.

1. Escriba **Name** y **Title** y haga clic en **Crear**.

Puede ver una carpeta de programación con el nombre y título designados en el proyecto.


## Visualización del panel {#viewing-dashboard}

Después de crear una carpeta de programaciones en el proyecto, puede ver los detalles en el panel de programaciones.

Siga los pasos a continuación para ver el panel de programación. El ejemplo siguiente muestra el tablero del proyecto `We.Retail`:

1. Vaya a la carpeta **Programaciones** del proyecto Screens (por ejemplo, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Haga clic en **Tablero** en la barra de acciones.

   Puede ver tres paneles diferentes, como **INFORMACIÓN DE PROGRAMACIÓN**, **CANALES ASIGNADOS** y **PANTALLAS ASIGNADAS**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panel de información de horario** Haga clic en Propiedades en la esquina superior derecha del Panel de información de horario para ver o cambiar las propiedades de la programación.

   **Panel de canales asignados** Haga clic en +Asignar canal desde la esquina superior derecha del panel CANALES ASIGNADOS para abrir el cuadro de diálogo Asignación de canal.

   **Panel de pantallas asignadas** Haga clic en cualquiera de las pantallas del panel de pantallas asignadas para abrir el panel de visualización.
