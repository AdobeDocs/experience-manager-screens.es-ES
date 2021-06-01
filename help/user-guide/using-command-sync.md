---
title: Uso de la sincronización de comandos
seo-title: Uso de la sincronización de comandos
description: Siga esta página para obtener información sobre cómo utilizar la sincronización de comandos.
seo-description: Siga esta página para obtener información sobre cómo utilizar la sincronización de comandos.
feature: Creación en Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 2%

---


# Sincronización de comandos {#command-sync}

En la siguiente página se describe cómo utilizar la sincronización de comandos. La sincronización de comandos permite la reproducción sincronizada entre diferentes reproductores. Los reproductores pueden reproducir contenido diferente, pero cada recurso debe tener la misma duración.

>[!IMPORTANT]
>
>Esta función no es compatible con Secuencias integradas, Secuencias integradas dinámicas, Canales de aplicación o Transiciones.

## Información general {#overview}

Las soluciones de señalización digital necesitan admitir paredes de vídeo y reproducción sincronizada para admitir escenarios como cuenta atrás de Año Nuevo o vídeo de gran tamaño cortado para reproducirse en varias pantallas, y aquí es donde entra en juego la sincronización de comandos.

Para utilizar la sincronización de comandos, un reproductor actúa como *master* y envía el comando y todos los demás reproductores actúan como *clientes* y juegan cuando reciben el comando.

El *master* envía un comando a todos los clientes registrados cuando está a punto de iniciar la reproducción de un elemento. La carga útil de esto puede ser el índice del elemento que se va a reproducir o el html externo del elemento que se va a reproducir.

## Implementación de sincronización de comandos {#using-command-sync}

En la siguiente sección se describe cómo puede utilizar la sincronización de comandos en un proyecto de AEM Screens.

>[!NOTE]
>
>Para la reproducción sincronizada, es necesario que todos los dispositivos de hardware tengan las mismas especificaciones de hardware y, preferiblemente, el mismo sistema operativo. No se recomienda la sincronización entre hardware y sistemas operativos diferentes.

### Configuración del proyecto {#setting-up}

Antes de utilizar la función de sincronización de comandos, asegúrese de que tiene un proyecto y un canal con contenido configurado para el proyecto.

1. En el siguiente ejemplo se muestra un proyecto de demostración denominado **CommandSyncDemo** y un canal de secuencia **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo crear un canal o añadir contenido a un canal, consulte [Creación y administración de canales](/help/user-guide/managing-channels.md)

   El canal contiene el siguiente contenido, como se muestra en la figura siguiente.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Cree una ubicación **Lobby** y luego una visualización titulada **LobbyDisplay** en la carpeta **Ubicaciones**, como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Asigne el canal **ChannelLobby** a su **LobbyDisplay**. Ahora puede ver el canal asignado a la visualización desde el panel de visualización.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de visualizaciones](/help/user-guide/managing-displays.md).

1. Vaya a la carpeta **Devices** y haga clic en **Device Manager** en la barra de acciones para registrar los dispositivos.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo registrar un dispositivo, consulte [Registro del dispositivo](/help/user-guide/device-registration.md)

1. Para fines de demostración, este ejemplo muestra un dispositivo Chrome y un reproductor de Windows como dos dispositivos independientes. Ambos dispositivos apuntan a la misma visualización.
   ![image1](assets/command-sync6.png)

### Actualización de la configuración de canal

1. Vaya a **ChannelLobby** y haga clic en **Editar** en la barra de acciones para actualizar la configuración del canal.

1. Seleccione todo el canal como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Página**.
   ![image1](assets/command-sync/command-sync8-1.png)

1. Introduzca la palabra clave *synced* en el campo **Strategy**.

   ![image1](assets/command-sync/command-sync9-1.png)


### Configuración de un maestro {#setting-up-master}

1. Vaya al panel de visualización desde **CommandSyncDemo** —> **Ubicaciones** —> **Lobby** —> **LobbyDisplay** y haga clic en **Panel** en la barra de acciones.
Verá los dos dispositivos (cromo y reproductor de Windows) en el panel **DISPOSITIVOS**, como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync10-1.png)

1. En el panel **DISPOSITIVOS**, seleccione el dispositivo que desee configurar como maestro. En el siguiente ejemplo se muestra la configuración del dispositivo Chrome como maestro. Haga clic en **Set as master device**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Introduzca la dirección IP en **Set as master device** y haga clic en **Save**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Puede configurar varios dispositivos como maestro.

### Sincronización con Master {#sync-up-master}

1. Una vez que haya configurado el dispositivo Chrome como maestro, puede sincronizar el otro dispositivo (en este caso, el reproductor de windows) para sincronizarlo con el maestro.
Seleccione el otro dispositivo (en este caso, el reproductor de windows) en el panel **DISPOSITIVOS** y haga clic en **Sincronizar con el dispositivo maestro**, como se muestra en la figura siguiente.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Seleccione el dispositivo de la lista y haga clic en **Save**.

   >[NOTA:]
   > El cuadro de diálogo **Sincronizar con el dispositivo maestro** mostrará la lista de dispositivos maestros. Puede seleccionar la que desee.

1. Una vez que el dispositivo (reproductor de Windows) se sincronice con el maestro (reproductor de Chrome), verá el dispositivo sincronizado en el panel **DISPOSITIVOS**.

   ![image1](assets/command-sync/command-sync14-1.png)

### Dessincronización con el maestro {#desync-up-master}

Una vez que haya sincronizado un dispositivo o dispositivos con un maestro, puede anular la sincronización de la asignación desde ese dispositivo.

>[!NOTE]
>
>Si desincroniza un dispositivo maestro, también desvinculará todos los dispositivos cliente asociados a ese dispositivo maestro.

Para eliminar la sincronización del dispositivo maestro, siga los pasos a continuación:

1. Vaya al panel **DEVICES** y seleccione el dispositivo.

1. Haga clic en **Desincronizar dispositivo(s)** para anular la sincronización del cliente desde el dispositivo maestro.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Haga clic en **Confirm** para anular la sincronización del dispositivo seleccionado desde el maestro.

   >[NOTA:]
   > Si selecciona el dispositivo maestro y utiliza la opción de desincronización, todos los dispositivos conectados al maestro se dessincronizarán en un solo paso.
