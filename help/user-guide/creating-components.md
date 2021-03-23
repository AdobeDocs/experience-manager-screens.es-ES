---
title: Creación de componentes
seo-title: Creación de componentes
description: AEM componentes se utilizan para guardar, dar formato y procesar el contenido disponible en las páginas web. Siga esta página para obtener más información sobre la creación de canales y la renderización de componentes.
seo-description: AEM componentes se utilizan para guardar, dar formato y procesar el contenido disponible en las páginas web. Siga esta página para obtener más información sobre la creación de canales y la renderización de componentes.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Desarrollo de pantallas
role: Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---


# Creación de componentes {#creating-components}

AEM componentes se utilizan para guardar, dar formato y procesar el contenido disponible en las páginas web.

>[!NOTE]
>
>Para obtener más información sobre la creación de componentes de AEM, consulte Desarrollo de componentes de AEM.

## Creación de canales {#authoring-channels}

El canal es el objeto central del contenido entregado a un conjunto de visualizaciones. Por lo tanto, un autor de contenido generalmente abriría un canal en el editor para añadir o modificar contenido. Dado que el canal es ***cq:Page***, seguirá el mismo patrón de experiencia de usuario tradicional para agregar y cambiar componentes en el canal.

Sin embargo, dado que los componentes de un canal suelen procesarse a pantalla completa, la experiencia de creación se verá afectada al intentar editar componentes únicos o componer nuevos pedidos. Por lo tanto, el canal dependerá de los selectores para procesar diferentes vistas de los componentes. El entorno de creación utilizará el selector de edición para activar el procesamiento de canal personalizado.

Por ejemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

El usuario no tiene que preocuparse de agregar el selector a la URL mientras edita. Una lógica del lado del cliente está escuchando el evento del conmutador de capas y agrega el selector si el canal tiene el tipo de recurso específico *pantallas/core/components/channel.*

## Representación de componentes {#rendering-components}

Para permitir una creación adecuada, los componentes deben proporcionar las dos representaciones siguientes:

| **Componente** | **Representaciones** |
|---|---|
| *my-component/my-component.html* | renderización de la producción |
| *my-component/edit.html* | edición de renderización en una vista más pequeña |

Los componentes integrados aprovechan las siguientes categorías de biblioteca de cliente:

| **Componente** | **Biblioteca de cliente** |
|---|---|
| *cq.screens.components.edit* | CSS y JS que deben cargarse durante la creación |
| *cq.screens.components.production* | CSS y JS que deben cargarse cuando el canal se está ejecutando |
| *cq.screens.components* | CSS y JS compartidos |

>[!NOTE]
>
>Para desarrollar componentes personalizados, utilice la plantilla de componente de muestra de AEM Screens ***[](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

