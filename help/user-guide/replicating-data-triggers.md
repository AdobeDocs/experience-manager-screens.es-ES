---
title: Replicar activadores de datos en servidores de publicación
seo-title: Replicar activadores de datos en el servidor de publicación
description: Replicar activadores de datos en el servidor de publicación.
seo-description: Replicar activadores de datos en el servidor de publicación.
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# Replicar activadores de datos en servidor de publicación {#replicating-data-triggers}

Al utilizar ContextHub y AEM Targeting Engine para personalizar el contenido en función de los desencadenantes de datos en una configuración de creación/publicación, todas las configuraciones relacionadas con ContextHub y Personalización no se replican automáticamente con los canales cuando se publican.

Siga esta página para conocer los pasos necesarios para publicar estas configuraciones por separado.

Básicamente, esto se reduce a la publicación manual:

1. Configuraciones de módulos de interfaz de usuario y de la Tienda ContextHub
1. Audiencias de personalización
1. Actividades de personalización

## Pasos para replicar activadores de datos en el servidor de publicación {#replicating-data-triggers-publish}

Siga los pasos a continuación para replicar los activadores de datos en el servidor de publicación:

### Replicar configuraciones de ContextHub {#replicating-contexthub-configurations}

1. Vaya a **Herramientas** > **Implementación** > **Distribución** > **Publicar agente** http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish
1. Haga clic en el botón Probar conexión para validar que el autor pueda comunicarse correctamente con la instancia de publicación
1. Si la prueba falla, debe corregir la configuración del agente de replicación entre el autor y la publicación
1. Asegúrese de que la dirección URL del extremo también apunte a la dirección URL del servidor de publicación en el agente de distribución
1. Editar > Extremos de importación
1. Haga clic en la ficha Distribuir
1. Seleccione el botón de radio Agregar árbol
1. En el navegador de rutas, seleccione la ruta de configuración del proyecto (p. ej. /conf/screen/settings/cloudsettings/configuration)
1. Haga clic en Enviar

### Replicar las audiencias {#replicating-audiences}

1. Vaya a Herramientas > Personalización > Audienciashttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html
1. Explorar en profundidad la carpeta del proyecto (p. ej. /conf/screen/)
1. Seleccionar todas las audiencias/segmentos en la interfaz de usuario
1. Haga clic en Administrar publicación
1. Haga clic en Siguiente
1. Haga clic en Publicar

### Replicar las actividades {#replicating-activities}

1. Vaya a Herramientas > Personalización > Actividadeshttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html
1. Explorar en profundidad la carpeta del proyecto (p. ej. /content/campaign/screen/...)
1. Seleccionar todas las actividades en la interfaz de usuario
1. Haga clic en Administrar publicación
1. Haga clic en Siguiente
1. Haga clic en Publicar

> [!Note]
>La replicación de las configuraciones y audiencias de ContextHub se realiza durante la configuración del proyecto, mientras que la replicación de actividades se requiere cada vez que se cambia la segmentación dentro de un canal.

#### Resultado {#result}

Si la replicación se realiza correctamente, debe ver la siguiente estructura en la instancia de publicación (o similar para el proyecto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`