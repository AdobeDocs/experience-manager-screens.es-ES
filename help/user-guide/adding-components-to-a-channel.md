---
title: Añadir componentes a un canal
seo-title: Añadir componentes a un canal
description: Siga esta página para obtener más información sobre cómo añadir componentes a los canales en un proyecto de AEM Screens.
seo-description: Siga esta página para obtener más información sobre cómo añadir componentes a los canales en un proyecto de AEM Screens.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: cec2a2f8b056bf713e56a9fab08d88e29263820b

---


# Añadir componentes a un canal{#adding-components-to-a-channel}

Los componentes son elementos fundamentales de la experiencia AEM (Adobe Experience Manager). Puede utilizar varios componentes y añadirlos al canal de un proyecto de AEM Screens.

## Componentes en AEM Screens {#components-in-aem-screens}

AEM Screens proporciona distintos componentes de AEM que se pueden utilizar en un proyecto de Screens.

### Visualizar componentes de AEM Screens {#viewing-aem-screens-components}

Cuando cree un proyecto de AEM Screens, verá una lista de componentes predeterminados que se pueden añadir al proyecto.

Para ver los componentes predeterminados del proyecto de Screens, siga los pasos que se describen a continuación:

1. Seleccione el canal. Por ejemplo,**We.Retail In Store** --&gt; **Canales** --&gt; **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones para abrir el editor de AEM.
1. Haga clic en el icono **+** en la barra lateral para abrir los componentes.
1. Todos los componentes que se incluyen de forma predeterminada en un proyecto de AEM Screens se visualizan tal y como se muestra en la figura siguiente.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Añadir un nuevo componente {#adding-a-new-component}

AEM proporciona otros componentes. También puede añadir otros componentes (no incluidos de forma predeterminada) al proyecto, dado que son compatibles con AEM Screens.

En el siguiente ejemplo se muestra la forma de añadir el componente Livefyre a un proyecto de AEM Screens:

1. Seleccione el canal en el que desee añadir un componente nuevo. Por ejemplo,**We.Retail In Store** --&gt; **Canales** --&gt; **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones para abrir el editor.
1. Seleccione el modo **Diseño**.
1. Seleccione todo el editor de diseño que está a la derecha y haga clic en el símbolo de configuración para abrir el cuadro de diálogo **Diseño de ParSys**.
1. Puede seleccionar los componentes que desee importar al proyecto AEM Screens. El siguiente ejemplo muestra la adición del componente **Livefyre** a un proyecto de AEM Screens.

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>Del mismo modo, se puede añadir al proyecto cualquier nuevo componente que sea compatible con AEM Screens.

## Información acerca de los componentes AEM Screens {#understanding-aem-screen-components}

En la siguiente sección se explican los componentes de AEM Screens que puede utilizar en el proyecto.

>[!NOTE]
>
>Para ver las propiedades de los componentes, seleccione un componente y haga clic en el icono con forma de martillo para abrir o ver las propiedades.

### Aplicación {#application}

El componente **Aplicación** le permite añadir una aplicación al canal.

El componente de la aplicación tiene las siguientes propiedades:

| **Propiedad** | **Descripción** |
|---|---|
| ***Ruta de acceso de la aplicación*** | Seleccione la ruta de acceso absoluta donde está la aplicación. |
| ***Duración (ms)*** | Seleccione la duración de la aplicación. De forma predeterminada, la duración se establece en -1, lo que significa que el elemento se ejecuta para siempre (es decir, una aplicación de una sola página). Si establece el valor de la duración como &gt;0, se mostrará el elemento de una duración específica y, a continuación, pasará al siguiente. |

En el siguiente ejemplo se muestra cómo integrar un componente de aplicación con la vista previa de sus propiedades.

![adding_components_application](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Consulte el ejemplo anterior para ver las propiedades de cada uno de los componentes que se describen a continuación.

### Canal {#channel}

El componente **Canal** le permite añadir todo un canal al proyecto.

El componente Canal tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong><em>Ruta de acceso del canal</em></strong></td>
   <td>Seleccione esta ruta de acceso absoluta donde existe la aplicación.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (ms)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado ejecutará toda su longitud en un canal determinado.</td>
  </tr>
 </tbody>
</table>

### Página integrada {#embedded-page}

La opción **Página integrada** le permite añadir una página integrada al proyecto. Por ejemplo, puede ser una aplicación web o un catálogo de productos.

La página integrada tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong><em>Ruta de acceso de página<br /> </em></strong></td>
   <td>Seleccione esta ruta de acceso absoluta que existe el canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (ms)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado ejecutará toda su longitud en un canal determinado.</td>
  </tr>
 </tbody>
</table>

### Secuencia integrada {#embedded-sequence}

>[!NOTE]
>
>Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

Una secuencia integrada le permite añadir un canal de secuencia integrada en el canal existente (con otros recursos).

La secuencia integrada tiene las propiedades de página siguientes:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td>Ruta de acceso del canal</td>
   <td>Seleccione la ruta de acceso absoluta de la secuencia que desee incluir en el canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (ms)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado ejecutará toda su longitud en un canal determinado.</td>
  </tr>
  <tr>
   <td><strong><em>Estrategia</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### Secuencia integrada dinámica {#dynamic-embedded-sequence}

Una secuencia integrada de forma dinámica permite añadir una secuencia similar al que se mencionó anteriormente, excepto en el rol del canal.

Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

La secuencia integrada dinámica tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong><em>Rol de asignación de canales</em></strong><br /> </td>
   <td>Especifique el rol del canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (ms)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado ejecutará toda su longitud en un canal determinado.</td>
  </tr>
  <tr>
   <td><strong><em>Estrategia</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### Fragmento de experiencias {#experience-fragment}

Un fragmento de experiencia permite añadir un fragmento de experiencia (grupo de uno o varios componentes, incluido el contenido y el diseño al que se puede hacer referencia en las páginas) al canal de pantallas de AEM. Arrastre y suelte el componente en el editor de AEM y seleccione el fragmento de experiencia.

Para obtener más información sobre cómo crear un fragmento de experiencia y utilizarlo en un proyecto de AEM Screens, consulte [Uso de fragmentos](experience-fragments-in-screens.md)de experiencia.

![exp](assets/exp.gif)

| **Propiedad** | **Descripción** |
|---|---|
| **Fragmento de experiencias** |
| ***Fragmento de experiencias*** | Seleccione el fragmento de experiencia. |
| ***Duración*** | Seleccione la duración completa del fragmento de experiencia que se reproduce en el canal. |
| **Configuración sin conexión** |
| ***Bibliotecas del lado cliente*** | Archivos Javascript y CSS. |
| ***Archivos estáticos*** | Archivos estáticos que se pueden agregar como configuraciones sin conexión al fragmento de experiencia. |

>[!NOTE]
>
>Las bibliotecas **del lado del** cliente y los archivos **** estáticos que agregue de este componente se sumarán a las bibliotecas **del lado del** cliente ya configuradas y a los archivos estáticos que se agregan desde las **propiedades** del fragmento de experiencia.

### Imagen {#image}

Una imagen permite añadir una imagen al canal.

El recurso de imagen tiene tres fichas denominadas **Imagen**, **Accesibilidad** y **Secuencia**:

| **Propiedad** | **Descripción** |
|---|---|
| **Imagen** |
| ***Recurso de imagen*** | Seleccione el recurso de imagen. |
| ***Título*** | Título de la imagen. |
| ***Vínculos*** | Añada un vínculo a la imagen. |
| ***Descripción*** | Descripción breve de la imagen. |
| ***Tamaño*** | Tamaño de la imagen. |
| **Accesibilidad** |
| ***Texto alternativo*** | Texto alternativo a la imagen. |
| **Secuencia** |
| ***Duración*** | De forma predeterminada, la duración se establece en *8000 ms*. Si desea cambiar la duración de reproducción de la imagen, actualice el campo **Duración** . |

### Transición {#transition}

El componente Transición permite añadir una transición al proyecto de Screens.

La siguiente imagen muestra el componente de transición (agregado mediante arrastrar y soltar) en el editor.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Seleccione el icono de transición y haga clic en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo **Transición** . Este cuadro de diálogo incluye tres fichas:

* **Transición**
* **Secuencia**
* **Activación**

>[!NOTE]
>
>De forma predeterminada, la secuencia se establece en 600 ms. Puede actualizar la secuencia de transición a otro valor mediante la ficha **Secuencia** .

![transición](assets/transition.gif)

El componente Transición tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong>Transición</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Tipo</em></strong></td>
   <td><p>El tipo de transición entre el elemento anterior y el siguiente. El <strong>tipo</strong> de transición incluye las siguientes opciones:</p>
    <ul>
     <li><strong>Normal</strong></li>
     <li><strong>Atenuación</strong></li>
     <li><strong>Aparecer por la derecha</strong></li>
     <li><strong>Aparecer por la izquierda</strong></li>
     <li><strong>Aparecer por la parte superior</strong></li>
     <li><strong>Aparecer por la parte inferior</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Secuencia</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Duración</em></strong></td>
   <td>Seleccione toda la duración de la transición. De forma predeterminada, se establece en 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Activación</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Activo desde</em></strong></td>
   <td>Marca de hora que describe desde cuándo puede estar activa la transición.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Activo hasta</em></strong></td>
   <td>Marca de hora que describe hasta cuándo puede estar activa la transición.</td>
  </tr>
  <tr>
   <td><strong><em>Programa</em></strong></td>
   <td>Agregue una programación predefinida.</td>
  </tr>
 </tbody>
</table>

### Vídeo {#video}

El componente Vídeo le permite añadir un vídeo al proyecto de Screens.

El componente Vídeo tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><em><strong>Recurso de vídeo</strong></em></td>
   <td>Seleccione el vínculo al vídeo.</td>
  </tr>
  <tr>
   <td><em><strong>Duración</strong></em></td>
   <td>Seleccione la duración del vídeo. De forma predeterminada, la duración se establece en -1, lo que significa que el elemento se ejecuta para siempre. Si establece el valor de la duración como &gt;0, se mostrará el elemento de una duración específica y, a continuación, pasará al siguiente.<br />  </td>
  </tr>
  <tr>
   <td><em><strong>Procesamiento</strong></em></td>
   <td><p>Si la proporción de aspecto del vídeo no se adapta a la pantalla, puede ajustar el procesamiento a <strong>contiene</strong> o<strong> cubierta</strong>.</p> <p><em>Contiene</em> significa que el vídeo completo se muestra y las áreas que faltan indicadas con un borde negro.</p> <p><em>Cubierta</em> significa que el vídeo cubre la ventana completa, pero si alguna parte superan el espacio permitido en los lados estará oculta.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Tamaño</strong></em></td>
   <td>Tamaño del vídeo.</td>
  </tr>
 </tbody>
</table>

