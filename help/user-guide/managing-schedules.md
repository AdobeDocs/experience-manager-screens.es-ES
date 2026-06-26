---
title: Crear y administrar horarios
description: Obtenga información sobre las programaciones que le permiten organizar canales en grupos reutilizables para que no tenga que repetir su asignación individualmente.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
TQID: https://experienceleague.adobe.com/FJomd-Wz-r8vJZK7PH6wgL4LY3zRmOucBhIbTdjUmQ4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: ba4275ba-c29a-4197-90dc-5a633402ca3cid: cf6d61d1-acb6-4411-ad1b-25fb57e94db6id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 0%

---

# Creación y administración de programaciones {#creating-and-managing-schedules}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Los **horarios** de AEM Screens le permiten organizar canales en grupos reutilizables. Hacerlo significa que no tiene que repetir su asignación individualmente para cada pantalla en la que desee mostrar el contenido.

Programaciones, cuando se combina con ***DayParting***, le permite establecer una programación global con varios canales que se ejecutan a horas específicas del día y reutilizar esa configuración para todas las pantallas a la vez.

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado el paquete de funciones 1 de AEM 6.3 Sites. Para obtener acceso a este paquete de funciones, póngase en contacto con el Soporte técnico de Adobe y solicite acceso. Una vez que tenga los permisos necesarios, puede descargarlo desde Package Share.

## Creación de una programación {#creating-a-schedule}

Puede crear una programación para su proyecto de Screens que pueda administrar todas las actividades de su caso de uso.

Siga los pasos a continuación para crear una programación para su canal:

1. Haga clic en el vínculo Adobe Experience Manager (parte superior izquierda) y, a continuación, en Screens. También puede ir directamente a: `http://localhost:4502/screens.html/content/screens`.
1. Vaya al proyecto de Screens y haga clic en **Horarios**.
1. Haga clic en **Crear** en la barra de acciones.
1. Haga clic en **Programar** en el asistente **Crear** y luego haga clic en **Siguiente**.

1. Escriba **Name** y **Title** y haga clic en **Crear**.

Puede ver una carpeta de programación con el nombre y título designados en el proyecto.


## Ver tablero {#viewing-dashboard}

Después de crear una carpeta de programaciones en el proyecto, puede ver los detalles en el panel de programaciones.

Siga los pasos a continuación para ver el panel de programación. El ejemplo siguiente muestra el tablero del proyecto `We.Retail`:

1. Vaya a la carpeta **Programaciones** del proyecto Screens (por ejemplo, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Haga clic en **Tablero** en la barra de acciones.

   Puede ver tres paneles diferentes, como **INFORMACIÓN DE PROGRAMACIÓN**, **CANALES ASIGNADOS** y **PANTALLAS ASIGNADAS**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panel de información de horario**: haga clic en Propiedades en la esquina superior derecha del panel INFORMACIÓN DE HORARIO para ver o cambiar las propiedades de la programación.

   **Panel de canales asignados**: haga clic en +Asignar canal desde la esquina superior derecha del panel CANALES ASIGNADOS para abrir el cuadro de diálogo Asignación de canal.

   **Panel de pantallas asignadas**: haga clic en cualquiera de las pantallas del panel de pantallas asignadas para abrir el panel de visualización.

