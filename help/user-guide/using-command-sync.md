---
title: Usar la sincronización de comandos
seo-title: Using Command Sync
description: Siga esta página para obtener información sobre cómo utilizar la sincronización de comandos.
seo-description: Follow this page to learn about how to use Command Sync.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Sincronización de comandos {#command-sync}

En la siguiente página se describe cómo utilizar la sincronización de comandos. La sincronización de comandos permite la reproducción sincronizada en diferentes reproductores. Los reproductores pueden reproducir contenido diferente, pero cada recurso debe tener la misma duración.

>[!IMPORTANT]
>
>Esta función no admite secuencias incrustadas, secuencias incrustadas dinámicas, canales de aplicación ni transiciones.

## Información general {#overview}

Las soluciones de comunicación digital deben admitir paredes de vídeo y reproducción sincronizada para poder reproducir en distintas pantallas situaciones, como la cuenta atrás de Año Nuevo o la reproducción de vídeo de gran tamaño. Aquí es donde comienza a funcionar la sincronización de comandos.

Para utilizar la sincronización de comandos, un reproductor actúa como *principal* y envía el comando y todos los demás jugadores actúan como *clientes* y juegan cuando reciben el comando.

El *principal* envía un comando a todos los clientes registrados cuando está a punto de iniciar la reproducción de un elemento. La carga útil de esto puede ser el índice del elemento que se va a reproducir o el HTML exterior del elemento que se va a reproducir.

## Implementar la sincronización de comandos {#using-command-sync}

En la sección siguiente se describe cómo utilizar la sincronización de comandos en un proyecto de AEM Screens.

>[!NOTE]
>
>Para la reproducción sincronizada, es necesario que todos los dispositivos de hardware tengan las mismas especificaciones de hardware y preferiblemente el mismo sistema operativo. No se recomienda la sincronización entre diferentes sistemas operativos y hardware.

### Configuración del proyecto {#setting-up}

Antes de usar la función de sincronización de comandos, asegúrese de que tiene un proyecto y un canal con contenido configurado para su proyecto.

1. El siguiente ejemplo muestra un proyecto de demostración denominado **CommandSyncDemo** y un canal de secuencia **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para aprender a crear un canal o añadir contenido a un canal, consulte [Creación y administración de canales](/help/user-guide/managing-channels.md)

   El canal contiene el siguiente contenido, como se muestra en la figura siguiente.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Crear una ubicación **Vestíbulo** y, a continuación, una pantalla titulada como **LobbyDisplay** en el **Ubicaciones** , como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Asigne el canal, **ChannelLobby** a su **LobbyDisplay**. Ahora puede ver el canal asignado a la visualización desde el panel de visualización.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para aprender a asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Vaya a **Dispositivos** y haga clic en **Administrador de dispositivos** en la barra de acciones para registrar los dispositivos.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para aprender a registrar un dispositivo, consulte [Registro de dispositivos](/help/user-guide/device-registration.md)

1. Para fines de demostración, este ejemplo muestra un dispositivo Chrome y un reproductor de Windows como dos dispositivos independientes. Ambos dispositivos apuntan a la misma pantalla.
   ![image1](assets/command-sync6.png)

### Actualizando configuración de canal

1. Vaya a **ChannelLobby** y haga clic en **Editar** en la barra de acciones para actualizar la configuración de canal.

1. Seleccione todo el canal como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Haga clic en el icono de la llave inglesa para abrir **Página** Cuadro de diálogo.
   ![image1](assets/command-sync/command-sync8-1.png)

1. Introduzca el *sincronizado* palabra clave en **Estrategia** field.

   ![image1](assets/command-sync/command-sync9-1.png)


### Configuración de un principal {#setting-up-primary}

1. Vaya al panel de visualización desde **CommandSyncDemo** > **Ubicaciones**  > **Vestíbulo** > **LobbyDisplay** y haga clic en **Tablero** de la barra de acciones.
Verá los dos dispositivos (cromo y reproductor de Windows) en **DISPOSITIVOS** panel, como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync10-1.png)

1. Desde el **DISPOSITIVOS** , seleccione el dispositivo que desea establecer como principal. En el siguiente ejemplo se muestra la configuración del dispositivo Chrome como dispositivo principal. Haga clic en **Establecer como dispositivo principal**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Introduzca la dirección IP en **Establecer como dispositivo principal** y haga clic en **Guardar**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Puede configurar varios dispositivos como principales.

### Sincronización con el principal {#sync-up-primary}

1. Una vez que haya establecido el dispositivo Chrome como principal, puede sincronizar el otro dispositivo (en este caso, el reproductor de Windows) con el principal.
Seleccione el otro dispositivo (en este caso, el reproductor de Windows) en la **DISPOSITIVOS** y haga clic en **Sincronizar con el dispositivo principal**, como se muestra en la figura siguiente.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Seleccione el dispositivo en la lista y haga clic en **Guardar**.

   >[NOTA:]
   > El **Sincronizar con el dispositivo principal** El cuadro de diálogo mostrará la lista de dispositivos principales. Puede seleccionar el que desee de su preferencia.

1. Una vez que el dispositivo (reproductor de Windows) esté sincronizado con el principal (reproductor Chrome), verá el dispositivo sincronizado en la **DISPOSITIVOS** panel.

   ![image1](assets/command-sync/command-sync14-1.png)

### Desincronización con el principal {#desync-up-primary}

Una vez que haya sincronizado uno o varios dispositivos con un dispositivo principal, puede desincronizar la asignación desde ese dispositivo.

>[!NOTE]
>
>Si se desincroniza un dispositivo principal, también se desvincularán todos los dispositivos cliente asociados a dicho dispositivo principal.

Para eliminar la sincronización del dispositivo principal, siga los pasos a continuación:

1. Vaya a **DISPOSITIVOS** y seleccione el dispositivo.

1. Haga clic en **Desincronizar dispositivo(s)** para desincronizar el cliente desde el dispositivo principal.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Clic **Confirmar** para desincronizar el dispositivo seleccionado del dispositivo principal.

   >[NOTA:]
   > Si selecciona el dispositivo principal y utiliza la opción de desincronización, todos los dispositivos conectados al dispositivo principal se desincronizarán en un solo paso.
