---
title: Usar la sincronización de comandos
description: Obtenga más información acerca de cómo utilizar la sincronización de comandos en AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Sincronización de comandos {#command-sync}

En la siguiente página se describe cómo utilizar la sincronización de comandos. La sincronización de comandos permite la reproducción sincronizada en diferentes reproductores. Los reproductores pueden reproducir contenido diferente, pero cada recurso debe tener la misma duración.

>[!IMPORTANT]
>
>Esta función no admite secuencias incrustadas, secuencias incrustadas dinámicas, canales de aplicación ni transiciones.

## Información general {#overview}

Las soluciones de comunicación digital deben admitir paredes de vídeo y reproducción sincronizada. Este escenario es verdadero si intenta admitir escenarios como la cuenta atrás de Año Nuevo o un vídeo grande dividido para reproducirse en varias pantallas. En estos escenarios es donde la sincronización de comandos entra en juego.

Para usar la sincronización de comandos, un reproductor actúa como *principal* y envía el comando, y todos los demás reproductores actúan como *clientes* y juegan cuando reciben el comando.

*primary* envía un comando a todos los clientes registrados cuando está a punto de iniciar la reproducción de un elemento. La carga útil de esta acción puede ser el índice del elemento que se va a reproducir, el HTML exterior del elemento que se va a reproducir o ambos.

## Implementar la sincronización de comandos {#using-command-sync}

En la sección siguiente se describe cómo utilizar la sincronización de comandos en un proyecto de AEM Screens.

>[!NOTE]
>
>Para la reproducción sincronizada, es necesario que todos los dispositivos de hardware tengan las mismas especificaciones de hardware y preferiblemente el mismo sistema operativo. No se recomienda la sincronización entre diferentes sistemas operativos y hardware.

### Configuración del proyecto {#setting-up}

Antes de usar la función Sincronización de comandos, asegúrese de que tiene un proyecto y un canal con contenido configurado para su proyecto.

1. El siguiente ejemplo muestra un proyecto de demostración denominado **CommandSyncDemo** y un canal de secuencia **ChannelLobby**.

   ![imagen1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo crear un canal o agregar contenido a un canal, consulte [Creación y administración de canales](/help/user-guide/managing-channels.md)

   El canal contiene el siguiente contenido, como se muestra en la figura siguiente.

   ![imagen1](assets/command-sync/command-sync2-1.png)

1. Cree una ubicación **Lobby** y luego una pantalla con el título **LobbyDisplay** en la carpeta **Locations**, como se muestra en la figura siguiente.
   ![imagen1](assets/command-sync/command-sync3-1.png)

1. Asigne el canal **ChannelLobby** a **LobbyDisplay**. Ahora puede ver el canal asignado a la visualización desde el panel de visualización.
   ![imagen1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Vaya a la carpeta **Dispositivos**.
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.

   ![imagen1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo registrar un dispositivo, consulte [Registro de dispositivos](/help/user-guide/device-registration.md)

1. Para fines de demostración, este ejemplo muestra un dispositivo Chrome y un Reproductor de Windows como dos dispositivos independientes. Ambos dispositivos apuntan a la misma pantalla.
   ![imagen1](assets/command-sync6.png)

### Actualizando configuración de canal

1. Vaya a **ChannelLobby**.
1. Haga clic en **Editar** en la barra de acciones.
1. Haga clic en todo el canal, como se muestra en la figura siguiente.
   ![imagen1](assets/command-sync/command-sync7-1.png)

1. Haga clic en el icono de llave inglesa.
   ![imagen1](assets/command-sync/command-sync8-1.png)

1. En el cuadro de diálogo **Página**, escriba la palabra clave *sincronizada* en el campo **Estrategia**.
   ![imagen1](assets/command-sync/command-sync9-1.png)


### Configuración de un principal {#setting-up-primary}

1. Vaya al panel de visualización desde **CommandSyncDemo** > **Ubicaciones** > **Lobby** > **LobbyDisplay**. A continuación, haga clic en **Tablero** en la barra de acciones.
Observe los dos dispositivos (Chrome y Windows Player) en el panel **DISPOSITIVOS**, como se muestra a continuación:
   ![imagen1](assets/command-sync/command-sync10-1.png)

1. En el panel **DISPOSITIVOS**, haga clic en el dispositivo que desee establecer como principal. En el siguiente ejemplo se muestra la configuración del dispositivo Chrome como dispositivo principal. Haga clic en **Establecer como dispositivo principal**.

   ![imagen1](assets/command-sync/command-sync11-1.png)

1. Escriba la dirección IP en **Establecer como dispositivo principal** y haga clic en **Guardar**.

   ![imagen1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Puede configurar varios dispositivos como dispositivos principales.

### Sincronización con el principal {#sync-up-primary}

1. Una vez establecido el dispositivo Chrome como principal, sincronice el otro dispositivo (en este caso, el Reproductor de Windows) para que se sincronice con el principal.
Haga clic en el otro dispositivo (en este caso, el Reproductor de Windows) en el panel **DISPOSITIVOS** y haga clic en **Sincronizar con el dispositivo principal**.

   ![imagen1](assets/command-sync/command-sync13-1.png)

1. Haga clic en el dispositivo en la lista y luego en **Guardar**.

   >[NOTA:]
   > El cuadro de diálogo **Sincronizar con el dispositivo principal** muestra la lista de dispositivos principales. Seleccione el preferido.

1. Cuando el dispositivo (Reproductor de Windows) se sincroniza con el principal (Reproductor de Chrome), puede ver el dispositivo sincronizado en el panel **DISPOSITIVOS**.

   ![imagen1](assets/command-sync/command-sync14-1.png)

### Desincronización con el principal {#desync-up-primary}

Una vez que haya sincronizado uno o varios dispositivos con un dispositivo principal, puede anular la sincronización de la asignación desde ese dispositivo.

>[!NOTE]
>
>Si se desincroniza un dispositivo principal, también se desvincularán todos los dispositivos cliente asociados a dicho dispositivo principal.

Para quitar la sincronización del dispositivo principal, siga los pasos a continuación:

1. Vaya al panel **DISPOSITIVOS** y haga clic en el dispositivo.

1. Haga clic en **Desincronizar dispositivos** para poder desincronizar el cliente desde el dispositivo principal.

   ![imagen1](assets/command-sync/command-sync15-1.png)

1. Haga clic en **Confirmar** para anular la sincronización del dispositivo seleccionado del dispositivo principal.

   >[NOTA:]
   > Si hace clic en el dispositivo principal y utiliza la opción de desincronización, todos los dispositivos conectados al dispositivo principal se desincronizan en un solo paso.
