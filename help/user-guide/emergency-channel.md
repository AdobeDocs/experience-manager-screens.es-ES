---
title: Canal de emergencia
description: Obtenga información acerca de la creación y administración de un canal de emergencia que el autor del contenido puede cambiar de un canal de secuencia si hay una condición previa.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# Canal de emergencia {#emergency-channel}

## Descripción del caso de uso {#use-case-description}

En esta sección se describe un ejemplo de caso de uso que hace hincapié en la creación y administración de un canal de emergencia que el autor de contenido puede cambiar de un canal de secuencia si hay una condición previa.

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

   1. Seleccione el **Canales** carpeta y seleccione **Crear**.

   1. Seleccionar **Canal de secuencia** en el asistente y cree el canal titulado como **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Adición de contenido al canal de secuencia**

   1. Seleccione el canal (**MainAdChannel**).
   1. Seleccionar **Editar** de la barra de acciones.
   1. Arrastre y suelte algunos recursos en el canal.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Creación de un canal de emergencia**

   1. Seleccione el **Canales** carpeta.
   1. Seleccione **Crear**.
   1. Seleccionar **Canal de secuencia** en el asistente y cree el canal titulado como **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalmente, el canal de emergencia se añade al proyecto de producción preexistente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Añadir contenido al canal de emergencia**

   1. Seleccione el canal (**Canal de emergencia)**.
   1. Seleccionar **Editar** de la barra de acciones.
   1. Arrastre y suelte el recurso que desea ejecutar durante una emergencia en su canal.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Creación de una ubicación**

   1. Vaya a **Ubicaciones** carpeta.
   1. Seleccionar **Crear** en la barra de acciones y cree una ubicación con el título **Almacenar** en el asistente.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Creación de pantallas en su ubicación**

   Vaya a su ubicación (**Almacenar**) y seleccione **Crear** de la barra de acciones. Después del asistente, cree dos **Visualizaciones** con título **StoreFront** y **StoreBack**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Creación de una programación**

   1. Navegue hasta su **Horarios** carpeta.
   1. Seleccionar **Crear** de la barra de acciones.
   1. Después del asistente, cree una programación titulada como **Programación de tienda**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Asigne ambas pantallas al programa y establezca prioridades

   1. Seleccione la programación **(StoreSchedule)** y seleccione **Tablero** de la barra de acciones.

   1. Seleccionar **+ Asignar canal** desde el **CANALES ASIGNADOS** panel.

   1. Desde el **Asignación de canales** Cuadro de diálogo:

      1. Seleccione la ruta al **MainAdChannel**
      1. Configure las variables **Prioridad** as 2
      1. Definir los eventos admitidos como **Carga inicial** y **Pantalla inactiva**.
      1. Seleccionar **Guardar**

      Del mismo modo, vuelva a seguir los mismos pasos para asignar el **EmergencyChannel** y establezca su **Prioridad**.

   >[!NOTE]
   >
   >La prioridad se usa para ordenar las asignaciones en caso de que varias coincidan con los criterios de reproducción. El que tiene el valor más alto siempre tiene prioridad sobre los valores más bajos.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Seleccionar **+ Asignar canal** desde el **CANALES ASIGNADOS** panel.

1. Desde el **Asignación de canales** Cuadro de diálogo:

   1. Seleccione la ruta al **EmergencyChannel**
   1. Configure las variables **Prioridad** como 1

   1. Definir los eventos admitidos como **Carga inicial**, **Pantalla inactiva**, y **Interacción del usuario**

   1. Seleccionar **Guardar**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Puede ver los canales asignados desde el **Programación de tienda** panel.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Asignación de programación a cada visualización**

   1. Navegue hasta cada pantalla, por ejemplo, **EmergencyChannel** > **Ubicaciones** > **Almacenar** >**StoreFront**.

   1. Seleccionar **Tablero** de la barra de acciones.
   1. Seleccionar **...** desde el **CANALES Y PROGRAMACIONES ASIGNADOS** panel y seleccione más **+Asignar horario**.

   1. Seleccione la ruta al Horario (por ejemplo, aquí, **EmergencyChannel** > **Horarios** >**Programación de tienda**).

   1. Seleccione **Guardar**.

   Puede ver la programación asignada en la pantalla desde el **Programación de tienda** panel.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registro de dispositivos**

   Complete el proceso de registro del dispositivo. Una vez registrado, puede ver la siguiente salida en su reproductor de AEM Screens.

   ![new30](assets/new30.gif)

## Cambio al canal de emergencia {#switching-to-emergency-channel}

Si hay una emergencia, realice los siguientes pasos:

1. Vaya a **EmergencyChannel** > **Horarios** > **Programación de tienda** y seleccione **Tablero** de la barra de acciones.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Seleccione el **EmergencyChannel** desde el **Programación de tienda** panel y seleccione **Editar asignación**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Actualice el **Prioridad** de la **EmergencyChannel** hasta **3** desde el **Asignación de canales** y seleccione. **Guardar**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Cuando se actualiza la prioridad del canal, todo el reproductor de AEM Screens muestra el **EmergencyChannel** contenido.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusión {#conclusion}

El **EmergencyChannel** continúa mostrando su contenido hasta que el autor del contenido restablece el valor de prioridad a 1.

Cuando el autor del contenido recibe las instrucciones de que la emergencia se ha borrado, debe actualizar la prioridad del **MainAdChannel** lo que hace que se reanude la reproducción normal.
