---
title: Canal de adquisición de un solo uso
seo-title: Single Use TakeOver Channel
description: Siga este caso de uso para crear un canal de aceptación de un solo uso.
seo-description: Follow this Use Case for creating a Single Use TakeOver Channel.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 2%

---

# Canal de adquisición de un solo uso {#single-use-takeover-channel}

La siguiente página muestra un caso de uso que hace hincapié en la configuración de un proyecto sobre cómo crear un canal de toma de control único que se reproduce una sola vez durante un tiempo específico.


## Descripción del caso de uso {#use-case-description}

Este caso de uso explica cómo crear un canal que *toma el control* del canal de reproducción normal para una pantalla o grupo de pantallas. La adquisición solo se producirá una vez y por un tiempo específico.
Por ejemplo, hay un canal Single TakeOver que se reproduce los viernes de 9 a. m. a 10 a. m. Durante este tiempo, no se debe reproducir ningún otro canal. Antes y después de este tiempo, el canal de adquisición de un solo uso no se reproducirá. El siguiente ejemplo muestra la creación de un único canal de adquisición que reproduce y permite que el contenido se reproduzca durante 2 minutos antes de las 12:00 a.m. del 31 de diciembre hasta las 12:01 a.m.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar horarios](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

**Configuración de los canales y la visualización**

1. Cree un proyecto de AEM Screens con el título **SingleUseTakeOver**, como se muestra a continuación.

   ![recurso](assets/single-takeover1.png)

1. Crear un **MainAdChannel** en el **Canales** carpeta.

   ![recurso](assets/single-takeover2.png)

1. Seleccione el **MainAdChannel** y haga clic en **Editar** de la barra de acciones. Arrastre y suelte algunos recursos (imágenes, vídeos, secuencias incrustadas) en su canal.

   ![recurso](assets/single-takeover2.png)


   >[!NOTE]
   >El **MainAdChannel** en este ejemplo se muestra un canal de secuencia que reproduce contenido de forma continua.

   ![recurso](assets/single-takeover3.png)

1. Crear un **TakeOver** canal que se hace cargo del contenido en **MainAdChannel** y jugarán solo para un día y hora específicos.

1. Seleccione el **TakeOver** y haga clic en **Editar** de la barra de acciones. Arrastre y suelte algunos recursos en su canal. El siguiente ejemplo muestra una imagen de zona única agregada a este canal.

   ![recurso](assets/single-takeover4.png)

1. Configure una ubicación y una visualización para sus canales. Por ejemplo, la siguiente ubicación **Vestíbulo** y visualización **MainLobbyDisplay** está configurado para este proyecto.

   ![recurso](assets/single-takeover5.png)

**Asignación de canales a una pantalla**

1. Seleccione la pantalla **MainLobbyDisplay** desde el **Ubicaciones** carpeta. Clic **Asignar canal** de la barra de acciones.

   ![recurso](assets/single-takeover6.png)

   >[!NOTE]
   >Para aprender a asignar un canal a una pantalla, consulte **[Asignación de canales](channel-assignment.md)**.

1. Rellene los campos (**Ruta de canal**, **Prioridad**, y **Eventos admitidos**) desde el **Asignación de canales** y haga clic en **Guardar**. Ahora ha asignado la variable **MainAdChannel** a la pantalla.

   ![recurso](assets/single-takeover7.png)

1. Seleccione la pantalla **TakeOver** desde el **Ubicaciones** carpeta. Clic **Asignar canal** en la barra de acciones para asignar el canal de adquisición de un solo uso.

1. Para asignar el **TakeOver** canal a la pantalla a una hora programada y rellene los campos siguientes desde el **Asignación de canales** y haga clic en **Guardar**:

   * **Ruta de canal**: seleccione la ruta al canal TakeOver
   * **Prioridad**: establezca la prioridad de este canal en bueno lugar que **MainAdChannel**. Por ejemplo, la prioridad establecida en este ejemplo es 8.

      >[!NOTE]
      >La prioridad puede ser cualquier valor superior al valor de prioridad del canal que se reproduce normalmente.
   * **Eventos admitidos**: seleccione la **Pantalla inactiva** y **Temporizador**.
   * **Programación**: introduzca el texto de la programación en la que desea que este canal ejecute la visualización. Por ejemplo, el texto aquí permite que el contenido se reproduzca 2 minutos antes de las 12:00 a.m. del 31 de diciembre hasta las 12:01 a.m.
El texto de la **Programación** mencionado en este ejemplo es *el 31 de diciembre después de las 23:58 y también el 1 de enero antes de las 00:01*.

      ![recurso](assets/single-takeover8.png)

      Navegue hasta la pantalla desde **SingleUseTakeOver** —> **Ubicaciones** —> **Vestíbulo** —> **MainLobbyDisplay** y haga clic en **Tablero** en la barra de acciones para ver los canales asignados con sus prioridades, como se muestra a continuación.

      >[!NOTE]
      >Es obligatorio establecer la prioridad del canal de adquisición como la más alta.

      ![recurso](assets/single-takeover9.png)

>[!NOTE]
>
>Se recomienda eliminar el canal de Toma de control de un solo uso, una vez que se reproduce.
