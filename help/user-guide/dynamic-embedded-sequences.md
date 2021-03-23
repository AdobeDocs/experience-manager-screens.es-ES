---
title: Usar la secuencia integrada dinámica
seo-title: Usar la secuencia integrada dinámica
description: Siga esta página para aprender a implementar Secuencias integradas dinámicas en su proyecto de AEM Screens.
seo-description: Siga esta página para aprender a implementar Secuencias integradas dinámicas en su proyecto de AEM Screens.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
feature: Creación en Screens
role: Administrador, Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '2540'
ht-degree: 3%

---


# Usar la secuencia integrada dinámica {#using-dynamic-embedded-sequence}

El uso de secuencias integradas dinámicas cubre los siguientes temas:

* **Información general**
* **Uso de la experiencia integrada dinámica en AEM Screens**
* **Visualización de los resultados**
* **Restricción de usuarios y modificación de las ACL**

## Información general {#overview}

***Las*** secuencias integradas dinámicas se crean para proyectos grandes que siguen la jerarquía secundaria principal, donde se hace referencia al elemento secundario dentro de una carpeta de ubicación y no de un canal. Permite al usuario incrustar una secuencia dentro de un canal mediante ***Rol del canal***. Permite al usuario definir marcadores de posición específicos de ubicación para diferentes oficinas mediante una secuencia integrada dentro de un canal principal.

Al asignar un canal a una visualización, tiene la opción de especificar la ruta de acceso de la visualización o la función del canal que se convertirá en un canal real por contexto.

Para utilizar Secuencia integrada dinámica, asigne un canal mediante ***Rol del canal***. Rol del canal define el contexto de la visualización. La función está dirigida por varias acciones y es independiente del canal real que cumple la función. En esta sección se describe un caso de uso sencillo que define los canales por rol y cómo se puede aprovechar ese contenido en un canal global. También puede considerar la función como un identificador para la asignación o como un alias para el canal en el contexto de .

### Ventajas del uso de secuencias integradas dinámicas {#benefits-of-using-dynamic-embedded-sequences}

La principal ventaja de colocar un canal de secuencia dentro de una ubicación en lugar de la carpeta de canales es permitir que los autores locales o regionales editen contenido relevante para ellos mientras se les restringe de editar canales en una posición superior de la jerarquía.

Al hacer referencia a un *canal por rol*, puede crear la versión local de un canal para así resolver de forma dinámica el contenido de una ubicación específica, así como crear un canal global que aproveche el contenido de los canales específicos de la ubicación.

>[!NOTE]
>
>**Secuencias integradas frente a secuencias integradas dinámicas**
>
>Una secuencia integrada dinámica es similar a una secuencia integrada, pero permite al usuario seguir una jerarquía en la que los cambios o actualizaciones realizados en un canal se propagan a otro relacionado. Rastrea la jerarquía principal-secundaria e incluye recursos como imágenes o vídeos.
>
>***Las*** secuencias integradas dinámicas le permiten mostrar contenido específico de la ubicación, mientras que las  ***secuencias*** incrustadas solo muestran diapositivas generales del contenido. Además, al configurar las secuencias integradas dinámicas, debe configurar el canal mediante el rol y el nombre del canal. Consulte los pasos que se indican a continuación para una implementación práctica.
>
>Para obtener más información sobre la implementación de secuencias integradas, consulte [Secuencias integradas](embedded-sequences.md) en AEM Screens.

El siguiente ejemplo proporciona una solución centrándose en los siguientes términos clave:

* a ***canal de secuencia principal*** para la secuencia global
* ***componentes de*** secuencias incrustadas dinámicas para cada parte personalizable localmente de la secuencia
* ***canales de secuencia individuales*** en las ubicaciones respectivas con una  ** función en la pantalla que coincida con la  **función *del componente de secuencia integrada*dinámica.**

>[!NOTE]
>
>Para obtener más información sobre la asignación de canales, consulte **[Asignación de canales](channel-assignment.md)** en la sección Creación de la documentación de AEM Screens.

## Usar la secuencia integrada dinámica {#using-dynamic-embedded-sequence-2}

