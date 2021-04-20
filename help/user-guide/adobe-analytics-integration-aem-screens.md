---
title: Integración de Adobe Analytics con AEM Screens
seo-title: Integración de Adobe Analytics con AEM Screens
description: Siga esta página para obtener más información sobre la integración de AEM Screens con Adobe Analytics y proporcione una prueba de reproducción.
seo-description: Siga esta página para obtener más información sobre la integración de AEM Screens con Adobe Analytics y proporcione una prueba de reproducción.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: Administering Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---


# Integración de Adobe Analytics con AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado la versión mínima de AEM 6.4.2 Feature Pack 2 o AEM 6.3.3 Feature Pack 4.

>[!NOTE]
>
>Para obtener acceso a cualquiera de estos Feature Packs, debe ponerse en contacto con el servicio de asistencia al Adobe y solicitar acceso. Puede descargar el último paquete de funciones para AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) con su Adobe ID.

Esta sección cubre los siguientes temas:

* **Información general**
* **Detalles arquitectónicos**
* **Configuración de las propiedades**

## Información general {#overview}

***AEM*** Screensaprovecha Adobe Analytics y, con ello, puede lograr algo único en el mercado: análisis entre canales que ayudan a correlacionar el contenido mostrado en la ubicación con otras fuentes de datos.

AEM Screens proporciona una integración predeterminada con Adobe Analytics y proporciona una prueba de reproducción.

En esta sección se describe la siguiente funcionalidad relacionada con la conexión de un proyecto de AEM Screens con Adobe Analytics:

* Permite informes de prueba de reproducción por dispositivo
* Permite informes de prueba de reproducción por recurso
* Garantiza que todos los eventos del reproductor se capturen y marquen la hora
* Garantiza que todos los eventos del reproductor se almacenen localmente si la reproducción no está conectada a una red
* Permite crear bucles de comentarios que rastrean eventos de reproducción a lo largo del tiempo
* Permite que el sistema modifique el contenido y los diseños en función de los criterios de éxito definidos por el autor del contenido

La integración de Adobe Analytics con AEM Screens, por lo tanto, impone los siguientes *objetivos*:

* Habilitar el ROI a partir de implementaciones de publicidad dinámica
* Integrar Analytics como base para la futura habilitación de la recopilación y el análisis de información de uso

## Detalles arquitectónicos {#architectural-details}

Los clientes de AEM Screens desean comprender qué contenido se mostró a qué hora y durante cuánto tiempo (agregado). Esta es la capacidad común de la solución de señalización. En lugar de crear nuestro propio análisis, AEM Screens aprovechará Adobe Analytics y, con ello, podremos lograr algo único en el mercado: análisis multicanal que ayuden a correlacionar el contenido mostrado en la ubicación con otras fuentes de datos.

En el siguiente diagrama arquitectónico se explica la integración de Adobe Analytics con AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Activación de Adobe Analytics en AEM Screens {#enabling-adobe-analytics-in-aem-screens}

La configuración de Adobe Analytics se puede configurar desde la consola OSGi.

Vaya a **Configuración de la consola web de Adobe Experience Manager** para configurar Adobe Analytics para AEM Screens, como se muestra en la figura siguiente:

![screen_shot_2018-09-04at2550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Análisis de pantallas: Flujo de habilitación {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Antes de configurar las propiedades, póngase en contacto con el administrador de relaciones de Adobe para crear un ticket para obtener una **Clave de API de Analytics** y un **Proyecto de Analytics** para usarlos con AEM Screens.

![]()

### Configuración de las propiedades {#configuring-the-properties}

>[!CAUTION]
>
>Antes de configurar las propiedades, póngase en contacto con el administrador de relaciones de Adobe para crear un ticket para obtener una **Clave de API de Analytics** y un **Proyecto de Analytics** para usarlos con AEM Screens.

La tabla siguiente resalta las propiedades con su descripción para la configuración de Adobe Analytics para AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td><strong>URL de Analytics</strong></td>
   <td>URL para anunciar datos de análisis desde el reproductor. <br>
   Para desarrollo/fase</em> : https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Para producción</em> : https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Clave de API de Analytics</strong></td>
   <td>Clave de API para autenticarse en el servidor de Adobe Analytics (proporcionada por el Administrador de cuentas).</td>
  </tr>
  <tr>
   <td><strong>Proyecto de Analytics</strong></td>
   <td>Proyecto de AEM Screens configurado en el análisis para recibir datos (proporcionado por el Administrador de cuentas).</td>
  </tr>
  <tr>
   <td><strong>creación</strong></td>
   <td><p>Entorno de fase o producción (seleccione Fase o Producción).</p></td>
  </tr>
  <tr>
   <td><strong>Frecuencia de envío de Analytics</strong></td>
   <td>Frecuencia en minutos para enviar datos de análisis desde los reproductores. De forma predeterminada, se establece en 15 minutos.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De forma predeterminada, la **Frecuencia de envío de Analytics** es de 15 minutos.

#### Uso del servicio Adobe Analytics en AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Este escenario invoca la API de Analytics a través de llamadas REST de un servicio de análisis en el firmware y los componentes principales de pantallas de instrumentos para crear y enviar eventos específicos de un caso de uso determinado, permitiendo al mismo tiempo la extensibilidad en la que se puede enviar cualquier mensaje personalizado a Analytics desde un canal desarrollado personalizado.

Los eventos de Analytics se almacenan sin conexión en indexedDB y posteriormente se cortan y envían a la nube.

>[!NOTE]
>
>Para obtener más información sobre el ***Modelo de datos estándar*** y el ***Modelo de datos estándar para eventos***, consulte **[Configuración de Adobe Analytics para AEM Screens](configuring-adobe-analytics-aem-screens.md)**.

