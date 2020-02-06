---
title: Creación de plantillas personalizadas en diseños de varias zonas
seo-title: Creación de plantillas personalizadas en diseños de varias zonas
description: Siga esta página para obtener información sobre la creación de plantillas personalizadas en diseños de varias zonas.
seo-description: Siga esta página para obtener información sobre la creación de plantillas personalizadas en diseños de varias zonas.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: a4d48ba04bb8ab863f4f07b932892676b70e1e23

---


# Creación de plantillas personalizadas en diseños de varias zonas {#creating-custom-templates-multizone}

En el siguiente ejemplo se muestra cómo crear una plantilla personalizada en diseños de varias zonas.

Por ejemplo, la sección siguiente muestra la creación de una plantilla personalizada en un diseño multizona con las configuraciones siguientes:

![image](assets/custom-template1.png)


## Creación de una plantilla personalizada con una configuración específica {#basic-flow-setting}

Siga los pasos a continuación para crear una plantilla personalizada.

1. Cree la plantilla en `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. Cree un diseño de página en `/apps/settings/wcm/designs/<project>`.

   >[!NOTE]
   >
   >Asegúrese de que la ruta `cq:designPath` anterior coincide con la ruta.

1. Actualice el nodo **offline-config** para que el diseño apunte también a la nueva ruta

1. Agregue un archivo **static.css** en la `/apps/settings/wcm/designs/<project>` carpeta y defina su contenido en

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

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



