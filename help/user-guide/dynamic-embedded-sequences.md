---
title: Usar la secuencia integrada dinámica
seo-title: Usar la secuencia integrada dinámica
description: Siga esta página para aprender a implementar secuencias incrustadas dinámicas en su proyecto de AEM Screens.
seo-description: Siga esta página para aprender a implementar secuencias incrustadas dinámicas en su proyecto de AEM Screens.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '2535'
ht-degree: 3%

---


# Usar la secuencia integrada dinámica {#using-dynamic-embedded-sequence}

El uso de secuencias incrustadas dinámicas abarca los siguientes temas:

* **Información general**
* **Uso de la experiencia incrustada dinámica en AEM Screens**
* **Visualización de los resultados**
* **Restricción de usuarios y modificación de las ACL**

## Información general {#overview}

***Las secuencias*** incrustadas dinámicas se crean para proyectos grandes que siguen la jerarquía secundaria principal, donde se hace referencia al elemento secundario dentro de una carpeta de ubicación y no en una carpeta de canal. It allows the user to embed a sequence inside a channel by ***Channel Role***. Permite al usuario definir marcadores de posición específicos de ubicación para diferentes oficinas mediante una secuencia incrustada dentro de un canal principal.

Al asignar un canal a una pantalla, tiene la opción de especificar la ruta de la pantalla o la función del canal que se resolverá en un canal real por contexto.

Para utilizar la secuencia incrustada dinámica, asigne un canal por función ***de*** Canal. Función de canal define el contexto de la visualización. La función está dirigida por varias acciones y es independiente del canal real que cumple la función. En esta sección se describe un caso de uso sencillo que define los canales por rol y cómo se puede aprovechar ese contenido en un canal global. También puede considerar la función como un identificador para la asignación o un alias para el canal en el contexto de.

### Ventajas del uso de secuencias incrustadas dinámicas {#benefits-of-using-dynamic-embedded-sequences}

La principal ventaja de colocar un canal de secuencia dentro de una ubicación en lugar de la carpeta canales es permitir que los autores locales o regionales editen contenido relevante para ellos mientras se les restringe la edición de canales en una posición superior de la jerarquía.

Referencing a *Channel By Role*, allows you to create local version of a channel, in order to dynamically resolve location-specific content and also allows you to create a global channel that leverages the content for the location-specific channels.

>[!NOTE]
>
>**Secuencias incrustadas frente a secuencias incrustadas dinámicas**
>
>Una secuencia incrustada dinámica es similar a una secuencia incrustada, pero permite al usuario seguir una jerarquía en la que los cambios/actualizaciones realizados en un canal se propagan a otro en relación. Sigue la jerarquía principal-secundario e incluye también recursos como imágenes o vídeos.
>
>***Las secuencias*** incrustadas dinámicas le permiten mostrar contenido específico de la ubicación, mientras que las secuencias ****** incrustadas solo muestran una presentación de diapositivas general del contenido. Además, al configurar las secuencias incrustadas dinámicas, debe configurar el canal con la función y el nombre del canal. Consulte los pasos que se indican a continuación para obtener información sobre la aplicación práctica.
>
>Para obtener más información sobre la implementación de secuencias incrustadas, consulte Secuencias [](embedded-sequences.md) incrustadas en AEM Screens.

El siguiente ejemplo proporciona una solución centrándose en los siguientes términos clave:

* un canal ***de secuencia*** principal para la secuencia global
* ***componentes de secuencia*** incrustada dinámica para cada parte personalizable localmente de la secuencia
* ***canales*** de secuencia individuales en las ubicaciones respectivas con una *función* en la pantalla que coincida con la **función *del componente de secuencia incrustada*dinámica.**

>[!NOTE]
>
>To learn more about channel assignment, see **[Channel Assignment](channel-assignment.md)** under Authoring section in AEM Screens documentation.

## Usar la secuencia integrada dinámica {#using-dynamic-embedded-sequence-2}

En la siguiente sección se explica la creación de una secuencia incrustada dinámica en un canal AEM Screens.

### Requisitos previos {#prerequisites}

