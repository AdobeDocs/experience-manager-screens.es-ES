---
title: Uso de la secuencia incrustada dinámica
description: Obtenga información sobre cómo implementar secuencias incrustadas dinámicas en el proyecto de AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '2451'
ht-degree: 1%

---

# Uso de la secuencia incrustada dinámica {#using-dynamic-embedded-sequence}

El uso de secuencias incrustadas dinámicas abarca los siguientes temas:

* **Información general**
* **Uso de la experiencia integrada dinámica en AEM Screens**
* **Visualización de los resultados**
* **Restringir usuarios y modificar las ACL**

## Información general {#overview}

***Las secuencias incrustadas dinámicas*** se crean para proyectos grandes que siguen una jerarquía principal-secundaria, en la que se hace referencia al elemento secundario dentro de una carpeta de ubicación y no en una carpeta de canal. Permite al usuario incrustar una secuencia en un canal mediante ***Rol del canal***. Permite al usuario definir marcadores de posición específicos de la ubicación para diferentes oficinas mediante una secuencia incrustada dentro de un canal principal.

Al asignar un canal a una visualización, tiene la opción de especificar la ruta de la visualización. O bien, puede especificar la función del canal que se resuelve en un canal real por contexto.

Para utilizar la secuencia incrustada dinámica, asigne un canal por ***Rol del canal***. La función del canal define el contexto de la visualización. La función se dirige a varias acciones y es independiente del canal real que cumple la función. En esta sección se describe un caso de uso que define canales por función y cómo puede aplicar ese contenido a un canal global. También puede considerar la función como un identificador para la asignación o como un alias para el canal en el contexto de.

### Ventajas de utilizar secuencias incrustadas dinámicas {#benefits-of-using-dynamic-embedded-sequences}

Colocar un canal de secuencia dentro de una ubicación en lugar de la carpeta de canales permite a los autores locales o regionales editar el contenido relevante para ellos. También permite restringir la edición de canales en la parte superior de la jerarquía.

La referencia a un *canal por rol* le permite crear una versión local de un canal. Al hacerlo, se resuelve dinámicamente el contenido específico de la ubicación y también se permite crear un canal global que utiliza el contenido para los canales específicos de la ubicación.

>[!NOTE]
>
>**Secuencias incrustadas en comparación con Secuencias incrustadas dinámicas**
>
>Una secuencia incrustada dinámica es similar a una secuencia incrustada, pero permite al usuario seguir una jerarquía en la que los cambios y actualizaciones realizados en un canal se propagan a otro en relación. Sigue una jerarquía principal-secundario y también incluye recursos como imágenes o vídeos.
>
>***Secuencias incrustadas dinámicas*** le permite mostrar contenido específico de la ubicación, mientras que ***Secuencias incrustadas*** solo muestran la presentación general del contenido. Además, al configurar Secuencias incrustadas dinámicas, configure el canal mediante la función y el nombre del canal. Consulte los pasos siguientes para ver una implementación práctica.
>
>Para obtener más información sobre la implementación de secuencias incrustadas, consulte [Secuencias incrustadas](embedded-sequences.md) en AEM Screens.

En el ejemplo siguiente se proporciona una solución centrándose en los términos clave siguientes:

* un ***canal de secuencia principal*** para la secuencia global.
* ***componentes de secuencia incrustada dinámica*** para cada parte personalizable localmente de la secuencia.
* ***canales de secuencia individual*** en las ubicaciones respectivas con un *rol* en la pantalla que coincide con el **rol &#x200B;***del componente de secuencia incrustada dinámica.*

>[!NOTE]
>
>Para obtener más información sobre la asignación de canales, consulte **[Asignación de canales](channel-assignment.md)** en la sección Creación de la documentación de AEM Screens.

## Uso de la secuencia incrustada dinámica {#using-dynamic-embedded-sequence-2}

En la siguiente sección se explica la creación de una secuencia incrustada dinámica en un canal de AEM Screens.

### Requisitos previos {#prerequisites}

