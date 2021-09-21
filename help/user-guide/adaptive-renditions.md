---
title: Representaciones adaptables en AEM Screens
description: En esta página se describe cómo utilizar las representaciones adaptables en AEM Screens.
index: false
source-git-commit: 0a870f337f69f3379abb15dac504ee8e8355bc98
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# Representaciones adaptables {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permitirá a los clientes centrarse únicamente en diseñar la experiencia *principal*.

## Objetivo {#objective}

Como autor de contenido de AEM Screens, ahora puede configurar las representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente.

Por lo tanto, si ha implementado una variedad de dispositivos, el uso de esta función permitirá que el dispositivo descargue y reproduzca automáticamente la representación más adecuada de un recurso en función de las reglas.

## Información general de arquitectura {#architectural-overview}

Las representaciones adaptables se basan en la idea de tener varias representaciones de recursos con el nombre según una convención de nombres específica. La decisión de reproducir una representación específica se toma al evaluar las expresiones de consulta de medios que solo se pueden resolver en dispositivos con capacidades esperadas. La capacidad de tener un patrón de nomenclatura de representación asociado define una regla de asignación de representación. Después de calcular todas las expresiones disponibles, el reproductor Screens recopilará los patrones de nomenclatura correspondientes a las reglas coincidentes. Los patrones se utilizan para encontrar las representaciones correctas durante la reproducción de la secuencia buscando los patrones en los nombres de representación.


## Configuración del uso de representaciones adaptables {#setup-adaptive-renditions}

Para habilitar la función Representaciones adaptables, las reglas de asignación deben estar presentes y la configuración de CA debe resolverse para los canales y visualizaciones:

1. Compruebe si la configuración de asignación de representación existe en `JCR`. Todos los paquetes de funciones más recientes tienen esta estructura de nodos previamente rellenada.

   >[!NOTE]
   >Todos los paquetes de funciones más recientes tienen esta estructura de nodos previamente rellenada.


1. Asegúrese de que el proyecto Screens tenga asociada la configuración de asignación de representación.

   * Cada nuevo proyecto creado con el asistente de proyecto Screens contendrá una referencia que señala a la configuración de asignación de representación.

   * En una versión anterior de los proyectos de Screens, se requiere que la asociación se defina explícitamente añadiendo la propiedad `sling:configRef` que señala `/conf/screens` al nodo de contenido del proyecto.

## Estrategia de migración {#migration-strategy}

>[!IMPORTANT]
>Para las redes grandes, se recomienda que la migración se realice gradualmente para mitigar los riesgos, ya que la función introducirá cambios en el formato de manifiesto y almacenamiento de archivos.

Para habilitar la función, agregue al menos una regla de asignación y asegúrese de que la configuración de asignación de representación se pueda resolver en el contexto de visualizaciones y canales:

1. Agregar reglas de asignación de representación.
1. Cree una carpeta para nuevos canales y añada una referencia que señale a la configuración de asignación de representaciones.
1. Cree nuevos canales reemplazando los antiguos y cargando representaciones.
1. Vuelva a asignar pantallas a los nuevos canales.
1. Agregue una referencia a las visualizaciones/ubicaciones migradas que apunten a la configuración de asignación de representación.
1. Repita los pasos 3, 4 y 5 para todos los canales y pantallas restantes.
1. Después de terminar con la migración, elimine todas las referencias de configuración de canales, visualizaciones/ubicaciones y agregue una sola al nodo de contenido del proyecto.

## Configuración de autor y publicación {#setup-author-publish}

Siga los pasos a continuación para configurar el autor y la publicación:

* La asignación de representación debe duplicarse manualmente.

* Las representaciones de recursos no se replican de forma predeterminada. Todos los recursos relevantes deben replicarse manualmente.


## Adición de reglas de asignación de representación {#adding-rendition-mapping-rules}

1. Para añadir una regla de asignación, debe crear un nodo de tipo `nt:unstructured` en el nodo de asignación de representación.

1. Agregue la propiedad expression con el valor que contiene la expresión de consulta.

   >[!NOTE]
   >Consulte [Uso de sintaxis de consulta de medios](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) para obtener más información.

1. Agregue la propiedad pattern con el valor que contiene el patrón de nomenclatura de representación que se seleccionará, si la expresión se evalúa como verdadera.

## Carga de representaciones {#upload-renditions}

1. Cree una versión del recurso que se adapte mejor a la visualización de señalización, por ejemplo, `portrait orientation`.

1. Elija el patrón de asignación de nombres de representación, por ejemplo,`portrait`.

1. Cambie el nombre del archivo de recursos para que contenga el patrón, por ejemplo, `my_asset_portrait.png`.

1. Cargue la representación haciendo clic en el botón Añadir representación de la barra de herramientas.


## Pasos siguientes {#next-steps}

Una vez cargadas las representaciones, ahora puede utilizar Representaciones adaptables en sus canales de AEM Screens.
