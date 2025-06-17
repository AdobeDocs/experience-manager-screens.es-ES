---
title: Replicar déclencheur de datos en servidores de publicación
description: Obtenga información sobre cómo replicar déclencheur de datos en el servidor de publicación para AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Duplicación de Déclencheur de datos en servidores de publicación {#replicating-data-triggers}

Al utilizar ContextHub y el motor de segmentación de AEM para personalizar el contenido en función de los déclencheur de datos en una configuración de autor/publicación, todas las configuraciones relacionadas con ContextHub y Personalization no se replican automáticamente con los canales cuando se publican.

Esta página le ayuda a conocer los pasos manuales necesarios para publicar estas configuraciones por separado.

Este proceso se reduce básicamente a la publicación manual de lo siguiente:

1. Configuraciones de los módulos de IU y tienda de ContextHub
1. Audiencias de Personalization
1. Actividades de Personalization

## Pasos para replicar Déclencheur de datos en el servidor de publicación {#replicating-data-triggers-publish}

Siga los pasos a continuación para replicar los déclencheur de datos en el servidor de publicación.

### Paso 1: Duplicación de configuraciones de ContextHub {#replicating-contexthub-configurations}

1. Vaya a **Herramientas** > **Implementación** > **Distribución** > **Agente de publicación** y haga clic en el agente de publicación para configurar los ajustes.

   ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >También puede usar `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para navegar directamente a la pantalla y configurar y probar la conexión.

1. Haga clic en **Probar conexión** en la barra de acciones para validar la comunicación del autor con la instancia de publicación, como se muestra a continuación:

   ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Si la prueba falla, corrija la configuración del agente de replicación entre la instancia Autor y Publicación. Consulte [Solución de problemas de conexión de prueba](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) para obtener más información.

1. Haga clic en **Agregar** en el árbol de pantalla de **Agente de distribución** y luego haga clic en la ruta de configuración del proyecto, por ejemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Haga clic en **Enviar**.

### Duplicación de audiencias {#replicating-audiences}

1. Vaya a la instancia de AEM > **Personalization** > **Audiencias** o use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar directamente.

1. Profundice en la carpeta del proyecto, por ejemplo, `/conf/screens/`.

   ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Haga clic en todas las audiencias y segmentos desde la interfaz de usuario.

1. Haga clic en **Administrar publicación** en la barra de acciones.

1. Haga clic en **Siguiente** y **Publicar**.

### Duplicación de actividades {#replicating-activities}

1. Vaya a la instancia de AEM > **Personalization** > **Actividades** o use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar directamente.

1. Profundice en la carpeta del proyecto, es decir, `/content/campaigns/screens/…`.

1. Haga clic en todas las actividades desde la interfaz de usuario.

1. Haga clic en **Administrar publicación** en la barra de acciones.

1. Haga clic en **Siguiente** y **Publicar**.

>[!IMPORTANT]
>
>La duplicación de configuraciones y audiencias de ContextHub se realiza durante la configuración del proyecto mientras se replican actividades y es necesaria cada vez que se cambia la segmentación dentro de un canal.

#### Resultado {#result}

Si la replicación se realiza correctamente, debe ver la siguiente estructura en la instancia de publicación (o similar para su proyecto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Solucionar problemas de conexión de prueba {#troubleshoot-test}

Si la conexión de prueba falla al replicar las configuraciones de ContextHub, siga la sección siguiente para solucionar el problema:

1. Vaya a **Herramientas** > **Implementación** > **Distribución** > **Agente de publicación**.

1. Haga clic en **Editar** en la barra de acciones y asegúrese de que la dirección URL del extremo del campo **Extremos del importador** también apunte a la dirección URL del servidor de publicación en el agente de distribución.
   ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Si no utiliza las credenciales de administrador predeterminadas, debe configurar el Agente de distribución con un nombre de usuario y una contraseña diferentes.

   Complete los siguientes pasos:

   1. Vaya a Herramientas > **Operaciones** > **Consola web** `http://localhost:4502/system/console/configMgr`para poder abrir la pantalla de la **Consola web de Adobe Experience Manager**.
   1. Buscar **`Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider`**

      ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Cree una configuración rellenando **Name**, **User name** y **password**, por ejemplo, *slingTransportSecretProvider*.

      ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Haga clic en **Guardar**
   1. Use `Cmd +F` para buscar **Apache Sling Distribution Agent - Forward Agents Factory** para abrir las configuraciones y buscar **Transport Secret Provider**.

      ![imagen1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Actualice `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Haga clic en **Guardar** y vuelva a ejecutar la conexión de prueba desde la pantalla de **Agente de distribución** de la instancia de AEM.
