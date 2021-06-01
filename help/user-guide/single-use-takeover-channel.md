---
title: Canal TakeOver de un solo uso
seo-title: Canal TakeOver de un solo uso
description: Siga este caso de uso para crear un canal TakeOver de un solo uso.
seo-description: Siga este caso de uso para crear un canal TakeOver de un solo uso.
contentOwner: jsyal
feature: Creación en Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 2%

---


# Canal TakeOver de un solo uso {#single-use-takeover-channel}

En la página siguiente se muestra un caso de uso que hace hincapié en la configuración de un proyecto para crear un canal de una sola toma de control que se reproduce una sola vez durante un tiempo específico.


## Descripción de caso de uso {#use-case-description}

Este caso de uso explica cómo crear un canal que *se haga cargo* del canal que se está reproduciendo normalmente para una visualización o un grupo de pantallas. La adquisición solo se producirá una vez y durante un tiempo específico.
Por ejemplo, hay un canal Single TakeOver que se reproduce el viernes de 9:00 a 10:00. Durante este tiempo, no se debe reproducir ningún otro canal. Antes y después de este tiempo, no se reproducirá el canal de adquisición de un solo uso. El siguiente ejemplo muestra la creación de un único canal de adquisición que se reproduce y permite que el contenido se reproduzca durante 2 minutos antes de las 12:00 am del 31 de diciembre hasta las 12:01 am.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar programaciones](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

**Configuración de los canales y la visualización**

1. Cree un proyecto de AEM Screens con el título **SingleUseTakeOver**, como se muestra a continuación.

   ![recurso](assets/single-takeover1.png)

1. Cree un **MainAdChannel** en la carpeta **Channels**.

   ![recurso](assets/single-takeover2.png)

1. Seleccione **MainAdChannel** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos (imágenes, vídeos, secuencias incrustadas) en el canal.

   ![recurso](assets/single-takeover2.png)


   >[!NOTE]
   >El **MainAdChannel** de este ejemplo muestra un canal de secuencia que reproduce el contenido continuamente.

   ![recurso](assets/single-takeover3.png)

1. Cree un canal **TakeOver** que tome el contenido en **MainAdChannel** y que solo se reproduzca durante un día y hora específicos.

1. Seleccione el **TakeOver** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos en el canal. El siguiente ejemplo muestra una imagen de zona única agregada a este canal.

   ![recurso](assets/single-takeover4.png)

1. Configure una ubicación y una visualización para sus canales. Por ejemplo, la siguiente ubicación **Lobby** y mostrar **MainLobbyDisplay** está configurada para este proyecto.

   ![recurso](assets/single-takeover5.png)

**Asignación de canales a una pantalla**

1. Seleccione la **MainLobbyDisplay** de la carpeta **Ubicaciones**. Haga clic en **Asignar canal** en la barra de acciones.

   ![recurso](assets/single-takeover6.png)

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte **[Asignación de canales](channel-assignment.md)**.

1. Rellene los campos (**Ruta del canal**, **Prioridad** y **Eventos admitidos**) del cuadro de diálogo **Asignación de canales** y haga clic en **Guardar**. Ahora ha asignado el **MainAdChannel** a su pantalla.

   ![recurso](assets/single-takeover7.png)

1. Seleccione la **TakeOver** de la carpeta **Ubicaciones**. Haga clic **Asignar canal** en la barra de acciones para asignar el canal de adquisición de un solo uso.

1. Para asignar el canal **TakeOver** a la pantalla en una hora programada y rellenar los campos siguientes del cuadro de diálogo **Asignación de canales** y haga clic en **Guardar**:

   * **Ruta** del canal: Seleccione la ruta del canal TakeOver
   * **Prioridad**: Establezca la prioridad de este canal bueno que  **MainAdChannel**. Por ejemplo, la prioridad establecida en este ejemplo es 8.

      >[!NOTE]
      >La prioridad puede ser cualquier valor que sea superior al valor de prioridad del canal que se está reproduciendo normalmente.
   * **Eventos** admitidos: Seleccione  **Idle** Screenand  **Timer**.
   * **Programación**: Introduzca el texto de la programación en la que desea que este canal ejecute la visualización. Por ejemplo, el texto aquí permite que el contenido se reproduzca 2 minutos antes de las 12:00 am del 31 de diciembre hasta las 12:01 am.
El texto del **Schedule** mencionado en este ejemplo es *el 31 de diciembre después de las 23:58 y también el 1 de enero antes de las 00.01*.

      ![recurso](assets/single-takeover8.png)

      Vaya a la visualización desde **SingleUseTakeOver** —> **Ubicaciones** —> **Lobby** —> **MainLobbyDisplay** y haga clic en **Panel** en la barra de acciones para ver los canales asignados con sus prioridades, como se muestra a continuación.

      >[!NOTE]
      >Es obligatorio establecer la prioridad del canal de adquisición como la más alta.

      ![recurso](assets/single-takeover9.png)

>[!NOTE]
>
>Una vez reproducido, se recomienda eliminar el canal TakeOver de un solo uso.