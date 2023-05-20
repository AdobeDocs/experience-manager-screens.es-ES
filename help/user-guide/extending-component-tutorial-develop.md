---
title: Ampliación de un componente de AEM Screens
seo-title: Extending an AEM Screens Component
description: El siguiente tutorial muestra los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens predeterminados. El componente Imagen se amplía para agregar una superposición de texto legible.
seo-description: The following tutorial walks through the steps and best practices for extending out of the box AEM Screens components. The Image component is extended to add an authorable text overlay.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: e316614f-2d40-4b62-a1e5-f30817def742
source-git-commit: 29116a15d5486b2c446cae0d092c4d4b802fe9e7
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 2%

---

# Ampliación de un componente de AEM Screens {#extending-an-aem-screens-component}

El siguiente tutorial muestra los pasos y las prácticas recomendadas para ampliar los componentes de AEM Screens predeterminados. El componente Imagen se amplía para agregar una superposición de texto legible.

## Información general {#overview}

Este tutorial está diseñado para desarrolladores que son nuevos en AEM Screens. En este tutorial, el componente Imagen de pantallas se amplía para crear un componente Póster. Sobre la imagen se superponen un título, una descripción y un logotipo para crear una experiencia atractiva en un canal de secuencias.

>[!NOTE]
>
>Antes de iniciar este tutorial, se recomienda completar el tutorial: [Desarrollo de un componente personalizado para AEM Screens](developing-custom-component-tutorial-develop.md).

![Componente de póster personalizado](assets/2018-05-07_at_4_09pm.png)

El componente Póster personalizado se crea ampliando el componente Imagen.

## Requisitos previos {#prerequisites}

Para completar este tutorial, necesita lo siguiente:

1. AEM Paquete de funciones de pantallas más reciente de 6.5
1. [Reproductor de AEM Screens](/help/user-guide/aem-screens-introduction.md)
1. Entorno de desarrollo local

Los pasos del tutorial y las capturas de pantalla se realizan con CRXDE-Lite. [Eclipse](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/aem-eclipse.html) o [IntelliJ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/ht-intellij.html) Los IDE también se pueden utilizar para completar el tutorial. Más información sobre cómo utilizar un IDE para [AEM desarrolle con la ayuda de la aplicación de la aquí](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

## Configuración del proyecto {#project-setup}

El código fuente de un proyecto de Screens se suele administrar como un proyecto Maven de varios módulos. Para acelerar el tutorial, se ha generado previamente un proyecto utilizando [AEM Arquetipo de proyecto 13](https://github.com/adobe/aem-project-archetype). Más información sobre [AEM Puede encontrar aquí la creación de un proyecto con el tipo de archivo del proyecto de Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

1. Descargue e instale los siguientes paquetes mediante **Administración de paquetes CRX** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[Obtener archivo](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Obtener archivo](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Opcionalmente,** si trabaja con Eclipse u otro IDE, descargue el siguiente paquete de origen. AEM Implemente el proyecto en una instancia de local mediante el comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Proyecto de ejecución de We.Retail de pantallas de inicio SRC

[Obtener archivo](assets/start-poster-screens-weretail-run.zip)

1. Entrada **Administrador de paquetes CRX** `http://localhost:4502/crx/packmgr/index.jsp` se instalan los dos paquetes siguientes:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Pantallas We.Retail Ejecutar paquetes Ui.Apps y Ui.Content instalados mediante el Administrador de paquetes CRX](assets/crx-packages.png)

   Pantallas We.Retail Ejecutar paquetes Ui.Apps y Ui.Content instalados mediante el Administrador de paquetes CRX

## Crear el componente Póster {#poster-cmp}

El componente Póster amplía el componente Imagen de pantallas integradas. Un mecanismo de Sling, `sling:resourceSuperType`, se utiliza para heredar la funcionalidad principal del componente Imagen sin tener que copiar y pegar. Más información sobre los conceptos básicos de [El procesamiento de solicitudes de Sling se puede encontrar aquí.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html?lang=es)

El componente Póster se representa en pantalla completa en el modo de previsualización/producción. En el modo de edición, es importante procesar el componente de forma diferente para facilitar la creación del canal de secuencia.

1. Entrada **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE de su elección) debajo de `/apps/weretail-run/components/content`crear un `cq:Component` nombrado `poster`.

   Añada las siguientes propiedades a `poster` componente:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![Propiedades de /apps/weretail-run/components/content/poster](assets/poster.png)

   Propiedades de /apps/weretail-run/components/content/poster

   Mediante la configuración de `sling:resourceSuperType`propiedad igual a `screens/core/components/content/image` el componente Póster hereda de forma efectiva toda la funcionalidad del componente Imagen. Nodos y archivos equivalentes encontrados debajo de `screens/core/components/content/image` se puede añadir debajo de `poster` para anular y ampliar la funcionalidad.

1. Copie el `cq:editConfig` nodo debajo `/libs/screens/core/components/content/image.`Pegue el `cq:editConfig` debajo de `/apps/weretail-run/components/content/poster` componente.

   En el `cq:editConfig/cq:dropTargets/image/parameters` actualización de nodos de `sling:resourceType` propiedad para igualar `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   La representación XML del cq:editConfig se representa a continuación:

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

1. Copiar WCM Foundation `image` diálogo que se utilizará para la `poster` componente.

   Es más fácil comenzar desde un cuadro de diálogo existente y luego realizar modificaciones.

   1. Copie el cuadro de diálogo de: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Pegue el cuadro de diálogo debajo de `/apps/weretail-run/components/content/poster`

   ![Cuadro de diálogo copiado de /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   Cuadro de diálogo copiado de /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster

   Las pantallas `image` El componente se superescribe en WCM Foundation `image` componente. Por lo tanto, `poster` El componente hereda la funcionalidad de ambos. El cuadro de diálogo del componente de póster se compone de una combinación de los cuadros de diálogo Screens y Foundation. Características de la **Fusión de recursos de Sling** se utilizan para ocultar campos de diálogo y fichas irrelevantes que se heredan de los componentes superescritos.

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

   La propiedad `sling:hideChildren`= `"[linkURL,size]`&quot; se utiliza en `items` para garantizar que la variable **linkURL** y **talla** Los campos de están ocultos en el cuadro de diálogo. No basta con quitar estos nodos del cuadro de diálogo del póster. La propiedad `sling:hideResource="{Boolean}true"` en la pestaña accesibilidad se utiliza para ocultar toda la pestaña.

   Se agregan dos campos de selección al cuadro de diálogo para que los autores controlen la posición del texto y el color del Título y la Descripción.

   ![Póster - Estructura final del diálogo](assets/2018-05-03_at_4_49pm.png)

   Póster - Estructura final del diálogo

   En este punto, una instancia de `poster` componente se puede añadir a **Canal inactivo** en el proyecto de ejecución de We.Retail: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Campos del cuadro de diálogo Póster](assets/poster-dialog-full.png)

   Campos del cuadro de diálogo Póster

