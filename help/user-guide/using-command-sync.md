---
title: Uso de la sincronización de comandos
seo-title: Using Command Sync
description: Siga esta página para obtener información sobre cómo utilizar la sincronización de comandos.
seo-description: Follow this page to learn about how to use Command Sync.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 43ac19cf7ef63ec17611cf19ca357f791dca6e87
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 2%

---

# Sincronización de comandos {#command-sync}

En la siguiente página se describe cómo utilizar la sincronización de comandos. La sincronización de comandos permite la reproducción sincronizada entre diferentes reproductores. Los reproductores pueden reproducir contenido diferente, pero cada recurso debe tener la misma duración.

>[!IMPORTANT]
>
>Esta función no es compatible con Secuencias integradas, Secuencias integradas dinámicas, Canales de aplicación o Transiciones.

## Información general {#overview}

Las soluciones de señalización digital necesitan admitir paredes de vídeo y reproducción sincronizada para admitir escenarios como cuenta atrás de Año Nuevo o vídeo de gran tamaño cortado para reproducirse en varias pantallas, y aquí es donde entra en juego la sincronización de comandos.

Para utilizar la sincronización de comandos, un reproductor actúa como *principal* y envía el comando y todos los demás reproductores actúan como *clientes* y reproduzca cuando reciban el comando.

La variable *principal* envía un comando a todos los clientes registrados cuando está a punto de iniciar la reproducción de un elemento. La carga útil de esto puede ser el índice del elemento que se va a reproducir o el html externo del elemento que se va a reproducir.

## Implementación de sincronización de comandos {#using-command-sync}

En la siguiente sección se describe cómo puede utilizar la sincronización de comandos en un proyecto de AEM Screens.

>[!NOTE]
>
>Para la reproducción sincronizada, es necesario que todos los dispositivos de hardware tengan las mismas especificaciones de hardware y, preferiblemente, el mismo sistema operativo. No se recomienda la sincronización entre hardware y sistemas operativos diferentes.

### Configuración del proyecto {#setting-up}

Antes de utilizar la función de sincronización de comandos, asegúrese de que tiene un proyecto y un canal con contenido configurado para el proyecto.

1. El siguiente ejemplo muestra un proyecto de demostración denominado **CommandSyncDemo** y un canal de secuencia **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo crear un canal o añadir contenido a un canal, consulte [Creación y administración de canales](/help/user-guide/managing-channels.md)

   El canal contiene el siguiente contenido, como se muestra en la figura siguiente.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Crear una ubicación **Lobby** y posteriormente una visualización titulada como **LobbyDisplay** en el **Ubicaciones** como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Asigne el canal, **ChannelLobby** a su **LobbyDisplay**. Ahora puede ver el canal asignado a la visualización desde el panel de visualización.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de visualizaciones](/help/user-guide/managing-displays.md).

1. Vaya a **Dispositivos** carpeta y haga clic en **Administrador de dispositivos** de la barra de acciones para registrar los dispositivos.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para aprender a registrar un dispositivo, consulte [Registro de dispositivos](/help/user-guide/device-registration.md)

1. Para fines de demostración, este ejemplo muestra un dispositivo Chrome y un reproductor de Windows como dos dispositivos independientes. Ambos dispositivos apuntan a la misma visualización.
   ![image1](assets/command-sync6.png)

### Actualización de la configuración de canal

1. Vaya a **ChannelLobby** y haga clic en **Editar** de la barra de acciones para actualizar la configuración del canal.

1. Seleccione todo el canal como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Haga clic en el icono de la llave inglesa para abrir el **Página** para abrir el Navegador.
   ![image1](assets/command-sync/command-sync8-1.png)

1. Introduzca la variable *sincronizado* en la variable **Estrategia** campo .

   ![image1](assets/command-sync/command-sync9-1.png)


### Configuración de una variable principal {#setting-up-primary}

1. Vaya al tablero de visualización desde **CommandSyncDemo** —> **Ubicaciones**  —> **Lobby** —> **LobbyDisplay** y haga clic en **Panel** de la barra de acciones.
Verá los dos dispositivos (cromo y reproductor de windows) en **DISPOSITIVOS** , tal como se muestra en la figura siguiente.
   ![image1](assets/command-sync/command-sync10-1.png)

1. En el **DISPOSITIVOS** , seleccione el dispositivo que desea establecer como principal. En el siguiente ejemplo se muestra la configuración del dispositivo Chrome como principal. Haga clic en **Establecer como dispositivo principal**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Introduzca la dirección IP en **Establecer como dispositivo principal** y haga clic en **Guardar**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Puede configurar varios dispositivos como principales.

### Sincronización con Principal {#sync-up-primary}

1. Una vez que haya configurado el dispositivo Chrome como principal, puede sincronizar el otro dispositivo (en este caso, el reproductor de windows) con el principal.
Seleccione el otro dispositivo (en este caso, el reproductor de windows) en la **DISPOSITIVOS** y haga clic en **Sincronizar con el dispositivo principal**, como se muestra en la figura siguiente.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Seleccione el dispositivo de la lista y haga clic en **Guardar**.

   >[NOTA:]
   > La variable **Sincronizar con el dispositivo principal** mostrará la lista de dispositivos principales. Puede seleccionar la que desee.

1. Una vez que el dispositivo (reproductor de Windows) se sincronice con el principal (reproductor de Chrome), verá que el dispositivo se sincroniza en la variable **DISPOSITIVOS** panel.

   ![image1](assets/command-sync/command-sync14-1.png)

### Dessincronización con el primario {#desync-up-primary}

Una vez que haya sincronizado un dispositivo o dispositivos en un dispositivo principal, puede anular la sincronización de la asignación desde ese dispositivo.

>[!NOTE]
>
>Si dessincroniza un dispositivo principal, también desvinculará todos los dispositivos cliente asociados a ese dispositivo principal.

Para eliminar la sincronización del dispositivo principal, siga los pasos a continuación:

1. Vaya a la **DISPOSITIVOS** y seleccione el dispositivo.

1. Haga clic en **Desincronizar dispositivos** para anular la sincronización del cliente desde el dispositivo principal.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Haga clic en **Confirmar** para anular la sincronización del dispositivo seleccionado desde el principal.

   >[NOTA:]
   > Si selecciona el dispositivo principal y utiliza la opción de desincronización, todos los dispositivos conectados al dispositivo principal se dessincronizarán en un solo paso.
