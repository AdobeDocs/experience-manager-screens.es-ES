---
title: Crear plantillas personalizadas en diseños de varias zonas
seo-title: Creating Custom Templates in MultiZone Layouts
description: Siga esta página para aprender a crear plantillas personalizadas en diseños MultiZone.
seo-description: Follow this page to learn about creating custom templates in MultiZone layouts.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 1%

---

# Crear plantillas personalizadas para diseños de varias zonas {#creating-custom-templates-multizone}

Esta página muestra cómo puede crear una plantilla personalizada para un diseño de varias zonas.

## Consideraciones importantes {#considerations}

Hay dos consideraciones importantes que debe tener en cuenta antes de crear una plantilla personalizada en un diseño de varias zonas:

1. **Tamaño de píxel fijo o porcentajes**:

   Debe decidir si desea utilizar un tamaño de píxel fijo para diferentes zonas del diseño personalizado o si desea crear un diseño personalizado con porcentajes.

   >[!NOTE]
   >La ventaja de utilizar percentage para establecer zonas para el diseño personalizado permite reutilizar la plantilla en una variedad de tamaños de pantalla.

1. **Convención de nomenclatura**:

   Antes de saber cómo crear plantillas de varias zonas personalizadas para utilizarlas en un proyecto de AEM Screens, se recomienda comprender el lenguaje de las plantillas que desea crear.

   | **Nombre del diseño** | **Descripción** |
   |---|---|
   | Left20-LandscapeHD3Zone | Se refiere a un diseño horizontal de 3 zonas que le permite crear 3 zonas con la zona 1 como 20 % de la pantalla horizontal y vertical desde la izquierda, la zona 2 como 80 % de la pantalla horizontal y 20 % de la pantalla vertical justificada a la derecha, la zona 3 como 100 % de la pantalla horizontal y 80 % de la pantalla vertical con una relación de aspecto de 16:9 |
   | Upper20-PortraitHD2Zone | Se refiere a una plantilla vertical de 2 zonas que cubre el 20 % de la pantalla desde arriba, con una relación de aspecto de 16:9 |
   | Right20-LandscapeSD3Zone | Se refiere a una plantilla de 3 zonas que cubre el 20 % de la pantalla desde la derecha, con una relación de aspecto de 4:3 |

   >[!IMPORTANT]
   >Es posible que las zonas definidas dentro del diseño personalizado no coincidan con la relación de aspecto general de todo el diseño. La convención de nombres que se sigue en este documento especifica la proporción de aspecto del diseño personalizado en su conjunto.

## Ejemplo de caso de uso Left20-LandscapeHD3Zone Diseño {#custom-template-one}

Siga la sección siguiente para crear una plantilla personalizada *Left20-LandscapeHD3Zone* con la siguiente configuración:

* **Izquierda20** se refiere a la zona superior de la izquierda que cubre el 20 % del tamaño de pantalla horizontal y vertical.
* **Horizontal** hace referencia a la orientación de la pantalla
* **HD** se refiere a la relación de aspecto como 16:9
* **3Zone** hace referencia a tres zonas de la visualización

## Representación visual del diseño de varias zonas {#multi-layout-visual-one}

El diseño Left20-LandscapeHD3Zone le permite crear el siguiente diseño de varias zonas en su proyecto:

