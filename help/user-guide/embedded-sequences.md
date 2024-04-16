---
title: Secuencias incrustadas
description: Obtenga información sobre las secuencias incrustadas para canales que le permiten agregar componentes al canal principal y también reutilizar el contenido de un canal diferente e incrustarlo en el canal principal.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

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

1. Haga clic en el canal en el que desee incrustar una página. Por ejemplo, **`We.Retail`En tienda** > **Canales** > **Canal inactivo**.

1. Clic **Editar** de la barra de acciones.
1. En el modo de editor, haga clic en el icono de componentes de la barra lateral izquierda para poder añadir la página incrustada. Arrastre y suelte el **Secuencia incrustada** al editor.
1. Haga doble clic en **Secuencia incrustada** para que pueda añadir el canal al canal de secuencia original.
1. Haga clic en **Ruta de canal** del canal.
1. Haga clic en **Duración (milisegundos)** para el canal incrustado en **Secuencia** pestaña. De forma predeterminada, la duración está configurada en **-1**, significa que el canal incrustado se ejecuta completamente. Si el usuario especifica una duración, la subsiguiente se interrumpe (es decir, se corta) a la hora especificada.

1. Configure las variables **Estrategia de reproducción medida** hasta **normal**.

De forma predeterminada, se establece en **normal**. Estableciendo el valor en **normal** (Reproducir todos los elementos) significa que la subsiguiente se ejecuta completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento**. Ese valor solo muestra un elemento de la subsiguiente en cada ejecución. Por ejemplo, el primer elemento del primer bucle y el segundo elemento del segundo bucle.

>[!IMPORTANT]
>
>Asigne el canal que se utiliza en la secuencia incrustada a la misma visualización.
>
>Siga los pasos a continuación después de agregar una secuencia incrustada al canal desde los pasos anteriores:
>
>1. Navegue hasta la pantalla y haga clic en la pantalla desde **Ubicaciones** carpeta.
>1. Clic **Tablero** de la barra de acciones.
>1. En el panel de visualización, haga clic en **+ Asignar canales** desde el **CANALES ASIGNADOS Y PANELES PROGRAMADOS** para poder abrir **Cuadro de diálogo Asignación de canales**.
>
>1. Haga clic en la ruta del canal en el que está (utilizado en la secuencia incrustada) **Ruta de canal**.
>1. Asegúrese de que la variable **Prioridad** es inferior al canal principal.
>
>1. No haga clic en ninguna **Eventos admitidos**.
>1. Clic **Guardar** cuando termine.
>

En el ejemplo siguiente se muestra la adición de una secuencia incrustada (**Canal inactivo - Noche**) a un canal existente (**Canal inactivo**).

![new2](assets/new2.gif)

### Adición de una secuencia incrustada dinámica {#adding-a-dynamic-embedded-sequence}

Puede añadir una secuencia incrustada dinámica al canal. Una secuencia incrustada dinámica es similar a una secuencia incrustada, pero permite al usuario seguir una jerarquía en la que los cambios/actualizaciones realizados en un canal se propagan a otro en relación. Sigue la jerarquía principal-secundario y también incluye recursos como imágenes o vídeos. Añadir una secuencia dinámica permite al usuario añadir un canal por función de canal.

>[!NOTE]
>
>***Función del canal*** define la función Canal define el contexto de la visualización.
>
>Para obtener más información acerca de *Función del canal*, consulte [Asignación de canales](channel-assignment.md) en Creación en Screens.

Siga los pasos a continuación para añadir una secuencia incrustada al canal:

1. Haga clic en el canal en el que desee incrustar una secuencia dinámica. Por ejemplo, **`We.Retail`En tienda** > **Canales** > **Canal inactivo**.

1. Clic **Editar** de la barra de acciones.
1. En el modo de editor, haga clic en el icono de componentes de la barra lateral izquierda para añadir la secuencia incrustada dinámica. Arrastre y suelte el **Dinámico** **Secuencia incrustada** al editor.

1. Haga doble clic en **Dinámico** **Secuencia incrustada** para poder añadir la página al canal de secuencia.

1. Introduzca el **Rol de asignación de canal**.
1. Configure las variables **Estrategia de reproducción medida** hasta **normal**. De forma predeterminada, se establece en **normal**. Estableciendo el valor en **normal** (Reproducir todos los elementos) significa que la subsiguiente se ejecuta completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento**. Ese valor solo muestra un elemento de la subsiguiente en cada ejecución. Por ejemplo, el primer elemento del primer bucle y el segundo elemento del segundo bucle.

1. Haga clic en **Duración (milisegundos)** in **Secuencia** para el canal incrustado en la secuencia.

![última versión](assets/latest.gif)
