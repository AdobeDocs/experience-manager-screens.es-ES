---
title: Aplicación de estilo y marca personalizados a las superposiciones de texto
description: Aprenda a aplicar una marca y un estilo personalizados a las superposiciones de texto aplicadas a los recursos de un canal de AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 2%

---

# Estilo y marca personalizados para superposiciones de texto {#creating-custom-branding-styling}

Aprenda a aplicar una marca y un estilo personalizados a las superposiciones de texto aplicadas a los recursos en un canal de AEM Screens.

## Creación de marca y estilo personalizados para superposiciones de texto {#steps-custom-branding}

Siga los pasos a continuación para crear una personalización de marca y estilo para las superposiciones de texto:

1. Cree un proyecto de AEM Screens. Este ejemplo muestra la funcionalidad creando un proyecto denominado **`customstyle`** y un canal titulado **DemoBrand**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Desde el editor, arrastre y suelte una imagen y agregue una superposición de texto al recurso.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para obtener información sobre cómo agregar una superposición de texto al recurso en un editor de canales, consulte [Superposición de texto](/help/user-guide/text-overlay.md).

1. Vaya al CRXDE Lite AEM desde la instancia de la > Herramientas > **CRXDE Lite**.

1. Creación de un diseño personalizado en `/apps/settings/wcm/designs/<your-project>/`, por ejemplo, en este caso, vaya a `/apps/settings/wcm/designs/customstyle/`

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crear un *static.css* y establezca las siguientes reglas css. También se muestra como ejemplo en la figura debajo de las reglas css.

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

1. Copie la ruta al proyecto; en este caso, la ruta es `/apps/settings/wcm/designs/customstyle`.

1. Vaya al canal con el título **DemoBrand** (creado en el paso(1)) y haga clic en **Propiedades** en la barra de acciones después de seleccionar el canal.

1. Vaya a **Avanzadas** y marque la **Diseño** field.
   ![imagen](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >De forma predeterminada, la variable **Diseño** muestra la ruta que señala a los diseños de la carpeta libs.

1. Actualice el **Diseño** con la ruta a la carpeta del proyecto. En este caso, es `/apps/settings/wcm/designs/customstyle`.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clic **Guardar y cerrar** para actualizar la ruta de diseño.

   >[!IMPORTANT]
   >Si lo desea, puede superponer las plantillas de Screens existentes para insertar sus propios diseños de forma predeterminada o crear su propia plantilla por completo. Consulte los pasos a continuación para obtener más información.

1. Para superponer las plantillas de Screens existentes e insertar sus propios diseños de forma predeterminada:

   1. Superposición `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modifique la *`cq:designPath`* propiedad en `/apps/screens/core/templates/sequencechannel/jcr:content` para que apunte al nuevo diseño.

1. Para crear su propia plantilla:
   1. Copie `/libs/screens/core/templates/sequencechannel` en `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique la *`cq:designPath`* propiedad en `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para que apunte al nuevo diseño.


### Actualización de ACL {#updating-acls}

Actualice las ACL de estos diseños para que el reproductor pueda descargarlos.

1. Vaya al administrador de usuarios y elija `screens-<project>-devices group` y conceda permiso de lectura a la ruta de diseño personalizada.

1. Proporcionar `screens-<project>-administrators` permisos de lectura y modificación de grupo para esta ruta.

## Visualización del resultado {#viewing-the-result}

Cuando haya completado los pasos anteriores, puede actualizar su *stats.css* archivo de **CRXDE Lite** y, por lo tanto, vea la actualización de la superposición de texto que ya se ha agregado al recurso.

Siga los pasos a continuación para ver el diseño actualizado en la superposición de texto:

1. Vaya al proyecto de AEM Screens titulado como **`customstyle`** > **Canales** > **DemoBrand**. Haga clic en el canal y en **Editar** de la barra de acciones.

1. Dado que ahora ha añadido el diseño a su **Diseños** , como se ha mencionado anteriormente, haga clic en **Previsualizar** para ver el estilo actual en la imagen con superposición de texto.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navegue hasta su *static.css* en el CRXDE Lite y agregue la fuente, como, `font-family: "Lucida Console", Courier, monospace;` a este archivo, como se muestra a continuación.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Cuando guarde los cambios y vuelva a cargar la vista previa, verá una actualización de la fuente de superposición de texto, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Además, puede eliminar los dos últimos bloques de código de la *static.css* para quitar el estilo de la caja alrededor de la superposición de texto.

![imagen](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Vea el cambio actualizado en la vista previa donde se agrega la superposición de texto a la imagen.

   ![imagen](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ahora está listo para actualizar su marca y su estilo personalizado para las superposiciones de texto agregadas a sus recursos.
