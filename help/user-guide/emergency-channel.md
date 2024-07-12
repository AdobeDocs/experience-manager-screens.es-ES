---
title: Canal de emergencia
description: Obtenga información acerca de la creación y administración de un canal de emergencia que el autor de contenido puede cambiar de un canal de secuencia si hay una condición previa.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Canal de emergencia {#emergency-channel}

## Descripción del caso de uso {#use-case-description}

En esta sección se describe un ejemplo de uso. Hace hincapié en la creación y administración de un canal de emergencia que el autor de contenido puede cambiar de un canal de secuencia, si hay una condición previa.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar horarios](managing-schedules.md)**
* **[Registro de dispositivo](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Flujo básico: Configuración del proyecto {#basic-flow-setting-up-the-project}

Siga los pasos a continuación para configurar un canal de emergencia:

1. Cree un proyecto de AEM Screens con el nombre **EmergencyChannel**, como se muestra a continuación.

   >[!NOTE]
   >Para obtener más información sobre la creación y administración de proyectos en AEM Screens, consulte Creación de un proyecto.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Creando un canal de secuencia**

   1. Haga clic en la carpeta **Canales** y luego en **Crear**.

   1. Haga clic en **Canal de secuencia** en el asistente y cree el canal con el título **Canal de publicidad principal**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Agregando contenido al canal de secuencia**

   1. Haga clic en el canal (**MainAdChannel**).
   1. Haga clic en **Editar** en la barra de acciones.
   1. Arrastre y suelte algunos recursos en el canal.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Creando un canal de emergencia**

   1. Haga clic en la carpeta **Canales**.
   1. Haga clic en **Crear**.
   1. Haga clic en **Canal de secuencia** en el asistente y cree el canal con el título **Canal de emergencia**.

   >[!NOTE]
   >
   >Normalmente, el canal de emergencia se añade al proyecto de producción preexistente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Agregando contenido al canal de emergencia**

   1. Haga clic en el canal (**Canal de emergencia)**.
   1. Haga clic en **Editar** en la barra de acciones.
   1. Arrastre y suelte el recurso que desea ejecutar durante una emergencia en su canal.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Creando una ubicación**

   1. Vaya a la carpeta **Ubicaciones**.
   1. Haga clic en **Crear** en la barra de acciones y cree una ubicación con el título **Almacenar** desde el asistente.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Creando pantallas en su ubicación**

   Vaya a su ubicación (**Tienda**) y haga clic en **Crear** desde la barra de acciones. Después del asistente, crea dos **pantallas** con el título **StoreFront** y **StoreBack**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Creando un horario**

   1. Vaya a la carpeta **Horarios**.
   1. Haga clic en **Crear** en la barra de acciones.
   1. Después del asistente, cree una programación con el título **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Asigne ambas pantallas al programa y establezca prioridades

   1. Haga clic en la programación **(StoreSchedule)** y, a continuación, haga clic en **Tablero** en la barra de acciones.

   1. Haga clic en **+ Asignar canal** desde el panel **CANALES ASIGNADOS**.

   1. Desde el cuadro de diálogo **Asignación de canal**:

      1. Haga clic en la ruta de acceso al **MainAdChannel**
      1. Establecer la **prioridad** como 2
      1. Configure los eventos admitidos como **Carga inicial** y **Pantalla inactiva**.
      1. Haga clic en **Guardar**

      Del mismo modo, siga los mismos pasos de nuevo para asignar **EmergencyChannel** y establecer su **Prioridad**.

   >[!NOTE]
   >
   >La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tiene el valor más alto siempre tiene prioridad sobre los valores más bajos.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Haga clic en **+ Asignar canal** desde el panel **CANALES ASIGNADOS**.

1. Desde el cuadro de diálogo **Asignación de canal**:

   1. Haga clic en la ruta al **canal de emergencia**
   1. Establecer la **prioridad** como 1

   1. Definir los eventos admitidos como **Carga inicial**, **Pantalla inactiva** e **Interacción del usuario**

   1. Haga clic en **Guardar**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Puede ver los canales asignados desde el panel **StoreSchedule**.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Asignando horario a cada pantalla**

   1. Vaya a cada pantalla, como **EmergencyChannel** > **Ubicaciones** > **Tienda** >**StoreFront**.

   1. Haga clic en **Tablero** en la barra de acciones.
   1. Haga clic en **...** en el panel **CANALES Y PROGRAMACIONES ASIGNADOS** y, a continuación, haga clic en **+Asignar programa**.

   1. Haga clic en la ruta de acceso al horario (por ejemplo, aquí, **CanalDeEmergencia** > **Horarios** >**HorarioDeTienda**).

   1. Haga clic en **Guardar**.

   Puede ver la programación asignada en la pantalla desde el panel **StoreSchedule**.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registro de dispositivo**

   Complete el proceso de registro del dispositivo. Una vez registrado, puede ver el siguiente resultado en su reproductor de AEM Screens.

   ![nuevo30](assets/new30.gif)

## Cambio al canal de emergencia {#switching-to-emergency-channel}

Si hay una emergencia, realice los siguientes pasos:

1. Vaya a **EmergencyChannel** > **Horarios** > **StoreSchedule** y haga clic en **Tablero** en la barra de acciones.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Haga clic en **EmergencyChannel** en el panel de **StoreSchedule** y luego en **Editar asignación**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Actualice la **prioridad** del **canal de emergencia** a **3** desde el cuadro de diálogo **Asignación de canal** y haga clic en **Guardar**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Cuando se actualiza la prioridad del canal, todo el reproductor de AEM Screens muestra el contenido de **EmergencyChannel**.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusión {#conclusion}

**EmergencyChannel** continúa mostrando su contenido hasta que el autor de contenido restablezca el valor de prioridad en 1.

Cuando el autor de contenido reciba las instrucciones de que se ha borrado la emergencia, deberá actualizar la prioridad de **MainAdChannel**. Al hacerlo, la reproducción normal se reanuda.
