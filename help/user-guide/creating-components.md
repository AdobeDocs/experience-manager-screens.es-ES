---
title: Crear componentes
description: Obtenga información sobre cómo se utilizan los componentes de AEM para mantener, dar formato y procesar el contenido disponible en las páginas web.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
TQID: https://experienceleague.adobe.com/0FSVmHOxse3eUn8eKvolCKk7-Wk9SGzA10iIcykLUs0
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 340
ht-degree: 1%

---

# Creación de componentes {#creating-components}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Los componentes de AEM se utilizan para mantener, dar formato y representar el contenido disponible en las páginas web.

>[!NOTE]
>
>Para obtener más información sobre los detalles de la creación de componentes de AEM, consulte Desarrollo de componentes de AEM.

## Canales de creación {#authoring-channels}

El canal es el objeto central del contenido enviado a un conjunto de pantallas. Por lo tanto, un autor de contenido suele abrir un canal en el editor para agregar o modificar contenido. Como el canal es un ***`cq:Page`***, sigue el mismo patrón de experiencia de usuario tradicional para agregar y cambiar componentes en el canal.

Sin embargo, como los componentes de un canal suelen procesarse a pantalla completa, la experiencia de creación sufre al intentar editar componentes únicos o componer nuevos pedidos. Por lo tanto, el canal depende de selectores para procesar diferentes vistas de los componentes. El entorno de creación utiliza el selector `edit` para activar el procesamiento del canal personalizado.

Por ejemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

El usuario no tiene que encargarse de añadir el selector a la URL durante la edición. Una lógica del lado del cliente escucha el evento del conmutador de capa y agrega el selector si el canal tiene el tipo de recurso dedicado *screens/core/components/channel*.

## Procesar componentes {#rendering-components}

Para permitir una creación adecuada, los componentes deben proporcionar las dos representaciones siguientes:

| **Componente** | **Representaciones** |
|---|---|
| *my-component/my-component.html* | renderización de producción |
| *my-component/edit.html* | edición del procesamiento en una vista más pequeña |

Los componentes integrados utilizan las siguientes categorías de biblioteca de cliente:

| **Componente** | **Biblioteca de cliente** |
|---|---|
| *cq.screens.components.edit* | CSS y JS que deben cargarse durante la creación |
| *cq.screens.components.production* | CSS y JS que deben cargarse cuando se ejecuta el canal |
| *cq.screens.components* | CSS y JS compartidos |

>[!NOTE]
>
>Para desarrollar componentes personalizados, use la ***[plantilla de componente de ejemplo de AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

