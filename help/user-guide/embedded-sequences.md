---
title: Secuencias incrustadas
seo-title: Embedded Sequences
description: Siga esta página para obtener más información sobre las secuencias incrustadas en los canales que permiten al usuario agregar componentes en el canal principal y también para reutilizar el contenido de un canal diferente e incrustarlo en el canal principal.
seo-description: Follow this page to learn about embedded sequences for channels that allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 2%

---

# Secuencias incrustadas {#embedded-sequences}

Uso de ***Secuencias incrustadas***, para los canales, permite al usuario añadir componentes en el canal principal y también reutilizar el contenido de un canal diferente e incrustarlo en el canal principal.

## Adición de secuencias incrustadas {#adding-embedded-sequences}

Tiene la opción de añadir los siguientes componentes al canal de secuencia:

* Secuencia integrada
* Secuencia integrada dinámica

>[!NOTE]
>
>Para obtener más información sobre el uso de otros componentes en el proyecto de Screens, consulte [Adición de componentes a un canal](adding-components-to-a-channel.md).

### Añadir una secuencia incrustada {#adding-an-embedded-sequence}

Puede añadir una secuencia incrustada al canal. Una secuencia incrustada es otro canal que incluye recursos como imágenes o vídeos. Añadir una secuencia incrustada permite al usuario añadir la secuencia a un canal mediante ***Ruta de canal***.

>[!NOTE]
>***Ruta de canal*** define una referencia explícita al canal.
>Para obtener más información acerca de *Ruta de canal*, consulte [Asignación de canales](channel-assignment.md) en Creación en Screens.

Siga los pasos a continuación para añadir una secuencia incrustada al canal:

1. Seleccione el canal en el que desea incrustar una página. Por ejemplo, **We.Retail en tienda** —> **Canales** —> **Canal inactivo**.

1. Clic **Editar** en la barra de acciones para abrir el canal en el modo editor.
1. Haga clic en el icono de componentes de la barra lateral izquierda para añadir la página incrustada. Arrastre y suelte el **Secuencia incrustada** al editor.
1. Haga doble clic en **Secuencia incrustada** para añadir el canal al canal de secuencia original.
1. Seleccione el **Ruta de canal** del canal.
1. Seleccione el **Duración (ms)** para el canal incrustado en **Secuencia** pestaña. De forma predeterminada, la duración está configurada en **-1**, significa que el canal incrustado se ejecuta completamente. Si el usuario especifica una duración, la subsiguiente se interrumpirá (es decir, se cortará) a la hora especificada.

1. Configure las variables **Estrategia de reproducción medida** hasta **normal**.

De forma predeterminada, se establece en **normal**. Estableciendo el valor en **normal** (Reproducir todos los elementos) significa que la subsiguiente se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento** (Reproducir un solo elemento) y que solo mostraría un elemento de la subsecuencia en cada ejecución (por ejemplo, el primer elemento del primer bucle, el segundo elemento del segundo bucle, etc.).

>[!IMPORTANT]
>
>Debe asignar el canal (utilizado en la secuencia incrustada) a la misma visualización.
>
>Siga los pasos a continuación después de agregar una secuencia incrustada al canal desde los pasos anteriores:
>
>1. Vaya a la pantalla y seleccione la pantalla **Ubicaciones** carpeta.
>1. Haga clic en **Tablero** en la barra de acciones para desplazarse al panel de visualización.
>1. Seleccionar **+ Asignar canales** desde el **CANALES ASIGNADOS Y PANELES PROGRAMADOS** para abrir **Cuadro de diálogo Asignación de canales**.
>
>1. Seleccione la ruta del canal en el que (utilizado en la secuencia incrustada) **Ruta de canal**.
>1. Asegúrese de que la variable **Prioridad** es inferior al canal principal.
>
>1. No debe seleccionar ninguna **Eventos admitidos**.
>1. Clic **Guardar** una vez finalizado.

>


En el ejemplo siguiente se muestra la adición de una secuencia incrustada (**Canal inactivo - Noche**) a un canal ya existente (**Canal inactivo**).

![new2](assets/new2.gif)

### Adición de una secuencia incrustada dinámica {#adding-a-dynamic-embedded-sequence}

Puede añadir una secuencia incrustada dinámica al canal. Una secuencia incrustada dinámica es similar a una secuencia incrustada, pero permite al usuario seguir una jerarquía en la que los cambios/actualizaciones realizados en un canal se propagan a otro en relación. Rastrea la jerarquía principal-secundaria e incluye recursos como imágenes o vídeos. Añadir una secuencia dinámica permite al usuario añadir un canal por función de canal.

>[!NOTE]
>
>***Función del canal*** define la función Canal define el contexto de la visualización.
>
>Para obtener más información acerca de *Función del canal*, consulte [Asignación de canales](channel-assignment.md) en Creación en Screens.

Siga los pasos a continuación para añadir una secuencia incrustada al canal:

1. Seleccione el canal en el que desea incrustar una secuencia dinámica. Por ejemplo, **We.Retail en tienda** —> **Canales** —> **Canal inactivo**.

1. Clic **Editar** en la barra de acciones para abrir el canal en el modo editor.
1. Haga clic en el icono de componentes de la barra lateral izquierda para añadir la secuencia incrustada dinámica. Arrastre y suelte el **Dinámico** **Secuencia incrustada**  al editor.

1. Haga doble clic en **Dinámico** **Secuencia incrustada** para añadir la página al canal de secuencia.

1. Introduzca el **Rol de asignación de canal**.
1. Configure las variables **Estrategia de reproducción medida** hasta **normal**. De forma predeterminada, se establece en **normal**. Estableciendo el valor en **normal** (Reproducir todos los elementos) significa que la subsiguiente se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento** (Reproducir un solo elemento) y que solo mostraría un elemento de la subsecuencia en cada ejecución (por ejemplo, el primer elemento del primer bucle, el segundo elemento del segundo bucle, etc.).

1. Seleccione el **Duración (ms)** in **Secuencia** para el canal incrustado en la secuencia.

![última versión](assets/latest.gif)
