---
title: Replicar déclencheur de datos en servidores de publicación
description: Obtenga información sobre cómo replicar déclencheur de datos en el servidor de publicación para AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---

# Duplicación de Déclencheur de datos en servidores de publicación {#replicating-data-triggers}

AEM Al utilizar ContextHub y el motor de segmentación de datos para personalizar el contenido en función de los déclencheur de datos en una configuración de autor/publicación, todas las configuraciones relacionadas con ContextHub y la personalización no se replican automáticamente con los canales cuando se publican.

Esta página le ayuda a conocer los pasos manuales necesarios para publicar estas configuraciones por separado.

Esto básicamente se reduce a la publicación manual:

1. Configuraciones de los módulos de IU y tienda de ContextHub
1. Audiencias de personalización
1. Actividades de personalización

## Pasos para replicar Déclencheur de datos en el servidor de publicación {#replicating-data-triggers-publish}

Siga los pasos a continuación para replicar los déclencheur de datos en el servidor de publicación.

### Paso 1: Duplicación de configuraciones de ContextHub {#replicating-contexthub-configurations}

1. Vaya a **Herramientas** > **Implementación** > **Distribución** > **Agente de publicación** y haga clic en el agente de publicación para configurar los ajustes.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Como alternativa, puede utilizar la variable `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para navegar directamente a la pantalla y configurar y probar la conexión.

1. Clic **Probar conexión** en la barra de acciones para validar la comunicación del autor con la instancia de publicación, como se muestra en los siguientes ejemplos:

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Si la prueba falla, corrija la configuración del agente de replicación entre la instancia Autor y Publicación. Consulte [Solucionar problemas de conexión de prueba](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) para obtener más información.

1. Clic **Añadir** desde el **Agente de distribución** y haga clic en la ruta de configuración de su proyecto, por ejemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Haga clic en **Enviar**.

### Duplicación de audiencias {#replicating-audiences}

1. AEM Vaya a la instancia de la > **Personalización** > **Audiencias** o use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar directamente.

1. Profundizar en la carpeta del proyecto, por ejemplo, `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Haga clic en todas las audiencias y segmentos desde la interfaz de usuario.

1. Clic **Administrar publicación** de la barra de acciones.

1. Clic **Siguiente** y **Publish**.

### Duplicación de actividades  {#replicating-activities}

1. AEM Vaya a la instancia de la > **Personalización** > **Actividades** o use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar directamente.

1. Profundizar en la carpeta del proyecto, es decir, `/content/campaigns/screens/…`.

1. Haga clic en todas las actividades desde la interfaz de usuario.

1. Clic **Administrar publicación** de la barra de acciones.

1. Clic **Siguiente** y **Publish**.

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

1. Vaya a Herramientas > **Implementación** > **Distribución** > **Agente de publicación**.

1. Clic **Editar** en la barra de acciones y asegúrese de que la dirección URL del extremo en **Extremos del importador** también apunta a la URL del servidor de publicación en el Agente de distribución.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Si no utiliza las credenciales de administrador predeterminadas, debe configurar el agente de distribución con un nombre de usuario y una contraseña diferentes.

   Complete los siguientes pasos:

   1. Vaya a Herramientas > **Operaciones** > **Consola web** `http://localhost:4502/system/console/configMgr`para poder abrir **Pantalla de la consola web Adobe Experience Manager**.
   1. Buscar por **Credenciales del transporte de distribución de Apache Sling: credenciales de usuario basadas en DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Cree una configuración rellenando **Nombre**, **Nombre de usuario**, y **contraseña**, por ejemplo, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Clic **Guardar**
   1. Uso `Cmd +F` para buscar **Agente de distribución de Apache Sling: fábrica de agentes de reenvío** para abrir las configuraciones de y buscar **Proveedor de secreto de transporte**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Actualice el `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Clic **Guardar** y vuelva a ejecutar la conexión de prueba desde el **Agente de distribución** AEM Vuelva a mostrar la pantalla de la instancia de.
