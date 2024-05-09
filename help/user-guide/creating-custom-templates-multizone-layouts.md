---
title: Crear plantillas personalizadas en diseños de varias zonas
description: Obtenga información sobre la creación de plantillas personalizadas en diseños de varias zonas para AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 1%

---

# Crear plantillas personalizadas para diseños de varias zonas {#creating-custom-templates-multizone}

Esta página muestra cómo puede crear una plantilla personalizada para un diseño de varias zonas.

## Consideraciones importantes {#considerations}

Hay dos consideraciones importantes que debe tener en cuenta antes de crear una plantilla personalizada en un diseño de varias zonas:

1. **Tamaño de píxel fijo o porcentajes**:

   Decida si desea utilizar un tamaño de píxel fijo para diferentes zonas del diseño personalizado o si desea crear un diseño personalizado utilizando porcentajes.

   >[!NOTE]
   >La ventaja de utilizar percentage para establecer zonas para el diseño personalizado permite reutilizar la plantilla en varios tamaños de pantalla.

1. **Convención de nomenclatura**:

   Ayuda a comprender cómo crear plantillas de varias zonas personalizadas para utilizarlas en un proyecto de AEM Screens. Pero primero, debe comprender el lenguaje de las plantillas que desea crear.

   | **Nombre del diseño** | **Descripción** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | Diseño horizontal de tres zonas que permite crear tres zonas:<br>* Zona 1 como 20% de la pantalla horizontal y vertical desde la izquierda<br>* Zona 2 como 80% de la pantalla horizontal y 20% de la pantalla vertical justificada a la derecha<br>* Zona 3 como 100% de la pantalla horizontal y 80% de la pantalla vertical. La relación de aspecto es de 16:9 |
   | `Upper20-PortraitHD2Zone` | Una plantilla vertical de dos zonas que cubre el 20% de la pantalla desde la parte superior, con una relación de aspecto de 16:9 |
   | `Right20-LandscapeSD3Zone` | Una plantilla de tres zonas que cubre el 20 % de la pantalla desde la derecha, con una relación de aspecto de 4:3 |

   >[!IMPORTANT]
   >Es posible que las zonas definidas dentro del diseño personalizado no coincidan con la relación de aspecto general de todo el diseño. La convención de nombres que se sigue en este documento especifica la proporción de aspecto del diseño personalizado en su conjunto.

## Ejemplo de caso de uso `Left20-LandscapeHD3Zone` Diseño {#custom-template-one}

Siga la sección siguiente para crear una plantilla personalizada *`Left20-LandscapeHD3Zone`* con la siguiente configuración:

* **`Left20`** - La zona superior a la izquierda cubriendo el 20% del tamaño de pantalla horizontal y vertical.
* **`Landscape`** - La orientación de la pantalla.
* **`HD`** - La relación de aspecto es de 16:9.
* **`3Zone`** - Tres zonas de la pantalla.

## Representación visual del diseño de varias zonas {#multi-layout-visual-one}

El `Left20-LandscapeHD3Zone` Diseño permite crear el siguiente diseño de varias zonas en el proyecto:

