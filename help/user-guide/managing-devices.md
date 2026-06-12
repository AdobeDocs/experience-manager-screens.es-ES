---
title: Administrar dispositivos
description: Obtenga información acerca de la asignación y administración de dispositivos en AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
TQID: https://experienceleague.adobe.com/BtVUYTZ9GisSxK6-M-QsYRGdykFB51IchqI7CX-vsa8
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 8%

---

# Administrar dispositivos {#managing-devices}

Esta página describe la asignación de dispositivos.

La consola Dispositivos permite acceder al administrador de dispositivos para asignar el dispositivo a una pantalla.

>[!CAUTION]
>
>Antes de asignar el dispositivo, regístrelo. Consulte [Registro de dispositivos](device-registration.md).

## Asignación de dispositivos {#device-assignment}

Siga los pasos a continuación para asignar un dispositivo a una pantalla:

1. Vaya a la carpeta Dispositivos de su proyecto, por ejemplo

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Haga clic en la carpeta **Dispositivos** y luego en **Administrador de dispositivos** en la barra de acciones. Se muestran los dispositivos asignados y no asignados.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Haga clic en un dispositivo sin asignar de la lista y, a continuación, en la barra de acciones, haga clic en **Asignar dispositivo**.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Haga clic en la pantalla a la que desee asignar el dispositivo desde la lista y, a continuación, haga clic en **Asignar**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Haga clic en **Finalizar** para completar el proceso de asignación.


   El panel de visualización muestra el dispositivo asignado en el panel **DISPOSITIVOS**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Haga clic en (**...**) en la esquina superior derecha del panel **DISPOSITIVOS** para agregar o actualizar los dispositivos.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Cada vez que se agrega el primer dispositivo a un nuevo proyecto de Screens, se crea un grupo de usuarios.
>Por ejemplo, si el nombre del nodo del proyecto es *we-retail*, el nombre del grupo de usuarios es *screens-we-retail-devices*.
>Este grupo se agrega como miembro del grupo **Colaboradores**, como se muestra en la figura siguiente:

![chlimage_1-39](assets/chlimage_1-39.png)

### Pasos siguientes {#the-next-steps}

Después de familiarizarse con la asignación de canales a una pantalla, consulte t[Monitorizar y solucionar problemas](monitoring-screens.md).