Antes de comenzar a implementar esta funcionalidad, asegúrese de que tiene los siguientes requisitos previos preparados para comenzar a implementar secuencias incrustadas dinámicas:

* Cree un proyecto de AEM Screens (en este ejemplo, **Demo**).
* Cree un canal **Global** en la carpeta **Canales**.
* Agregue contenido a su canal **Global** (*Compruebe **Resources.zip**&#x200B;para ver si hay recursos relevantes*).

La siguiente imagen muestra el proyecto **Demo** con el canal **Global** en la carpeta **Channels**.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Recursos {#resources}

Puede descargar los siguientes recursos (imágenes y añadirlos a los recursos) y utilizarlos más como contenido de canal para fines de demostración.

[Obtener archivo](assets/resources.zip)

>[!NOTE]
>
>Para obtener información adicional sobre cómo crear un proyecto y cómo crear un canal de secuencia, consulte los siguientes recursos:
>
>* **[Creación y administración de proyectos](creating-a-screens-project.md)**
>* **[Administrar un canal](managing-channels.md)**
>

La implementación de la secuencia incrustada dinámica en un proyecto de AEM Screens implica tres tareas principales:

1. **Configurando taxonomía de proyecto que incluye canales, ubicaciones y pantallas**
1. **Creando un horario**
1. **Asignando horario a cada pantalla**

Siga los pasos a continuación para implementar la funcionalidad:

>[!CAUTION]
>
>Al implementar secuencias incrustadas dinámicas, tenga cuidado con los campos **Nombre** y **Título** al crear canales en cada ubicación. Siga cuidadosamente las instrucciones de nomenclatura.

1. **Crear dos carpetas de ubicaciones.**

   Vaya a la carpeta **Ubicaciones** de su proyecto de AEM Screens y cree dos carpetas de ubicación como **Región A** y **Región B**.

   >[!NOTE]
   >
   >Al crear la carpeta de ubicación **Region A**, asegúrese de escribir el **Título** como **Region A** y de dejar vacío el campo **Name**, de modo que se seleccione automáticamente el nombre **region-a**.
   >
   >Es similar el caso para crear la carpeta de ubicación **Región B**, como se muestra a continuación:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Para obtener información sobre cómo crear una ubicación, vea **[Crear y administrar ubicaciones](managing-locations.md)**.

1. **Cree dos ubicaciones y un canal en cada carpeta de ubicación.**

   1. Vaya a **Demostración** > **Ubicaciones** > **Región A**.
   1. Haga clic en **Región A** y luego haga clic en **+ Crear** en la barra de acciones.
   1. Haga clic en **Ubicación** del asistente con **Título** como **Tienda 1**. Del mismo modo, cree otra ubicación del asistente con el título **Tienda 2** y el título **Title** como **Tienda 2**. Puede dejar vacío el campo **Nombre** al crear **tienda 1** y **tienda 2**.
   1. Repita el paso (b) y ahora haga clic en **Canal de secuencia** desde el asistente. Escriba **Title** como **Región A** y **Name** como **Región** para este canal.

   >[!CAUTION]
   >
   >Asegúrese de que al crear el canal **Región A**, escriba el **Título** como **Región A** y el **Nombre** como **Región**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Del mismo modo, cree dos ubicaciones en **Región B** con el título **Tienda 3** y **Tienda 4**. Además, cree un **Canal de secuencia** con **Título** como **Región B** y **Nombre** como **Región**.

   >[!CAUTION]
   >
   >Asegúrese de que puede usar el mismo nombre para los canales creados en **Región A** y **Región B** que en **Región**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Crear pantalla y canal en cada ubicación.**

   1. Vaya a **Demostración** > **Ubicaciones** > **Región A** > **Tienda 1**.
   1. Haga clic en **Almacenar 1** y luego en **+ Crear** en la barra de acciones.
   1. Haga clic en **Mostrar** en el asistente y cree **`Store1Display`**.
   1. Repita el paso (b) y esta vez haga clic en **Canal de secuencia** desde el asistente. Escriba **Title** como **`Store1Channel`** y **Name** como **store**.

   >[!CAUTION]
   >
   >Es importante que cuando cree un canal de secuencia, el **Título** del canal se pueda usar como requisito, pero el **Nombre** debería ser el mismo en todos los canales locales.
   >En este ejemplo, los canales bajo **Región A** y **Región B** comparten **Nombre** como **región** y los canales bajo **`Store 1`**, **`Store 2`**, **`Store 3`** y **`Store 4`** comparten **Nombre** como **tienda**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Del mismo modo, cree una pantalla como **`Store2Display`** y un canal **`Store2Channel`** en **`Store `2** (con el nombre **store**).

   >[!NOTE]
   >Asegúrese de que puede usar el mismo nombre para los canales creados en **`Store 1`** y **`Store 2`** que **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Siga los pasos anteriores para poder crear un canal y mostrarlo en **`Store 3`** y **`Store 4`** en la **región B**. De nuevo, asegúrese de usar el mismo **Nombre** que **tienda** al crear el canal **`Store3Channel`** y **`Store4Channel`** respectivamente.

   La siguiente imagen muestra la visualización y el canal en **`Store 3`**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   La siguiente imagen muestra la visualización y el canal en **`Store 4`**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Agregar contenido a los canales en sus respectivas ubicaciones.**

   Vaya a **Demostración** > **Ubicaciones** > **Región A** > **Región A** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte los recursos que desee añadir a su canal.

   >[!NOTE]
   >Puede usar el archivo ***Resources.zip*** de la sección **Resources** anterior para usar las imágenes como recursos para el contenido del canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Del mismo modo, ve a **Demo** > **Ubicaciones** > **Región B** > **Región B** y haz clic en **Editar** en la barra de acciones para arrastrar y soltar los recursos en tu canal, como se muestra a continuación:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Siga los pasos anteriores y los recursos para poder agregar contenido a los siguientes canales:

   * **`Store1Channel`**
   * **`Store2Channel`**
   * **`Store3Channel`**
   * **`Store4Channel`**

1. **Crear un horario**

   Vaya a la carpeta **Programaciones** de su proyecto de AEM Screens y haga clic en ella. A continuación, haga clic en **Crear** en la barra de acciones.

   La siguiente imagen muestra el **AdSchedule** creado en el proyecto **Demo**.

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Asignar canales a un horario**

   1. Vaya a **Demostración** > **Programas** > **AdSchedule** y haga clic en **Tablero** desde la barra de acciones.
   1. Haga clic en **+ Asignar canal** del panel **CANALES ASIGNADOS** para poder abrir el cuadro de diálogo **Asignación de canal**.
   1. Haga clic en **Canal de referencia** por ruta.
   1. Haga clic en la **Ruta del canal**, igual que en **Demostración** > ***Canales*** > ***Global***.
   1. Escriba el **Rol del canal**, igual que **GlobalAdSegment**.
   1. Haga clic en **Eventos admitidos**, al igual que en **Carga inicial**, **Pantalla inactiva** y **Interacción del usuario**.
   1. Haga clic en **Guardar**.

   **Asignar canal por rol para la región:**

   1. Haga clic en **+ Asignar canal** desde el panel **CANALES ASIGNADOS**.
   1. En el cuadro de diálogo Asignación de canal, haga clic en **Canal de referencia** por nombre.
   1. Escriba el **Nombre de canal** como **región***.
   1. Escriba el **Rol de canal** como **RegionAdSegment**.
   1. Haga clic en **Guardar**.

   **Asignar canal por rol para tienda:**

   1. Haga clic en **+ Asignar canal** desde el panel **CANALES ASIGNADOS**.
   1. En el cuadro de diálogo Asignación de canal, haga clic en **Canal de referencia** por nombre.
   1. Escriba el **Nombre de canal** como **tienda**.
   1. Escriba el **Rol del canal** como **StoreAdSegment**.
   1. Haga clic en **Guardar**.

   La siguiente imagen muestra los canales asignados por ruta y por función.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuración de la secuencia incrustada dinámica en el canal global.**

   Vaya al canal **Global** que creó inicialmente en el proyecto **Demo**.

   Haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   En el editor, arrastre y suelte dos componentes de **Secuencia incrustada dinámica** en el editor de canales.

   Abra las propiedades de uno de los componentes e introduzca **Rol de asignación de canal** como **RegiónAdSegment**.

   Del mismo modo, haga clic en los demás componentes y abra las propiedades para escribir la **función de asignación de canal** como **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Asignando horario a cada pantalla**

   1. Vaya a cada pantalla, como **Demo** > **Ubicaciones** > **Región A** >**Tienda 1** >**`Store1Display`**.
   1. Haga clic en **Tablero** en la barra de acciones.
   1. En el panel, haga clic en **...** en el panel **CANALES Y PROGRAMACIONES ASIGNADOS** y, a continuación, haga clic en **+Asignar programa**.
   1. Haga clic en la ruta al horario (por ejemplo, aquí, **Demostración** > **Horarios** > **AdSchedule**).
   1. Haga clic en **Guardar**.

## Visualización de los resultados {#viewing-the-results}

Cuando haya completado la configuración de los canales y la visualización, inicie el Reproductor de AEM Screens para ver el contenido.

>[!NOTE]
>
>Para obtener más información acerca del Reproductor de AEM Screens, consulte los siguientes recursos:
>
>* [Descargar el Reproductor de AEM Screens](https://download.macromedia.com/screens/)
>* [Trabajando con el reproductor de AEM Screens](working-with-screens-player.md)


La siguiente salida confirma el contenido del canal en el Reproductor de AEM Screens, según la ruta de visualización.

**Ejemplo 1**:

Si asigna la ruta de visualización como **Demo** > **Ubicaciones** > **Región A** > **Tienda 1** > **`Store1Display`**, se mostrará el siguiente contenido en el reproductor AEM Screens.

![channeldisplay1](assets/channeldisplay1.gif)

**Ejemplo 1**:

Si asigna la ruta de visualización como **Demo** > **Ubicaciones** > **Región B** > **Tienda 3** > **`Store3Display`**, se mostrará el siguiente contenido en el reproductor AEM Screens.

![channeldisplay2](assets/channeldisplay2.gif)

## Restricción de usuarios y modificación de las ACL {#restricting-users-and-modifying-the-acls}

Puede crear autores globales, regionales o locales para editar el contenido relevante para ellos mientras se restringe la edición de canales superiores en la jerarquía.

Edite las ACL para que pueda restringir el acceso del usuario al contenido en función de su ubicación.

### Ejemplo de caso de uso {#example-use-case}

El siguiente ejemplo permite crear tres usuarios para el proyecto de demostración anterior.

Los privilegios asignados a cada grupo son los siguientes:

**Grupos**:

* **Autor global**: Consta de usuarios que tienen acceso a todas las ubicaciones y canales del proyecto **Demo** y que tienen todos los permisos de lectura, escritura y edición.

* **Autor de región**: Consta de usuarios que tienen permisos de lectura, escritura y edición en **Región A** y **Región B**.

* **Store-Author**: Consta de usuarios que tienen permisos de lectura, escritura y edición solo para **Store 1**, **Store 2**, **Store 3** y **Store 4**.

#### Pasos para crear grupos de usuarios, usuarios y configurar ACL {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Para obtener información detallada sobre cómo separar proyectos mediante ACL para que cada individuo o equipo administre su propio proyecto, consulte **Configuración de ACL**.

Siga los pasos a continuación para crear grupos y usuarios, y modificar las ACL según los permisos:

1. **Crear grupos**

   1. Vaya a **Adobe Experience Manager**.
   1. Haga clic en **Herramientas** > **Seguridad** > **Grupos**.
   1. Haga clic en **Crear grupo** e introduzca **Autor global** en **ID**.
   1. Haga clic en **Guardar y cerrar**.

   Del mismo modo, cree otros dos grupos, como **Region-Author** y **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Crear usuarios y agregar usuarios a grupos**

   1. Vaya a **Adobe Experience Manager**.
   1. Haga clic en **Herramientas** > **Seguridad** > **Usuarios**.
   1. Haz clic en **Crear usuario** y luego, en **ID**, escribe **Usuario global**.
   1. Escriba **Password** y confirme la contraseña de este usuario.
   1. Haga clic en la ficha **Grupos** e introduzca el nombre del grupo en **Haga clic en Grupo**; por ejemplo, escriba **Autor global** para agregar **Usuario global** a ese grupo específico.
   1. Haga clic en **Guardar y cerrar**.

   Del mismo modo, cree otros dos usuarios, como **Region-User** y **Store-User**, y agréguelos a **Region-Author** y **Store-Author** respectivamente.

   >[!NOTE]
   >Se recomienda agregar usuarios en un grupo y luego asignar permisos a cada grupo de usuarios en particular.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Agregar todos los grupos a los colaboradores**

   1. Vaya a **Adobe Experience Manager**.
   1. Haga clic en **Herramientas** > **Seguridad** > **Grupos**.
   1. Haga clic en **Colaboradores** de la lista y luego en la ficha **Miembros**.
   1. Haga clic en el **grupo**, como **Global-Author**, **Region-Author,** y **Store-Author**, para mostrar a los colaboradores.
   1. Haga clic en **Guardar y cerrar**.

1. **Permisos de acceso para cada grupo**

   1. Vaya a *User admin* y utilice esta interfaz de usuario para modificar los permisos para diferentes grupos.
   1. Busque **Autor global** y haga clic en la ficha **Permisos**, como se muestra en la figura siguiente.
   1. Del mismo modo, puede obtener acceso a los permisos de **Region-Author** y **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modificar permisos para cada grupo**

   **Para autor global:**

   1. Vaya a la ficha **Permisos**
   1. Vaya a ***/content/screens/demo*** y compruebe todos los permisos
   1. Vaya a ***/content/screens/demo/locations*** y compruebe todos los permisos
   1. Vaya a ***/content/screens/demo/locations/region-a*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos de **`region-b`**.

   Consulte la siguiente figura para comprender los pasos:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   Lo siguiente muestra que **Global-User** tiene acceso al **Canal global**. Y también acceso a **Región A** y **Región B** con las cuatro tiendas, a saber **Tienda 1**, **Tienda 2**, **Tienda 3** y **Tienda 4**.

   ![global](assets/global.gif)

   **Para Region-Author:**

   1. Vaya a la ficha **Permisos**.
   1. Vaya a ***/content/screens/demo*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/locations*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/channels*** y desmarque los permisos para el canal **Global**.
   1. Vaya a ***/content/screens/demo/locations***/***region-a*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos de **`region-b`**.

   Consulte la siguiente imagen para comprender los pasos:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   A continuación se muestra que el usuario de la región tiene acceso a **Región A** y a **Región B**. Además, tiene acceso a las cuatro tiendas, a saber, **Tienda 1**, **Tienda 2**, **Tienda 3** y **Tienda 4**, pero no tiene acceso al canal **Global**.

   ![región](assets/region.gif)

   **Para Store-Author:**

   1. Vaya a la ficha **Permisos**.
   1. Vaya a ***/content/screens/demo*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/locations*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/channels*** y desmarque los permisos para el canal **Global**.
   1. Vaya a ***/content/screens/demo/locations/region-a*** y compruebe solo los permisos de **Read**. Del mismo modo, compruebe solamente los permisos de **Read** para **`region-b`**.
   1. Vaya a ***/content/screens/demo/locations***/***region-a /store-1*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos de **store-2, store-3,** y **store-4**.

   Consulte la siguiente imagen para comprender los pasos:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   A continuación se muestra que **Store-User** solo tiene acceso a **Store 1**, **Store 2**, **Store 3** y **Store 4**. Sin embargo, no tiene permisos para acceder a los canales de **Global** o región (**Región A** y **Región B**).

   ![tienda](assets/store.gif)

>[!NOTE]
>
>Para obtener información detallada sobre la configuración de permisos, consulte [Configuración de ACL](setting-up-acls.md).
