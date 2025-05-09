---
title: Uso de representaciones adaptables en AEM Screens
description: Aprenda a utilizar las representaciones adaptables en AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Uso de representaciones adaptables en AEM Screens {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos hacer clic en la mejor representación automáticamente para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargan y reproducen automáticamente la representación más adecuada de un recurso en función de estas reglas. Permite a los clientes centrarse en diseñar la experiencia *main*.

## Objetivo {#objective}

AEM Como autor de contenido de Scrßeens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente.
Una vez que un desarrollador agrega las propiedades y reglas de asignación de representación, estará listo para aplicar la asignación de representación a los recursos e incluirlos en un canal de AEM Screens.

>[!IMPORTANT]
>Antes de empezar a utilizar representaciones adaptables en un canal de AEM Screens, Adobe recomienda que conozca la Información general y la configuración de arquitectura de esta función. Ver [representaciones adaptables: información general de arquitectura y configuraciones](/help/user-guide/adaptive-renditions.md).

## Uso de representaciones adaptables en canales {#using-adaptive-renditions}

>[!NOTE]
>Después de agregar la propiedad de asignación de representación [al proyecto de Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) y las [reglas de asignación de representación](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), como autor de contenido, ya puede aplicar las representaciones a sus recursos.

### Aplicación de representaciones a Assets {#apply-renditions-assets}

Para aplicar representaciones a los recursos que desee utilizar en el canal Tour Screens, haga lo siguiente.

1. Navegue hasta la carpeta **Assets AEM** de la instancia de la.
1. Cree una versión del recurso que se adapte mejor a la pantalla de señalización, por ejemplo, `seahorse.jpg`.
1. Elija el patrón de nomenclatura de la representación, por ejemplo, `landscape`, similar a lo que se definió en la propiedad **pattern** de **CRXDE Lite**. Consulte [Agregar reglas de asignación de representación](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) para obtener más información.
1. Haga clic en **Agregar representación** para cargar la representación, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Haga clic en el nombre cambiado del archivo de recursos. La representación que está agregando debe contener el patrón (definido en el paso 3), por ejemplo, `seahorse-landscape.png`.
1. Cuando haya agregado el recurso, haga clic en él y seleccione **Administrar publicación** en la barra de acciones para publicarlo.

   ![imagen](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Consulte [Actualización de contenido bajo demanda](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) para obtener más información sobre cómo administrar la publicación y enviar actualizaciones de contenido de Autor a Publish en el dispositivo.

## Estrategia de migración {#migration-strategy}

>[!IMPORTANT]
>Para las redes grandes, Adobe recomienda que la migración se realice gradualmente para mitigar los riesgos. El motivo es que la función puede introducir cambios en el manifiesto y en el formato de almacenamiento de archivos. Agregar `sling:configRef` a todo el proyecto implica la actualización de todos los reproductores al Feature Pack 6.5.9. En caso de que haya actualizado algunos reproductores, agregue `sling:configRef` solo a las pantallas, ubicaciones o carpetas de canal que tengan todos los reproductores actualizados al Feature Pack 6.5.9.

El diagrama siguiente muestra la estrategia de migración para redes grandes:

![imagen](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para habilitar la función, agregue al menos una regla de asignación y asegúrese de que la configuración de asignación de representación se pueda resolver en el contexto de pantallas y canales. Siga los pasos a continuación para migrar:

1. Agregar [reglas de asignación de representación](/help/user-guide/adaptive-renditions.md).
1. Cree una carpeta para nuevos canales y agregue una referencia que apunte a la configuración de representación y asignación.
1. Cree canales reemplazando los antiguos y cargue representaciones.
1. Reasignar visualizaciones a los nuevos canales.
1. Agregue una referencia a las pantallas o ubicaciones migradas que apunten a la configuración de asignación de representación.
1. Repita los pasos 3, 4 y 5 para todos los canales y pantallas restantes.

   >[!NOTE]
   >Después de completar la migración, asegúrese de quitar todas las referencias de configuración de los canales, las pantallas y las ubicaciones, y agregue una sola al nodo de contenido del proyecto.
