---
title: Información general y configuraciones de la arquitectura de representaciones adaptables
description: Obtenga información acerca de la descripción general de la arquitectura y las configuraciones en CRXDE Lite para representaciones adaptables en AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 2%

---

# Representaciones adaptables: Información general de arquitectura y configuraciones {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos hacer clic en la mejor representación automáticamente para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargan y reproducen automáticamente la representación más adecuada de un recurso según estas reglas, lo que permite a los clientes centrarse en diseñar únicamente la experiencia *main*.

## Objetivo {#objective}

Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Configure las representaciones adaptables para que un autor de contenido pueda utilizar esta función en un canal de AEM Screens.

## Información general de la arquitectura {#architectural-overview}

Las representaciones adaptables se basan en la idea de tener varias representaciones de un recurso con el nombre según una convención de nombres específica. La decisión de reproducir una representación específica se toma mediante la evaluación de expresiones de consulta de medios que solo se pueden resolver en dispositivos con las capacidades esperadas.

La capacidad de tener un patrón de nomenclatura de representación asociado define una regla de asignación de representación, como vertical u horizontal, como se muestra en la figura siguiente. Después de calcular todas las expresiones disponibles, el reproductor de Screens recopila los patrones de nomenclatura correspondientes a las reglas coincidentes. Los patrones se utilizan para encontrar las representaciones correctas durante la reproducción de la secuencia buscando los patrones en los nombres de representación.

![imagen](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Agregar la propiedad de asignación de representación al proyecto de Screens {#rendition-mapping-new}

Para habilitar la función Representaciones adaptables, deben estar presentes las siguientes reglas de asignación y la Configuración según el contexto (CA) debe poder resolverse en canales y pantallas.

>[!NOTE]
>Para obtener más información acerca de las configuraciones según el contenido, vea [aquí](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Siga los pasos a continuación para configurar la configuración:

1. Vaya a **CRXDE Lite**. Compruebe si la configuración **rendition-mapping** existe en `/conf/screens/sling:configs/rendition-mapping`, como se muestra en la figura siguiente.

   >![imagen](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si ha instalado el paquete de funciones más reciente 202109, verá la estructura de nodos **rendition-mapping** previamente rellenada en `/conf/screens/sling:configs/rendition-mapping` en el CRXDE Lite. Consulte [Notas de la versión del paquete de funciones 202109](/help/user-guide/release-notes-fp-202109.md) para obtener información sobre el paquete de funciones más reciente.
   >Para los proyectos existentes, asegúrese de que el proyecto de Screens tenga la configuración **rendition-mapping** asociada. Consulte [Agregar asignación de representación a un proyecto existente](#rendition-mapping-existing) para obtener más información.

### Agregar una propiedad de asignación de representación a un proyecto existente {#rendition-mapping-existing}

1. Vaya a **CRXDE Lite**.

1. Defina explícitamente la asociación de representación-asignación agregando la propiedad `sling:configRef` que señala a `/conf/screens` al nodo de contenido del proyecto, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Adición de reglas de asignación de representación {#add-rendition-mapping-rules}

Siga los pasos a continuación para agregar un nodo en Asignación de representación:

1. Vaya a esta ruta de acceso `/conf/screens/sling:configs/rendition-mapping` desde **CRXDE Lite**.
1. Cree un nodo en **rendition-mapping**. Haga clic con el botón derecho en **rendition-mapping** y haga clic en **Crear** > **Crear nodo**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Escriba **Name** para la regla de asignación, como **rule1** y el nodo **Type** como **`nt:unstructured`** en el cuadro de diálogo **Crear nodo**. Haga clic en **OK**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Agregue la propiedad expression con el valor que contiene la expresión de consulta.

   >[!NOTE]
   >Consulte [Uso de sintaxis de consulta de medios](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) para obtener más información.

   Haga clic en la **regla1** que creó e introduzca la **expresión** en **Nombre** y **(orientación:horizontal)** en **Valor**, como se muestra a continuación. Haga clic en **Agregar**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Agregue la propiedad pattern con el valor que contiene el patrón de nomenclatura de representación.

   >[!NOTE]
   >El valor definido en la propiedad pattern coincide con la nueva representación de recursos y se selecciona, si la expresión se evalúa como true.

   Para agregar la propiedad pattern, haga clic en **rule1** que ha creado e introduzca el **pattern** en **Name** y **landscape** en **Value**, como se muestra a continuación. Haga clic en **Agregar**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Haga clic en **Guardar todo** y observe las propiedades en el nodo que creó en **rendition-mapping**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Pasos siguientes {#next-steps}

Después de agregar propiedades y reglas de asignación de representación, como autor de contenido, puede configurar los recursos. Puede utilizar representaciones adaptables y también migrar los dispositivos de redes grandes para utilizar esta función en los canales de AEM Screens. Consulte [Uso de representaciones adaptables en AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obtener más información.
