---
title: Creación de plantillas personalizadas en diseños de varias zonas
seo-title: Creación de plantillas personalizadas en diseños de varias zonas
description: Siga esta página para obtener información sobre la creación de plantillas personalizadas en diseños de varias zonas.
seo-description: Siga esta página para obtener información sobre la creación de plantillas personalizadas en diseños de varias zonas.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---


# Creación de plantillas personalizadas para diseños de varias zonas {#creating-custom-templates-multizone}

Esta página muestra cómo se puede crear una plantilla personalizada para un diseño de varias zonas.

## Consideraciones importantes {#considerations}

Hay dos consideraciones importantes que debe tener en cuenta antes de crear una plantilla personalizada en el diseño de varias zonas:

1. **Tamaño o porcentajes** de píxeles fijos:

   Debe decidir si se utiliza un tamaño de píxel fijo para las diferentes zonas del diseño personalizado o si se desea crear un diseño personalizado con porcentajes.

   >[!NOTE]
   >La ventaja de utilizar el porcentaje para establecer zonas para el diseño personalizado le permite reutilizar la plantilla en una variedad de tamaños de pantalla.

1. **Convención** de nombres:

   Antes de comprender cómo crear plantillas de varias zonas personalizadas para utilizarlas en un proyecto de AEM Screens, se recomienda comprender la versión de las plantillas que desea crear.

   | **Nombre del diseño** | **Descripción** |
   |---|---|
   | Left20-LandscapeHD3Zone | Se refiere a un diseño horizontal de 3 zonas que le permite crear 3 zonas con una zona 1 del 20 % de la pantalla horizontal y vertical desde la izquierda, una zona 2 del 80 % de la pantalla horizontal y un 20 % de la pantalla vertical hacia la derecha, una zona 3 del 100 % de la pantalla horizontal y un 80 % de la pantalla vertical con una proporción de aspecto de 16:9 |
   | Upper20-PortraitHD2Zone | Se refiere a una plantilla vertical de 2 zonas que cubre el 20 % de la pantalla desde la parte superior, con una proporción de aspecto de 16:9 |
   | Right20-LandscapeSD3Zone | Se refiere a una plantilla de 3 zonas que cubre el 20 % de la pantalla desde la derecha, con una proporción de aspecto de 4:3 |

   >[!IMPORTANT]
   >Es posible que las zonas definidas en el diseño personalizado no coincidan con la proporción de aspecto general de todo el diseño. La convención de nombre seguida en este documento especifica la proporción de aspecto del diseño personalizado en su conjunto.

## Ejemplo de caso de uso Left20-LandscapeHD3Zone Diseño {#custom-template-one}

Siga la sección siguiente para crear una plantilla personalizada *Left20-LandscapeHD3Zone* con la siguiente configuración:

* **Left20** hace referencia a la zona superior izquierda que cubre el 20% del tamaño de pantalla horizontal y vertical.
* **** Landscaperefers a la orientación de la pantalla
* **** HDse refiere a la proporción de aspecto como 16:9
* **3** Zonhace referencia a tres zonas de la pantalla

## Representación visual del diseño de MultiZone {#multi-layout-visual-one}

El diseño Left20-LandscapeHD3Zone permite crear el siguiente diseño multizona en el proyecto:

