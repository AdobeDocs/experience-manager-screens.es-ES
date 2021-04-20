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
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 43%

---


# Secuencias integradas {#embedded-sequences}

El uso de ***Secuencias integradas***, para los canales, permite al usuario añadir componentes en el canal principal y reutilizar el contenido de un canal diferente e incrustarlo en el canal principal.

## Añadir secuencias integradas {#adding-embedded-sequences}

Tiene la opción de añadir los siguientes componentes al canal de secuencia:

* Secuencia integrada
* Secuencia integrada dinámica

>[!NOTE]
>
>Para obtener más información sobre el uso de otros componentes en el proyecto de Screens, consulte [Añadir componentes a un canal](adding-components-to-a-channel.md).

### Añadir una secuencia integrada {#adding-an-embedded-sequence}

Puede añadir una secuencia integrada al canal. Una secuencia integrada es otro canal que incluye recursos como imágenes o vídeos. Al añadir una secuencia integrada, el usuario puede añadir la secuencia a un canal según la ***ruta de acceso del canal***.

>[!NOTE]
>***La ruta de acceso del canal*** define una referencia explícita al canal.
>Para obtener más información sobre la *Ruta de acceso del canal*, consulte [Asignación de canales](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una página. Por ejemplo, **We.Retail In-Store** —> **Canales** —> **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones para abrir el canal en el modo de editor.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la página integrada. Arrastre y suelte la **Secuencia integrada** en el editor.
1. Haga doble clic en el componente **Secuencia integrada** para añadir el canal al canal de secuencia original.
1. Seleccione la **ruta de acceso al canal** del canal.
1. Seleccione **Duration (ms)** para el canal incrustado en la pestaña **Sequence**. De forma predeterminada, la duración está configurada en **-1**, lo que significa que el canal incrustado se ejecuta completamente. Si el usuario especifica una duración, se interrumpe la secuencia secundaria (es decir, se limita) en el tiempo especificado.

1. Establezca la **Estrategia de reproducción medida** en **normal**.

De forma predeterminada, se establece en **normal**. Si establece el valor en **normal** (Reproducir todos los elementos), la secuencia secundaria se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento** (Reproducir un solo elemento) y que solo mostrará un elemento de la secuencia secundaria en cada ejecución (por ejemplo, el primer elemento del primer bucle, el segundo elemento del segundo bucle, etc.).

>[!IMPORTANT]
>
>Se debe asignar el canal (utilizado en la secuencia integrada) a la misma pantalla.
>
>Siga los pasos que se indican a continuación después de agregar una secuencia integrada al canal desde los pasos anteriores:
>
>1. Vaya a la visualización y seleccione la visualización de la carpeta **Locations** .
>1. Haga clic en **Dashboard** en la barra de acciones para ir al tablero de visualización.
>1. Seleccione **+ Asignar canales** en los **CANALES ASIGNADOS y PANELES PROGRAMADOS** para abrir el cuadro de diálogo **Asignación de canales**.

   >
   >
1. Seleccione la ruta del canal que utiliza (en la secuencia integrada) en **Ruta del canal**.
>1. Asegúrese de que **Priority** es menor que el canal principal.

   >
   >
1. No debe seleccionar ningún **Eventos admitidos**.
>1. Haga clic en **Guardar** una vez finalizado.

>



En el siguiente ejemplo se muestra la forma de añadir una secuencia integrada (**Canal inactivo - noche**) a un canal ya existente (**Canal inactivo**).

![new2](assets/new2.gif)

### Añadir una secuencia integrada dinámica {#adding-a-dynamic-embedded-sequence}

Puede añadir una secuencia integrada dinámica al canal. Una secuencia integrada de forma dinámica es similar a una secuencia integrada, pero permite que el usuario siga una jerarquía en la cual los cambios o actualizaciones que se hicieron en el canal se propagan a otro canal relacionado. Rastrea la jerarquía principal-secundaria e incluye recursos como imágenes o vídeos. Al añadir secuencia dinámica, el usuario puede añadir un canal según el rol de canal.

>[!NOTE]
>
>***Rol del canal*** define el rol del canal que define a su vez el contexto de la visualización.
>
>Para obtener más información acerca de los *Roles de canales*, consulte [Asignación de canales](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una secuencia dinámica. Por ejemplo, **We.Retail In-Store** —> **Canales** —> **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones para abrir el canal en el modo de editor.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la secuencia integrada dinámica. Arrastre y suelte el **Dynamic** **Embedded Sequence** en el editor.

1. Haga doble clic en el componente **Dynamic** **Embedded Sequence** para añadir la página al canal de secuencia.

1. Introduzca la **Función de asignación de canales**.
1. Establezca la **Estrategia de reproducción medida** en **normal**. De forma predeterminada, se establece en **normal**. Si establece el valor en **normal** (Reproducir todos los elementos), la secuencia secundaria se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento** (Reproducir un solo elemento) y que solo mostrará un elemento de la secuencia secundaria en cada ejecución (por ejemplo, el primer elemento del primer bucle, el segundo elemento del segundo bucle, etc.).

1. Seleccione **Duration (ms)** en la pestaña **Sequence** para el canal incrustado en la secuencia.

![última versión](assets/latest.gif)

