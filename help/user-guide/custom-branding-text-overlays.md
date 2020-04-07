---
title: Aplicación de personalización de marca y estilo para superposiciones de texto
seo-title: Aplicación de personalización de marca y estilo para superposiciones de texto
description: Siga esta página para conocer cómo aplicar la personalización de la marca y el estilo a las superposiciones de texto.
seo-description: Siga esta página para conocer cómo aplicar la personalización de la marca y el estilo a las superposiciones de texto.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: a475e373b0717b69610cb78907542f1da9ad8992

---


# Estilo y personalización de marca para superposiciones de texto {#creating-custom-branding-styling}

Siga esta página para aprender a aplicar personalización de marca y estilo para las superposiciones de texto aplicadas a los recursos en un canal de pantallas.

## Creación de personalización de marca y estilo para superposiciones de texto {#steps-custom-branding}

Siga los pasos a continuación para crear una marca y un estilo personalizados para las superposiciones de texto:

1. Creación de un proyecto de AEM Screens. En este ejemplo se muestra la funcionalidad creando un proyecto llamado **customstyle** y un canal titulado **DemoBrand** , como se muestra en la siguiente figura.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. En el editor, arrastre y suelte una imagen y agregue una superposición de texto al recurso.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para obtener información sobre cómo agregar una superposición de texto al recurso en un editor de canal, consulte [Superposición](/help/user-guide/text-overlay.md)de texto.

1. Vaya a CRXDE Lite desde su instancia de AEM —> Herramientas —> **CRXDE Lite**.

1. Debe crear un diseño personalizado en `/apps/settings/wcm/designs/<your-project>/`, por ejemplo, en este caso, navegue hasta `/apps/settings/wcm/designs/customstyle/`

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Cree el archivo *static.css* y defina las siguientes reglas css. También se muestra como ejemplo en la figura debajo de las reglas css.

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

1. Copie la ruta de acceso al proyecto; en este caso, la ruta será `/apps/settings/wcm/designs/customstyle`.

1. Vaya al canal titulado como **DemoBrand** (creado en el paso 1) y haga clic en **Propiedades** en la barra de acciones después de seleccionar el canal.

1. Vaya a la ficha **Avanzado** y marque el campo **Diseño** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >De forma predeterminada, el campo **Diseño** muestra la ruta que apunta a los diseños en la carpeta libs.

1. Actualice el campo **Diseño** con la ruta a la carpeta del proyecto. En este caso, lo será, `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Haga clic en **Guardar y cerrar** para actualizar la ruta de diseño.

>[!IMPORTANT]
> Tiene la opción de superponer las plantillas de Pantallas existentes para insertar sus propios diseños de forma predeterminada o crear su propia plantilla por completo. Consulte los pasos a continuación para obtener más detalles.

1. Para superponer las plantillas de pantallas existentes para insertar sus propios diseños de forma predeterminada:

   1. Superponer `/libs/screens/core/templates/sequencechannel` en `/apps/screens/core/templates/sequencechannel`.
   1. Modifique la propiedad *cq:designPath* en `/apps/screens/core/templates/sequencechannel/jcr:content` para que señale al nuevo diseño.

1. Para crear su propia plantilla por completo:
   1. Copiar `/libs/screens/core/templates/sequencechannel` a `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique la propiedad *cq:designPath* en `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para que señale al nuevo diseño.


### Actualización de ACL {#updating-acls}

Debe actualizar las ACL de estos diseños para que el reproductor pueda descargarlos.

1. Vaya a useradmin, elija la ruta de diseño personalizada `screens-<project>-devices group` y asígnele permiso de lectura.

1. Proporcione permisos de lectura y modificación de `screens-<project>-administrators` grupos a esta ruta.

## Visualización del resultado {#viewing-the-result}

Una vez que haya completado los pasos anteriores, puede actualizar el archivo *statis.css* desde **CRXDE Lite** y, en consecuencia, vista la actualización a la superposición de texto que ya se ha agregado al recurso.

Siga los pasos a continuación para vista del diseño actualizado a la superposición de texto:

1. Vaya a su proyecto de AEM Screens titulado como **custom style** —> **Canales** —> **DemoBrand**. Select the channel and click **Edit** from the action bar to open the editor.

1. Dado que ahora ha agregado el diseño al campo **Diseños** , como se mencionó anteriormente, haga clic en **Previsualización** para vista del estilo actual de la imagen con una superposición de texto.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Vaya al archivo *static.css* en CRXDE Lite y agregue la fuente como, por ejemplo, `font-family: "Lucida Console", Courier, monospace;` a este archivo, como se muestra a continuación.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Una vez que guarde los cambios y vuelva a cargar la previsualización, verá una actualización de la fuente de superposición de texto, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Además, puede eliminar los dos últimos bloques de código del archivo *static.css* para eliminar el estilo en caja alrededor de la superposición de texto.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Se vista el cambio actualizado en la previsualización donde se agrega la superposición de texto a la imagen.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

En relación con el tutorial, ahora puede actualizar la marca y el estilo personalizado para las superposiciones de texto agregadas a los recursos.