Antes de implementar esta funcionalidad en inicio, asegúrese de tener los siguientes requisitos previos listos para inicio para implementar secuencias dinámicas incrustadas:

* Creación de un proyecto de AEM Screens (en este ejemplo, **Demostración**)

* Crear un canal como **global** en la carpeta **Canales**

* Añadir contenido a su Canal **global** (*consulte **Resources.zip**para ver los recursos* relevantes)

La siguiente imagen muestra el proyecto **Demo** con canal **global** en la carpeta **Canales** .
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Medios {#resources}

Puede descargar los siguientes recursos (imágenes y agregarlas a los recursos) y usarlas como contenido de canal para fines de demostración.

[Obtener archivo](assets/resources.zip)

>[!NOTE]
>
>Para obtener información adicional sobre cómo crear un proyecto y cómo crear un canal de secuencia, consulte los recursos siguientes:
>
>* **[Creación y administración de proyectos](creating-a-screens-project.md)**
>* **[Administración de un Canal](managing-channels.md)**

>



La implementación de la secuencia incrustada dinámica en un proyecto de AEM Screens implica tres tareas principales:

1. **Configuración de la taxonomía del proyecto, incluidos Canales, ubicaciones y pantallas**
1. **Creación de un programa**
1. **Asignación de programación a cada visualización**

Siga los pasos a continuación para implementar la funcionalidad:

>[!CAUTION]
>
>Al implementar secuencias incrustadas dinámicas, tenga cuidado con los campos **Nombre** y **Título** al crear canales en cada ubicación. Siga cuidadosamente las instrucciones sobre la nomenclatura.

1. **Cree dos carpetas de ubicaciones.**

   Vaya a la carpeta **Ubicaciones** del proyecto de AEM Screens y cree dos carpetas de ubicación como **Región A** y **Región B**.

   >[!NOTE]
   >
   >Al crear la carpeta de ubicación **Región A** , asegúrese de introducir el **Título** como **Región A** y puede dejar vacío el campo **Nombre** , de modo que se recoja automáticamente el nombre de **región** .
   >
   >De manera similar, se puede crear la carpeta de ubicación **Región B**, como se muestra a continuación:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Para obtener información sobre cómo crear una ubicación, consulte **[Creación y administración de ubicaciones](managing-locations.md)**.

1. **Cree dos ubicaciones y un Canal debajo de cada carpeta de ubicación.**

   1. Vaya a **Demostración** —> **Ubicaciones** —> **Región A**.
   1. Seleccione **Región A** y haga clic en **+ Crear** en la barra de acciones.
   1. Seleccione **Ubicación** en el asistente con **Título** como **Tienda 1**. Del mismo modo, cree otra ubicación desde el asistente titulada **Tienda 2** con **Título** como **Tienda 2**. Puede dejar vacío el campo **Nombre** al crear **Tienda 1** y **Tienda 2**.
   1. Repita el paso (b) y seleccione **Secuencia Canal** en el asistente. Introduzca el **Título** como **Región A** y **Nombre** como **región** para este canal.

   >[!CAUTION]
   >
   >Asegúrese de que, al crear la **región A** de canal, introduzca el **título** como **región A** y el **nombre** como **región**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Del mismo modo, cree dos ubicaciones en la **región B** con el título **Tienda 3** y **Tienda 4**. También puede crear un Canal **** de secuencia con **Título** como **Región B** y **Nombre** como **región**.

   >[!CAUTION]
   >
   >Asegúrese de que puede utilizar el mismo nombre para los canales creados en la **región A** y en la **región B** como **región**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Cree la visualización y el Canal debajo de cada ubicación.**

   1. Vaya a **Demostración** —> **Ubicaciones** —> **Región A** —> **Tienda 1**.
   1. Seleccione **Tienda 1** y haga clic en **+ Crear** en la barra de acciones.
   1. Seleccione **Mostrar** en el asistente y cree **Store1Display.**
   1. Repita el paso (b) y seleccione esta vez **Secuencia Canal** en el asistente. Introduzca el **Título** como **Canal** Store1 y el **Nombre** como **almacén**.

   >[!CAUTION]
   >
   >Es importante crear un canal de secuencia, el **Título** del canal puede ser el que se requiera, pero el **Nombre** debe ser el mismo en todos los canales locales.
   >En este ejemplo, los canales de la **Región A** y la **Región B** comparten el mismo **nombre** que **región** y canales de la **Tienda 1************** **** ****, Tienda 2, Tienda 3, Tienda y Tienda 4comparten el mismo nombrede tiendacon tienda.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Del mismo modo, cree una pantalla como **Store2Display** y un **Canal** canal Store2 en **Store 2** (con el nombre de **tienda**).

   >[!NOTE]
   >Asegúrese de que puede usar el mismo nombre para los canales creados en la **tienda 1** y en la **tienda 2** como **tienda**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Siga los pasos anteriores para crear un canal y mostrarlo en la **Tienda 3** y en la **Tienda 4** en la **Región B**. De nuevo, asegúrese de usar el mismo **nombre** que la **tienda** al crear canal **Store3Canal** y **Store4Canal** respectivamente.

   La siguiente imagen muestra la visualización y el canal en la **Tienda 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   La siguiente imagen muestra la visualización y el canal en la **Tienda 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Añadir contenido a los Canales de sus respectivas ubicaciones.**

   Vaya a **Demostración** -> **Ubicaciones** -> **Región A** -> **Región A** y haga clic en **Editar** en la barra de acciones. Arrastre y suelte los recursos que desee agregar al canal.

   >[!NOTE]
   >Puede utilizar el archivo ***Resources.zip*** de la sección **Recursos** anterior para utilizar las imágenes como recursos para el contenido de canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Del mismo modo, vaya a la **demostración** -> **Ubicaciones** -> **Región B** -> **Región B** y haga clic en **Editar** en la barra de acciones para arrastrar y soltar los recursos en el canal, como se muestra a continuación:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Siga los pasos anteriores y los recursos para agregar contenido a los siguientes canales:

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **Crear una programación**

   Desplácese y seleccione la carpeta **Programaciones** en el proyecto de AEM Screens y haga clic en **Crear** en la barra de acciones para crear una nueva programación.

   La siguiente imagen muestra el **AdSchedule** creado en el proyecto de **demostración** .

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Asignar Canales a una programación**

   1. Vaya a **Demostración** —> **Programaciones** —> **Programación** de publicidad y haga clic en **Panel** en la barra de acciones.
   1. Haga clic en **+ Asignar Canal** desde el panel CANALES **** ASIGNADOS para abrir el cuadro de diálogo Asignación **de** Canal.
   1. Select **Reference Channel**.. by path.
   1. Seleccione la Ruta **de** Canal como **Demostración** —> ***Canales*** —> ***Global***.
   1. Enter the **Channel Role** as **GlobalAdSegment**.
   1. Seleccione los Eventos **** admitidos como Carga **** inicial, **Pantalla** inactiva e Interacción **del usuario**.
   1. Haga clic en **Guardar**.

   **Asignar Canal por función para la región:**

   1. Haga clic en **+ Asignar Canal** desde el panel CANALES **** ASIGNADOS para abrir el cuadro de diálogo Asignación **de** Canal.
   1. Seleccione **Canal** de referencia. por nombre.
   1. Introduzca el nombre **del** Canal como **región***.
   1. Enter the **Channel Role** as **RegionAdSegment**.
   1. Haga clic en **Guardar**.

   **Asignar Canal por función para la tienda:**

   1. Haga clic en **+ Asignar Canal** desde el panel CANALES **** ASIGNADOS para abrir el cuadro de diálogo Asignación **de** Canal.
   1. Seleccione **Canal** de referencia. por nombre.
   1. Introduzca el nombre **del** Canal como **tienda**.
   1. Enter the **Channel Role** as **StoreAdSegment**.
   1. Haga clic en **Guardar**.

   La siguiente imagen muestra los canales asignados por ruta y función.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuración de la secuencia incrustada dinámica en el Canal global.**

   Vaya al Canal **global** que creó inicialmente en el proyecto de **demostración** .

   Click **Edit** from the action to open the editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Arrastre y suelte dos componentes de secuencia **incrustada** dinámica en el editor de canal.

   Abra las propiedades de uno de los componentes e introduzca la función **de asignación de** Canales como **RegiónAdSegment**.

   Del mismo modo, seleccione el otro componente y abra las propiedades para introducir la función **de asignación de** Canal como **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Asignación de programación a cada visualización**

   1. Vaya a cada pantalla, como **Demostración** —> **Ubicaciones** —> **Región A** —>**Tienda 1** —>**Tienda1 Visualización**.
   1. Click **Dashboard** from the action to open the display dashboard.
   1. Haga clic en **...** en el panel CANALES y PROGRAMAS **ASIGNADOS y haga clic en** +Asignar programación ****.
   1. Seleccione la ruta de la programación (por ejemplo, aquí, **Demostración** —> **Programaciones** —>**AnuncioProgramación**).
   1. Haga clic en **Guardar**.

## Visualización de los resultados {#viewing-the-results}

Una vez que haya configurado los canales y se haya completado la visualización, inicie el reproductor de AEM Screens para la vista del contenido.

>[!NOTE]
>
>Para obtener más información sobre AEM reproductor de pantalla, consulte los siguientes recursos:
>
>* [Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/)
>* [Uso de AEM Screens Player](working-with-screens-player.md)



El siguiente resultado confirma el contenido de canal en el reproductor de AEM Screens, según la ruta de visualización.

**Escenario 1**:

Si asigna la ruta de visualización como **Demostración** —> **Ubicaciones** —> **Región A** —> **Tienda 1** —> **Tienda1 Visualización**, se mostrará el siguiente contenido en su reproductor de AEM Screens.

![channeldisplay1](assets/channeldisplay1.gif)

**Escenario 1**:

Si asigna la ruta de visualización como **Demostración** —> **Ubicaciones** —> **Región B** —> **Tienda 3** —> **Tienda3Visualización**, se mostrará el siguiente contenido en su reproductor de AEM Screens.

![channeldisplay2](assets/channeldisplay2.gif)

## Restricción de usuarios y modificación de las ACL {#restricting-users-and-modifying-the-acls}

Puede crear autores globales, regionales o locales para editar contenido relevante para ellos mientras se les restringe la edición de canales en una posición superior de la jerarquía.

Debe modificar las ACL para restringir el acceso de los usuarios al contenido en función de su ubicación.

### Ejemplo de caso de uso {#example-use-case}

El siguiente ejemplo permite crear tres usuarios para el proyecto de demostración anterior.

Los privilegios se asignan a cada grupo de la siguiente manera:

**Grupos**:

* **Autor** global: Consiste en usuarios que tienen acceso a todas las ubicaciones y canales del proyecto de **demostración** y tienen todos los permisos de lectura, escritura y edición.

* **Región-Autor**: Consiste en usuarios que tienen permisos de lectura, escritura y edición para la **región A** y la **región B**.

* **Store-Author**: Consta de usuarios que tienen permisos de lectura, escritura y edición solamente para **Tienda 1**, **Tienda 2**, **Tienda 3** y **Tienda 4**.

#### Pasos para crear grupos de usuarios, usuarios y configurar ACL {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Para aprender en detalle cómo segregar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto, consulte **Configuración de ACL**.

Siga los pasos a continuación para crear grupos, usuarios y modificar las ACL según los permisos:

1. **Crear grupos**

   1. Vaya a **Adobe Experience Manager**.
   1. Click **Tools** --> **Security** --> **Groups**.
   1. Haga clic en **Crear grupo** e introduzca Autor **** global en **ID**.
   1. Haga clic en **Guardar y cerrar**.

   Del mismo modo, cree otros dos grupos, como **Región-Autor** y **Tienda-Autor**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Crear usuarios y agregar usuarios a grupos**

   1. Vaya a **Adobe Experience Manager**.
   1. Click **Tools** --> **Security** --> **Users**.
   1. Haga clic en **Crear usuario** e introduzca Usuario **** global en **ID**.
   1. Introduzca **la contraseña** y confirme la contraseña de este usuario.
   1. Haga clic en la ficha **Grupos** e introduzca el nombre del grupo en **Seleccionar grupo**, por ejemplo, escriba **Global-Author** para agregar **Global-User** a ese grupo específico.
   1. Haga clic en **Guardar y cerrar**.

   Del mismo modo, cree otros dos usuarios, como **Región-usuario** y **Tienda-usuario** , y agréguelos a **Región-autor** y **Tienda-autor** respectivamente.

   >[!NOTE]
   >Se recomienda agregar usuarios a un grupo y luego asignar permisos a cada grupo de usuarios en particular.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Añadir todos los grupos a colaboradores**

   1. Vaya a **Adobe Experience Manager**.
   1. Click **Tools** --> **Security** --> **Groups**.
   1. Seleccione **Colaboradores** en la lista y seleccione la ficha **Miembros** .
   1. Seleccione el **grupo** como Autor **global**, Autor **regional,** Autor de **tienda y Autor** de tienda para colaboradores.
   1. Haga clic en **Guardar y cerrar**.

1. **Acceso a permisos para cada grupo**

   1. Vaya a *Useradmin* y utilice esta interfaz de usuario para modificar los permisos de los distintos grupos.
   1. Busque **Global-Author** y haga clic en la ficha **Permisos** , como se muestra en la figura siguiente.
   1. Del mismo modo, puede acceder a los permisos para **Región-Autor** y **Tienda-Autor**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modificación de permisos para cada grupo**

   **Para Global-Author:**

   1. Navigate to the **Permissions** tab
   1. Vaya a ***/content/screen/demo*** y compruebe todos los permisos
   1. Vaya a ***/content/screen/demo/locations*** y compruebe todos los permisos
   1. Vaya a ***/content/screen/demo/locations/region-a*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos para **region-b**.

   Consulte la figura siguiente para comprender los pasos:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   La siguiente imagen muestra que ahora el Usuario **** Global tiene acceso al Canal **** Global y a la **Región A** y a la **Región B** con las cuatro tiendas, a saber, **Store 1**************, Tienda 2, Tienda 3y Tienda 4.

   ![global](assets/global.gif)

   **Para Región-Autor:**

   1. Navigate to the **Permissions** tab.
   1. Vaya a ***/content/screen/demo*** y compruebe únicamente los permisos de **lectura** .
   1. Vaya a ***/content/screen/demo/locations*** y compruebe únicamente los permisos de **lectura** .
   1. Vaya a ***/content/screen/demo/canales*** y desmarque los permisos de canal **global** .
   1. Vaya a ***/content/screen/demo/locations***/***region-a*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos para **region-b**.

   Consulte la figura siguiente para comprender los pasos:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   La siguiente imagen muestra que ahora la Región-Usuario tiene acceso tanto a la **Región A** como a la **Región B** con las cuatro tiendas, a saber, **Tienda 1**, **Tienda 2**, **Tienda 3****** **** y Tienda 4no tiene acceso al CanalGlobal.

   ![región](assets/region.gif)

   **Para Store-Author:**

   1. Navigate to the **Permissions** tab.
   1. Vaya a ***/content/screen/demo*** y compruebe únicamente los permisos de **lectura** .
   1. Vaya a ***/content/screen/demo/locations*** y compruebe únicamente los permisos de **lectura** .
   1. Vaya a ***/content/screen/demo/canales*** y desmarque los permisos de canal **global** .
   1. Vaya a ***/content/screen/demo/locations/region-a*** y compruebe únicamente los permisos de **lectura** . Del mismo modo, compruebe únicamente los permisos de **lectura** para **region-b**.
   1. Vaya a ***/content/screen/demo/locations***/***region-a/store-1*** y compruebe todos los permisos. Del mismo modo, compruebe los permisos para **store-2,** store-3 y **store-4**.

   Consulte la figura siguiente para comprender los pasos:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   La siguiente imagen muestra que ahora el usuario **de la** tienda solo tiene acceso a las cuatro tiendas, a saber, **Tienda 1**, **Tienda 2**, **Tienda 3** y **Tienda 4** ******** ****, pero no tiene permisos para acceder a los canales de la región (Región AGlobal) y de la región (Región B).

   ![store](assets/store.gif)

>[!NOTE]
>
>Para obtener información detallada sobre la configuración de permisos, consulte [Configuración de ACL](setting-up-acls.md).