![imagen](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Creación de un diseño de zona HD3 horizontal izquierda20 {#landscape-layout-one}

Siga los pasos a continuación para crear un diseño Left20-LandscapeHD3Zone para un proyecto de AEM Screens:

1. Cree un proyecto de AEM Screens titulado como **customtemplate**.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Vaya a **CRXDE Lite** AEM desde la instancia de la —> Herramientas —> **CRXDE Lite**.

1. Cree una carpeta en **apps** con título **customtemplate**. Del mismo modo, cree otra carpeta con el título **plantilla** bajo **customtemplate**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Se recomienda hacer clic en **Guardar todo** en la barra de acciones de CRXDE Lite cada vez que cree, edite o copie contenido en cualquiera de los nodos; de lo contrario, no podrá confirmar las actualizaciones.

1. Copie la plantilla de la barra izquierda de `/libs/screens/core/templates/splitscreenchannel/lbar-left` hasta `/apps/customtemplate/template`.

1. Cambie el nombre del copiado **lbar-left** (`/apps/customtemplate/template`) a **my-custom-layout**.
   ![imagen](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Vaya a `/apps/customtemplate/template/my-custom-layout` y actualice las propiedades **jcr:description** hasta *Plantilla para Left20-LandscapeHD3Zone* y **jcr:título** hasta *Left20-LandscapeHD3Zone*.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Vaya a **offline-config** nodo de `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` y actualice el **jcr:título** hasta *Left20-LandscapeHD3Zone*.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Vaya a *jcr:contenido* propiedad de **my-custom-template** de `/apps/customtemplate/template/my-custom-layout/jcr:content` y actualice el **cq:cssClass** propiedad a **aem-Layout my-custom-layout**.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En referencia al paso (4), en el que ha copiado la plantilla de la barra izquierda, verá 3 cuadrículas adaptables en `my-custom-layout/jcr:content`. Agregue una clase css personalizada a cada una de las cuadrículas adaptables de la *cq:cssClass* , por ejemplo, *my-custom-layout-top-left* para *r1c1* nodo.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Del mismo modo, agregue *my-custom-layout-top-right* para *r1c2*  y, *my-custom-layout-bottom* para *r2c1* nodo.

   >[!NOTE]
   >Estas clases personalizadas se utilizarán en el CSS para establecer la anchura y altura de estas cuadrículas adaptables.

   >[!NOTE]
   >Puede agregar o quitar las cuadrículas adaptables en función del número total de cuadrículas que desee. En este ejemplo, mostramos 2 cuadrículas en la primera fila y 1 cuadrícula en la segunda fila, por lo que hay un total de 3 cuadrículas adaptables (r1c1, r1c2, r2c1).

1. Copiar `/libs/settings/wcm/designs/screens` hasta `/apps/settings/wcm/designs/` y cambie el nombre del diseño copiado por **custom-template-designs**.

1. Vaya a `/apps/settings/wcm/designs/custom-template-designs` y actualice la propiedad *jcr:título* de **custom-template-designs** hasta **customtemplate-design**.

1. Vaya a `/apps/settings/wcm/designs/custom-template-designs` y cree un archivo static.css.

1. Copie el contenido en `static.css` archivo:

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >Puede actualizar los porcentajes para que coincidan con los requisitos de la plantilla personalizada.

1. Vaya a `/apps/<project>/templates/my-custom-layout/jcr:content` y actualice la propiedad *cq:designPath* hasta `/apps/settings/wcm/designs/customtemplate-designs` para cargar los estilos configurados en static.css

   >[!NOTE]
   >Se recomienda escribir todos los estilos en lugar de copiar o pegar, lo que puede causar espacios en blanco y problemas de estilo css.

## Visualización del resultado {#viewing-result}

Siga los pasos a continuación para utilizar la plantilla personalizada anterior en su proyecto de AEM Screens:

1. Vaya al proyecto de Screens que ha creado en el paso (1) y seleccione. **Canales** carpeta.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Clic **Crear** en la barra de acciones y seleccione la plantilla **Left20-LandscapeHD3Zone** desde el **Crear** asistente.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Una vez creado un canal con la plantilla personalizada, puede añadir recursos al canal desde el editor. La siguiente vista previa muestra las imágenes en una plantilla personalizada.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserción de una imagen como capa de fondo  {#inserting-image}

Puede insertar una imagen como capa de fondo en el diseño:

Puede ajustar la regla CSS para utilizar lo que se denomina &quot;data-uri&quot; y directamente en línea la imagen (codificada en Base64) en el archivo CSS que creó en (paso 13). *static.css*.

Esto se hace de la siguiente manera:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

O bien, puede seguir los pasos a continuación:

1. Asegúrese de que la imagen se incluya de alguna manera en la configuración sin conexión del canal
1. Utilice un vínculo directo a la imagen en el CSS anterior, en lugar de la variante &quot;uri de datos&quot;


## Actualizando color de fondo {#updating-color}

Para cambiar el color de fondo, agregue el siguiente código al archivo xml (paso 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
