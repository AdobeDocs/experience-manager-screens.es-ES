---
title: Representaciones adaptables en AEM Screens
description: Esta página describe la Información general de arquitectura y las configuraciones para representaciones adaptables en AEM Screens.
index: false
source-git-commit: d3a2c7695afb296e9344aa55f6630798db5b1941
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 1%

---


# Representaciones adaptables: Información general y configuraciones de arquitectura {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permitirá a los clientes centrarse únicamente en diseñar la experiencia *principal*.

## Objetivo {#objective}

Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Debe configurar las representaciones adaptables para que un autor de contenido pueda utilizar esta función en un canal de AEM Screens.

Por lo tanto, si ha implementado una variedad de dispositivos, el uso de esta función permitirá que el dispositivo descargue y reproduzca automáticamente la representación más adecuada de un recurso en función de las reglas.

## Información general de arquitectura {#architectural-overview}

Las representaciones adaptables se basan en la idea de tener varias representaciones de recursos con el nombre según una convención de nombres específica. La decisión de reproducir una representación específica se toma al evaluar las expresiones de consulta de medios que solo se pueden resolver en dispositivos con capacidades esperadas. La capacidad de tener un patrón de nomenclatura de representación asociado define una regla de asignación de representación. Después de calcular todas las expresiones disponibles, el reproductor Screens recopilará los patrones de nomenclatura correspondientes a las reglas coincidentes. Los patrones se utilizan para encontrar las representaciones correctas durante la reproducción de la secuencia buscando los patrones en los nombres de representación.

![image](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Configuración del uso de representaciones adaptables {#setup-adaptive-renditions}

Para habilitar la función Representaciones adaptables, las reglas de asignación deben estar presentes y la Configuración según el contexto debe resolverse para los canales y muestra:

1. Compruebe si la configuración de asignación de representación existe en `JCR`. Todos los paquetes de funciones más recientes tienen esta estructura de nodos previamente rellenada.

   >[!NOTE]
   >Todos los paquetes de funciones más recientes tienen esta estructura de nodos previamente rellenada.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Asegúrese de que el proyecto Screens tenga asociada la configuración de asignación de representación.

   * Cada nuevo proyecto creado con el asistente de proyecto Screens contendrá una referencia que señala a la configuración de asignación de representación.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * En una versión anterior de los proyectos de Screens, se requiere que la asociación se defina explícitamente añadiendo la propiedad `sling:configRef` que señala `/conf/screens` al nodo de contenido del proyecto.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## Configuración de autor y publicación {#setup-author-publish}

Considere las siguientes recomendaciones en Autor y Publicación antes de utilizar Representaciones adaptables:

* La asignación de representación debe duplicarse manualmente.

* Las representaciones de recursos no se replican de forma predeterminada. Todos los recursos relevantes deben replicarse manualmente.

## Adición de reglas de asignación de representación {#add-rendition-mapping-rules}

1. Para añadir una regla de asignación, debe crear un nodo de tipo `nt:unstructured` en el nodo de asignación de representación.

1. Agregue la propiedad expression con el valor que contiene la expresión de consulta.

   >[!NOTE]
   >Consulte [Uso de sintaxis de consulta de medios](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) para obtener más información.

1. Agregue la propiedad pattern con el valor que contiene el patrón de nomenclatura de representación que se seleccionará, si la expresión se evalúa como verdadera.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)



## Pasos siguientes {#next-steps}

Una vez que haya configurado y cargado las representaciones, como Autor de contenido, ahora puede utilizar Representaciones adaptables y también migrar los dispositivos para aplicar esta función en sus canales de AEM Screens. Consulte [Uso de representaciones adaptables](/help/user-guide/using-adaptive-renditions.md) para obtener más información.