![image](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Creación de un diseño Left20-LandscapeHD3Zone {#landscape-layout-one}

Siga los pasos a continuación para crear un diseño Left20-LandscapeHD3Zone para un proyecto de AEM Screens:

1. Cree un proyecto de AEM Screens titulado **plantilla personalizada**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Vaya a **CRXDE Lite** desde su instancia de AEM —> Herramientas —> **CRXDE Lite**.

1. Cree una carpeta en **aplicaciones** titulada como **plantilla personalizada**. Del mismo modo, cree otra carpeta titulada como **plantilla** en **plantilla personalizada**, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Se recomienda hacer clic en **Guardar todo** desde la barra de acciones del CRXDE Lite cada vez que cree, edite o copie contenido en cualquiera de los nodos, de lo contrario no podrá confirmar las actualizaciones.

1. Copie la plantilla de la izquierda de la barra de `/libs/screens/core/templates/splitscreenchannel/lbar-left` a `/apps/customtemplate/template`.

1. Cambie el nombre del **lbar-left** copiado (`/apps/customtemplate/template`) a **my-custom-layout**.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Vaya a `/apps/customtemplate/template/my-custom-layout` y actualice las propiedades **jcr:description** a *Template for Left20-LandscapeHD3Zone* y **jcr:title** a *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Vaya al nodo **offline-config** desde `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` y actualice el **jcr:title** a *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Vaya a la propiedad *jcr:content* de **my-custom-template** desde `/apps/customtemplate/template/my-custom-layout/jcr:content` y actualice la propiedad **cq:cssClass** a **aem-Layout my-custom-layout**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Haciendo referencia al paso (4), en el que ha copiado la plantilla de la izquierda, vista 3 cuadrículas adaptables en `my-custom-layout/jcr:content`. Añada la clase css personalizada en cada una de las cuadrículas adaptables de la propiedad *cq:cssClass*; por ejemplo, *my-custom-layout—top-left* para el nodo *r1c1*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Del mismo modo, agregue *my-custom-layout—top-right* para *r1c2* y, *my-custom-layout—bottom* para el nodo *r2c1*.

   >[!NOTE]
   >Estas clases personalizadas se utilizarán en css para definir la anchura y la altura de estas cuadrículas adaptables.

   >[!NOTE]
   >Puede agregar o quitar las cuadrículas adaptables en función del número total de cuadrículas que desee. En este ejemplo, se muestran 2 cuadrículas en la primera fila y 1 cuadrícula en la segunda fila, por lo que hay un total de 3 cuadrículas adaptables (r1c1, r1c2, r2c1).

1. Copie `/libs/settings/wcm/designs/screens` en `/apps/settings/wcm/designs/` y cambie el nombre del diseño copiado como **custom-template-designs**.

1. Vaya a `/apps/settings/wcm/designs/custom-template-designs` y actualice la propiedad *jcr:title* de **custom-template-designs** a **custom template-design**.

1. Vaya a `/apps/settings/wcm/designs/custom-template-designs` y cree un archivo static.css.

1. Copie el contenido en el archivo `static.css`:

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

1. Vaya a `/apps/<project>/templates/my-custom-layout/jcr:content` y actualice la propiedad *cq:designPath* a `/apps/settings/wcm/designs/customtemplate-designs` para cargar los estilos configurados en static.css

   >[!NOTE]
   >Se recomienda escribir todos los estilos en lugar de copiarlos o pegarlos, lo que puede provocar que los espacios en blanco produzcan problemas de estilo css.

## Visualización del resultado {#viewing-result}

Siga los pasos a continuación para utilizar la plantilla personalizada anterior en su proyecto de AEM Screens:

1. Vaya al proyecto Pantallas que ha creado en el paso (1) y seleccione la carpeta **Canales**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Haga clic en **Crear** en la barra de acciones y seleccione la plantilla **Left20-LandscapeHD3Zone** en el asistente **Crear**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Una vez creado un canal con la plantilla personalizada, puede agregar recursos a su canal desde el editor. La siguiente previsualización muestra las imágenes en una plantilla personalizada.

   ![image](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserción de una imagen como capa de fondo {#inserting-image}

Puede insertar una imagen como capa de fondo en el diseño:

Puede ajustar la regla CSS para utilizar lo que se denomina &quot;uri-datos&quot; y poner directamente en línea la imagen (codificada en Base64) en el archivo CSS, creado en (paso 13), *static.css*.

Esto se hace de la siguiente manera:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

O bien, puede seguir los pasos a continuación:

1. Asegúrese de que la imagen esté incluida de alguna manera en la configuración sin conexión del canal
1. Utilice un vínculo directo a la imagen en el CSS anterior, en lugar de la variante &quot;data-uri&quot;


## Actualizando color de fondo {#updating-color}

Para cambiar el color de fondo, agregue el siguiente código al archivo xml (paso 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



