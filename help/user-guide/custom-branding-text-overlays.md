---
title: Aplicación de personalización de marca y estilo para superposiciones de texto
seo-title: Aplicación de personalización de marca y estilo para superposiciones de texto
description: Siga esta página para aprender a aplicar personalización de marca y estilo para las superposiciones de texto.
seo-description: Siga esta página para aprender a aplicar personalización de marca y estilo para las superposiciones de texto.
contentOwner: Jyotika Syal
feature: Desarrollo de pantallas
role: Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---


# Personalizar la marca y el estilo para las superposiciones de texto {#creating-custom-branding-styling}

Siga esta página para aprender a aplicar personalización de marca y estilo para las superposiciones de texto aplicadas a sus recursos en un canal de AEM Screens.

## Creación de diseños y marcas personalizados para superposiciones de texto {#steps-custom-branding}

Siga los pasos a continuación para crear una marca y un estilo personalizados para las superposiciones de texto:

1. Cree un proyecto de AEM Screens. En este ejemplo se muestra la funcionalidad creando un proyecto denominado **customstyle** y un canal denominado **DemoBrand** , como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Desde el editor, arrastre y suelte una imagen y agregue superposición de texto al recurso.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para obtener información sobre cómo añadir una superposición de texto al recurso en un editor de canales, consulte [Superposición de texto](/help/user-guide/text-overlay.md).

1. Vaya al CRXDE Lite desde la instancia de AEM —> herramientas —> **CRXDE Lite**.

1. Debe crear un diseño personalizado en `/apps/settings/wcm/designs/<your-project>/`, por ejemplo, en este caso, vaya a `/apps/settings/wcm/designs/customstyle/`

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Cree el archivo *static.css* y establezca las siguientes reglas css. También se muestra como ejemplo en la figura debajo de las reglas css.

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copie la ruta al proyecto; en este caso, la ruta será `/apps/settings/wcm/designs/customstyle`.

1. Vaya al canal denominado **DemoBrand** (creado en el paso 1) y haga clic en **Properties** en la barra de acciones después de seleccionar el canal.

1. Vaya a la pestaña **Advanced** y marque el campo **Design**.
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >De forma predeterminada, el campo **Design** muestra la ruta que señala a los diseños en la carpeta de bibliotecas.

1. Actualice el campo **Design** con la ruta a la carpeta del proyecto. En este caso, será `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Haga clic en **Guardar y cerrar** para actualizar la ruta de diseño.

   >[!IMPORTANT]
   >Tiene la opción de superponer las plantillas Screens existentes para insertar sus propios diseños de forma predeterminada o crear su propia plantilla por completo. Consulte los pasos a continuación para obtener más información.

1. Para superponer las plantillas de Screens existentes para insertar sus propios diseños de forma predeterminada:

   1. Superponga `/libs/screens/core/templates/sequencechannel` en `/apps/screens/core/templates/sequencechannel`.
   1. Modifique la propiedad *cq:designPath* en `/apps/screens/core/templates/sequencechannel/jcr:content` para que apunte al nuevo diseño.

1. Para crear su propia plantilla por completo:
   1. Copie `/libs/screens/core/templates/sequencechannel` en `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique la propiedad *cq:designPath* en `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para que apunte al nuevo diseño.


### Actualización de ACL {#updating-acls}

Debe actualizar las ACL para estos diseños para que el reproductor pueda descargarlos.

1. Vaya al administrador de usuarios, elija `screens-<project>-devices group` y asígnele permiso de lectura a la ruta de diseño personalizada.

1. Proporcione `screens-<project>-administrators` permisos de lectura y modificación del grupo a esta ruta.

## Visualización del resultado {#viewing-the-result}

Una vez completados los pasos anteriores, puede actualizar el archivo *statis.css* desde **CRXDE Lite** y, en consecuencia, ver la actualización de la superposición de texto que ya se ha agregado al recurso.

Siga los pasos a continuación para ver el diseño actualizado de la superposición de texto:

1. Vaya al proyecto de AEM Screens titulado como **customstyle** —> **Channels** —> **DemoBrand**. Seleccione el canal y haga clic en **Edit** en la barra de acciones para abrir el editor.

1. Como ahora ha añadido el diseño al campo **Diseños**, como se ha mencionado anteriormente, haga clic en **Vista previa** para ver el estilo actual de la imagen con superposición de texto.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Vaya al archivo *static.css* en el CRXDE Lite y añada la fuente como `font-family: "Lucida Console", Courier, monospace;` a este archivo, como se muestra a continuación.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Una vez que guarde los cambios y vuelva a cargar la vista previa, verá una actualización de la fuente de superposición de texto, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Además, puede quitar los dos últimos bloques de código del archivo *static.css* para eliminar el estilo en caja que rodea la superposición de texto.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Verá el cambio actualizado en la vista previa, donde la superposición de texto se agrega a la imagen.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ya está listo para actualizar su marca y el estilo personalizado para las superposiciones de texto agregadas a sus recursos.









