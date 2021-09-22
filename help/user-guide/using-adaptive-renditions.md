---
title: Uso de representaciones adaptables en AEM Screens
description: En esta página se describe cómo utilizar las representaciones adaptables en AEM Screens.
index: false
source-git-commit: 97354c05f3b01dd76b6b8d4bdaf45c9be3ce4db2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 1%

---

# Uso de representaciones adaptables en AEM Screens {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permitirá a los clientes centrarse únicamente en diseñar la experiencia *principal*.

## Objetivo {#objective}

Como autor de contenido de AEM Screens, ahora puede configurar las representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente.

Por lo tanto, si ha implementado una variedad de dispositivos, el uso de esta función permitirá que el dispositivo descargue y reproduzca automáticamente la representación más adecuada de un recurso en función de las reglas.

>[!IMPORTANT]
>Antes de empezar a utilizar Representaciones adaptables, en un canal de AEM Screens, se recomienda conocer la Información general de arquitectura y la configuración de esta función. Consulte Representaciones adaptables: Información general de arquitectura y configuraciones para obtener más información.

## Estrategia de migración {#migration-strategy}

>[!IMPORTANT]
>Para las redes grandes, se recomienda que la migración se realice gradualmente para mitigar los riesgos, ya que la función introducirá cambios en el formato de manifiesto y almacenamiento de archivos.

En el diagrama siguiente se describe la estrategia de migración para las redes grandes:

![image](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para habilitar la función, agregue al menos una regla de asignación y asegúrese de que la configuración de asignación de representación se pueda resolver en el contexto de las visualizaciones y los canales. Siga los pasos a continuación para migrar:

1. Agregar [Reglas de asignación de representación](/help/user-guide/adaptive-renditions.md).
1. Cree una carpeta para nuevos canales y añada una referencia que señale a la configuración de asignación de representaciones.
1. Cree nuevos canales reemplazando los antiguos y cargando representaciones.
1. Vuelva a asignar pantallas a los nuevos canales.
1. Agregue una referencia a las visualizaciones migradas o a las ubicaciones que apunten a la configuración de asignación de representación.
1. Repita los pasos 3, 4 y 5 para todos los canales y pantallas restantes.

   >[!NOTE]
   >Después de completar la migración, asegúrese de eliminar todas las referencias de configuración de los canales, las pantallas y las ubicaciones y de agregar una sola al nodo de contenido del proyecto.


## Carga de representaciones y uso de representaciones adaptables en un canal de AEM Screens {#upload-renditions}

1. Cree una versión del recurso que se adapte mejor a la visualización de señalización, por ejemplo, `portrait orientation`.

1. Elija el patrón de asignación de nombres de representación, por ejemplo,`portrait`.

1. Cambie el nombre del archivo de recursos para que contenga el patrón, por ejemplo, `my_asset_portrait.png`.

1. Haga clic en **Add Rendition** para cargar la representación, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/adaptive-renditions/add-rendition.png)