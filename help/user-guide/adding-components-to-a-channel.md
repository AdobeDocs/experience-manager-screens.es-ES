---
title: Adición de componentes a un canal
description: Obtenga más información sobre cómo añadir componentes a canales en un proyecto de AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 5%

---

# Adición de componentes a un canal{#adding-components-to-a-channel}

Los componentes son los elementos fundamentales de la experiencia de AEM (Adobe Experience Manager). Puede utilizar varios componentes y añadirlos al canal en un proyecto de AEM Screens.

## Componentes en AEM Screens {#components-in-aem-screens}

AEM Screens proporciona diferentes componentes de AEM que se pueden utilizar en un proyecto de Screens.

### Visualización de componentes de AEM Screens {#viewing-aem-screens-components}

Siempre que cree un proyecto de AEM Screens, verá una lista de componentes predeterminados que se pueden agregar al proyecto.

Para ver los componentes predeterminados del proyecto de Screens, siga los pasos a continuación:

1. Haga clic en el canal. Por ejemplo, **`We.Retail In Store`** > **Canales** > **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones.
1. En el Editor de AEM, haga clic en el icono **+** de la barra lateral.
1. Se muestran todos los componentes que se incluyen de forma predeterminada en un proyecto de AEM Screens, como se muestra en la figura siguiente.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Agregar un nuevo componente {#adding-a-new-component}

AEM proporciona otros componentes. Siempre puede agregar otros componentes (no incluidos de forma predeterminada) al proyecto, dado que esos componentes son compatibles con AEM Screens.

El siguiente ejemplo muestra la adición de un componente Livefyre a un proyecto de AEM Screens:

1. Haga clic en el canal en el que desee añadir un componente. Por ejemplo, **`We.Retail In Store`** > **Canales** > **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones.
1. Haga clic en el modo **Diseño**.
1. Haga clic en todo el editor de diseño de la derecha y haga clic en el símbolo de configuración para poder abrir el cuadro de diálogo **Diseño Parsys**.
1. Puede hacer clic en los componentes que desea importar al proyecto de AEM Screens. El siguiente ejemplo muestra la adición del componente **Livefyre** a un proyecto de AEM Screens.

![agregar_componentes](assets/adding_components.gif)

>[!NOTE]
>
>Del mismo modo, puede agregar al proyecto cualquier otro número de componentes nuevos que sean compatibles con AEM Screens.

## Explicación de los componentes de pantalla de AEM {#understanding-aem-screen-components}

En la siguiente sección se explican los componentes de AEM Screens que puede utilizar en el proyecto.

>[!NOTE]
>
>Para ver las propiedades de cualquier componente, haga clic en el componente y haga clic en el icono de martillo para abrir o ver las propiedades.

### Aplicación {#application}

El componente **Aplicación** le permite agregar una aplicación a su canal.

El componente de la aplicación tiene las siguientes propiedades:

| **Propiedad** | **Descripción** |
|---|---|
| ***Ruta de la aplicación*** | Haga clic en la ruta absoluta donde existe la aplicación. |
| ***Duración (milisegundos)*** | Haga clic en la duración de la aplicación. De forma predeterminada, la duración se establece en -1, lo que significa que el elemento se ejecuta para siempre (es decir, una aplicación de una sola página). Al establecer el valor de duración >0, se muestra el elemento para la duración especificada y, a continuación, se pasa al siguiente. |

El siguiente ejemplo muestra cómo incrustar un componente de aplicación junto con la vista previa de sus propiedades:

![agregando_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Consulte el ejemplo anterior para ver las propiedades de cada uno de los componentes siguientes.

### Canal {#channel}

El componente **Canal** le permite agregar un canal completo a su proyecto.

El componente Canal tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong><em>Ruta de canal</em></strong></td>
   <td>Seleccione esta ruta de acceso absoluta donde existe la aplicación.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (milisegundos)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado se ejecuta a toda su longitud en un canal concreto.</td>
  </tr>
 </tbody>
</table>

### Página integrada {#embedded-page}

Una **página incrustada** le permite agregar una página incrustada al proyecto. Por ejemplo, puede ser una aplicación web o un catálogo de productos.

La página incrustada tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong><em>Ruta de página<br /> </em></strong></td>
   <td>Seleccione esta ruta de acceso absoluta donde existe el canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (milisegundos)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado se ejecuta a toda su longitud en un canal concreto.</td>
  </tr>
 </tbody>
</table>

### Secuencia integrada {#embedded-sequence}

>[!NOTE]
>
>Para obtener información detallada sobre las secuencias incrustadas, consulte [Secuencias incrustadas](embedded-sequences.md) en la sección Creación de Screens.

Una secuencia incrustada le permite agregar un canal de secuencia incrustada dentro del canal existente (con otros recursos).

La secuencia incrustada tiene las siguientes propiedades de página:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td>Ruta de canal</td>
   <td>Seleccione la ruta absoluta de la secuencia que desea incluir en el canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (milisegundos)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado se ejecuta a toda su longitud en un canal concreto.</td>
  </tr>
  <tr>
   <td><strong><em>Estrategia</em></strong></td>
   <td>Configúrelo en <strong>original</strong> o <strong>único</strong>. Si establece el valor en <strong>original</strong>, la subsiguiente secuencia se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es <strong>single</strong>. Este valor solo muestra un elemento de la subsiguiente en cada ejecución. Por ejemplo, el primer elemento del primer bucle y el segundo elemento del segundo bucle.</td>
  </tr>
 </tbody>
</table>

### Secuencia integrada dinámica {#dynamic-embedded-sequence}

Una secuencia incrustada dinámica le permite agregar una secuencia similar a la mencionada anteriormente, excepto por función de canal.

Para obtener más información sobre las secuencias incrustadas, consulte [Secuencias incrustadas](embedded-sequences.md) en la sección Creación de Screens.

La secuencia incrustada dinámica tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong><em>Rol de asignación de canal</em></strong><br /> </td>
   <td>Escriba el rol de canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duración (milisegundos)</em></strong></td>
   <td>Seleccione toda la duración del canal. Si establece la duración como -1, indica que el canal incrustado se ejecuta a toda su longitud en un canal concreto.</td>
  </tr>
  <tr>
   <td><strong><em>Estrategia</em></strong></td>
   <td>Configúrelo en <strong>original</strong> o <strong>único</strong>. Si establece el valor en <strong>original</strong>, la subsiguiente secuencia se ejecutará completamente en cada ciclo de la secuencia principal. El otro valor posible es <strong>single</strong>. Este valor solo mostraría un elemento de la subsiguiente en cada ejecución. Por ejemplo, el primer elemento del primer bucle y el segundo elemento del segundo bucle.</td>
  </tr>
 </tbody>
</table>

### Fragmento de experiencias {#experience-fragment}

Un fragmento de experiencia le permite añadir un fragmento de experiencia (un grupo de uno o más componentes, incluido contenido y diseño, al que se puede hacer referencia dentro de las páginas) al canal de AEM Screens. Arrastre y suelte el componente en el Editor de AEM y haga clic en el Fragmento de experiencia.

Para obtener más información sobre cómo crear un fragmento de experiencia y aplicarlo a un proyecto de AEM Screens, consulte [Uso de fragmentos de experiencias](experience-fragments-in-screens.md).

![exp](assets/exp.gif)

| **Propiedad** | **Descripción** |
|---|---|
| **Fragmento de experiencias** |
| ***Fragmento de experiencias*** | Seleccione el Fragmento de experiencia. |
| ***Duración*** | Seleccione toda la duración del fragmento de experiencia que se reproduce en el canal. |
| **Configuración sin conexión** |
| ***Bibliotecas de cliente*** | Archivos JavaScript y CSS. |
| ***Archivos estáticos*** | Archivos estáticos que se pueden agregar como configuraciones sin conexión al Fragmento de experiencia. |

>[!NOTE]
>
>Las **bibliotecas del lado cliente** y los **archivos estáticos** que agrega desde este componente se suman a las **bibliotecas del lado cliente** ya configuradas y a los archivos estáticos que se agregan desde las **propiedades** del fragmento de experiencia.

### Imagen {#image}

Una imagen permite añadir una imagen al canal.

El recurso de imagen tiene tres fichas, a saber **Imagen**, **Accesibilidad** y **Secuencia**:

| **Propiedad** | **Descripción** |
|---|---|
| **Imagen** |
| ***Recurso de imagen*** | Haga clic en el recurso de imagen. |
| ***Título*** | Título de la imagen. |
| ***Vincular A*** | Añada un vínculo a la imagen. |
| ***Descripción*** | Descripción breve de la imagen. |
| ***Tamaño*** | Tamaño de la imagen. |
| **Accesibilidad** |
| ***Texto alternativo*** | Texto alternativo a la imagen. |
| **Secuencia** |
| ***Duración*** | De manera predeterminada, la duración está establecida en *8000 milisegundos*. Si desea cambiar la duración de reproducción de la imagen, actualice el campo **Duration**. |

### Transición {#transition}

El componente Transición permite añadir una transición al proyecto de Screens.

La siguiente imagen muestra el componente de transición (añadido mediante la función de arrastrar y soltar) en el editor.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Haga clic en el icono de transición y luego en **Configurar** (icono de llave inglesa) para abrir el cuadro de diálogo **Transición**. Este cuadro de diálogo incluye tres fichas:

* **Transición**
* **Secuencia**
* **Activación**

>[!NOTE]
>
>De forma predeterminada, la secuencia se establece en 600 milisegundos. Puede actualizar la secuencia de transición a otros valores mediante la ficha **Secuencia**.

![transición](assets/transition.gif)

El componente de transición tiene las siguientes propiedades:

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
   <td><p>Tipo de transición entre el elemento anterior y el elemento posterior. La transición <strong>Type</strong> incluye las siguientes opciones:</p>
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
   <td>Seleccione toda la duración de la transición. De forma predeterminada, se establece en 600 milisegundos.</td>
  </tr>
  <tr>
   <td><strong>Activación</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Activo desde</em></strong></td>
   <td>Marca de tiempo que describe cuándo puede estar activa la transición.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Activo hasta</em></strong></td>
   <td>La marca de tiempo describe hasta cuándo puede estar activa la transición.</td>
  </tr>
  <tr>
   <td><strong><em>Programación</em></strong></td>
   <td>Añada una programación predefinida.</td>
  </tr>
 </tbody>
</table>

### Vídeo {#video}

El componente Vídeo permite agregar un vídeo al proyecto de Screens.

El componente de vídeo tiene las siguientes propiedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><em><strong>Recurso de vídeo</strong></em></td>
   <td>Haga clic en el vínculo del vídeo.</td>
  </tr>
  <tr>
   <td><em><strong>Duración</strong></em></td>
   <td>Seleccione la duración del vídeo. De forma predeterminada, la duración se establece en -1, lo que significa que el elemento se ejecuta para siempre. Al establecer el valor de duración &gt;0, se muestra el elemento para la duración especificada y, a continuación, se pasa al siguiente.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Procesamiento</strong></em></td>
   <td><p>Si la proporción de aspecto del vídeo no se ajusta a la pantalla, puede ajustar la representación a <strong>contain</strong> o <strong>cover</strong>.</p> <p><em>Contain</em> significa que se muestra el vídeo completo y que las áreas que faltan se rellenan con un borde negro.</p> <p><em>Portada</em> significa que el vídeo cubre toda la ventanilla móvil, pero algunas partes que se desbordan en los lados están ocultas.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Tamaño</strong></em></td>
   <td>Tamaño del vídeo.</td>
  </tr>
 </tbody>
</table>
