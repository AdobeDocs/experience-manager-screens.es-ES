---
title: Replicar déclencheur de datos en servidores de publicación
seo-title: Replicar déclencheur de datos en el servidor de publicación
description: Siga esta página para aprender a duplicar déclencheur de datos en el servidor de publicación.
seo-description: Replicar déclencheur de datos en el servidor de publicación.
feature: Administración de Screens, Déclencheur de datos
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# Duplicación de Déclencheur de datos en servidores de publicación {#replicating-data-triggers}

Cuando se utiliza ContextHub y AEM motor de orientación para personalizar el contenido en función de los déclencheur de datos en una configuración de autor/publicación, todas las configuraciones relacionadas con ContextHub y personalización no se replican automáticamente con los canales cuando se publican.

Siga esta página para conocer los pasos manuales necesarios para publicar estas configuraciones por separado.

Esto básicamente se reduce a la publicación manual:

1. Configuración de módulos de interfaz de usuario y almacenamiento de ContextHub
1. Audiencias de personalización
1. Actividades de personalización

## Pasos para replicar Déclencheur de datos en el servidor de publicación {#replicating-data-triggers-publish}

Siga los pasos a continuación para duplicar los déclencheur de datos en el servidor de publicación.

### Paso 1: Duplicación de configuraciones de ContextHub {#replicating-contexthub-configurations}

1. Vaya a **Tools** > **Deployment** > **Distribution** > **Publish Agent** y haga clic en el agente de publicación para configurar los ajustes.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Como alternativa, puede utilizar `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para desplazarse a la pantalla directamente para configurar y probar la conexión.

1. Haga clic en **Probar conexión** en la barra de acciones para validar la comunicación del autor con la instancia de publicación, como se muestra en la figura siguiente.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Si la prueba falla, debe corregir la configuración del agente de replicación entre la instancia de autor y publicación. Consulte [Resolución de problemas de la conexión de prueba](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) para obtener más información.

1. Seleccione **Add** en el árbol de pantalla **Distribution Agent** y seleccione la ruta de configuración de su proyecto, por ejemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Haga clic en **Submit**.

### Duplicación de audiencias {#replicating-audiences}

1. Vaya a la instancia de AEM > **Personalization** > **Audiences** o utilice `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar directamente.

1. Desplácese hacia abajo en la carpeta del proyecto, por ejemplo, `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Seleccione todas las audiencias y segmentos de la interfaz de usuario.

1. Haga clic en **Administrar publicación** en la barra de acciones.

1. Haga clic en **Siguiente** y **Publicar**.

### Duplicación de actividades {#replicating-activities}

1. Vaya a la instancia de AEM > **Personalization** > **Activities** o utilice `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar directamente.

1. Desplácese hacia abajo en la carpeta del proyecto, es decir, `/content/campaigns/screens/…`.

1. Seleccione todas las actividades de la interfaz de usuario.

1. Haga clic en **Administrar publicación** en la barra de acciones.

1. Haga clic en **Siguiente** y **Publicar**.

>[!IMPORTANT]
>
>La replicación de las configuraciones y audiencias de ContextHub se realiza durante la configuración del proyecto, mientras que la replicación de actividades y será necesaria cada vez que se cambie la segmentación dentro de un canal.

#### Resultado {#result}

Si la replicación se realiza correctamente, debería ver la siguiente estructura en la instancia de publicación (o similar para su proyecto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Solución de problemas de la conexión de prueba {#troubleshoot-test}

Si la conexión de prueba falla al replicar las configuraciones de ContextHub, siga la sección siguiente para solucionar el problema:

1. Vaya a Herramientas > **Implementación** > **Distribución** > **Agente de publicación**.

1. Haga clic en **Editar** en la barra de acciones y asegúrese de que la URL del extremo del campo **Puntos finales del importador** también señale a la URL del servidor de publicación en el agente de distribución.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Si no utiliza las credenciales de administrador predeterminadas, debe configurar el agente de distribución con un nombre de usuario y contraseña diferentes.

   Complete los siguientes pasos:

   1. Vaya a Herramientas > **Operaciones** > **Consola Web** `http://localhost:4502/system/console/configMgr`para abrir la pantalla **Consola Web de Adobe Experience Manager**.
   1. Busque **Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Cree una configuración rellenando **Name**, **User name** y **password**, por ejemplo, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Haga clic en **Guardar**
   1. Utilice `Cmd +F` para buscar **Apache Sling Distribution Agent - Forward Agents Factory** para abrir las configuraciones y buscar **Transport Secret Provider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Actualice el `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Haga clic en **Save** y vuelva a ejecutar la conexión de prueba desde la pantalla **Distribution Agent** de la instancia de AEM.
