---
title: Canal Takover perpetuo
seo-title: Canal Takover perpetuo
description: Siga este caso de uso para crear un canal TakeOver perpetuo.
seo-description: Siga este caso de uso para configurar un proyecto que cree un canal TakeOver perpetuo que se reproduzca durante un día y hora específicos de forma continua.
contentOwner: jsyal
feature: Creación en Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---

# Canal Takover perpetuo {#perpetual-takeover-channel}

En la página siguiente se muestra un caso de uso que hace hincapié en la configuración de un proyecto sobre cómo crear un canal de aceptación permanente que se reproduce para un día y hora específicos de forma continua.

## Descripción de caso de uso {#use-case-description}

Este caso de uso explica cómo crear un canal que *se haga cargo* del canal que se está reproduciendo normalmente para una visualización o un grupo de pantallas. La adquisición se producirá de forma perpetua durante un día y hora específicos.
Por ejemplo, hay un canal TakeOver perpetuo que se reproduce todos los viernes de 09:00 a 00:00. Durante este tiempo, no se debe reproducir ningún otro canal. El siguiente ejemplo muestra la creación de un canal de adquisición perpetuo que se reproduce y permite que el contenido se reproduzca cada miércoles durante 2 horas desde las 14:00 hasta las 16:00.

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

1. Cree un proyecto de AEM Screens con el título **PerpetualTakeOver**, como se muestra a continuación.

   ![recurso](assets/p_usecase1.png)

1. Cree un **MainAdChannel** en la carpeta **Channels**.

   ![recurso](assets/p_usecase2.png)

1. Seleccione **MainAdChannel** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos (imágenes, vídeos, secuencias incrustadas) en el canal.

   ![recurso](assets/p_usecase3.png)


   >[!NOTE]
   >El **MainAdChannel** de este ejemplo muestra un canal de secuencia que reproduce el contenido continuamente.

1. Cree un canal **TakeOver** que se haga cargo del contenido en **MainAdChannel** y se reproducirá todos los miércoles de 2:00 a 4:00 pm.

1. Seleccione el **TakeOver** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte algunos recursos en el canal. El siguiente ejemplo muestra una imagen de zona única agregada a este canal.

   ![recurso](assets/p_usecase4.png)

1. Configure una ubicación y una visualización para sus canales. Por ejemplo, la siguiente ubicación **MainLobby** y mostrar **MainLobbyDisplay** está configurada para este proyecto.

   ![recurso](assets/p_usecase5.png)

**Asignación de canales a una pantalla**

1. Seleccione la **MainLobbyDisplay** de la carpeta **Ubicaciones**. Haga clic en **Asignar canal** en la barra de acciones para abrir el cuadro de diálogo **Asignación de canales**.

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte **[Asignación de canales](channel-assignment.md)**.

1. Rellene los campos (**Ruta del canal**, **Prioridad** y **Eventos admitidos**) del cuadro de diálogo **Asignación de canales** y haga clic en **Guardar** para asignar el **Canal de publicidad principal** a la pantalla .

   * **Ruta** del canal: Seleccione la ruta al canal  **** MainAdChannel
   * **Prioridad**: Establezca la prioridad de este canal como 1.
   * **Eventos** admitidos: Seleccione  **Carga inicial** y  **Pantalla inactiva**.

   ![recurso](assets/p_usecase6.png)

1. Seleccione la **TakeOver** de la carpeta **Ubicaciones**. Haga clic **Asignar canal** en la barra de acciones para asignar el canal de adquisición.

1. Para asignar el canal **TakeOver** a la pantalla en una hora programada y rellenar los campos siguientes del cuadro de diálogo **Asignación de canales** y haga clic en **Guardar**:

   * **Ruta** del canal: Seleccione la ruta de acceso al canal  **** TakeOverchannel
   * **Prioridad**: Establezca la prioridad de este canal bueno que  **MainAdChannel**. Por ejemplo, la prioridad establecida en este ejemplo es 8.
   * **Eventos** admitidos: Seleccione  **Idle** Screenand  **Timer**.
   * **Programación**: Introduzca el texto de la programación en la que desea que este canal ejecute la visualización. El texto del **Schedule** mencionado en este ejemplo es *el miércoles después de las 14:00 y antes de las 16:00*.

      >[!NOTE]
      >Para obtener más información sobre las expresiones que puede agregar a **Schedule**, consulte la sección [Example Expressions](#example-expressions) que aparece a continuación.
   * **activo desde**: Fecha y hora de inicio.
   * **activa hasta**: Fecha y hora de finalización.

      Por ejemplo, el texto en **Schedule** y **active from** and **active hasta** fecha y hora aquí permite que el contenido se reproduzca cada miércoles de 14:00 a 16:00.


      ![recurso](assets/p_usecase7.png)

      Vaya a la pantalla de **TakeOver** —> **Ubicaciones** —> **MainLobby** —> **MainLobbyDisplay** y haga clic en **Panel** en la barra de acciones para ver los canales asignados con sus prioridades, como se muestra a continuación.

      >[!NOTE]
      >Es obligatorio establecer la prioridad del canal de adquisición como la más alta.

      ![](assets/p_usecase8.png)
assetNow,  **** TakeOverchannel se hará cargo del  **** MainAdChannelat a las 2:00 pm durante dos horas hasta las 4:00 pm cada miércoles y reproducirá su contenido desde el 9 de enero de 2020 hasta el 31 de enero de 2020.

## Expresiones de ejemplo {#example-expressions}

En la tabla siguiente se resumen algunas expresiones de ejemplo que se pueden agregar a la programación al asignar canales a una visualización.

| **Expresión** | **Interpretación** |
|---|---|
| antes de las 8:00 am | el canal se reproduce antes de las 8:00 am todos los días |
| después de las 2:00 pm | el canal se reproduce después de las 2:00 pm todos los días |
| después de las 12:15 y antes de las 12:45 | el canal se reproduce después de las 12:15 todos los días durante 30 minutos |
| antes de las 12:15 también después de las 12:45 | el canal se reproduce antes de las 12:15 todos los días y después de las 12:45 |
| el 1 de enero después de las 14:00 también el 2 de enero también el 3 de enero antes de las 3:00 am | el canal comienza a reproducirse después de las 2:00 pm del 1 de enero y continúa reproduciéndose durante todo el día el 2 de enero hasta las 3:00 am del 3 de enero |
| el día 1-2 de enero después de las 2:00 pm también el día 2-3 de enero antes de las 3:00 am | el canal inicia el reproductor después de las 2:00 pm del 1 de enero, continúa reproduciendo hasta las 3:00 am del 2 de enero, luego vuelve a empezar el 2 de enero a las 2:00 pm y continúa reproduciendo hasta las 3:00 am del 3 de enero |

>[!NOTE]
>
>También puede utilizar la notación _hora militar_ (es decir, 14:00) en lugar de la notación *am/pm* (es decir, las 2:00 pm).
