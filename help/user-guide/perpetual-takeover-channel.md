---
title: Perpetual TakeOver Canal
seo-title: Perpetual TakeOver Canal
description: Siga este Caso de uso para crear un Canal de aceptación perpetua.
seo-description: Siga este Caso de uso para configurar un proyecto que cree un canal de toma de control perpetuo que se reproduzca durante un día y hora específicos de forma continua.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---


# Canal de aceptación permanente {#perpetual-takeover-channel}

En la página siguiente se muestra un caso de uso que hace hincapié en la configuración de un proyecto para crear un canal de aceptación permanente que se reproduce para un día y hora específicos de forma continua.

## Descripción de caso de uso {#use-case-description}

Este caso de uso explica cómo crear un canal que *toma el control* del canal de reproducción normal para una visualización o un grupo de pantallas. La toma de control tendrá lugar perpetuamente durante un día y hora específicos.
Por ejemplo, hay un canal de TakeOver perpetuo que se reproduce todos los viernes de 9:00 a 10:00. Durante este tiempo, no debería jugar ningún otro canal. En el siguiente ejemplo se muestra la creación de un canal de adquisición perpetua que se reproduce permite que el contenido se reproduzca todos los miércoles durante 2 horas desde las 14:00 hasta las 16:00.

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

1. Cree un proyecto de AEM Screens titulado **PerpetualTakeOver**, como se muestra a continuación.

   ![recurso](assets/p_usecase1.png)

1. Cree un **MainAdChannel** en la carpeta **Canales**.

   ![recurso](assets/p_usecase2.png)

1. Seleccione **MainAdChannel** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos (imágenes, vídeos, secuencias incrustadas) en el canal.

   ![recurso](assets/p_usecase3.png)


   >[!NOTE]
   >El **MainAdChannel** de este ejemplo muestra un canal de secuencia que reproduce el contenido de forma continua.

1. Cree un canal **TakeOver** que se haga cargo del contenido en **MainAdChannel** y se reproducirá cada miércoles de 2:00 a 4:00 pm.

1. Seleccione el **Tocar** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos en el canal. En el siguiente ejemplo se muestra una imagen de zona única agregada a este canal.

   ![recurso](assets/p_usecase4.png)

1. Configure una ubicación y una pantalla para sus canales. Por ejemplo, la siguiente ubicación **MainLobby** y mostrar **MainLobbyDisplay** se ha configurado para este proyecto.

   ![recurso](assets/p_usecase5.png)

**Asignación de Canales a una visualización**

1. Seleccione la **MainLobbyDisplay** de la carpeta **Ubicaciones**. Haga clic en **Asignar Canal** en la barra de acciones para abrir el cuadro de diálogo **Asignación de Canal**.

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte **[Asignación de Canal](channel-assignment.md)**.

1. Rellene los campos (**Ruta de Canal**, **Prioridad** y **Eventos admitidos**) del cuadro de diálogo **Asignación de Canal** y haga clic en **Guardar** para asignar el **CanalDePublicidad Principal&lt;a1111/>/> en la pantalla.**

   * **Ruta** de canal: Seleccione la ruta de acceso al canal  **** MainAdChannelchannel
   * **Prioridad**: Establezca la prioridad de este canal como 1.
   * **Eventos** admitidos: Seleccione la  **carga inicial y la pantalla** de  **inactividad**.

   ![recurso](assets/p_usecase6.png)

1. Seleccione la carpeta **TakeOver** de la carpeta **Ubicaciones**. Haga clic en **Asignar Canal** en la barra de acciones para asignar el canal de adquisición.

1. Para asignar el canal **TakeOver** a la pantalla en un momento programado y rellenar los siguientes campos del cuadro de diálogo **Asignación de Canal** y hacer clic en **Guardar**:

   * **Ruta** de canal: Seleccione la ruta de acceso a  **** TakeOverchannel
   * **Prioridad**: Establezca la prioridad de este canal bueno que  **MainAdChannel**. Por ejemplo, la prioridad establecida en este ejemplo es 8.
   * **Eventos** admitidos: Seleccione la  **pantalla y el** temporizador de  **inactividad**.
   * **Programar**: Introduzca el texto de la programación en la que desea que este canal ejecute la visualización. El texto del **Programa** mencionado en este ejemplo es *el miércoles después de las 14:00 y antes de las 16:00*.

      >[!NOTE]
      >Para obtener más información acerca de las expresiones que puede agregar a la **Programación**, consulte la sección [Expresiones de ejemplo](#example-expressions) a continuación.
   * **activo desde**: Fecha y hora del inicio.
   * **activa hasta**: Fecha y hora de finalización.

      Por ejemplo, el texto de **Programar** y **activo de** y **activo hasta** fecha y hora aquí permite que el contenido se reproduzca cada miércoles de 2:00 pm a 4:00 pm.


      ![recurso](assets/p_usecase7.png)

      Vaya a la pantalla desde **TakeOver** —> **Ubicaciones** —> **MainLobby** —> **MainLobbyDisplay** y haga clic en **Panel** de la barra de acciones para vista de los canales asignados con sus prioridades, como se muestra ...

      >[!NOTE]
      >Es obligatorio establecer la prioridad del canal de adquisición como la más alta.

      ![](assets/p_usecase8.png)
assetAhora,  **** TakeOverchannel se hará cargo del  **** MainAdChannelat a las 2:00 pm durante dos horas hasta las 4:00 pm cada miércoles y reproducirá su contenido desde el 9 de enero de 2020 hasta el 31 de enero de 2020.

## Expresiones de ejemplo {#example-expressions}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 am | el canal juega antes de las 8:00 todos los días |
| después de las 2:00 pm | el canal se reproduce después de las 14:00 todos los días |
| después de las 12:15 y antes de las 12:45 | el canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el canal toca antes de las 12:15 todos los días y después de las 12:45 |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | los inicios de canal que se juegan después de las 2:00 pm del 1 de enero continúan jugando todo el día el 2 de enero hasta las 3:00 am del 3 de enero |
| del 1 al 2 de enero después de las 2:00 pm también del 2 al 3 de enero antes de las 3:00 am | el jugador de inicios de canal después de las 2:00 pm del 1 de enero, sigue jugando hasta las 3:00 am del 2 de enero, luego vuelve a inicio el 2 de enero a las 2:00 pm y sigue jugando hasta las 3:00 am del 3 de enero |

>[!NOTE]
>
>También puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, a las 2:00 pm).
