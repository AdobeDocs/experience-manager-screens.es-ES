---
title: Información general y configuraciones de la arquitectura de representaciones adaptables
description: En esta página se describe la Información general de arquitectura y las configuraciones en CRXDE Lite para representaciones adaptables en AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 2%

---

# Representaciones adaptables: Información general de arquitectura y configuraciones {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permite a los clientes centrarse únicamente en diseñar el *main* experiencia.

## Objetivo {#objective}

Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Debe configurar las representaciones adaptables para que un autor de contenido pueda utilizar esta función en un canal de AEM Screens.

## Información general de la arquitectura {#architectural-overview}

Las representaciones adaptables se basan en la idea de tener varias representaciones de recursos con nombres según una convención de nombres específica. La decisión de reproducir una representación específica se toma mediante la evaluación de expresiones de consulta de medios que solo se pueden resolver en dispositivos con las capacidades esperadas.

La capacidad de tener un patrón de nomenclatura de representación asociado define una regla de asignación de representación, como vertical u horizontal, como se muestra en la figura siguiente. Después de calcular todas las expresiones disponibles, el reproductor de Screens recopilará los patrones de nomenclatura correspondientes a las reglas coincidentes. Los patrones se utilizan para encontrar las representaciones correctas durante la reproducción de la secuencia buscando los patrones en los nombres de representación.

![imagen](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Adición de la propiedad de asignación de representación al proyecto de Pantallas {#rendition-mapping-new}

Para habilitar la función Representaciones adaptables, deben estar presentes las siguientes reglas de asignación y la Configuración según el contexto (CA) debe poder resolverse en canales y pantallas.

>[!NOTE]
>Para obtener más información sobre las configuraciones según el contenido, consulte [aquí](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Siga los pasos a continuación para configurar la configuración:

1. Vaya a **CRXDE Lite**. Compruebe si el **rendition-mapping** La configuración de existe en `/conf/screens/sling:configs/rendition-mapping`, como se muestra en la figura siguiente.

   >![imagen](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si ha instalado el paquete de funciones más reciente 202109, verá lo siguiente **rendition-mapping** estructura de nodos previamente rellenada en `/conf/screens/sling:configs/rendition-mapping` en CRXDE Lite. Consulte [Notas de la versión del paquete de funciones 202109](/help/user-guide/release-notes-fp-202109.md) para obtener más información sobre el último paquete de funciones.
   >Para los proyectos existentes, asegúrese de que el proyecto de Pantallas tenga el **rendition-mapping** configuración asociada. Consulte [Agregar una asignación de representación a un proyecto existente](#rendition-mapping-existing) para obtener más información.

### Agregar una propiedad de asignación de representación a un proyecto existente {#rendition-mapping-existing}

1. Vaya a **CRXDE Lite**.

1. Defina explícitamente la asociación de asignación de representación añadiendo `sling:configRef` propiedad que señala a `/conf/screens` al nodo de contenido del proyecto, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Adición de reglas de asignación de representación {#add-rendition-mapping-rules}

Siga los pasos a continuación para agregar un nodo en Asignación de representación:

1. Vaya a esta ruta `/conf/screens/sling:configs/rendition-mapping` de **CRXDE Lite**.

1. Cree un nodo en **rendition-mapping**. Clic derecho en **rendition-mapping** y haga clic en **Crear** > **Crear nodo**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Introduzca el **Nombre** para la regla de asignación, como **regla1** y el nodo **Tipo** as **nt:unstructured** in **Crear nodo** Cuadro de diálogo. Haga clic en **OK**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Debe agregar la propiedad expression con el valor que contiene la expresión de consulta.

   >[!NOTE]
   >Consulte [Uso de sintaxis de consulta de medios](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) para obtener más información.

   Haga clic en **regla1** que ha creado y escriba **expresión** in **Nombre** y **(orientación:horizontal)** in **Valor**, como se muestra a continuación. Haga clic en **Añadir**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Agregue la propiedad pattern con el valor que contiene el patrón de nomenclatura de representación.

   >[!NOTE]
   >El valor definido en la propiedad pattern se comparará con la nueva representación de recursos y se seleccionará, si la expresión se evalúa como true.

   Para añadir la propiedad pattern, haga clic en **regla1** que ha creado y escriba **pattern** in **Nombre** y **horizontal** in **Valor**, como se muestra a continuación. Haga clic en **Añadir**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Haga clic en **Guardar todo** y verá las propiedades bajo el nodo que creó en **rendition-mapping**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## Pasos siguientes {#next-steps}

Una vez añadidas las propiedades y reglas de asignación de representación, ahora como autor de contenido, puede configurar los recursos para que utilicen representaciones adaptables y también migrar los dispositivos para redes grandes para aprovechar esta función en los canales de AEM Screens. Consulte [Uso de representaciones adaptables en AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obtener más información.
