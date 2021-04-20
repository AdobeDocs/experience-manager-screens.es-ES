---
title: Ampliación de un componente de AEM Screens
seo-title: Ampliación de un componente de AEM Screens
description: En el siguiente tutorial se explican los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens predeterminados. El componente Imagen se amplía para añadir una superposición de texto legible.
seo-description: En el siguiente tutorial se explican los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens predeterminados. El componente Imagen se amplía para añadir una superposición de texto legible.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 2%

---


# Ampliación de un componente de AEM Screens {#extending-an-aem-screens-component}

En el siguiente tutorial se explican los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens predeterminados. El componente Imagen se amplía para añadir una superposición de texto legible.

## Información general {#overview}

Este tutorial está diseñado para desarrolladores que utilicen AEM Screens por primera vez. En este tutorial, el componente Imagen de Screens se amplía para crear un componente de póster. Un título, una descripción y un logotipo se superponen sobre una imagen para crear una experiencia atractiva en un canal de secuencia.

>[!NOTE]
>
>Antes de iniciar este tutorial, se recomienda completar el tutorial: [Desarrollo de un componente personalizado para AEM Screens](developing-custom-component-tutorial-develop.md).

![Componente de póster personalizado](assets/2018-05-07_at_4_09pm.png)

El componente Póster personalizado se crea ampliando el componente Imagen .

## Requisitos previos {#prerequisites}

Para completar este tutorial, es necesario lo siguiente:

