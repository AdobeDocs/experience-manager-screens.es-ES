---
title: Creación de componentes
seo-title: Creación de componentes
description: AEM componentes se utilizan para mantener, dar formato y procesar el contenido disponible en las páginas web. Siga esta página para obtener información sobre la creación de canales y la representación de componentes.
seo-description: AEM componentes se utilizan para mantener, dar formato y procesar el contenido disponible en las páginas web. Siga esta página para obtener información sobre la creación de canales y la representación de componentes.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---


# Creación de componentes {#creating-components}

AEM componentes se utilizan para mantener, dar formato y procesar el contenido disponible en las páginas web.

>[!NOTE]
>
>Para obtener más información sobre la creación de componentes AEM, consulte Desarrollo de componentes AEM.

## Creación de Canales {#authoring-channels}

El canal es el objeto central del contenido enviado a un conjunto de pantallas. Por lo tanto, un autor de contenido generalmente abre un canal en el editor para agregar o modificar contenido. Dado que el Canal es ***cq:Page*** , seguirá el mismo patrón UX tradicional para agregar y cambiar componentes en el canal.

Sin embargo, como los componentes de un canal suelen representarse a pantalla completa, la experiencia de creación se verá afectada al intentar editar componentes únicos o al componer nuevos pedidos. Por lo tanto, el canal recurrirá a los selectores para presentar distintas vistas de los componentes. El entorno de creación aprovechará el selector de edición para activar el procesamiento de canales personalizado.

Por ejemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

El usuario no tiene que preocuparse de agregar el selector a la URL mientras edita. Una lógica del lado del cliente está escuchando el evento del conmutador de capas y agrega el selector si un canal tiene el tipo de recurso dedicado *pantallas/núcleo/componentes/canal.*

## Representación de componentes {#rendering-components}

Para habilitar la creación adecuada, los componentes deben proporcionar las dos representaciones siguientes:

| **Componente** | **Representaciones** |
|---|---|
| *my-component/my-component.html* | procesamiento de producción |
| *my-component/edit.html* | editar procesamiento en una vista más pequeña |

Los componentes integrados aprovechan las siguientes categorías de biblioteca de cliente:

| **Componente** | **Biblioteca de cliente** |
|---|---|
| *cq.screen.components.edit* | CSS y JS que deben cargarse durante la creación |
| *cq.screen.components.production* | CSS y JS que deben cargarse cuando se ejecuta el canal |
| *cq.screen.components* | CSS compartida y JS |

>[!NOTE]
>
>Para desarrollar componentes personalizados, utilice la plantilla[***](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)AEM Screens de componentes de muestra***.

