---
title: Canal TakeOver de un solo uso
seo-title: Canal TakeOver de un solo uso
description: Siga este Caso de uso para crear un único canal TakeOver de uso.
seo-description: Siga este Caso de uso para crear un único canal TakeOver de uso.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 7678f8b4e940963daa346383d70379fab8cc1765

---


# Canal TakeOver de un solo uso {#single-use-takeover-channel}

En la página siguiente se muestra un caso de uso que hace hincapié en la configuración de un proyecto para crear un canal de una sola toma que se reproduce una sola vez durante un tiempo específico.


## Descripción de caso de uso {#use-case-description}

Este caso de uso explica cómo crear un canal que *toma el control* del canal de reproducción normal para una visualización o un grupo de pantallas. La adquisición sólo se producirá una vez y durante un tiempo específico.
Por ejemplo, hay un canal de Single TakeOver que se reproduce el viernes de 9:00 a 10:00. Durante este tiempo, no debería reproducirse ningún otro canal. Antes y después de este tiempo, no se reproducirá el canal de adquisición de un solo uso. El siguiente ejemplo muestra la creación de un único canal de adquisición que se reproduce y permite que el contenido se reproduzca durante 2 minutos antes de las 12:00 del 31 de diciembre hasta las 12:01 de la mañana.

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

**Configuración de los canales y visualización**

1. Cree un proyecto de AEM Screens con el título **SingleUseTakeOver**, como se muestra a continuación.

   ![recurso](assets/single-takeover1.png)

1. Cree un **MainAdChannel** en la carpeta **Canales** .

   ![recurso](assets/single-takeover2.png)

1. Seleccione **MainAdChannel** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos (imágenes, vídeos, secuencias incrustadas) en el canal.

   ![recurso](assets/single-takeover2.png)


   >[!NOTE]
   >En este ejemplo, **MainAdChannel** muestra un canal de secuencia que reproduce el contenido de forma continua.

   ![recurso](assets/single-takeover3.png)

1. Cree un canal **TakeOver** que tome el control del contenido en **MainAdChannel** y se reproduzca solo durante un día y una hora específicos.

1. Seleccione la opción **Realizar** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos en el canal. El siguiente ejemplo muestra una imagen de zona única agregada a este canal.

   ![recurso](assets/single-takeover4.png)

1. Configure una ubicación y una visualización para los canales. Por ejemplo, la siguiente ubicación **Punto de encuentro** y mostrar **MainLobbyDisplay** está configurada para este proyecto.

   ![recurso](assets/single-takeover5.png)

**Asignación de canales a una visualización**

1. Seleccione **MainLobbyDisplay** en la carpeta **Ubicaciones** . Haga clic en **Asignar canal** en la barra de acciones.

   ![recurso](assets/single-takeover6.png)

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte Asignación **[de canal](channel-assignment.md)**.

1. Rellene los campos (Ruta **del** canal, **Prioridad** y Eventos **** admitidos) del cuadro de diálogo Asignación **de** canal y haga clic en **Guardar**. Ahora, ha asignado el **MainAdChannel** a la pantalla.

   ![recurso](assets/single-takeover7.png)

1. Seleccione la pantalla **Realizar** en la carpeta **Ubicaciones** . Haga clic en **Asignar canal** en la barra de acciones para asignar el canal de adquisición de un solo uso.

1. Para asignar el canal **Toma** del control a la pantalla en un momento programado y completar los siguientes campos desde el cuadro de diálogo Asignación **de** canal y hacer clic en **Guardar**:

   * **Ruta** de canal: Seleccione la ruta del canal TakeOver
   * **Prioridad**: Establezca la prioridad de este canal mayor que **MainAdChannel**. Por ejemplo, la prioridad establecida en este ejemplo es 8.
   * **Eventos** admitidos: Seleccione la **Pantalla** inactiva y el **Temporizador**.
   * **Programar**: Introduzca el texto de la programación en la que desea que este canal ejecute la visualización. Por ejemplo, el texto aquí permite que el contenido se reproduzca 2 minutos antes de las 12:00 am del 31 de diciembre hasta las 12:01 am.
El texto de la **programación** mencionada en este ejemplo es *el 31 de diciembre después de las 23:58 y también el 1 de enero antes de las 00.01*.

      ![recurso](assets/single-takeover8.png)

      >[!NOTE]
      >Puede mencionar la programación para diferentes casos de uso. Consulte Caso de uso perpetuo para obtener más detalles.