---
title: Caso de uso de las transiciones de MultiZone a SingleZone
description: Siga esta página para conocer el caso de uso de las transiciones de MultiZone a SingleZone.
seo-description: Caso de uso de MultiZone a SingleZone Transitions.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3

---


# Transición de zonas múltiples a zonas únicas {#multizone-to-singlezone-use-case}


## Descripción de caso de uso {#use-case-description}

En esta sección se describe un ejemplo de caso de uso que hace hincapié en cómo configurar un canal de diseño de varias zonas que se alterne con un canal de diseño de una sola zona. El canal de varias zonas tiene recursos de vídeo/imagen secuenciados y muestra cómo se puede configurar un proyecto que alterne de varias zonas a una sola zona y viceversa.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar programaciones](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

1. Cree un proyecto de AEM Screens denominado **TakoverLoop**, como se muestra a continuación.

   ![recurso](assets/mz-to-sz1.png)


1. **Creación de un canal de pantallas de varias zonas**

   1. Seleccione la carpeta **Canales** y haga clic en **Crear** en la barra de acciones para abrir el asistente y crear un canal.
   1. Seleccione Canal **de pantalla dividido de barras** izquierda-izquierda en el asistente y cree el canal titulado **MultiZoneLayout**.
   1. Agregue contenido al canal. Arrastre y suelte los recursos en cada una de las zonas. El siguiente ejemplo muestra un canal **MultiZoneLayout** que consta de un vídeo, una imagen y una pancarta de texto (en una secuencia incrustada), como se muestra a continuación.
   ![recurso](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para obtener más información sobre la creación de un diseño de varias zonas en el canal, consulte Diseño de [varias zonas](multi-zone-layout-aem-screens.md).


1. Cree otro canal denominado **TakoverChannel** en la carpeta **Canales** .

   ![recurso](assets/mz-to-sz3.png)

1. Haga clic en **Editar** en la barra de acciones para agregar contenido a este canal. Agregue a este canal un componente **Canal** y un recurso de imagen al que desee cambiar, como se muestra en la figura siguiente:

   ![recurso](assets/mz-to-sz4.png)

1. Abra la configuración del componente Canal y señale al canal **MultiZoneLayout** que creó en el *paso 2*.

   ![recurso](assets/mz-to-sz5.png)

1. Establezca la duración del campo **Secuencia** en **10000 ms**.

   ![recurso](assets/mz-to-sz6.png)

1. Del mismo modo, abra la configuración de la imagen (recurso que ha agregado) y defina su duración desde el campo **Secuencia** a **3000 ms**.

   ![recurso](assets/mz-to-sz7.png)

## Comprobación de la vista previa {#checking-the-preview}

Puede ver la salida deseada desde el reproductor o simplemente haciendo clic en la **Vista previa** desde el editor.

El resultado mostrará cómo se reproduce un diseño de varias zonas durante *10000 ms* y, a continuación, cambiará al diseño de una sola zona con una duración de reproducción de *3000 ms* y, a continuación, volverá al diseño de varias zonas.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Puede personalizar la transición de canal (desde el diseño de varias zonas a una sola zona o viceversa) según sus necesidades.