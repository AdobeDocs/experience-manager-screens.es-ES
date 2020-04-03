---
title: Aplicación de personalización de marca y estilo para superposiciones de texto
seo-title: Aplicación de personalización de marca y estilo para superposiciones de texto
description: Siga esta página para conocer cómo aplicar la personalización de la marca y el estilo a las superposiciones de texto.
seo-description: Siga esta página para conocer cómo aplicar la personalización de la marca y el estilo a las superposiciones de texto.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# Estilo y personalización de marca para superposiciones de texto {#creating-custom-branding-styling}

Siga esta página para conocer cómo aplicar la personalización de la marca y el estilo a las superposiciones de texto.

## Creación de personalización de marca y estilo para superposiciones de texto {#steps-custom-branding}

Siga los pasos a continuación para crear una marca y un estilo personalizados para las superposiciones de texto:

1. Cree un proyecto de AEM Screens con el título de **estilo** personalizado y un canal con el título **DemoBrand**, como se muestra en la ilustración siguiente.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. En el editor, arrastre y suelte una imagen y agregue una superposición de texto al recurso.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para obtener información sobre cómo agregar una superposición de texto al recurso en un editor de canal, consulte [Superposición](/help/user-guide/text-overlay.md)de texto.

1. Vaya a CRXDE Lite desde su instancia de AEM —> Herramientas —> **CRXDE Lite**.

1. En este caso, debe crear un diseño personalizado `/apps/settings/wcm/designs/<your-project>/`, por ejemplo

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Vaya al archivo static.css y establezca las siguientes reglas css. También se muestra en la figura siguiente.

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copie la ruta de acceso al proyecto; en este caso, la ruta será `/apps/settings/wcm/designs/customstyle`.

1. Vaya al canal titulado como **DemoBrand** (creado en step(1)) y haga clic en **Propiedades** en la barra de acciones después de seleccionar el canal.

1. Vaya a la ficha **Avanzado** y marque el campo **Diseño** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >De forma predeterminada, el campo **Diseño** muestra la ruta que apunta a los diseños en la carpeta libs.

1. Actualice el campo **Diseño** con la ruta a la carpeta del proyecto. En este caso, lo será, `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Haga clic en **Guardar y cerrar** para actualizar la ruta de diseño.


## Visualización del resultado {#viewing-the-result}

Una vez que haya completado los pasos anteriores, puede actualizar el archivo *statis.css* desde **CRXDE Lite** y, en consecuencia, vista la actualización a la presentación de texto agregada al recurso.

Siga los pasos a continuación para vista del diseño actualizado al diseño de texto:

1. Vaya a su proyecto de AEM Screens titulado como estilo **** personalizado y a un canal titulado como **DemoBrand** y haga clic en **Editar** en la barra de acciones para abrir el editor.

1. Dado que ahora ha agregado el diseño al campo **Diseños** , como se mencionó anteriormente, haga clic en **Previsualización** para vista del estilo actual de la imagen con una superposición de texto.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Vaya al archivo static.css en CRXDE Lite, por ejemplo, agregue la fuente.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Una vez que guarde los cambios y vuelva a cargar la previsualización, verá una actualización de la fuente de superposición de texto, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Además, puede quitar los dos últimos bloques de código del archivo static.css para eliminar el estilo en caja alrededor de la superposición de texto.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. vista el cambio actualizado en la previsualización donde se agrega la superposición de texto a la imagen, como se muestra a continuación.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Por lo tanto, siguiendo los pasos de las secciones anteriores, puede actualizar la marca y el estilo personalizado para las superposiciones de texto agregadas a sus recursos.









