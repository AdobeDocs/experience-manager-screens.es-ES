---
title: Caso de uso de transiciones de varias zonas a una sola zona
description: Siga esta página para obtener más información sobre el caso de uso Transiciones de varias zonas a una sola zona.
seo-description: MultiZone to SingleZone Transitions use case.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 3%

---

# Transición de varias zonas a una sola zona {#multizone-to-singlezone-use-case}


## Descripción del caso de uso {#use-case-description}

En esta sección se describe un ejemplo de uso que hace hincapié en cómo configurar un canal de diseño de varias zonas que alterna con un canal de diseño de una sola zona. El canal de varias zonas tiene recursos de imagen/vídeo de secuenciación y muestra cómo puede configurar proyectos que alternan entre varias zonas y una sola zona, y viceversa.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar horarios](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

1. Cree un proyecto de AEM Screens con el nombre **TakeoverLoop**, como se muestra a continuación.

   ![recurso](assets/mz-to-sz1.png)


1. **Creación de un canal de pantallas de varias zonas**

   1. Seleccione el **Canales** y haga clic en **Crear** en la barra de acciones para abrir el asistente y crear un canal.
   1. Seleccionar **Canal de pantalla dividida de barra izquierda** en el asistente y cree el canal titulado como **MultiZoneLayout**.
   1. Añada contenido al canal. Arrastre y suelte los recursos en cada una de las zonas. El siguiente ejemplo muestra un **MultiZoneLayout** canal formado por un vídeo, una imagen y un titular de texto (en una secuencia incrustada), como se muestra a continuación.

   ![recurso](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para obtener más información sobre la creación de un diseño de varias zonas en el canal, consulte [Diseño de varias zonas](multi-zone-layout-aem-screens.md).


1. Cree otro canal con el título **TakeoverChannel** a su **Canales** carpeta.

   ![recurso](assets/mz-to-sz3.png)

1. Clic **Editar** en la barra de acciones para añadir contenido a este canal. Añadir un **Canal** y un recurso de imagen al que desee cambiar a este canal, como se muestra en la figura siguiente:

   ![recurso](assets/mz-to-sz4.png)

1. Abra la configuración del componente Canal y diríjase al **MultiZoneLayout** canal que ha creado en *paso 2*.

   ![recurso](assets/mz-to-sz5.png)

1. Establezca la duración desde el **Secuencia** field a **10000 ms**.

   ![recurso](assets/mz-to-sz6.png)

1. Del mismo modo, abra la configuración de la imagen (recurso que ha agregado) y establezca su duración en **Secuencia** field a **3000 ms**.

   ![recurso](assets/mz-to-sz7.png)

## Comprobación de la previsualización {#checking-the-preview}

Puede ver la salida deseada desde el reproductor o simplemente haciendo clic en el **Previsualizar** del editor.

El resultado mostrará cómo se reproduce un diseño de varias zonas para *10000 ms* y, a continuación, cambia al diseño de zona única que tiene una duración de reproducción de *3000 ms* y vuelve al diseño de varias zonas.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Puede personalizar la transición de canal (del diseño de varias zonas a una sola zona o viceversa) según sus necesidades.