1. [AEM 6.4](https://docs.adobe.com/content/help/es-ES/experience-manager-64/release-notes/release-notes.html) o  [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + Último paquete de funciones de Screens
1. [Reproductor de AEM Screens](/help/user-guide/aem-screens-introduction.md)
1. Entorno de desarrollo local

Los pasos del tutorial y las capturas de pantalla se realizan con CRXDE-Lite. [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) También se pueden utilizar Eclipseor  [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) IntelliJIDE para completar el tutorial. Puede encontrar más información sobre el uso de un IDE para [desarrollarse con AEM aquí](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide).

## Configuración del proyecto {#project-setup}

El código fuente de un proyecto de Screens se administra normalmente como un proyecto Maven de varios módulos. Para acelerar el tutorial, se generó un proyecto previamente utilizando el [AEM tipo de archivo del proyecto 13](https://github.com/adobe/aem-project-archetype). Puede encontrar más información sobre la [creación de un proyecto con el tipo de archivo del proyecto Maven AEM aquí](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule).

1. Descargue e instale los siguientes paquetes utilizando **CRX package manage** `http://localhost:4502/crx/packmgr/index.jsp)r:`

   [Obtener archivo](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Obtener archivo](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Opcionalmente,** si trabaja con Eclipse u otro IDE, descargue el siguiente paquete de origen. Implemente el proyecto en una instancia de AEM local mediante el comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Proyecto de ejecución de We.Retail en Screens de inicio de SRC

   [Obtener archivo](assets/start-poster-screens-weretail-run.zip)

1. En **CRX Package Manager** `http://localhost:4502/crx/packmgr/index.jsp` se instalan los dos paquetes siguientes:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens Los paquetes de We.Retail Run Ui.Apps y Ui.Content instalados a través del administrador de paquetes CRX](assets/crx-packages.png)

   Screens Los paquetes de We.Retail Run Ui.Apps y Ui.Content instalados a través del administrador de paquetes CRX

## Crear el componente de póster {#poster-cmp}

El componente Póster extiende el componente Imagen fuera de las pantallas de cuadro. Un mecanismo de Sling, `sling:resourceSuperType`, se utiliza para heredar la funcionalidad principal del componente Imagen sin tener que copiar y pegar. Puede encontrar más información sobre los conceptos básicos del [Procesamiento de solicitudes de Sling aquí.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

El componente Póster se representa en pantalla completa en modo de vista previa/producción. En el modo de edición, es importante procesar el componente de forma diferente para facilitar la creación del canal de secuencia.

1. En **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE de su elección) debajo de `/apps/weretail-run/components/content`cree un nuevo `cq:Component` con el nombre `poster`.

   Agregue las siguientes propiedades al componente `poster` :

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

   Al establecer la propiedad `sling:resourceSuperType`en `screens/core/components/content/image`, el componente Póster hereda de forma efectiva toda la funcionalidad del componente Imagen. Los nodos y archivos equivalentes que se encuentran debajo de `screens/core/components/content/image` se pueden agregar debajo del componente `poster` para anular y ampliar la funcionalidad.

1. Copie el nodo `cq:editConfig` debajo de `/libs/screens/core/components/content/image.`Pegar el `cq:editConfig` debajo del componente `/apps/weretail-run/components/content/poster`.

   En el nodo `cq:editConfig/cq:dropTargets/image/parameters`, actualice la propiedad `sling:resourceType` a igual a `weretail-run/components/content/poster`.

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

1. Copie el cuadro de diálogo WCM Foundation `image` que se utilizará para el componente `poster`.

   Es más fácil empezar desde un cuadro de diálogo existente y luego realizar modificaciones.

   1. Copie el cuadro de diálogo desde: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Pegue el cuadro de diálogo debajo de `/apps/weretail-run/components/content/poster`

   ![Cuadro de diálogo copiado de /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   Cuadro de diálogo copiado de /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster

   El componente Screens `image` está superescrito al componente WCM Foundation `image`. Por lo tanto, el componente `poster` hereda la funcionalidad de ambos. El cuadro de diálogo para el componente de póster se compone de una combinación de los cuadros de diálogo Screens y Foundation. Las funciones de la **fusión de recursos de Sling** se utilizan para ocultar campos de diálogo y pestañas irrelevantes que se heredan de los componentes superescritos.

1. Actualice el cuadro de diálogo cq:dialog debajo de `/apps/weretail-run/components/content/poster` con los siguientes cambios representados en XML:

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

   La propiedad `sling:hideChildren`= `"[linkURL,size]`&quot; se utiliza en el nodo `items` para garantizar que los campos **linkURL** y **size** estén ocultos en el cuadro de diálogo. No basta con eliminar estos nodos del cuadro de diálogo de póster. La propiedad `sling:hideResource="{Boolean}true"` de la pestaña de accesibilidad se utiliza para ocultar toda la pestaña.

   Se añaden dos campos de selección al cuadro de diálogo para que los autores puedan controlar la posición y el color del texto del Título y la Descripción.

   ![Afiche - Estructura de diálogo final](assets/2018-05-03_at_4_49pm.png)

   Afiche - Estructura de diálogo final

   En este punto, se puede añadir una instancia del componente `poster` a la página **Canal inactivo** en el proyecto de ejecución de We.Retail: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Campos de diálogo de póster](assets/poster-dialog-full.png)

   Campos de diálogo de póster

1. Cree un archivo debajo de `/apps/weretail-run/components/content/poster` con el nombre `production.html.`

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

   Arriba está el marcado de producción para el componente de póster. El script HTL anula `screens/core/components/content/image/production.html`. El `image.js` es una secuencia de comandos del lado del servidor que crea un objeto de imagen de tipo POJO. A continuación, se puede llamar al objeto Image para procesar el `src` como una imagen de fondo de estilo en línea.

   `The h1` Las etiquetas h2 y h2 se añaden para mostrar el Título y la Descripción en función de las propiedades del componente:  `${properties.jcr:title}` y  `${properties.jcr:description}`.

   Rodeando las etiquetas `h1` y `h2` hay un envoltorio div con tres clases CSS con variaciones de &quot; `cmp-poster__text`&quot;. El valor de las propiedades `textPosition` y `textColor` se utiliza para cambiar la clase CSS representada en función de la selección de diálogo del autor. En la siguiente sección CSS de las bibliotecas de cliente se escriben para habilitar estos cambios en pantalla.

   Un logotipo también se incluye como superposición en el componente. En este ejemplo, la ruta al logotipo de We.Retail está codificada en DAM. Según el caso de uso, puede que sea más sensato crear un nuevo campo de diálogo para que la ruta del logotipo sea un valor rellenado dinámicamente.

   Tenga en cuenta también que la notación BEM (Modificador de elemento de bloque) se utiliza con el componente. BEM es una convención de codificación CSS que facilita la creación de componentes reutilizables. BEM es la notación que utilizan los [AEM componentes principales](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). Puede encontrar más información en: [https://getbem.com/](https://getbem.com/)

1. Cree un archivo debajo de `/apps/weretail-run/components/content/poster` con el nombre `edit.html.`

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

   Arriba está el marcado **edit** para el componente de póster. El script HTL anula `/libs/screens/core/components/content/image/edit.html`. El marcado es similar al marcado `production.html` y muestra el título y la descripción encima de la imagen.

   Se añade `aem-Screens-editWrapper`para que el componente no se muestre en pantalla completa en el editor. El atributo `data-emptytext` garantiza que se muestre un marcador de posición cuando no se haya rellenado ninguna imagen o contenido.

## Crear bibliotecas del lado del cliente {#clientlibs}

Las bibliotecas del lado del cliente proporcionan un mecanismo para organizar y administrar los archivos CSS y JavaScript necesarios para una implementación de AEM. Puede encontrar más información sobre el uso de [bibliotecas del lado del cliente aquí.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

Los componentes de AEM Screens se representan de forma diferente en el modo de edición frente al modo de producción/previsualización. Se crean dos conjuntos de bibliotecas de cliente, una para el modo de edición y otra para la vista previa/producción.

1. Cree una carpeta para bibliotecas del lado del cliente para el componente Póster .

   Debajo de `/apps/weretail-run/components/content/poster,`cree una nueva carpeta denominada `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Debajo de la carpeta `clientlibs` cree un nuevo nodo denominado `shared` de tipo `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. Agregue las siguientes propiedades a la biblioteca de cliente compartida:

   * `allowProxy` | Booleano | `true`
   * `categories` | Cadena[] |  `cq.screens.components`

   ![Propiedades para /apps/weretail-run/components/content/poster/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Propiedades para /apps/weretail-run/components/content/poster/clientlibs/shared

   La propiedad `categories` es una cadena que identifica la biblioteca del cliente. La categoría `cq.screens.components` se utiliza en los modos Edición y Vista previa/Producción. Por lo tanto, cualquier CSS/JS definido en la clientlib `shared` se carga en todos los modos.

   Se recomienda no exponer nunca ninguna ruta directamente a /apps en un entorno de producción. La propiedad `allowProxy` garantiza que la biblioteca de cliente CSS y JS se haga referencia a través de un prefijo `/etc.clientlibs`. Puede encontrar más información sobre la propiedad [allowProxy aquí.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. Cree un archivo con el nombre `css.txt` debajo de la carpeta compartida.

   Rellene el archivo con lo siguiente:

   ```
   #base=css
   
   styles.less
   ```

1. Cree una carpeta con el nombre `css` debajo de la carpeta `shared`. Añada un archivo denominado `style.less` debajo de la carpeta `css`. La estructura de las bibliotecas de cliente debería tener este aspecto:

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   En lugar de escribir CSS directamente, este tutorial utiliza LESS. [](https://lesscss.org/) LESSes un precompilador CSS popular que admite variables, mezclas y funciones CSS. AEM bibliotecas de cliente admiten de forma nativa la compilación de LESS. Se pueden utilizar sass u otros precompiladores, pero deben compilarse fuera de AEM.

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
   >Las fuentes web de Google se utilizan para las familias de fuentes. Las fuentes web requieren conectividad a Internet y no todas las implementaciones de pantallas tendrán una conexión fiable. La planificación del modo sin conexión es una consideración importante para las implementaciones de Screens.

1. Copie la carpeta de biblioteca de cliente `shared`. Péguelo como hermano y renómbralo como `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. Actualice la propiedad `categories` de la biblioteca clientlibrary de producción para que sea `cq.screens.components.production.`

   La categoría `cq.screens.components.production` garantiza que los estilos solo se carguen en el modo de vista previa/producción.

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

   Los estilos anteriores muestran el Título y la Descripción en una posición absoluta en la pantalla. El título se mostrará mucho más grande que la descripción. La notación BEM del componente facilita sobremanera el alcance de los estilos dentro de la clase cmp-poster.

Una tercera categoría clientlibrary: `cq.screens.components.edit` se puede utilizar para agregar Editar solo estilos específicos al componente.

| Categoría de Clientlib | Uso |
|---|---|
| `cq.screens.components` | Estilos y secuencias de comandos que se comparten entre los modos de edición y producción |
| `cq.screens.components.edit` | Estilos y secuencias de comandos que solo se utilizan en el modo de edición |
| `cq.screens.components.production` | Estilos y secuencias de comandos que solo se utilizan en el modo de producción |

## Agregar componente de póster a un canal de secuencia {#add-sequence-channel}

El componente Póster está diseñado para utilizarse en un canal de secuencia. El paquete de inicio de este tutorial incluía un canal inactivo. El canal inactivo está preconfigurado para permitir componentes del grupo **We.Retail Run - Content**. El grupo del componente Póster se establece en `We.Retail Run - Content` y está disponible para añadirse al canal.

1. Abra el canal inactivo en el proyecto de ejecución de We.Retail: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Arrastre y suelte una nueva instancia del componente **Póster** desde la barra lateral hasta la página.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Edite el cuadro de diálogo del componente Póster para añadir una imagen, un título, una descripción. Utilice las opciones Posición del texto y Color del texto para asegurarse de que el Título/Descripción sea legible sobre la imagen.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Repita los pasos anteriores para añadir algunos componentes de póster. Añada transiciones entre los componentes.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## Uniéndolo todo {#putting-it-all-together}

El siguiente vídeo muestra el componente terminado y cómo se puede añadir a un canal de secuencia. A continuación, el canal se agrega a la visualización Ubicación y, finalmente, se asigna a un reproductor Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## Código finalizado {#finished-code}

A continuación se muestra el código terminado del tutorial. Los **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** y **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** son los paquetes AEM compilados. El **SRC-screens-weretail-run-0.0.1.zip **es el código fuente no compilado que se puede implementar mediante Maven.

[Obtener archivo](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Obtener archivo](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

Proyecto de ejecución de We.Retail de SRC Final Screens

[Obtener archivo](assets/src-screens-weretail-run-001.zip)
