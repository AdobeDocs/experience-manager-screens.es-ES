---
title: Administración de dispositivos
seo-title: Managing Devices
description: Esta página describe la asignación de dispositivos.
seo-description: Follow this page to learn about device assignment. The Devices console allows you to access the device manager to assign your device to a display.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# Administración de dispositivos {#managing-devices}

Esta página describe la asignación de dispositivos.

La consola Dispositivos permite acceder al administrador de dispositivos para asignar el dispositivo a una pantalla.

>[!CAUTION]
>
>Antes de asignar el dispositivo, debe registrarlo. Para obtener más información, consulte [Registro de dispositivos](device-registration.md).

## Asignación de dispositivos {#device-assignment}

Siga los pasos a continuación para asignar un dispositivo a una pantalla:

1. Vaya a la carpeta Dispositivos de su proyecto, por ejemplo

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Seleccione su **Dispositivos** y pulse o haga clic en **Administrador de dispositivos** en la barra de acciones. Se muestran los dispositivos asignados y no asignados.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Seleccione un dispositivo no asignado de la lista y pulse o haga clic en el botón **Asignar dispositivo** en la barra de acciones.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Seleccione la pantalla a la que desee asignar el dispositivo en la lista y pulse o haga clic en el botón **Asignar**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Pulse o haga clic en **Finalizar** para completar el proceso de asignación.


   El panel de visualización muestra el dispositivo asignado en la **DISPOSITIVOS** panel.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Haga clic en el botón (**...**), en la esquina superior derecha de la **DISPOSITIVOS** panel para añadir la configuración del dispositivo o actualizar los dispositivos.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Cada vez que se añade el primer dispositivo a un nuevo proyecto de Pantallas, se crea un grupo de usuarios.
>Por ejemplo, si el nombre del nodo del proyecto es *we-retail*, el nombre del grupo de usuarios es *screens-we-retail-devices*.
>Este grupo se agregará como miembro del **Colaboradores** , como se muestra en la figura siguiente:

![chlimage_1-39](assets/chlimage_1-39.png)

### Pasos siguientes {#the-next-steps}

Una vez que esté familiarizado con la asignación de canales a una pantalla, consulte los siguientes recursos:

* [Monitorización y solución de problemas](monitoring-screens.md)