![imagen](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Creación de un `Left20-LandscapeHD3Zone` Diseño {#landscape-layout-one}

Siga los pasos a continuación para crear una `Left20-LandscapeHD3Zone` Diseño para un proyecto de AEM Screens.

1. Cree un proyecto de AEM Screens titulado como **`customtemplate`**.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Vaya a **CRXDE Lite** AEM en la instancia de su > Herramientas > **CRXDE Lite**.

1. Cree una carpeta en **apps** con título **`customtemplate`**. Del mismo modo, cree otra carpeta con el título **plantilla** bajo **`customtemplate`**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Clic **Guardar todo** en la barra de acciones de CRXDE Lite cada vez que cree, edite o copie contenido en cualquiera de los nodos. De lo contrario, no podrá confirmar las actualizaciones.

1. Copie la plantilla de la barra izquierda de `/libs/screens/core/templates/splitscreenchannel/lbar-left` hasta `/apps/customtemplate/template`.

1. Cambie el nombre del copiado **lbar-left** (`/apps/customtemplate/template`) a **my-custom-layout**.
   ![imagen](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Vaya a `/apps/customtemplate/template/my-custom-layout` y actualice las propiedades **`jcr:description`** hasta *Plantilla para`Left20-LandscapeHD3Zone`* y **`jcr:title`** hasta *`Left20-LandscapeHD3Zone`*.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Vaya a **`offline-config`** nodo de `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` y actualice el **`jcr:title`** hasta *`Left20-LandscapeHD3Zone`*.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Vaya a *`jcr:content`* propiedad de **my-custom-template** de `/apps/customtemplate/template/my-custom-layout/jcr:content` y actualice el **`cq:cssClass`** propiedad para que pueda utilizar **aem-Layout my-custom-layout**.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En referencia al paso (4) en el que ha copiado la plantilla de la barra izquierda, puede ver tres cuadrículas adaptables en `my-custom-layout/jcr:content`. Agregue una clase css personalizada a cada una de las cuadrículas adaptables de la *`cq:cssClass`* , por ejemplo, *my-custom-layout-top-left* para *r1c1* nodo.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Del mismo modo, agregue *my-custom-layout-top-right* para *r1c2* y *my-custom-layout-bottom* para *r2c1* nodo.

   >[!NOTE]
   >Estas clases personalizadas se utilizan en el CSS para establecer la anchura y la altura de estas cuadrículas adaptables.

   >[!NOTE]
   >Puede agregar o quitar las cuadrículas adaptables en función del número total de cuadrículas que desee. En este ejemplo, se muestran dos cuadrículas en la primera fila y una cuadrícula en la segunda fila, por lo que hay un total de tres cuadrículas adaptables (r1c1, r1c2, r2c1).

1. Copiar `/libs/settings/wcm/designs/screens` hasta `/apps/settings/wcm/designs/` y cambie el nombre del diseño copiado por **custom-template-designs**.

1. Vaya a `/apps/settings/wcm/designs/custom-template-designs` y actualice la propiedad *`jcr:title`* de **custom-template-designs** hasta **customtemplate-design**.

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

1. Vaya a `/apps/<project>/templates/my-custom-layout/jcr:content` y actualice la propiedad *`cq:designPath`* hasta `/apps/settings/wcm/designs/customtemplate-designs` para poder cargar los estilos configurados en static.css.

   >[!NOTE]
   >Escriba todos los estilos en lugar de copiarlos o pegarlos, lo que puede generar espacios en blanco que producen problemas de estilo css.

## Visualización del resultado {#viewing-result}

Siga los pasos a continuación para utilizar la plantilla personalizada anterior en su proyecto de AEM Screens:

1. Vaya al proyecto de Screens que ha creado en el paso (1) y haga clic en **Canales** carpeta.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Clic **Crear** en la barra de acciones y haga clic en la plantilla **`Left20-LandscapeHD3Zone`** desde el **Crear** asistente.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Después de crear un canal con la plantilla personalizada, puede agregar recursos al canal desde el editor. La siguiente vista previa muestra las imágenes en una plantilla personalizada.

   ![imagen](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserción de una imagen como capa de fondo {#inserting-image}

Puede insertar una imagen como capa de fondo en el diseño:

Puede ajustar la regla CSS para utilizar &quot;data-uri&quot; y directamente en línea la imagen (`Base64` codificado) en el archivo CSS que ha creado en (paso 13), *static.css*.

Esta disposición se hace de la siguiente manera:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

O bien, puede seguir los pasos a continuación:

1. Asegúrese de que la imagen se incluya de alguna manera en la configuración sin conexión del canal.
1. Utilice un vínculo directo a la imagen en el CSS anterior, en lugar de la variante &quot;uri de datos&quot;.


## Actualizando color de fondo {#updating-color}

Para cambiar el color de fondo, agregue el siguiente código al archivo xml (paso 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