En la siguiente sección se explica la creación de una secuencia integrada dinámica en un canal de AEM Screens.

### Requisitos previos {#prerequisites}

Antes de empezar a implementar esta funcionalidad, asegúrese de que tiene los siguientes requisitos previos listos para empezar a implementar secuencias integradas dinámicas:

* Crear un proyecto de AEM Screens (en este ejemplo, **Demostración**)

* Cree un canal como **Global** en la carpeta **Channels**

* Añadir contenido a su canal **global** (*Consulte **Resources.zip**para ver los recursos relevantes*)

La siguiente imagen muestra el proyecto **Demo** con el canal **Global** en la carpeta **Channels**.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Medios {#resources}

Puede descargar los siguientes recursos (imágenes y agregarlas a recursos) y usarlos como contenido de canal con fines de demostración.

[Obtener archivo](assets/resources.zip)

>[!NOTE]
>
>Para obtener información adicional sobre cómo crear un proyecto y cómo crear un canal de secuencia, consulte los recursos a continuación:
>
>* **[Creación y administración de proyectos](creating-a-screens-project.md)**
>* **[Administración de un canal](managing-channels.md)**

>



La implementación de Secuencia integrada dinámica en un proyecto de AEM Screens implica tres tareas principales:

1. **Configuración de la taxonomía del proyecto, incluidos Canales, Ubicaciones y Visualizaciones**
1. **Creación de un programa**
1. **Asignación de programación a cada visualización**

Siga los pasos a continuación para implementar la funcionalidad:

>[!CAUTION]
>
>Al implementar Secuencias integradas dinámicas, tenga cuidado con los campos **Name** y **Title** al crear canales en cada ubicación. Siga cuidadosamente las instrucciones sobre la nomenclatura.

1. **Crear dos carpetas de ubicaciones.**

   Vaya a la carpeta **Ubicaciones** del proyecto de AEM Screens y cree dos carpetas de ubicación como **Región A** y **Región B**.

   >[!NOTE]
   >
   >Al crear la carpeta de ubicación **Región A**, asegúrese de introducir el **Título** como **Región A** y puede dejar vacío el campo **Nombre**, por lo que se selecciona automáticamente el nombre **región-a**.
   >
   >De forma similar, es el caso para crear la carpeta de ubicación **Región B**, como se muestra a continuación:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Para aprender a crear una ubicación, consulte **[Creación y administración de ubicaciones](managing-locations.md)**.

1. **Cree dos ubicaciones y un canal debajo de cada carpeta de ubicación.**

   1. Vaya a **Demostración** —> **Ubicaciones** —> **Región A**.
   1. Seleccione **Región A** y haga clic en **+ Crear** en la barra de acciones.
   1. Seleccione **Ubicación** del asistente con **Título** como **Almacenamiento 1**. Del mismo modo, cree otra ubicación desde el asistente con el título **Store 2** con **Title** como **Store 2**. Puede dejar vacío el campo **Name** al crear **Store 1** y **Store 2**.
   1. Repita el paso (b) y seleccione **Canal de secuencia** en el asistente. Introduzca el **Título** como **Región A** y **Nombre** como **región** para este canal.

   >[!CAUTION]
   >
   >Asegúrese de que, al crear el canal **Region A**, introduzca **Title** como **Region A** y **Name** como **region**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Del mismo modo, cree dos ubicaciones en **Región B** con el título **Tienda 3** y **Tienda 4**. Además, cree un **Canal de secuencia** con **Título** como **Región B** y **Nombre** como **región**.

   >[!CAUTION]
   >
   >Asegúrese de que puede utilizar el mismo nombre para los canales creados en **Región A** y **Región B** que **región**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Cree Mostrar y Canal debajo de cada Ubicación.**

   1. Vaya a **Demostración** —> **Ubicaciones** —> **Región A** —> **Almacenar 1**.
   1. Seleccione **Store 1** y haga clic en **+ Crear** en la barra de acciones.
   1. Seleccione **Display** del asistente y cree **Store1Display.**
   1. Repita el paso (b) y esta vez seleccione **Canal de secuencia** en el asistente. Introduzca **Title** como **Store1Channel** y **Name** como **store**.

   >[!CAUTION]
   >
   >Es importante que al crear un canal de secuencia, el **Título** del canal pueda ser el requisito, pero el **Nombre** debe ser el mismo en todos los canales locales.
   >En este ejemplo, los canales de **Región A** y **Región B** comparten el mismo **Nombre** que **región** y los canales de **Tienda 1**, **Tienda 2**, **Store 3** y **Store 4** comparten el mismo **Name** que **store**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Del mismo modo, cree una visualización como **Store2Display** y un canal **Store2Channel** en **Store 2** (con el nombre **store**).

   >[!NOTE]
   >Asegúrese de que puede utilizar el mismo nombre para los canales creados en **Store 1** y **Store 2** que **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Siga los pasos anteriores para crear un canal y mostrarlo en **Store 3** y **Store 4** en **Región B**. De nuevo, asegúrese de utilizar el mismo **Name** que **store** al crear el canal **Store3Channel** y **Store4Channel** respectivamente.

   La siguiente imagen muestra la visualización y el canal en **Store 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   La siguiente imagen muestra la visualización y el canal en **Store 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Agregue contenido a los canales en sus respectivas ubicaciones.**

   Vaya a la **Demostración** -> **Ubicaciones** -> **Región A** -> **Región A** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte los recursos que desee añadir al canal.

   >[!NOTE]
   >Puede utilizar el archivo ***Resources.zip*** de la sección **Resources** anterior para usar las imágenes como recursos para el contenido del canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Del mismo modo, vaya a la **Demostración** -> **Ubicaciones** -> **Región B** -> **Región B** y haga clic en **Editar** en la barra de acciones para arrastrar y soltar los recursos en el canal, como se muestra a continuación:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Siga los pasos anteriores y los recursos para añadir contenido a los siguientes canales:

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **Crear un programa**

   Desplácese y seleccione la carpeta **Programas** en el proyecto de AEM Screens y haga clic en **Crear** en la barra de acciones para crear una nueva programación.

   La siguiente imagen muestra el **AdSchedule** creado en el proyecto **Demo**.

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Asignar canales a una programación**

   1. Vaya a **Demo** —> **Programas** —> **AdSchedule** y haga clic en **Panel** en la barra de acciones.
   1. Haga clic en **+ Asignar canal** en el panel **CANALES ASIGNADOS** para abrir el cuadro de diálogo **Asignación de canales**.
   1. Seleccione **Canal de referencia**.. por ruta.
   1. Seleccione la **Ruta del canal** como **Demostración** —> ***Canales*** —> ***Global***.
   1. Introduzca el **Rol del canal** como **GlobalAdSegment**.
   1. Seleccione **Eventos admitidos** como **Carga inicial**, **Pantalla inactiva** e **Interacción del usuario**.
   1. Haga clic en **Guardar**.

   **Asignar canal por función para la región:**

   1. Haga clic en **+ Asignar canal** en el panel **CANALES ASIGNADOS** para abrir el cuadro de diálogo **Asignación de canales**.
   1. Seleccione **Canal de referencia**. por nombre.
   1. Introduzca el **Nombre del canal** como **region***.
   1. Introduzca el **Rol del canal** como **RegionAdSegment**.
   1. Haga clic en **Guardar**.

   **Asignar canal por función para la tienda:**

   1. Haga clic en **+ Asignar canal** en el panel **CANALES ASIGNADOS** para abrir el cuadro de diálogo **Asignación de canales**.
   1. Seleccione **Canal de referencia**. por nombre.
   1. Introduzca **Channel Name** como **store**.
   1. Introduzca el **Rol del canal** como **StoreAdSegment**.
   1. Haga clic en **Guardar**.

   La siguiente imagen muestra los canales asignados por ruta y por rol.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuración de la secuencia integrada dinámica en el canal global.**

   Vaya al canal **Global** que creó inicialmente en el proyecto **Demostración**.

   Haga clic en **Editar** en la acción para abrir el editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Arrastre y suelte dos componentes **Secuencia integrada dinámica** en el editor de canales.

   Abra las propiedades de uno de los componentes e introduzca **Channel Assignment Role** como **RegionAdSegment**.

   Del mismo modo, seleccione el otro componente y abra las propiedades para introducir el **Rol de asignación de canales** como **StoreAdSegment**.

   ![pantalla del canal4](assets/channeldisplay4.gif)

1. **Asignación de la programación a cada visualización**

   1. Vaya a cada pantalla, como **Demo** —> **Ubicaciones** —> **Región A** —>**Tienda 1** —>**Tienda1Pantalla**.
   1. Haga clic en **Dashboard** desde la acción para abrir el tablero de visualización.
   1. Haga clic en **...** del panel **CANALES Y PROGRAMAS ASIGNADOS** y haga clic en **+Asignar programación**.
   1. Seleccione la ruta de acceso a la programación (por ejemplo, aquí, **Demostración** —> **Programas** —>**AdSchedule**).
   1. Haga clic en **Guardar**.

## Visualización de los resultados {#viewing-the-results}

Una vez que haya configurado los canales y se haya completado la visualización, inicie el reproductor AEM Screens para ver el contenido.

>[!NOTE]
>
>Para obtener más información sobre AEM reproductor de pantalla, consulte los siguientes recursos:
>
>* [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/)
>* [Uso de AEM Screens Player](working-with-screens-player.md)



La siguiente salida confirma el contenido del canal en el reproductor AEM Screens, según la ruta de visualización.

**Escenario 1**:

Si asigna la ruta de visualización como **Demostración** —> **Ubicaciones** —> **Región A** —> **Tienda 1** —> **Tienda1Pantalla**, el siguiente contenido se mostrará en el reproductor de AEM Screens.

![pantalla del canal1](assets/channeldisplay1.gif)

**Escenario 1**:

Si asigna la ruta de visualización como **Demostración** —> **Ubicaciones** —> **Región B** —> **Tienda 3** —> **Tienda3Display**, el siguiente contenido se mostrará en el reproductor de AEM Screens.

![channelDisplay2](assets/channeldisplay2.gif)

## Restricción de usuarios y modificación de las ACL {#restricting-users-and-modifying-the-acls}

Puede crear autores globales, regionales o locales para editar contenido relevante para ellos mientras se les restringe la edición de canales arriba en la jerarquía.

Debe modificar las ACL para restringir el acceso de los usuarios al contenido en función de su ubicación.

### Ejemplo de caso de uso {#example-use-case}

El siguiente ejemplo le permite crear tres usuarios para el proyecto Demo anterior.

Los privilegios se asignan a cada grupo de la siguiente manera:

**Grupos**:

* **Autor global**: Consiste en usuarios que tienen acceso a todas las ubicaciones y canales del  **** proyecto Demoproject y que tienen todos los permisos de lectura, escritura y edición.

* **Autor de región**: Consta de usuarios que tienen permisos de lectura, escritura y edición en la  **región** y la  **región B**.

* **Store-Author**: Consta de usuarios que tienen permisos de lectura, escritura y edición solo para  **Tienda 1**,  **Tienda 2**,  **Tienda 3** y  **Tienda 4**.

#### Pasos para crear grupos de usuarios, usuarios y configurar ACL {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Para aprender en detalle cómo segregar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto, consulte **Configuración de ACL**.

Siga los pasos a continuación para crear grupos, usuarios y modificar las ACL según los permisos:

1. **Crear grupos**

   1. Vaya a **Adobe Experience Manager**.
   1. Haga clic en **Herramientas** —> **Seguridad** —> **Grupos**.
   1. Haga clic en **Crear grupo** e introduzca **Global-Author** en **ID**.
   1. Haga clic en **Guardar y cerrar**.

   Del mismo modo, cree otros dos grupos, como **Region-Author** y **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Crear usuarios y agregar usuarios a grupos**

   1. Vaya a **Adobe Experience Manager**.
   1. Haga clic en **Herramientas** —> **Seguridad** —> **Usuarios**.
   1. Haga clic en **Crear usuario** e introduzca **Usuario global** en **ID**.
   1. Introduzca **Password** y confirme la contraseña de este usuario.
   1. Haga clic en la ficha **Grupos** e introduzca el nombre del grupo en **Seleccionar grupo**, por ejemplo, introduzca **Autor global** para agregar **Usuario global** a ese grupo específico.
   1. Haga clic en **Guardar y cerrar**.

   Del mismo modo, cree otros dos usuarios, como **Region-User** y **Store-User**, y agréguelos a **Region-Author** y **Store-Author** respectivamente.

   >[!NOTE]
   >Se recomienda agregar usuarios a un grupo y luego asignar permisos a cada grupo de usuarios en particular.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Agregar todos los grupos a los colaboradores**

   1. Vaya a **Adobe Experience Manager**.
   1. Haga clic en **Herramientas** —> **Seguridad** —> **Grupos**.
   1. Seleccione **Contributors** de la lista y seleccione la pestaña **Members**.
   1. Seleccione el **Grupo** como **Autor global**, **Autor de región,** y **Autor de tienda** para los colaboradores.
   1. Haga clic en **Guardar y cerrar**.

1. **Acceso a los permisos de cada grupo**

   1. Vaya a *Useradmin* y utilice esta IU para modificar los permisos de los distintos grupos.
   1. Busque **Global-Author** y haga clic en la pestaña **Permisos**, como se muestra en la figura siguiente.
   1. Del mismo modo, puede acceder a los permisos de **Region-Author** y **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modificación de los permisos de cada grupo**

   **Para Autor global:**

   1. Vaya a la pestaña **Permisos**
   1. Vaya a ***/content/screens/demo*** y compruebe todos los permisos
   1. Vaya a ***/content/screens/demo/locations*** y compruebe todos los permisos
   1. Vaya a ***/content/screens/demo/locations/region-a*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos de **region-b**.

   Consulte la figura siguiente para comprender los pasos:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   La siguiente imagen muestra que ahora el **Usuario global** tiene acceso al **Canal global** y a la **Región A** y la **Región B** con las cuatro tiendas, concretamente **Tienda 1**, **Tienda 2&lt;a11/** Store 3 **y** Store 4 **.**

   ![global](assets/global.gif)

   **Para Región-Autor:**

   1. Vaya a la pestaña **Permissions**.
   1. Vaya a ***/content/screens/demo*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/locations*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/channels*** y desmarque los permisos del canal **Global**.
   1. Vaya a ***/content/screens/demo/locations***/***region-a*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos de **region-b**.

   Consulte la figura siguiente para comprender los pasos:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   La siguiente imagen muestra que ahora el usuario de la región tiene acceso a las regiones **A** y **B** con las cuatro tiendas, a saber **Store 1**, **Store 2**, **Store 3** y **Store 4&lt;a1 1/> pero no tiene acceso al canal** Global **.**

   ![región](assets/region.gif)

   **Para Store-Author:**

   1. Vaya a la pestaña **Permissions**.
   1. Vaya a ***/content/screens/demo*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/locations*** y compruebe solo los permisos de **Read**.
   1. Vaya a ***/content/screens/demo/channels*** y desmarque los permisos del canal **Global**.
   1. Vaya a ***/content/screens/demo/locations/region-a*** y compruebe solo los permisos de **Read**. Del mismo modo, compruebe solo los permisos de **Read** para **region-b**.
   1. Vaya a ***/content/screens/demo/locations***/***region-a /store-1*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos de **store-2, store-3,** y **store-4**.

   Consulte la figura siguiente para comprender los pasos:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   La siguiente imagen muestra que ahora el **Store-User** solo tiene acceso a las cuatro tiendas, a saber **Store 1**, **Store 2**, **Store 3** y **Store 4**, pero no tiene permisos para acceder al **Global&lt;a> 11/> o los canales de la región (** Región A **y** Región B **).**

   ![almacenar](assets/store.gif)

>[!NOTE]
>
>Para obtener más información sobre la configuración de permisos, consulte [Configuración de ACL](setting-up-acls.md).

