---
title: Configurar el agente de replicación de Screens
description: Siga esta página para obtener información sobre cómo configurar Screens Replication Agent.
role: Developer
level: Intermediate
source-git-commit: 75250cf11254499dbb30b3a5b04b1849753ea266
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 6%

---


# Configuración del agente de replicación de Screens {#configuring-screens-replication-agent}

En esta sección se describe cómo configurar el agente de replicación de Screens.

## Activación de usuarios y actualización de la contraseña {#enable-users}

Complete los siguientes pasos:

1. Vaya a la instancia de AEM.

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
   >Debe especificar **admin** en **Su contraseña** campo .

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

## Actualización del agente de replicación de Screens {#replicate-agent}

Siga la sección siguiente para actualizar la configuración en el agente de replicación de Screens:

1. Vaya a la instancia de AEM.

1. Haga clic en las herramientas —> **Implementación** —> **Replicación**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Haga clic en **Agentes en autor**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Haga clic en el vínculo, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Haga clic en **Editar**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Marque **Habilitado** de la variable **Configuración** pestaña .

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Vaya a **Transporte** en la ficha **Configuración del agente** e introduzca la misma contraseña que definió anteriormente en el paso (8) de [Activación de usuarios y actualización de la contraseña](#enable-users). Haga clic en **OK**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. Una vez completados los pasos anteriores, puede hacer clic en **Probar conexión** para verificar la conexión.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la verificación de la conexión se ha realizado correctamente, ha completado la configuración del agente de replicación de Screens.