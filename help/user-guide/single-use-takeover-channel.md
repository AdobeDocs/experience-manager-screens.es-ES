---
title: Canal TakeOver de un solo uso
seo-title: Canal TakeOver de un solo uso
description: Siga este Caso de uso para crear un Canal TakeOver de un solo uso.
seo-description: Siga este Caso de uso para crear un Canal TakeOver de un solo uso.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---


# Canal TakeOver de un solo uso {#single-use-takeover-channel}

En la página siguiente se muestra un caso de uso que hace hincapié en la configuración de un proyecto para crear un canal de toma única que se reproduce una sola vez durante un tiempo específico.


## Descripción de caso de uso {#use-case-description}

Este caso de uso explica cómo crear un canal que *toma el control* del canal de reproducción normal para una visualización o un grupo de pantallas. La adquisición sólo se producirá una vez y durante un tiempo específico.
Por ejemplo, hay un canal de Single TakeOver que se reproduce el viernes de 9:00 a 10:00. Durante este tiempo, no debería jugar ningún otro canal. Antes y después de este tiempo, no se reproducirá el canal de adquisición de un solo uso. En el siguiente ejemplo se muestra la creación de un solo canal de adquisición que se reproduce y permite que el contenido se reproduzca durante 2 minutos antes de las 12:00 del 31 de diciembre hasta las 12:01 de la mañana.

### Precondiciones {#preconditions}

Antes de inicio de este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar Canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar programaciones](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

**Configuración de los Canales y visualización**

1. Cree un proyecto de AEM Screens titulado **SingleUseTakeOver**, como se muestra a continuación.

   ![recurso](assets/single-takeover1.png)

1. Cree un **MainAdChannel** en la carpeta **Canales**.

   ![recurso](assets/single-takeover2.png)

1. Seleccione **MainAdChannel** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos (imágenes, vídeos, secuencias incrustadas) en el canal.

   ![recurso](assets/single-takeover2.png)


   >[!NOTE]
   >El **MainAdChannel** de este ejemplo muestra un canal de secuencia que reproduce el contenido de forma continua.

   ![recurso](assets/single-takeover3.png)

1. Cree un **canal TakeOver** que se haga cargo del contenido en **MainAdChannel** y se reproducirá solamente durante un día y una hora específicos.

1. Seleccione el **Tocar** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos en el canal. En el siguiente ejemplo se muestra una imagen de zona única agregada a este canal.

   ![recurso](assets/single-takeover4.png)

1. Configure una ubicación y una pantalla para sus canales. Por ejemplo, la siguiente ubicación **Punto de encuentro** y mostrar **MainLobbyDisplay** está configurada para este proyecto.

   ![recurso](assets/single-takeover5.png)

**Asignación de Canales a una visualización**

1. Seleccione la **MainLobbyDisplay** de la carpeta **Ubicaciones**. Haga clic en **Asignar Canal** en la barra de acciones.

   ![recurso](assets/single-takeover6.png)

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte **[Asignación de Canal](channel-assignment.md)**.

1. Rellene los campos (**Ruta de Canal**, **Prioridad** y **Eventos admitidos**) del cuadro de diálogo **Asignación de Canal** y haga clic en **Guardar**. Ahora ha asignado el **MainAdChannel** a la pantalla.

   ![recurso](assets/single-takeover7.png)

1. Seleccione la carpeta **TakeOver** de la carpeta **Ubicaciones**. Haga clic en **Asignar Canal** en la barra de acciones para asignar el canal de adquisición de un solo uso.

1. Para asignar el canal **TakeOver** a la pantalla en un momento programado y rellenar los siguientes campos del cuadro de diálogo **Asignación de Canal** y hacer clic en **Guardar**:

   * **Ruta** de canal: Seleccione la ruta del canal TakeOver
   * **Prioridad**: Establezca la prioridad de este canal bueno que  **MainAdChannel**. Por ejemplo, la prioridad establecida en este ejemplo es 8.

      >[!NOTE]
      >La prioridad puede ser cualquier valor que sea superior al valor de prioridad del canal que se esté reproduciendo normalmente.
   * **Eventos** admitidos: Seleccione la  **pantalla y el** temporizador de  **inactividad**.
   * **Programar**: Introduzca el texto de la programación en la que desea que este canal ejecute la visualización. Por ejemplo, el texto aquí permite que el contenido se reproduzca 2 minutos antes de las 12:00 am del 31 de diciembre hasta las 12:01 am.
El texto del **Programa** mencionado en este ejemplo es *el 31 día de diciembre después de las 23:58 y también el 1 día de enero antes de 00.01*.

      ![recurso](assets/single-takeover8.png)

      Navegue hasta la pantalla desde **SingleUseTakeOver** —> **Ubicaciones** —> **Punto de encuentro** —> **Pantalla del vestíbulo principal** y haga clic en **Panel** desde la barra de acciones para vista de los canales asignados con sus prioridades, como se muestra a continuación.

      >[!NOTE]
      >Es obligatorio establecer la prioridad del canal de adquisición como la más alta.

      ![recurso](assets/single-takeover9.png)

>[!NOTE]
>
>Una vez reproducido, se recomienda eliminar el canal TakeOver de un solo uso.