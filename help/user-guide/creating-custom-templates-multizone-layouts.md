---
title: Creación de plantillas personalizadas en diseños de varias zonas
seo-title: Creación de plantillas personalizadas en diseños de varias zonas
description: Siga esta página para obtener información sobre la creación de plantillas personalizadas en diseños de varias zonas.
seo-description: Siga esta página para obtener información sobre la creación de plantillas personalizadas en diseños de varias zonas.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 23208ed9e4e293cfcec65305918f35573c20cc02

---


# Creación de plantillas personalizadas en diseños de varias zonas {#creating-custom-templates-multizone}

Esta página muestra cómo se puede crear una plantilla personalizada en un diseño de varias zonas.

## Convención de nombres {#name-terms}

Antes de comprender cómo crear plantillas multizona personalizadas para utilizarlas en un proyecto de AEM Screens, se recomienda conocer la versión de las plantillas que desea crear.

| **Nombre del diseño** | **Descripción** |
|---|---|
| Left20-LandscapeHD3Zone | Se refiere a un diseño horizontal de 3 zonas que permite crear 3 zonas con una zona 1 del 20 % de la pantalla horizontal y vertical desde la izquierda, una zona 2 del 80 % de la pantalla horizontal y un 20 % de la pantalla vertical hacia la derecha, una zona 3 del 100 % de la pantalla horizontal y un 80 % de la pantalla vertical con una proporción de aspecto de 16:9 |
| Upper20-PortraitHD2Zone | Se refiere a una plantilla vertical de 2 zonas que cubre el 20 % de la pantalla desde la parte superior, con una proporción de aspecto de 16:9 |
| Right20-LandscapeSD3Zone | Se refiere a una plantilla de 3 zonas que cubre el 20 % de la pantalla desde la derecha, con una proporción de aspecto de 4:3 |

##  Casos de uso de ejemplo {#example-use-cases}

## Diseño Left20-LandscapeHD3Zone {#custom-template-one}

Siga la sección siguiente para crear una plantilla personalizada *Left20-LandscapeHD3Zone* con la siguiente configuración:

* **Left20** hace referencia a la zona superior de la izquierda que cubre el 20% del tamaño de pantalla horizontal y vertical.
* **Horizontal** hace referencia a la orientación de la pantalla
* **HD** hace referencia a la proporción de aspecto como 16:9
* **3Zone** se refiere a tres zonas de la pantalla

## Representación visual del diseño MultiZone {#multi-layout-visual-one}

El diseño Left20-LandscapeHD3Zone permite crear el siguiente diseño multizona en el proyecto:

![image](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

## Creación de un diseño Left20-LandscapeHD3Zone {#landscape-layout-one}

Siga los pasos a continuación para crear un diseño Left20-LandscapeHD3Zone para un proyecto de AEM Screens:

1. Cree un proyecto de AEM Screens titulado como plantilla **personalizada**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Vaya a **CRXDE Lite** desde su instancia de AEM —> Herramientas —> **CRXDE Lite**.

1. Cree una carpeta en **aplicaciones** con el título de plantilla **personalizada**. Del mismo modo, cree otra carpeta titulada como **plantilla** en plantilla **personalizada**, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > Se recomienda hacer clic en **Guardar todo** desde la barra de acciones de CRXDE Lite cada vez que cree, edite o copie contenido en cualquiera de los nodos; de lo contrario, no podrá confirmar las actualizaciones.

1. Copie la plantilla de la barra izquierda de `/libs/screens/core/templates/splitscreenchannel/lbar-left` a `/apps/customtemplate/template`.

1. Cambie el nombre de la **barra izquierda** copiada (`/apps/customtemplate/template`) a **mi diseño**personalizado.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Vaya a `/apps/customtemplate/template/my-custom-layout` las propiedades **jcr:description** y actualícelas en *Template para Left20-LandscapeHD3Zone* y **jcr:title** en *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Vaya al nodo **offline-config** desde `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` y actualice **jcr:title** a *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Vaya a la propiedad *jcr:content* de **my-custom-template** desde `/apps/customtemplate/template/my-custom-layout/jcr:content` y actualice la propiedad **cq:cssClass** a **aem-Layout my-custom-layout**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En relación con el paso (4), en el que ha copiado la plantilla de la barra izquierda, verá 3 cuadrículas adaptables debajo de `my-custom-layout/jcr:content`. Agregue una clase css personalizada a cada una de las cuadrículas interactivas de la propiedad *cq:cssClass* ; por ejemplo, *my-custom-layout (superior izquierda* para el nodo *r1c1* ).

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Del mismo modo, agregue *my-custom-layout—top-right* para *r1c2* y, *my-custom-layout—bottom* para el nodo *r2c1* .

   >[!NOTE]
   >Estas clases personalizadas se utilizarán en css para definir la anchura y la altura de estas cuadrículas adaptables.

   >[!NOTE]
   > Puede agregar o quitar las cuadrículas adaptables en función del número total de cuadrículas que desee. En este ejemplo, se muestran 2 cuadrículas en la primera fila y 1 cuadrícula en la segunda fila, por lo que hay un total de 3 cuadrículas adaptables (r1c1, r1c2, r2c1).

1. Copie `/libs/settings/wcm/designs/screens` en el diseño copiado `/apps/settings/wcm/designs/` y cámbiele el nombre como diseños **de plantilla** personalizados.

1. Navegue hasta `/apps/settings/wcm/designs/custom-template-designs` y actualice la propiedad *jcr:title* de diseños **de plantilla** personalizados para **personalizar el diseño** de plantilla.

1. Vaya a `/apps/settings/wcm/designs/custom-template-designs` y cree un archivo static.css.

1. Copie el contenido en el archivo static.css:

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
   > Puede actualizar los porcentajes para que coincidan con los requisitos de la plantilla personalizada.

1. Vaya a `/apps/<project>/templates/my-custom-layout/jcr:content` la propiedad *cq:designPath* y actualícela para `/apps/settings/wcm/designs/customtemplate-designs` cargar los estilos configurados en static.css

   >[!NOTE]
   > Se recomienda escribir todos los estilos en lugar de copiarlos o pegarlos, lo que puede provocar que los espacios en blanco produzcan problemas de estilo css.

## Visualización del resultado {#viewing-result}

Siga los pasos a continuación para utilizar la plantilla personalizada anterior en el proyecto de AEM Screens:

1. Vaya al proyecto Pantallas que ha creado en el paso (1) y seleccione la carpeta **Canales** .

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Haga clic en **Crear** en la barra de acciones y seleccione la plantilla **Left20-LandscapeHD3Zone** en el asistente **Crear** .

1. Una vez creado un canal con la plantilla personalizada, puede agregar recursos al canal desde el editor.

## Inserción de una imagen como capa de fondo {#inserting-image}

Puede insertar una imagen como capa de fondo en el diseño:

Puede ajustar la regla CSS para utilizar lo que se denomina &quot;uri-datos&quot; y poner directamente en línea la imagen (con codificación Base64) en el archivo CSS.

Esto se hace de la siguiente manera:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

O bien, puede seguir los pasos a continuación:

1. Asegúrese de que la imagen esté incluida de alguna manera en la configuración sin conexión del canal
1. Utilice un vínculo directo a la imagen en el CSS anterior, en lugar de la variante &quot;data-uri&quot;


## Actualización del color de fondo {#updating-color}

Para cambiar el color de fondo, agregue el siguiente código al archivo xml:

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



