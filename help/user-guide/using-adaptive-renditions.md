---
title: Uso de representaciones adaptables en AEM Screens
description: En esta página se describe cómo utilizar las representaciones adaptables en AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Uso de representaciones adaptables en AEM Screens {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargarán y reproducirán automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permite a los clientes centrarse únicamente en diseñar el *main* experiencia.

## Objetivo {#objective}

Como autor de contenido de AEM Screens, ahora puede configurar las representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente.
Una vez que un desarrollador agrega las propiedades y reglas de asignación de representación, ya puede aplicar la asignación de representación a los recursos e incluirlos posteriormente en un canal de AEM Screens.

>[!IMPORTANT]
>Antes de empezar a usar representaciones adaptables, en un canal de AEM Screens, se recomienda conocer la Información general y la configuración de arquitectura de esta función. Consulte [Representaciones adaptables: Información general de arquitectura y configuraciones](/help/user-guide/adaptive-renditions.md) para obtener más información.

## Uso de representaciones adaptables en canales {#using-adaptive-renditions}

>[!NOTE]
>Una vez que haya agregado [representación de la propiedad de asignación al proyecto de Pantallas](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) y [reglas de asignación de representación](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), como autor de contenido, ya está listo para aplicar las representaciones a sus recursos.

### Aplicación de representaciones a los recursos {#apply-renditions-assets}

Siga los pasos a continuación para aplicar representaciones a los recursos que desee utilizar en el canal de Screens de recorrido:

1. Vaya a **Assets** AEM carpeta en la instancia de la.

1. Cree una versión del recurso que se adapte mejor a la visualización de la señalización, por ejemplo, `seahorse.jpg`.

1. Elija el patrón de nomenclatura de la representación, por ejemplo,`landscape`, similar a lo definido en **pattern** propiedad en **CRXDE Lite**. Consulte [Adición de reglas de asignación de representación](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) para obtener más información.

1. Haga clic en **Agregar representación** para cargar la representación, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Seleccione el archivo de recursos cuyo nombre ha cambiado. La representación que está agregando debe contener el patrón (definido en el paso 3), por ejemplo, `seahorse-landscape.png`.

1. Una vez agregado el recurso, selecciónelo y haga clic en **Administrar publicación** en la barra de acciones para publicar el recurso.

   ![imagen](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Consulte [Actualización de contenido bajo demanda](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) para obtener más información sobre la administración de Publicación y la entrega de actualizaciones de contenido de Autor a Publicar en el dispositivo.


## Estrategia de migración {#migration-strategy}

>[!IMPORTANT]
>En el caso de redes grandes, se recomienda realizar la migración gradualmente para mitigar los riesgos, ya que la función introducirá cambios en el manifiesto y en el formato de almacenamiento de archivos. Añadir el `sling:configRef` Para completar todo el proyecto, es necesario actualizar todos los reproductores al paquete de funciones 6.5.9. En caso de que haya actualizado algunos reproductores, debe añadir el `sling:configRef` solo a las pantallas, ubicaciones o carpetas de canal que tengan todos los reproductores actualizados a Feature Pack 6.5.9.

El diagrama siguiente muestra la estrategia de migración para redes grandes:

![imagen](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para habilitar la función, agregue al menos una regla de asignación y asegúrese de que la configuración de asignación de representación se pueda resolver en el contexto de pantallas y canales. Siga los pasos a continuación para migrar:

1. Añadir [Reglas de asignación de representación](/help/user-guide/adaptive-renditions.md).
1. Cree una carpeta para nuevos canales y añada una referencia que apunte a la configuración de asignación de representación.
1. Cree nuevos canales para reemplazar los antiguos y cargar representaciones.
1. Reasignar visualizaciones a los nuevos canales.
1. Agregue una referencia a las pantallas o ubicaciones migradas que apunten a la configuración de asignación de representación.
1. Repita los pasos 3, 4 y 5 para todos los canales y pantallas restantes.

   >[!NOTE]
   >Después de completar la migración, asegúrese de quitar todas las referencias de configuración de los canales, las pantallas y las ubicaciones, y agregue una sola al nodo de contenido del proyecto.
