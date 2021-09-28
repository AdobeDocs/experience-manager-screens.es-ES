---
title: Uso de representaciones adaptables en AEM Screens
description: En esta página se describe cómo utilizar las representaciones adaptables en AEM Screens.
source-git-commit: 99102513b100f1f3b086eff9dcd21e5afb4f493c
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Uso de representaciones adaptables en AEM Screens {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permitirá a los clientes centrarse únicamente en diseñar la experiencia *principal*.

## Objetivo {#objective}

Como autor de contenido de AEM Screens, ahora puede configurar las representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente.
Una vez que un desarrollador agrega las propiedades y reglas de asignación de representación, ya está listo para aplicar la asignación de representación a los recursos y, posteriormente, incluirlos en un canal de AEM Screens.

>[!IMPORTANT]
>Antes de empezar a utilizar Representaciones adaptables, en un canal de AEM Screens, se recomienda conocer la Información general de arquitectura y la configuración de esta función. Consulte [Representaciones adaptables: Información general de arquitectura y configuraciones](/help/user-guide/adaptive-renditions.md) para obtener más información.

## Uso de representaciones adaptables en los canales {#using-adaptive-renditions}

>[!NOTE]
>Una vez que haya agregado la propiedad [de asignación de representación a las reglas de asignación de representación ](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) y [de Screens Project](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), como autor de contenido, ya estará listo para aplicar las representaciones a sus recursos.

### Aplicación de representaciones a recursos {#apply-renditions-assets}

Siga los pasos a continuación para aplicar representaciones a los recursos que desee utilizar en el canal de tour Screens:

1. Vaya a la carpeta **Assets** de la instancia de AEM.

1. Cree una versión del recurso que se adapte mejor a la visualización de señalización, por ejemplo, `seahorse.jpg`.

1. Elija el patrón de nomenclatura de la representación, por ejemplo,`landscape`, similar al definido en la propiedad **pattern** en **CRXDE Lite**. Consulte [Añadir reglas de asignación de representación](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) para obtener más información.

1. Cambie el nombre del archivo de recursos para que contenga el patrón (definido en el paso 3), por ejemplo, `seahorse_landscape.png`.

1. Haga clic en **Add Rendition** para cargar la representación, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/adaptive-renditions/add-rendition.png)


## Estrategia de migración {#migration-strategy}

>[!IMPORTANT]
>Para las redes grandes, se recomienda que la migración se realice gradualmente para mitigar los riesgos, ya que la función introducirá cambios en el formato de manifiesto y almacenamiento de archivos. Añadir el `sling:configRef` a todo el proyecto implica tener todos los reproductores actualizados al Feature Pack 6.5.9. En caso de que haya actualizado algunos de los reproductores, solo deberá agregar el `sling:configRef` a las visualizaciones, ubicaciones o carpetas de canal que tengan todos los reproductores actualizados al Feature Pack 6.5.9.

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

