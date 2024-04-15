---
title: Configuración de agentes de replicación de Screens
description: Obtenga información acerca de cómo configurar agentes de replicación de Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 4%

---

# Configuración de agentes de replicación de Screens {#configuring-screens-replication-agent}

En esta página se describe cómo configurar los agentes de replicación de Screens.

## Objetivo {#objective}

El agente de replicación de Screens es responsable de traer datos de comandos como, *usuario*, *contraseña*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* y muchos más de estos valores, de publicación a autor. Es esencial configurarlo para que el autor pueda mostrar el ping del dispositivo.

>[!NOTE]
>Para obtener más información sobre los agentes de replicación de Screens, consulte [Agentes y comandos de replicación de Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Complete ambas secciones si desea completar la configuración del Agente de replicación de pantallas:

1. [Habilitar usuarios y actualizar la contraseña](#enable-users)
1. [Actualización de la configuración del agente de replicación de Screens](#replicate-agent)

## Habilitar usuarios y actualizar la contraseña {#enable-users}

Siga los pasos a continuación para habilitar usuarios y actualizar la contraseña para `screens-receiver-user`:

>[!NOTE]
>Por motivos de seguridad, se recomienda evitar el uso de la contraseña de administrador para `screens-receiver-user`.

1. AEM Vaya a la instancia de autor de la.

1. Seleccione herramientas > **Seguridad** > **Usuarios**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Buscar por **`screens-receiver-user`**.

1. Seleccione el **`screens-receiver-user`** y seleccione **Activar** de la barra de acciones.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Seleccionar **OK** para confirmar.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Cuando haya habilitado al usuario, verá el **`screens-receiver-user`** as **Habilitado** en el **Estado** field.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Seleccione el **`screens-receiver-user`** y seleccione **Propiedades** de la barra de acciones.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Seleccionar **Cambiar contraseña** bajo **Configuración de cuenta** desde el **Detalles** , como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Introduzca una nueva contraseña en **Cambiar contraseña** y seleccione. **Guardar**.

   >[!NOTE]
   >Introduzca la contraseña de usuario de administrador existente en **Su contraseña** field.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Seleccione **Guardar y cerrar**.

1. Seleccione el **`screens-receiver-user`** y seleccione **Activar** de la barra de acciones.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Seleccionar **OK** para confirmar.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Seleccione el **`screens-receiver-user`** y seleccione **Deshabilitar** de la barra de acciones.

   >[!IMPORTANT]
   > Desactivando **`screens-receiver-user`** solo deshabilita este usuario de la instancia de creación y todos los usuarios de la instancia de publicación permanecen activos. No seleccionar **Desactivar** en la barra de acciones, ya que la desactivación elimina el usuario de las instancias de publicación también.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Seleccionar **OK** para confirmar.

## Actualización de la configuración del agente de replicación de Screens {#replicate-agent}

Siga esta sección para actualizar la configuración del agente de replicación de AEM Screens:

>[!IMPORTANT]
>Complete los siguientes pasos en TODOS los agentes de replicación de AEM Screens existentes.

1. AEM Vaya a la instancia de la.
1. Seleccione herramientas > **Implementación** > **Replicación**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Seleccionar **Agentes en el autor**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Busque todos los agentes de replicación de AEM Screens en Autor y seleccione el vínculo, como se muestra en la figura siguiente.

   >[!NOTE]
   >Busque todos los agentes de replicación de AEM Screens. El nombre del agente de replicación de pantallas incluye la carta **S** en el título.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Seleccione **Editar**.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Marque **Habilitado** desde el **Configuración** pestaña.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Vaya a **Transporte** de la pestaña **Configuración de agente** y actualice la variable **Usuario** hasta **`screens-receiver-user`** e introduzca la misma contraseña que configuró anteriormente en el paso (8) de [Habilitar usuarios y actualizar la contraseña](#enable-users).

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Seleccionar **OK**.

1. Después de completar los pasos anteriores, seleccione **Probar conexión** para verificar la conexión.

   ![imagen](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la verificación de la conexión se realiza correctamente, ha completado la configuración del Agente de replicación de Screens.
