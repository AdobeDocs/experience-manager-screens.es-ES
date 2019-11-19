---
title: Ampliación del componente AEM Screens
seo-title: Ampliación del componente AEM Screens
description: En el siguiente tutorial se explican los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens de forma predeterminada. El componente Imagen se amplía para añadir una superposición de texto de autoría.
seo-description: En el siguiente tutorial se explican los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens de forma predeterminada. El componente Imagen se amplía para añadir una superposición de texto de autoría.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Ampliación del componente AEM Screens {#extending-an-aem-screens-component}

En el siguiente tutorial se explican los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens de forma predeterminada. El componente Imagen se amplía para añadir una superposición de texto de autoría.

## Información general {#overview}

Este tutorial está dirigido a desarrolladores que no conocen AEM Screens. En este tutorial, el componente Imagen de pantalla se amplía para crear un componente de póster. Un título, una descripción y un logotipo se superponen sobre una imagen para crear una experiencia atractiva en un canal de secuencia.

>[!NOTE]
>
>Antes de iniciar este tutorial, se recomienda completar el tutorial: [Desarrollo de un componente personalizado para pantallas](developing-custom-component-tutorial-develop.md)AEM.

![Componente de póster personalizado](assets/2018-05-07_at_4_09pm.png)

El componente Póster personalizado se crea ampliando el componente Imagen.

## Requisitos previos {#prerequisites}

## Configuración del proyecto {#project-setup}

1. Descargue e instale los siguientes paquetes mediante la administración **del paquete** CRX `http://localhost:4502/crx/packmgr/index.jsp)r:`

   [Obtener archivo](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Obtener archivo](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Opcionalmente,** si trabaja con Eclipse u otro IDE, descargue el siguiente paquete de origen. Implemente el proyecto en una instancia local de AEM mediante el comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   SRC Start Screens We.Retail Run Project

   [Obtener archivo](assets/start-poster-screens-weretail-run.zip)

1. En el Administrador **de paquetes** CRX `http://localhost:4502/crx/packmgr/index.jsp` se instalan los dos paquetes siguientes:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![Screens We.Retail Ejecute los paquetes Ui.Apps y Ui.Content instalados mediante el administrador de paquetes CRX](assets/crx-packages.png)

   Screens We.Retail Ejecute los paquetes Ui.Apps y Ui.Content instalados mediante el administrador de paquetes CRX

## Creación del componente de póster {#poster-cmp}

El componente Póster extiende el componente Imagen fuera de las pantallas del cuadro. Un mecanismo de Sling, `sling:resourceSuperType`, se utiliza para heredar la funcionalidad básica del componente Imagen sin tener que copiar y pegar. Puede encontrar más información sobre los conceptos básicos del procesamiento de solicitudes de [Sling aquí.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

El componente Póster se procesa en pantalla completa en el modo de vista previa/producción. En el modo de edición, es importante representar el componente de forma diferente para facilitar la creación del canal de secuencia.

1. En **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE de su elección) debajo de para `/apps/weretail-run/components/content`crear un nuevo `cq:Component` llamado `poster`.

   Agregue las siguientes propiedades al `poster` componente:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![Propiedades para /apps/weretail-run/components/content/poster](assets/poster.png)

   Propiedades para /apps/weretail-run/components/content/poster

   Al establecer la `sling:resourceSuperType`propiedad igual al componente `screens/core/components/content/image` Póster, se hereda de forma efectiva toda la funcionalidad del componente Imagen. Los nodos y archivos equivalentes encontrados debajo `screens/core/components/content/image` pueden agregarse debajo del `poster` componente para anular y ampliar la funcionalidad.

1. Copie el `cq:editConfig` nodo debajo de `/libs/screens/core/components/content/image.`Pegar el `cq:editConfig` debajo del `/apps/weretail-run/components/content/poster` componente.

   En el `cq:editConfig/cq:dropTargets/image/parameters` nodo, actualice la `sling:resourceType` propiedad a igual `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   Representación XML de cq:editConfig representada a continuación:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. Copiar cuadro de diálogo de WCM Foundation `image` que se usará para el `poster` componente.

   Es más fácil empezar desde un cuadro de diálogo existente y luego realizar modificaciones.

   1. Copie el cuadro de diálogo de: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Pegar el cuadro de diálogo debajo `/apps/weretail-run/components/content/poster`
   ![Cuadro de diálogo copiado de /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   Cuadro de diálogo copiado de /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster

   El componente Pantallas `image` se superpone al componente WCM Foundation `image` . Por lo tanto, el `poster` componente hereda la funcionalidad de ambos. El cuadro de diálogo para el componente de póster se compone de una combinación de los cuadros de diálogo Pantallas y Fundación. Las funciones de la fusión **de recursos** Sling se utilizan para ocultar los campos de diálogo y las fichas irrelevantes heredados de los componentes con supertipos.

1. Actualice el cuadro de diálogo cq:debajo `/apps/weretail-run/components/content/poster` con los siguientes cambios representados en XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   La propiedad `sling:hideChildren`= `"[linkURL,size]`" se utiliza en el `items` nodo para asegurarse de que los campos **linkURL** y **size** están ocultos en el cuadro de diálogo. No basta con quitar estos nodos del cuadro de diálogo de póster. La propiedad `sling:hideResource="{Boolean}true"` de la ficha de accesibilidad se utiliza para ocultar toda la ficha.

   Se añaden dos campos de selección al cuadro de diálogo para que los autores puedan controlar la posición y el color del texto del título y la descripción.

   ![Póster - Estructura de diálogo final](assets/2018-05-03_at_4_49pm.png)

   Póster - Estructura de diálogo final

   En este punto, se puede agregar una instancia del `poster` componente a la página Canal **** inactivo del proyecto de ejecución We.Retail: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Campos de diálogo de póster](assets/poster-dialog-full.png)

   Campos de diálogo de póster

1. Crear un archivo con el `/apps/weretail-run/components/content/poster` nombre `production.html.`

   Rellene el archivo con lo siguiente:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   Arriba está el marcado de producción para el componente de póster. El script HTL anula `screens/core/components/content/image/production.html`. El `image.js` es una secuencia de comandos del lado del servidor que crea un objeto de imagen como POJO. A continuación, se puede llamar al objeto Image para representar el `src` como una imagen de fondo de estilo en línea.

   `The h1` y las etiquetas h2 se agregan para mostrar el Título y la Descripción en función de las propiedades del componente: `${properties.jcr:title}` y `${properties.jcr:description}`.

   Alrededor de las etiquetas `h1` y `h2` hay un envoltorio div con tres clases CSS con variaciones de " `cmp-poster__text`". El valor de las propiedades `textPosition` y `textColor` se utiliza para cambiar la clase CSS representada en función de la selección de cuadro de diálogo del autor. En la siguiente sección, se escriben las CSS de las bibliotecas de cliente para habilitar estos cambios en la pantalla.

   Un logotipo también se incluye como superposición en el componente. En este ejemplo, la ruta al logotipo de We.Retail está codificada en DAM. Según el caso de uso, puede que sea más lógico crear un nuevo campo de diálogo para que la ruta del logotipo sea un valor que se rellene dinámicamente.

   Tenga en cuenta también que la notación BEM (Modificador de elemento de bloque) se utiliza con el componente. BEM es una convención de codificación CSS que facilita la creación de componentes reutilizables. BEM es la notación utilizada por los componentes [principales de](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)AEM. Puede encontrar más información en: [https://getbem.com/](https://getbem.com/)

1. Crear un archivo con el `/apps/weretail-run/components/content/poster` nombre `edit.html.`

   Rellene el archivo con lo siguiente:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   Arriba está el marcador de **edición** para el componente de póster. El script HTL anula `/libs/screens/core/components/content/image/edit.html`. El marcado es similar al `production.html` marcado y mostrará el título y la descripción encima de la imagen.

   El `aem-Screens-editWrapper`se agrega para que el componente no se procese a pantalla completa en el editor. El `data-emptytext` atributo garantiza que se muestre un marcador de posición cuando no se haya rellenado ninguna imagen o contenido.

## Crear bibliotecas del lado del cliente {#clientlibs}

Las bibliotecas del lado del cliente proporcionan un mecanismo para organizar y administrar los archivos CSS y JavaScript necesarios para una implementación de AEM. Puede encontrar más información sobre el uso de las bibliotecas del lado del [cliente aquí.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

Los componentes de AEM Screens se procesan de forma distinta en el modo de edición y en el modo de vista previa/producción. Se crean dos conjuntos de bibliotecas de cliente, uno para el modo de edición y otro para la vista previa/producción.

1. Cree una carpeta para las bibliotecas del lado del cliente para el componente Póster.

   Debajo de `/apps/weretail-run/components/content/poster,`crear una nueva carpeta con el nombre `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Debajo de la `clientlibs` carpeta, cree un nuevo nodo denominado `shared` de tipo `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. Agregue las siguientes propiedades a la biblioteca de cliente compartida:

   * `allowProxy` | Booleano | `true`
   * `categories` | Cadena[] | `cq.screens.components`
   ![Propiedades para /apps/weretail-run/components/content/poster/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Propiedades para /apps/weretail-run/components/content/poster/clientlibs/shared

   La `categories` propiedad es una cadena que identifica la biblioteca del cliente. La `cq.screens.components` categoría se utiliza tanto en el modo de edición como en el modo de vista previa/producción. Por lo tanto, cualquier CSS/JS definido en la `shared` clientlib se carga en todos los modos.

   Se recomienda no exponer nunca ninguna ruta directamente a /apps en un entorno de producción. La `allowProxy` propiedad garantiza que se haga referencia a CSS y JS de la biblioteca del cliente mediante un prefijo de `/etc.clientlibs`. Puede encontrar más información sobre la propiedad [allowProxy aquí.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. Cree un archivo con el nombre `css.txt` debajo de la carpeta compartida.

   Rellene el archivo con lo siguiente:

   ```
   #base=css
   
   styles.less
   ```

1. Cree una carpeta con el nombre `css` debajo de la `shared` carpeta. Agregue un archivo con el nombre `style.less` debajo de la `css` carpeta. La estructura de las bibliotecas cliente ahora debería tener este aspecto:

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   En lugar de escribir CSS directamente, este tutorial utiliza MENOS. [LESS](https://lesscss.org/) es un precompilador de CSS popular que admite variables, mezclas y funciones de CSS. Las bibliotecas de cliente de AEM admiten de forma nativa la compilación LESS. Se pueden utilizar los compiladores de serie u otros precompiladores, pero es necesario compilarlos fuera de AEM.

1. Rellene `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` con lo siguiente:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >Las fuentes web de Google se utilizan para las familias de fuentes. Las fuentes web requieren conectividad a Internet y no todas las implementaciones de pantallas tendrán una conexión fiable. La planificación del modo sin conexión es una consideración importante para las implementaciones de Pantallas.

1. Copie la carpeta de la biblioteca del `shared` cliente. Póngalo como hermano y cámbiele el nombre `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. Actualice la `categories` propiedad de la biblioteca de clientes de producción para que sea `cq.screens.components.production.`

   La `cq.screens.components.production` categoría garantiza que los estilos solo se carguen en el modo de vista previa/producción.

   ![Propiedades para /apps/weretail-run/components/content/poster/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Propiedades para /apps/weretail-run/components/content/poster/clientlibs/production

1. Rellene `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` con lo siguiente:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   Los estilos anteriores muestran el Título y la Descripción en una posición absoluta en la pantalla. El título se mostrará mucho más grande que la descripción. La notación BEM del componente facilita considerablemente el alcance de los estilos dentro de la clase cmp-poster.

Una tercera categoría clientlibrary: `cq.screens.components.edit` se puede usar para agregar al componente Editar solo estilos específicos.

| Categoría de biblioteca de clientes | Uso |
|---|---|
| `cq.screens.components` | Estilos y secuencias de comandos que se comparten entre los modos de edición y producción |
| `cq.screens.components.edit` | Estilos y secuencias de comandos que solo se utilizan en el modo de edición |
| `cq.screens.components.production` | Estilos y secuencias de comandos que solo se utilizan en el modo de producción |

## Agregar componente de póster a un canal de secuencia {#add-sequence-channel}

El componente Póster está diseñado para utilizarse en un canal de secuencia. El paquete de inicio para este tutorial incluía un canal inactivo. El canal inactivo está preconfigurado para permitir componentes del grupo **We.Retail Run - Content**. El grupo del componente Póster está definido en `We.Retail Run - Content` y está disponible para agregarse al canal.

1. Abra el canal inactivo en el proyecto de ejecución We.Retail: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Arrastre y suelte una nueva instancia del componente **Póster** desde la barra lateral de la página.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Edite el cuadro de diálogo del componente Póster para añadir una imagen, un título y una descripción. Utilice las opciones Posición del texto y Color del texto para asegurarse de que el Título/Descripción se puede leer sobre la imagen.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Repita los pasos anteriores para agregar algunos componentes de póster. Agregue transiciones entre los componentes.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## Colocando todo juntos {#putting-it-all-together}

El siguiente vídeo muestra el componente terminado y cómo se puede agregar a un canal de secuencia. A continuación, el canal se agrega a la pantalla Ubicación y, finalmente, se asigna a un reproductor de Pantallas.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9&captions=spa)

## Código finalizado {#finished-code}

A continuación se muestra el código terminado del tutorial. Los **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** y **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** son los paquetes compilados de AEM. El **SRC-screen-weretail-run-0.0.1.zip **es el código fuente no compilado que se puede implementar con Maven.

[Obtener archivo](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Obtener archivo](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail Run Project

[Obtener archivo](assets/src-screens-weretail-run-001.zip)
