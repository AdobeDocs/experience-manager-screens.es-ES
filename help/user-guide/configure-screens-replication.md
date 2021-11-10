---
title: Configurar agentes de replicación de Screens
description: Siga esta página para obtener información sobre cómo configurar los agentes de replicación de Screens.
role: Developer
level: Intermediate
source-git-commit: ede0eb02c97c99732c64a92c603e51bedecdbac8
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---


# Configuración de agentes de replicación de Screens {#configuring-screens-replication-agent}

En esta página siguiente se describe cómo configurar los agentes de replicación de Screens.

## Objetivo {#objective}

El agente de replicación de Screens es responsable de obtener datos de comandos como, por ejemplo, *usuario*, *password*, *restartSchedule*, *maxNumberOfLogFilesToKeep*, y muchos más de estos valores de publicación a autor. Es esencial configurarlo para que el autor pueda mostrar el ping del dispositivo.

>[!NOTE]
>Para obtener más información sobre los agentes de replicación de Screens, consulte [Comandos y agentes de replicación de Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Debe completar ambas secciones para completar la configuración de Screens Replication Agent:

1. [Activación de usuarios y actualización de la contraseña](#enable-users)
1. [Actualización de la configuración del agente de replicación de Screens](#replicate-agent)

## Activación de usuarios y actualización de la contraseña {#enable-users}

Siga los pasos a continuación para habilitar usuarios y actualizar la contraseña para pantallas-receptor-usuario:

>[!NOTE]
>Por motivos de seguridad, se recomienda evitar el uso de la contraseña de administrador para screens-Recei-user.

1. Vaya a la instancia de autor de AEM.

1. Haga clic en las herramientas —> **Seguridad** —> **Usuarios**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Buscar **screens-receptor-user**.

1. Seleccione el **screens-receptor-user** y haga clic en **Habilitar** de la barra de acciones.

   ![image](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Haga clic en **OK** para confirmar.

   ![image](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Una vez que haya habilitado el usuario, verá la variable **screens-receptor-user** como **Habilitado** en el **Estado** campo .

   ![image](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Seleccione el **screens-receptor-user** y haga clic en **Propiedades** de la barra de acciones.

   ![image](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Haga clic en **Cambiar contraseña** under **Configuración de la cuenta** de la variable **Detalles** , tal y como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Escriba una contraseña nueva en la **Cambiar contraseña** y haga clic en **Guardar**.

   >[!NOTE]
   >Debe introducir la contraseña de usuario administrador existente en **Su contraseña** campo .

   ![image](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Haga clic en **Guardar y cerrar**.

1. Seleccione el **screens-receptor-user** y haga clic en **Activar** de la barra de acciones.

   ![image](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Haga clic en **OK** para confirmar.

   ![image](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Seleccione el **screens-receptor-user** y haga clic en **Deshabilitar** de la barra de acciones.

   >[!IMPORTANT]
   > Desactivación **screens-receptor-user** solo deshabilita este usuario de la instancia de autor y todos los usuarios de la instancia de publicación siguen activos. No haga clic en **Desactivar** en la barra de acciones, si se desactiva, también se eliminará el usuario de las instancias de publicación.

   ![image](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Haga clic en **OK** para confirmar.

## Actualización de la configuración del agente de replicación de Screens {#replicate-agent}

Siga la sección siguiente para actualizar la configuración en el agente de replicación de Screens:

>[!IMPORTANT]
>Debe completar los siguientes pasos en TODOS los agentes de replicación de pantallas existentes.

1. Vaya a la instancia de AEM.

1. Haga clic en las herramientas —> **Implementación** —> **Replicación**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Haga clic en **Agentes en autor**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Busque todos los agentes de replicación de Screens en el autor y haga clic en el vínculo , como se muestra en la figura siguiente.

   >[!NOTE]
   >Busque todos los agentes de replicación de Screens. El nombre del agente de replicación de Screens incluirá una letra **S** en el título.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Haga clic en **Editar**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Marque **Habilitado** de la variable **Configuración** pestaña .

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Vaya a **Transporte** en la ficha **Configuración del agente** y actualice la variable **Usuario** a **screens-receptor-user** e introduzca la misma contraseña que definió anteriormente en el paso (8) de [Activación de usuarios y actualización de la contraseña](#enable-users).

   ![image](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Haga clic en **OK**.

1. Una vez completados los pasos anteriores, puede hacer clic en **Probar conexión** para verificar la conexión.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la verificación de la conexión se ha realizado correctamente, ha completado la configuración del agente de replicación de Screens.