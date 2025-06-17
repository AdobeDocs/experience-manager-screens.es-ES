---
title: Aplicación de estilo y marca personalizados a las superposiciones de texto
description: Aprenda a aplicar una marca y un estilo personalizados a las superposiciones de texto aplicadas a los recursos de un canal de AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 2%

---

# Estilo y marca personalizados para superposiciones de texto {#creating-custom-branding-styling}

Aprenda a aplicar una marca y un estilo personalizados a las superposiciones de texto aplicadas a los recursos en un canal de AEM Screens.

## Creación de marca y estilo personalizados para superposiciones de texto {#steps-custom-branding}

Siga los pasos a continuación para crear una personalización de marca y estilo para las superposiciones de texto:

1. Cree un proyecto de AEM Screens. Este ejemplo muestra la funcionalidad creando un proyecto denominado **`customstyle`** y un canal denominado **DemoBrand**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Desde el editor, arrastre y suelte una imagen y agregue una superposición de texto al recurso.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para obtener información sobre cómo agregar una superposición de texto al recurso en un editor de canales, consulte [Superposición de texto](/help/user-guide/text-overlay.md).

1. Vaya a CRXDE Lite desde su instancia de AEM > Herramientas > **CRXDE Lite**.

1. Crear un diseño personalizado en `/apps/settings/wcm/designs/<your-project>/`; por ejemplo, en este caso, vaya a `/apps/settings/wcm/designs/customstyle/`

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Cree un archivo *static.css* y establezca las siguientes reglas css. También se muestra como ejemplo en la figura debajo de las reglas css.

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

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copie la ruta de acceso a su proyecto; en este caso, la ruta de acceso es `/apps/settings/wcm/designs/customstyle`.

1. Vaya al canal con el título **DemoBrand** (creado en el paso ) y haga clic en **Propiedades** de la barra de acciones después de seleccionar el canal.

1. Vaya a la pestaña **Avanzado** y marque el campo **Diseño**.
   ![imagen](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >De forma predeterminada, el campo **Diseño** muestra la ruta que señala a los diseños de la carpeta libs.

1. Actualice el campo **Diseño** con la ruta a la carpeta del proyecto. En este caso, es `/apps/settings/wcm/designs/customstyle`.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Haga clic en **Guardar y cerrar** para actualizar la ruta de diseño.

   >[!IMPORTANT]
   >Opcionalmente, puede superponer las plantillas de Screens existentes para insertar sus propios diseños de forma predeterminada o crear su propia plantilla por completo. Consulte los pasos a continuación para obtener más información.

1. Para superponer las plantillas de Screens existentes e insertar sus propios diseños de forma predeterminada:

   1. Superposición `/libs/screens/core/templates/sequencechannel` en `/apps/screens/core/templates/sequencechannel`.
   1. Modifique la propiedad *`cq:designPath`* en `/apps/screens/core/templates/sequencechannel/jcr:content` para que apunte al nuevo diseño.

1. Para crear su propia plantilla:
   1. Copie `/libs/screens/core/templates/sequencechannel` en `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique la propiedad *`cq:designPath`* en `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para que apunte al nuevo diseño.


### Actualización de ACL {#updating-acls}

Actualice las ACL de estos diseños para que el reproductor pueda descargarlos.

1. Vaya a la administración de usuarios, elija `screens-<project>-devices group` y asígnele permiso de lectura en la ruta de diseño personalizada.

1. Proporcione permisos de lectura y modificación del grupo `screens-<project>-administrators` a esta ruta.

## Visualización del resultado {#viewing-the-result}

Cuando haya completado los pasos anteriores, puede actualizar su archivo *stat.css* desde **CRXDE Lite** y, por lo tanto, ver la actualización de la superposición de texto que ya se ha agregado al recurso.

Siga los pasos a continuación para ver el diseño actualizado en la superposición de texto:

1. Vaya a su proyecto de AEM Screens titulado **`customstyle`** > **Canales** > **DemoBrand**. Haga clic en el canal y luego en **Editar** en la barra de acciones.

1. Dado que ahora ha agregado el diseño a su campo **Diseños**, como se mencionó anteriormente, haga clic en **Vista previa** para ver el estilo actual en la imagen con superposición de texto.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Vaya al archivo *static.css* en CRXDE Lite y agregue la fuente como `font-family: "Lucida Console", Courier, monospace;` a este archivo, como se muestra a continuación.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Cuando guarde los cambios y vuelva a cargar la vista previa, verá una actualización de la fuente de superposición de texto, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Además, puede quitar los dos últimos bloques de código del archivo *static.css* para quitar el estilo en forma de caja alrededor de la superposición de texto.

![imagen](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Vea el cambio actualizado en la vista previa donde se agrega la superposición de texto a la imagen.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ahora está listo para actualizar su marca y su estilo personalizado para las superposiciones de texto agregadas a sus recursos.
