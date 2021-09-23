---
title: Representaciones adaptables en AEM Screens
description: Esta página describe la Información general de arquitectura y las configuraciones para representaciones adaptables en AEM Screens.
index: false
source-git-commit: 3ced907f4611ff7499ca4c013c4b25e1315e3726
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 2%

---


# Representaciones adaptables: Información general y configuraciones de arquitectura {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permitirá a los clientes centrarse únicamente en diseñar la experiencia *principal*.

## Objetivo {#objective}

Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Debe configurar las Representaciones adaptables para que un autor de contenido pueda utilizar esta función en un canal de AEM Screens.

## Información general de arquitectura {#architectural-overview}

Las representaciones adaptables se basan en la idea de tener varias representaciones de recursos con el nombre según una convención de nombres específica. La decisión de reproducir una representación específica se toma al evaluar las expresiones de consulta de medios que solo se pueden resolver en dispositivos con capacidades esperadas.

La capacidad de tener un patrón de nomenclatura de representación asociado define una regla de asignación de representación, como vertical u horizontal, como se muestra en la figura siguiente. Después de calcular todas las expresiones disponibles, el reproductor Screens recopilará los patrones de nomenclatura correspondientes a las reglas coincidentes. Los patrones se utilizan para encontrar las representaciones correctas durante la reproducción de la secuencia buscando los patrones en los nombres de representación.

![image](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Adición de una propiedad de asignación de representación al proyecto Screens {#rendition-mapping-new}

Para habilitar la función Representaciones adaptables, deben estar presentes las siguientes reglas de asignación y la configuración según el contexto (CA) debe resolverse para canales y pantallas.

>[!NOTE]
>Para obtener más información sobre las configuraciones según el contenido, consulte [aquí](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Siga los pasos a continuación para configurar la configuración:

1. Vaya a **CRXDE Lite**. Compruebe si la configuración **rendition-mapping** existe en `/conf/screens/sling:configs/rendition-mapping`, como se muestra en la figura siguiente.

   >![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si ha instalado el último Feature Pack 202109, verá **rendition-mapping** estructura de nodos previamente rellenada en `/conf/screens/sling:configs/rendition-mapping` en el CRXDE Lite. Consulte [Notas de la versión para Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md) para obtener más información sobre el paquete de funciones más reciente.
   >Para los proyectos existentes, asegúrese de que el proyecto Screens tenga asociada la configuración **rendition-mapping**. Consulte [Adición de asignaciones de representación a un proyecto existente](#rendition-mapping-existing) para obtener más información.

### Adición de una propiedad de asignación de representación a un proyecto existente {#rendition-mapping-existing}

1. Vaya a **CRXDE Lite**.

1. Defina explícitamente la asociación de asignación de representación añadiendo la propiedad `sling:configRef` que señala `/conf/screens` al nodo de contenido del proyecto, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Configuración de autor y publicación {#setup-author-publish}

Considere las siguientes recomendaciones en Autor y Publicación antes de utilizar Representaciones adaptables:

* La asignación de representación debe duplicarse manualmente.

* Las representaciones de recursos no se replican de forma predeterminada. Todos los recursos relevantes deben replicarse manualmente.

## Adición de reglas de asignación de representación {#add-rendition-mapping-rules}

Siga los pasos a continuación para agregar un nodo en Asignación de representación:

1. Vaya a esta ruta `/conf/screens/sling:configs/rendition-mapping` desde **CRXDE Lite**.

1. Cree un nodo en **rendition-mapping**. Haga clic con el botón derecho en **rendition-mapping** y haga clic en **Create** —> **Create Node**, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Introduzca el **Name** de la regla de asignación como **rule1** y el nodo **Type** como **nt:unstructured** en el cuadro de diálogo **Crear nodo**. Haga clic en **OK**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Debe añadir la propiedad expression con el valor que contiene la expresión de consulta.

   >[!NOTE]
   >Consulte [Uso de sintaxis de consulta de medios](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) para obtener más información.

   Haga clic en **rule1** que ha creado e introduzca **expression** en **Name** y **(orientation:horizontal)** en **Value**, como se muestra a continuación. Haga clic en **Add**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Agregue la propiedad pattern con el valor que contiene el patrón de nomenclatura de la representación.

   >[!NOTE]
   >El valor definido en la propiedad pattern coincidirá con la nueva representación de recursos y se seleccionará, si la expresión se evalúa como verdadera.

   Para añadir la propiedad pattern , haga clic en **rule1** que ha creado e introduzca **pattern** en **Name** y **horizontal** en **Value**, como se muestra a continuación. Haga clic en **Add**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Haga clic en **Guardar todo** y verá las propiedades bajo el nodo que creó en **rendition-mapping**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## Pasos siguientes {#next-steps}

Una vez que haya configurado y cargado las representaciones, como Autor de contenido, ahora puede utilizar Representaciones adaptables y también migrar los dispositivos de redes grandes para utilizar esta función en sus canales de AEM Screens. Consulte [Uso de representaciones adaptables](/help/user-guide/using-adaptive-renditions.md) para obtener más información.
