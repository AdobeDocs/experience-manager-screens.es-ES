---
title: Representaciones adaptables en AEM Screens
description: Esta página describe la Información general de arquitectura y las configuraciones para representaciones adaptables en AEM Screens.
index: false
source-git-commit: 898eb8e7e9b7442aead9fb6fb89c2646aef65e05
workflow-type: tm+mt
source-wordcount: '712'
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

Para habilitar la función Representaciones adaptables, las reglas de asignación deben estar presentes y la configuración de CA debe resolverse para los canales y visualizaciones:

1. Compruebe si la configuración de asignación de representación existe en `JCR`. Todos los paquetes de funciones más recientes tienen esta estructura de nodos previamente rellenada.

   >[!NOTE]
   >Todos los paquetes de funciones más recientes tienen esta estructura de nodos previamente rellenada.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Asegúrese de que el proyecto Screens tenga asociada la configuración de asignación de representación.

   * Cada nuevo proyecto creado con el asistente de proyecto Screens contendrá una referencia que señala a la configuración de asignación de representación.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * En una versión anterior de los proyectos de Screens, se requiere que la asociación se defina explícitamente añadiendo la propiedad `sling:configRef` que señala `/conf/screens` al nodo de contenido del proyecto.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## Estrategia de migración {#migration-strategy}

>[!IMPORTANT]
>Para las redes grandes, se recomienda que la migración se realice gradualmente para mitigar los riesgos, ya que la función introducirá cambios en el formato de manifiesto y almacenamiento de archivos.

En el diagrama siguiente se describe la estrategia de migración para las redes grandes:

![image](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para habilitar la función, agregue al menos una regla de asignación y asegúrese de que la configuración de asignación de representación se pueda resolver en el contexto de las visualizaciones y los canales. Siga los pasos a continuación para migrar:

1. Agregar [Reglas de asignación de representación](#adding-rendition-mapping-rules).
1. Cree una carpeta para nuevos canales y añada una referencia que señale a la configuración de asignación de representaciones.
1. Cree nuevos canales reemplazando los antiguos y cargando representaciones.
1. Vuelva a asignar pantallas a los nuevos canales.
1. Agregue una referencia a las visualizaciones migradas o a las ubicaciones que apunten a la configuración de asignación de representación.
1. Repita los pasos 3, 4 y 5 para todos los canales y pantallas restantes.
1. Después de completar la migración, elimine todas las referencias de configuración de los canales, las pantallas y las ubicaciones y agregue una sola al nodo de contenido del proyecto.

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


## Carga de representaciones {#upload-renditions}

1. Cree una versión del recurso que se adapte mejor a la visualización de señalización, por ejemplo, `portrait orientation`.

1. Elija el patrón de asignación de nombres de representación, por ejemplo,`portrait`.

1. Cambie el nombre del archivo de recursos para que contenga el patrón, por ejemplo, `my_asset_portrait.png`.

1. Haga clic en **Add Rendition** para cargar la representación, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

## Pasos siguientes {#next-steps}

Una vez que haya configurado y cargado las representaciones, ahora puede utilizar Representaciones adaptables en sus canales de AEM Screens. Consulte Uso de representaciones adaptables para obtener más información.
