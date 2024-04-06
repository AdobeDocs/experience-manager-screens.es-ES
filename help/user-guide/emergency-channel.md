---
title: Canal de emergencia
seo-title: Emergency Channel
description: Siga este ejemplo de caso de uso para obtener información sobre la creación y administración de un canal de emergencia que el autor de contenido puede cambiar de un canal de secuencia en caso de una condición previa.
seo-description: Follow this use case example to learn about creating and managing an emergency channel that the content author can switch from a sequence channel in case of a precondition.
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# Canal de emergencia {#emergency-channel}

## Descripción del caso de uso {#use-case-description}

En esta sección se describe un ejemplo de uso que hace hincapié en la creación y administración de un canal de emergencia que el autor de contenido puede cambiar de un canal de secuencia en caso de una condición previa.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar horarios](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Flujo básico: Configuración del proyecto {#basic-flow-setting-up-the-project}

Siga los pasos a continuación para configurar un canal de emergencia:

1. Cree un proyecto de AEM Screens con el nombre **EmergencyChannel**, como se muestra a continuación.

   >[!NOTE]
   >Para obtener más información sobre la creación y administración de proyectos en AEM Screens, consulte Creación de un proyecto.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Creación de un canal de secuencia**

   1. Seleccione el **Canales** y haga clic en **Crear** para abrir el asistente y crear un canal.

   1. Seleccionar **Canal de secuencia** en el asistente y cree el canal titulado como **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Adición de contenido al canal de secuencia**

   1. Seleccione el canal (**MainAdChannel**).
   1. Clic **Editar** en la barra de acciones para abrir el editor. Arrastre y suelte algunos recursos en su canal.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Creación de un canal de emergencia**

   1. Seleccione el **Canales** carpeta.
   1. Haga clic en **Crear** para abrir el asistente y crear un canal.
   1. Seleccionar **Canal de secuencia** en el asistente y cree el canal titulado como **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalmente, el canal de emergencia se añade al proyecto de producción preexistente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Añadir contenido al canal de emergencia**

   1. Seleccione el canal (**Canal de emergencia)**.
   1. Clic **Editar** en la barra de acciones para abrir el editor. Arrastre y suelte el recurso que desea ejecutar durante una emergencia en su canal.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Creación de una ubicación**

   1. Vaya a **Ubicaciones** carpeta.
   1. Clic **Crear** en la barra de acciones y cree una ubicación con el título **Almacenar** en el asistente.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Creación de pantallas en su ubicación**

   Vaya a su ubicación (**Almacenar**) y haga clic en **Crear** de la barra de acciones. Siga el asistente para crear dos **Visualizaciones** con título **StoreFront** y **StoreBack**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Creación de una programación**

   1. Navegue hasta su **Horarios** carpeta.
   1. Clic **Crear** de la barra de acciones. Siga el asistente para crear una programación titulada como **Programación de tienda**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Asigne ambas pantallas al programa y establezca prioridades

   1. Seleccione la programación **(StoreSchedule)** y haga clic en **Tablero** de la barra de acciones.

   1. Clic **+ Asignar canal** desde el **CANALES ASIGNADOS** panel.

   1. Desde el **Asignación de canales** Cuadro de diálogo:

      1. Seleccione la ruta al **MainAdChannel**
      1. Configure las variables **Prioridad** as 2
      1. Definir los eventos admitidos como **Carga inicial** y **Pantalla inactiva**.
      1. Clic **Guardar**

      Del mismo modo, tendrá que seguir los mismos pasos nuevamente para asignar el **EmergencyChannel** y establezca su **Prioridad**.

   >[!NOTE]
   >
   >La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tenga el valor más alto siempre tendrá prioridad sobre los valores más bajos.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Clic **+ Asignar canal** desde el **CANALES ASIGNADOS** panel.

1. Desde el **Asignación de canales** Cuadro de diálogo:

   1. Seleccione la ruta al **EmergencyChannel**
   1. Configure las variables **Prioridad** como 1

   1. Definir los eventos admitidos como **Carga inicial**, **Pantalla inactiva**, y **Interacción del usuario**

   1. Clic **Guardar**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Puede ver los canales asignados desde el **Programación de tienda** panel.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Asignación de programación a cada visualización**

   1. Navegue hasta la pantalla correspondiente, por ejemplo, **EmergencyChannel** > **Ubicaciones** > **Almacenar** >**StoreFront**.

   1. Clic **Tablero** en la acción para abrir el panel de visualización.
   1. Clic **...** desde el **CANALES Y PROGRAMACIONES ASIGNADOS** y haga clic en **+Asignar horario**.

   1. Seleccione la ruta al Horario (por ejemplo, aquí, **EmergencyChannel** > **Horarios** >**Programación de tienda**).

   1. Haga clic en **Guardar**.

   Puede ver la programación asignada en la pantalla desde el **Programación de tienda** panel.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registro de dispositivos**

   Complete el proceso de registro del dispositivo y, una vez que se haya registrado, verá la siguiente salida en su reproductor de AEM Screens.

   ![new30](assets/new30.gif)

## Cambio al canal de emergencia {#switching-to-emergency-channel}

En caso de emergencia, siga los siguientes pasos:

1. Vaya a **EmergencyChannel** > **Horarios** > **Programación de tienda** y seleccione **Tablero** de la barra de acciones.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Seleccione el **EmergencyChannel** desde el **Programación de tienda** panel y haga clic en **Editar asignación**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Actualice el **Prioridad** de la **EmergencyChannel** hasta **3** desde el **Asignación de canales** y haga clic en **Guardar**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. En cuanto se actualice la prioridad del canal, todo el reproductor de AEM Screens mostrará el **EmergencyChannel** contenido, como se muestra a continuación.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusión {#conclusion}

El **EmergencyChannel** seguirá mostrando su contenido hasta que el autor del contenido restablezca el valor de prioridad en 1.

Una vez que el autor del contenido recibe las instrucciones de que la emergencia se ha borrado, debe actualizar la prioridad del **MainAdChannel** lo que hará que se reanude la reproducción normal.