1. Cree un archivo debajo de `/apps/weretail-run/components/content/poster` nombrado `production.html.`

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

   Arriba se encuentra el marcado de producción para el componente Póster. La secuencia de comandos HTL anula `screens/core/components/content/image/production.html`. El `image.js` es un script del lado del servidor que crea un objeto Image de tipo POJO. A continuación, se puede llamar al objeto Image para procesar el `src` como una imagen de fondo de estilo en línea.

   `The h1` y las etiquetas h2 se añaden para mostrar el Título y la Descripción en función de las propiedades del componente: `${properties.jcr:title}` y `${properties.jcr:description}`.

   Rodeando el `h1` y `h2` es un contenedor div con tres clases CSS con variaciones de &quot; `cmp-poster__text`&quot;. El valor de `textPosition` y `textColor` Las propiedades de se utilizan para cambiar la clase CSS representada en función de la selección del cuadro de diálogo del autor. En la siguiente sección, se escribe CSS desde las bibliotecas de cliente para habilitar estos cambios en la visualización.

   También se incluye un logotipo como superposición en el componente. En este ejemplo, la ruta al logotipo de We.Retail está codificada en DAM. Según el caso de uso, puede tener más sentido crear un campo de diálogo para que la ruta del logotipo sea un valor rellenado dinámicamente.

   Tenga en cuenta también que la notación BEM (Modificador de elementos de bloque) se utiliza con el componente. BEM es una convención de codificación CSS que facilita la creación de componentes reutilizables. BEM es la notación utilizada por [AEM Componentes principales](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. Cree un archivo debajo de `/apps/weretail-run/components/content/poster` nombrado `edit.html.`

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

   Arriba se encuentra la **editar** marcado para el componente Póster. La secuencia de comandos HTL anula `/libs/screens/core/components/content/image/edit.html`. El marcado es similar al `production.html` y muestra el título y la descripción encima de la imagen.

   El `aem-Screens-editWrapper`se añade para que el componente no se represente a pantalla completa en el editor. El `data-emptytext` garantiza que se muestre un marcador de posición cuando no se haya rellenado ninguna imagen o contenido.

## Creación de bibliotecas del lado del cliente {#clientlibs}

AEM Las bibliotecas del lado del cliente proporcionan un mecanismo para organizar y administrar los archivos CSS y JavaScript necesarios para una implementación de la. Más información sobre el uso de [Las bibliotecas del lado del cliente se pueden encontrar aquí.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

Los componentes de AEM Screens se representan de forma diferente en el modo de edición frente al modo de previsualización/producción. Se crean dos conjuntos de bibliotecas de cliente, una para el modo de edición y otra para la vista previa/producción.

1. Cree una carpeta para las bibliotecas del lado del cliente para el componente Póster.

   Debajo `/apps/weretail-run/components/content/poster,`cree una carpeta llamada `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Debajo del `clientlibs` carpeta cree un nodo llamado `shared` de tipo `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. Agregue las siguientes propiedades a la biblioteca de cliente compartida:

   * `allowProxy` | Booleana | `true`
   * `categories` | Cadena[] | `cq.screens.components`

   ![Propiedades de /apps/weretail-run/components/content/poster/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Propiedades de /apps/weretail-run/components/content/poster/clientlibs/shared

   El `categories` es una cadena que identifica la biblioteca de cliente. El `cq.screens.components` se utiliza en los modos de edición y de previsualización/producción. Por lo tanto, cualquier CSS/JS definido en `shared` clientlib se carga en todos los modos.

   Se recomienda no exponer nunca ninguna ruta directamente a /apps en un entorno de producción. El `allowProxy` garantiza que se haga referencia a la biblioteca de cliente CSS y JS mediante un prefijo de `/etc.clientlibs`. Más información sobre la [La propiedad allowProxy se puede encontrar aquí.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

1. Crear archivo con el nombre `css.txt` debajo de la carpeta compartida.

   Rellene el archivo con lo siguiente:

   ```
   #base=css
   
   styles.less
   ```

1. Cree una carpeta llamada `css` debajo de `shared` carpeta. Añada un archivo llamado `style.less` debajo de `css` carpeta. La estructura de las bibliotecas de cliente debería tener este aspecto:

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   En lugar de escribir CSS directamente, este tutorial utiliza LESS. [MENOS](https://lesscss.org/) es un precompilador de CSS popular que admite variables, mezclas y funciones CSS. AEM Las bibliotecas de cliente de admiten de forma nativa la compilación LESS. AEM Sass u otros pre-compiladores pueden ser utilizados pero deben ser compilados fuera de la.

1. Rellenar `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` con lo siguiente:

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
   >Los Web Fonts Google se utilizan para las familias de fuentes. Los Web Fonts requieren conectividad a Internet y no todas las implementaciones de pantallas ofrecerán una conexión confiable. La planificación del modo sin conexión es una consideración importante para las implementaciones de Screens.

1. Copie el `shared` carpeta de la biblioteca del cliente. Péguelo como elemento secundario y cambie su nombre a `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. Actualice el `categories` propiedad de la biblioteca de cliente de producción que se va a almacenar `cq.screens.components.production.`

   El `cq.screens.components.production` garantiza que los estilos solo se carguen en el modo de Previsualización/Producción.

   ![Propiedades de /apps/weretail-run/components/content/poster/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Propiedades de /apps/weretail-run/components/content/poster/clientlibs/production

1. Rellenar `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` con lo siguiente:

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

   Los estilos anteriores muestran el Título y la Descripción en una posición absoluta en la pantalla. El título se muestra más grande que la descripción. La notación BEM del componente facilita la definición cuidadosa de los estilos dentro de la clase cmp-poster.

Una tercera categoría clientlibrary: `cq.screens.components.edit` se puede usar para agregar Editar solo estilos específicos al componente.

| Categoría de Clientlib | Uso |
|---|---|
| `cq.screens.components` | Estilos y scripts compartidos entre los modos de edición y producción |
| `cq.screens.components.edit` | Estilos y scripts que solo se utilizan en el modo de edición |
| `cq.screens.components.production` | Estilos y scripts que solo se utilizan en el modo de producción |

## Agregar el componente Póster a un canal de secuencia {#add-sequence-channel}

El componente Póster se utiliza en un canal de secuencia. El paquete de inicio de este tutorial incluye un canal inactivo. El canal inactivo está preconfigurado para permitir componentes del grupo **Ejecución de We.Retail: contenido**. El grupo del componente Póster está establecido en `We.Retail Run - Content` y está disponible para añadirse al canal.

1. Abra el canal inactivo desde el proyecto de ejecución de We.Retail: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Arrastre y suelte una nueva instancia de **Póster** de la barra lateral a la página.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Edite el cuadro de diálogo del componente Póster para añadir una imagen, un título o una descripción. Utilice las opciones Posición del texto y Color del texto para asegurarse de que el Título/Descripción sea legible sobre la imagen.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Repita los pasos anteriores para agregar algunos componentes de póster. Añada transiciones entre los componentes.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## En resumen {#putting-it-all-together}

El siguiente vídeo muestra el componente terminado y cómo se puede añadir a un canal de secuencia. A continuación, el canal se añade a una pantalla de ubicación y, finalmente, se asigna a un reproductor de Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## Código finalizado {#finished-code}

A continuación se muestra el código terminado del tutorial. El **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** y **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** AEM son los paquetes compilados de la. El ** **SRC-screens-weretail-run-0.0.1.zip es el código fuente no compilado que se puede implementar mediante Maven.

[Obtener archivo](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Obtener archivo](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

Proyecto de ejecución de We.Retail de pantallas finales SRC

[Obtener archivo](assets/src-screens-weretail-run-001.zip)
