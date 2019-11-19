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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Secuencias integradas {#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

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
>
>***Ruta de canal ***define una referencia explícita al canal.
>
>Para obtener más información sobre la *Ruta de acceso del canal*, consulte [Asignación de canales](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una página. For example, **We.Retail In-Store** --&gt; **Channels** --&gt;** Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la página integrada. Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Seleccione la **ruta de acceso al canal** del canal.
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. Si el usuario especifica una duración, se interrumpe la secuencia secundaria (es decir, se limita) en el tiempo especificado.

1. Establezca la estrategia **de reproducción** con contador en **normal**.

By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

>[!NOTE]
>
>**Importante:**
>
>Debe asignar el canal (utilizado en la secuencia incrustada) a la misma pantalla.
>
>Siga los pasos que se describen a continuación después de haber agregado una secuencia incrustada al canal desde los pasos anteriores:
>
>1. Vaya a la pantalla y seleccione la visualización en la carpeta **Ubicaciones** .
>1. Haga clic en **Tablero** en la barra de acciones para navegar hasta el tablero de visualización.
>1. Seleccione **+ Asignar canales** en los PANELES **CANALES** ASIGNADOS Y PROGRAMADOS para abrir el cuadro **de diálogo Asignación de** canal.
   >
   >
1. Seleccione la ruta del canal que utiliza (en secuencia incrustada) en Ruta **** del canal.
>1. Asegúrese de que la **prioridad** es menor que el canal principal.
   >
   >
1. No debe seleccionar ningún evento **** admitido.
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

1. Seleccione el canal en el que desee insertar una secuencia dinámica. For example, **We.Retail In-Store** --&gt; **Channels** --&gt; **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la secuencia integrada dinámica. Arrastre y **suelte la secuencia dinámica** **integrada **al editor.

1. Double-click the **Dynamic** **Embedded Sequence **component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. Establezca la estrategia **de reproducción** con contador en **normal**. By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![más reciente](assets/latest.gif)

