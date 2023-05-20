---
title: Creación de componentes
seo-title: Creating Components
description: AEM Los componentes de se utilizan para mantener, dar formato y representar el contenido disponible en las páginas web. Siga esta página para obtener más información sobre la creación de canales y el procesamiento de componentes.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages. Follow this page to learn about authoring channels and rendering components.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---

# Creación de componentes {#creating-components}

AEM Los componentes de se utilizan para mantener, dar formato y representar el contenido disponible en las páginas web.

>[!NOTE]
>
>AEM AEM Para obtener más información sobre los detalles de la creación de componentes de, consulte Desarrollo de componentes de.

## Creación de canales {#authoring-channels}

El canal es el objeto central del contenido enviado a un conjunto de pantallas. Por lo tanto, un autor de contenido suele abrir un canal en el editor para agregar o modificar contenido. Dado que el canal es un ***cq:Page*** seguirá el mismo patrón de experiencia de usuario tradicional para añadir y cambiar componentes en el canal.

Sin embargo, dado que los componentes de un canal suelen procesarse a pantalla completa, la experiencia de creación se verá afectada al intentar editar componentes únicos o componer nuevos pedidos. Por lo tanto, el canal dependerá de los selectores para procesar diferentes vistas de los componentes. El entorno de creación utilizará el selector de edición para activar el procesamiento de canal personalizado.

Por ejemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`. 

El usuario no tiene que encargarse de añadir el selector a la URL durante la edición. Una lógica del lado del cliente escucha el evento del conmutador de capa y agrega el selector si el canal tiene el tipo de recurso dedicado *screens/core/components/channel.*

## Componentes de procesamiento {#rendering-components}

Para permitir una creación adecuada, los componentes deben proporcionar las dos representaciones siguientes:

| **Componente** | **Representaciones** |
|---|---|
| *my-component/my-component.html* | renderización de producción |
| *my-component/edit.html* | edición del procesamiento en una vista más pequeña |

Los componentes integrados aprovechan las siguientes categorías de bibliotecas de cliente:

| **Componente** | **Biblioteca de cliente** |
|---|---|
| *cq.screens.components.edit* | CSS y JS que deben cargarse durante la creación |
| *cq.screens.components.production* | CSS y JS que deben cargarse cuando se está ejecutando el canal |
| *cq.screens.components* | CSS y JS compartidos |

>[!NOTE]
>
>Para desarrollar componentes personalizados, utilice el ***[Plantilla de componente de muestra de AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
