---
title: Secuencias integradas
seo-title: Secuencias integradas
description: Siga esta página para obtener más información sobre las secuencias integradas de canales que permiten al usuario añadir componentes en el canal principal y reutilizar el contenido de otro canal e integrarlo en el canal principal.
seo-description: Siga esta página para obtener más información sobre las secuencias integradas de canales que permiten al usuario añadir componentes en el canal principal y reutilizar el contenido de otro canal e integrarlo en el canal principal.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 42%

---


# Secuencias integradas {#embedded-sequences}

El uso de ***Secuencias incrustadas***, para canales, permite al usuario agregar componentes en el canal principal y también volver a utilizar el contenido de un canal diferente e incrustarlo en el canal principal.

## Añadir secuencias integradas {#adding-embedded-sequences}

Tiene la opción de agregar los siguientes componentes al canal de secuencia:

* Secuencia integrada
* Secuencia integrada dinámica

>[!NOTE]
>
>Para obtener más información sobre el uso de otros componentes en el proyecto de Screens, consulte [Añadir componentes a un canal](adding-components-to-a-channel.md).

### Añadir una secuencia integrada {#adding-an-embedded-sequence}

Puede añadir una secuencia integrada al canal. Una secuencia incrustada es otro canal que incluye recursos como imágenes o vídeos. Al añadir una secuencia integrada, el usuario puede añadir la secuencia a un canal según la ***ruta de acceso del canal***.

>[!NOTE]
>***Ruta de canal*** define una referencia explícita al canal.
>Para obtener más información sobre la *Ruta de acceso del canal*, consulte [Asignación de canales](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una página. Por ejemplo, **Almacenamiento en tiendas We.Retail** —> **Canales** —> **Canal en reposo**.

1. Haga clic en **Editar** en la barra de acciones para abrir el canal en el modo de editor.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la página integrada. Arrastre y suelte la **Secuencia integrada** en el editor.
1. Haga clic con el botón doble en el componente **Secuencia integrada** para agregar el canal al canal de secuencia original.
1. Seleccione la **ruta de acceso al canal** del canal.
1. Seleccione la **Duración (ms)** para el canal incrustado en la ficha **Secuencia**. De forma predeterminada, la duración se establece en **-1**, lo que significa que el canal incrustado se ejecuta completamente. Si el usuario especifica una duración, se interrumpe la secuencia secundaria (es decir, se limita) en el tiempo especificado.

1. Establezca la **Estrategia de reproducción con contador** en **normal**.

De forma predeterminada, se establece en **normal**. Definir el valor en **normal** (Reproducir todos los elementos) significa que la subsecuencia se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento** (Reproducir un solo elemento) y eso sólo mostrará un elemento de la subsiguiente en cada ejecución (por ejemplo, el primer elemento del primer bucle, el segundo elemento del segundo bucle, etc.).

>[!IMPORTANT]
>
>Debe asignar el canal (utilizado en la secuencia incrustada) a la misma pantalla.
>
>Siga los pasos que se describen a continuación después de haber agregado una secuencia incrustada al canal desde los pasos anteriores:
>
>1. Vaya a la pantalla y seleccione la opción de visualización en la carpeta **Ubicaciones**.
>1. Haga clic en **Panel** en la barra de acciones para navegar hasta el panel de visualización.
>1. Seleccione **+ Asignar Canales** en los **PANELES PROGRAMADOS Y CANALES ASIGNADOS** para abrir el cuadro de diálogo **Asignación de Canales**.

   >
   >
1. Seleccione la ruta del canal que utiliza (en secuencia incrustada) en **Ruta de Canal**.
>1. Asegúrese de que **Priority** es menor que el canal principal.

   >
   >
1. No debe seleccionar ningún **Evento admitido**.
>1. Haga clic en **Guardar** una vez finalizado.

>



En el siguiente ejemplo se muestra la forma de añadir una secuencia integrada (**Canal inactivo - noche**) a un canal ya existente (**Canal inactivo**).

![new2](assets/new2.gif)

### Añadir una secuencia integrada dinámica {#adding-a-dynamic-embedded-sequence}

Puede añadir una secuencia integrada dinámica al canal. Una secuencia integrada de forma dinámica es similar a una secuencia integrada, pero permite que el usuario siga una jerarquía en la cual los cambios o actualizaciones que se hicieron en el canal se propagan a otro canal relacionado. Sigue la jerarquía principal-secundario e incluye también recursos como imágenes o vídeos. Al añadir secuencia dinámica, el usuario puede añadir un canal según el rol de canal.

>[!NOTE]
>
>***Rol del canal*** define el rol del canal que define a su vez el contexto de la visualización.
>
>Para obtener más información acerca de los *Roles de canales*, consulte [Asignación de canales](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una secuencia dinámica. Por ejemplo, **Almacenamiento en tiendas We.Retail** —> **Canales** —> **Canal en reposo**.

1. Haga clic en **Editar** en la barra de acciones para abrir el canal en el modo de editor.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la secuencia integrada dinámica. Arrastre y suelte la **secuencia integrada** **dinámica** en el editor.

1. Haga clic con el doble en el componente **Dynamic** **Embedded Sequence** para agregar la página al canal de secuencia.

1. Introduzca la **Función de asignación de Canal**.
1. Establezca la **Estrategia de reproducción con contador** en **normal**. De forma predeterminada, se establece en **normal**. Definir el valor en **normal** (Reproducir todos los elementos) significa que la subsecuencia se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento** (Reproducir un solo elemento) y eso sólo mostrará un elemento de la subsiguiente en cada ejecución (por ejemplo, el primer elemento del primer bucle, el segundo elemento del segundo bucle, etc.).

1. Seleccione la ficha **Duración (ms)** en **Secuencia** para el canal incrustado en la secuencia.

![más reciente](assets/latest.gif)

