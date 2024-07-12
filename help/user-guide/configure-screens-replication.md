---
title: Configuración de agentes de replicación de Screens
description: Obtenga información sobre cómo configurar agentes de replicación de Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 4%

---

# Configuración de agentes de replicación de Screens {#configuring-screens-replication-agent}

En esta página se describe cómo configurar los agentes de replicación de Screens.

## Objetivo {#objective}

El Agente de replicación de Screens es responsable de traer datos de comandos como *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* y muchos más valores de este tipo de la publicación al autor. Es esencial configurar este agente para que el autor pueda mostrar el ping del dispositivo.

>[!NOTE]
>Para obtener más información acerca de los agentes de replicación de Screens, vea [Agentes y comandos de replicación de Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Complete ambas secciones si desea completar la configuración del Agente de replicación de Screens:

1. [Habilitar usuarios y actualizar la contraseña](#enable-users)
1. [Actualizar la configuración del agente de replicación de Screens](#replicate-agent)

## Habilitar usuarios y actualizar la contraseña {#enable-users}

Siga los pasos a continuación para habilitar usuarios y actualizar la contraseña de `screens-receiver-user`:

>[!NOTE]
>Por motivos de seguridad, se recomienda evitar el uso de la contraseña de administrador para `screens-receiver-user`.

1. AEM Vaya a la instancia de autor de la.

1. Haga clic en herramientas > **Seguridad** > **Usuarios**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Busque **`screens-receiver-user`**.

1. Haga clic en **`screens-receiver-user`** y luego en **Habilitar** en la barra de acciones.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Haga clic en **Aceptar** para confirmar.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Cuando haya habilitado el usuario, verá **`screens-receiver-user`** como **Habilitado** en el campo **Estado**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Haga clic en **`screens-receiver-user`** y luego en **Propiedades** en la barra de acciones.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Haga clic en **Cambiar contraseña** en **Configuración de la cuenta** desde la ficha **Detalles**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Escriba una nueva contraseña en el cuadro de diálogo **Cambiar contraseña** y haga clic en **Guardar**.

   >[!NOTE]
   >Escriba la contraseña del usuario administrador existente en el campo **Su contraseña**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Haga clic en **Guardar y cerrar**.

1. Haga clic en **`screens-receiver-user`** y luego en **Activar** en la barra de acciones.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Haga clic en **Aceptar** para confirmar.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Haga clic en **`screens-receiver-user`** y luego en **Deshabilitar** en la barra de acciones.

   >[!IMPORTANT]
   > Al deshabilitar **`screens-receiver-user`**, solo se deshabilita este usuario de la instancia de creación y todos los usuarios de la instancia de publicación permanecen activos. No haga clic en **Desactivar** en la barra de acciones, ya que la desactivación también elimina al usuario de las instancias de publicación.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Haga clic en **Aceptar** para confirmar.

## Actualizar la configuración del agente de replicación de Screens {#replicate-agent}

Siga esta sección para actualizar la configuración del agente de replicación de AEM Screens:

>[!IMPORTANT]
>Complete los siguientes pasos en TODOS los agentes de replicación de AEM Screens existentes.

1. AEM Vaya a la instancia de la.
1. Haga clic en herramientas > **Implementación** > **Replicación**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Haga clic en **agentes en autor**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Busque todos los agentes de replicación de AEM Screens en Author y haga clic en el vínculo, como se muestra en la figura siguiente.

   >[!NOTE]
   >Busque todos los agentes de replicación de AEM Screens. El nombre del Agente de replicación de Screens incluye la carta **S** en el título.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Haga clic en **Editar**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Seleccione **Habilitado** en la ficha **Configuración**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Vaya a la ficha **Transporte** del cuadro de diálogo **Configuración del agente**, actualice el **Usuario** a **`screens-receiver-user`** e introduzca la misma contraseña que configuró antes en el paso (8) de [Habilitar usuarios y actualizar la contraseña](#enable-users).

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Haga clic en **OK**.

1. Después de completar los pasos anteriores, haga clic en **Probar conexión** para comprobar la conexión.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la verificación de la conexión se realiza correctamente, habrá completado la configuración del Agente de replicación de Screens.
