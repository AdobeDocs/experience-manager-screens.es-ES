---
title: Caso de uso de transiciones de varias zonas a una sola zona
description: Siga esta página para obtener más información sobre el caso de uso Transiciones de varias zonas a una sola zona.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
TQID: https://experienceleague.adobe.com/MTRkmtP5J3PL13VZWm9nalthBX-03nu-Z2OsbnMO1Q4
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 1%

---

# Transición de varias zonas a una sola zona {#multizone-to-singlezone-use-case}

## Descripción del caso de uso {#use-case-description}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

En esta sección se describe un ejemplo de uso que hace hincapié en cómo configurar un canal de diseño de varias zonas que alterna con un canal de diseño de una sola zona. El canal de varias zonas tiene recursos de imagen/vídeo de secuenciación y muestra cómo puede configurar un proyecto que alterna entre varias zonas y una sola zona, y a la inversa.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar horarios](managing-schedules.md)**
* **[Registro de dispositivo](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

1. Cree un proyecto de AEM Screens llamado **TakeoverLoop**, como se muestra a continuación.

   ![recurso](assets/mz-to-sz1.png)


1. **Creación de un canal de Screens de varias zonas**

   1. Haga clic en la carpeta **Canales**, luego en **Crear** en la barra de acciones y abra el asistente para crear un canal.
   1. Haga clic en **Canal de pantalla dividida de barra izquierda** en el asistente y cree el canal con el título **MultiZoneLayout**.
   1. Añada contenido al canal. Arrastre y suelte los recursos en cada una de las zonas. El ejemplo siguiente muestra un canal **MultiZoneLayout** que consta de un vídeo, una imagen y un titular de texto (en una secuencia incrustada), como se muestra a continuación.

   ![recurso](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para obtener más información sobre cómo crear un diseño de varias zonas en el canal, consulte [Diseño de varias zonas](multi-zone-layout-aem-screens.md).


1. Cree otro canal con el título **TakeoverChannel** en su carpeta **Channels**.

   ![recurso](assets/mz-to-sz3.png)

1. Haz clic en **Editar** en la barra de acciones para agregar contenido a este canal. Agregue un componente **Canal** y un recurso de imagen a los que desee cambiar para este canal, como se muestra en la figura siguiente:

   ![recurso](assets/mz-to-sz4.png)

1. Abra la configuración del componente Canal y diríjala al canal **MultiZoneLayout** que creó en el *paso 2*.

   ![recurso](assets/mz-to-sz5.png)

1. Establezca la duración del campo **Secuencia** en **10000 milisegundos**.

   ![recurso](assets/mz-to-sz6.png)

1. Del mismo modo, abra la configuración de la imagen (recurso que agregó) y establezca su duración del campo **Secuencia** en **3000 milisegundos**.

   ![recurso](assets/mz-to-sz7.png)

## Comprobación de la previsualización {#checking-the-preview}

Puedes ver la salida deseada desde el reproductor o simplemente seleccionando **Vista previa** en el editor.

El resultado muestra cómo se reproduce un diseño de varias zonas durante *10000 milisegundos*. A continuación, cambia a un diseño de zona única que tiene una duración de reproducción de *3000 milisegundos*. Y finalmente, vuelve al diseño de varias zonas.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Puede personalizar la transición de canal (del diseño de varias zonas a una sola zona o a la inversa) según sus necesidades.
