---
title: Replicar activadores de datos en servidores de publicación
seo-title: Replicar activadores de datos en el servidor de publicación
description: Replicar activadores de datos en el servidor de publicación.
seo-description: Replicar activadores de datos en el servidor de publicación.
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 2%

---


# Replicar activadores de datos en servidores de publicación {#replicating-data-triggers}

Al utilizar ContextHub y AEM Targeting Engine para personalizar el contenido en función de los desencadenantes de datos en una configuración de creación/publicación, todas las configuraciones relacionadas con ContextHub y Personalización no se replican automáticamente con los canales cuando se publican.

Siga esta página para conocer los pasos necesarios para publicar estas configuraciones por separado.

Básicamente, esto se reduce a la publicación manual:

1. Configuraciones de módulos de interfaz de usuario y de la Tienda ContextHub
1. audiencias de personalización
1. actividades de personalización

## Pasos para replicar activadores de datos en el servidor de publicación {#replicating-data-triggers-publish}

Siga los pasos a continuación para replicar los activadores de datos en el servidor de publicación.

### Paso 1: Replicar configuraciones de ContextHub {#replicating-contexthub-configurations}

1. Vaya a **Herramientas** > **Implementación** > **Distribución** > **Publicar agente** y haga clic en el agente de publicación para configurar la configuración.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Note]
   >Como alternativa, puede utilizar `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para desplazarse directamente a la pantalla para configurar y probar la conexión.

1. Haga clic en **Probar conexión** en la barra de acciones para validar la comunicación del autor con la instancia de publicación, como se muestra en la figura siguiente.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >Si la prueba falla, debe corregir la configuración del agente de replicación entre la instancia de creación y la de publicación. Consulte [Resolución de problemas de conexión](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) de prueba para obtener más información.

1. Seleccione **Añadir** en el árbol de pantalla **Agente** de distribución y seleccione la ruta de configuración del proyecto, por ejemplo `/conf/screens/settings/cloudsettings/configuration`.

1. Haga clic en **Enviar**.

### Replicar las Audiencias {#replicating-audiences}

1. Vaya a la instancia de AEM > **Personalización** > **Audiencias** o utilice `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para desplazarse directamente.

1. Explore en la carpeta del proyecto, por ejemplo, `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Seleccione todas las audiencias y segmentos en la interfaz de usuario.

1. Haga clic en **Administrar publicación** en la barra de acciones.

1. Haga clic en **Siguiente** y **Publicar**.

### Replicar las Actividades  {#replicating-activities}

1. Vaya a la instancia de AEM > **Personalización** > **Actividades** o utilice `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para desplazarse directamente.

1. Explore en la carpeta del proyecto, es decir, `/content/campaigns/screens/…`.

1. Seleccione todas las actividades en la interfaz de usuario.

1. Haga clic en **Administrar publicación** en la barra de acciones.

1. Haga clic en **Siguiente** y **Publicar**.

>[!IMPORTANT]
>
>La replicación de las configuraciones y audiencias de ContextHub se realiza durante la configuración del proyecto, mientras que la replicación de actividades se requiere cada vez que se cambia la segmentación dentro de un canal.

#### Resultado {#result}

Si la replicación se realiza correctamente, debe vista de la siguiente estructura en la instancia de publicación (o similar para el proyecto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Resolución de problemas de la conexión de prueba {#troubleshoot-test}

Si la conexión de prueba falla al replicar las configuraciones de ContextHub, siga la sección siguiente para solucionar el problema:

1. Vaya a Herramientas > **Implementación** > **Distribución** > **Agente** de publicación.

1. Haga clic en **Editar** en la barra de acciones y asegúrese de que la dirección URL del extremo en el campo Extremos **del** importador también apunta a la dirección URL del servidor de publicación en el agente de distribución.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Si no utiliza las credenciales de administrador predeterminadas, deberá configurar el agente de distribución con un nombre de usuario y una contraseña diferentes.

   Complete los siguientes pasos:

   1. Vaya a Herramientas > **Operaciones** > Consola **** web `http://localhost:4502/system/console/configMgr`para abrir la pantalla **de la consola web de** Adobe Experience Manager.
   1. Buscar las credenciales de transporte de **Apache Sling Distribution - User Credentials based DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Cree una configuración rellenando **Nombre**, Nombre **** de usuario y **contraseña**, por ejemplo, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Haga clic en **Guardar**
   1. Utilice `Cmd +F` para buscar **Apache Sling Distribution Agent - Forward Agent Factory** para abrir las configuraciones y buscar **Transport Secret Provider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Actualice el `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Haga clic en **Guardar** y vuelva a ejecutar la conexión de prueba desde la pantalla Agente **de** distribución de su instancia de AEM.
