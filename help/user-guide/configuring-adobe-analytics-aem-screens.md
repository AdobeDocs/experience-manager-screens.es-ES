---
title: Configuración de Adobe Analytics con AEM Screens
description: Obtenga más información sobre la secuenciación y el envío de eventos personalizados mediante Adobe Analytics sin conexión.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 10%

---

# Configuración de Adobe Analytics con AEM Screens {#configuring-adobe-analytics-with-aem-screens}

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.4.2 Feature Pack 2 and AEM 6.3.3 Feature Pack 4.
>
>To get access to either of these Feature Packs, you must contact Adobe Support and request access. Once you have permissions, download it from Package Share. -->

Esta sección trata los siguientes temas:

* **Secuenciación en Adobe Analytics con AEM Screens**
* **Envío De Eventos Personalizados Mediante Adobe Analytics Sin Conexión**

## Secuenciación en Adobe Analytics con AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

El ***proceso de secuenciación*** comienza con el servicio de almacenamiento de datos que activa el servicio Adobe Analytics. El contenido del canal envía eventos de Adobe Analytics con nómina, es decir, captura de prueba de datos a E/S de Windows y se activan eventos de permanencia. Los eventos se guardan en la base de datos de índice y se colocan posteriormente en el almacén de objetos. En función de la programación que establezca el administrador, corta los datos del almacén de objetos y los transfiere más en el almacén de fragmentos. Intenta enviar la máxima cantidad de datos al conectarse.

### Diagrama de secuencia {#sequencing-diagram}

En el siguiente diagrama de secuencia se explica la integración de Adobe Analytics con AEM Screens:

![analytics_chunking](assets/analytics_chunking.png)

## Envío De Eventos Personalizados Mediante Adobe Analytics Sin Conexión {#sending-custom-events-using-offline-adobe-analytics}

La siguiente tabla resume el modelo de datos estándar para eventos. Enumera todos los campos enviados a Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Sección</strong></td> 
   <td><strong>Etiqueta de propiedad</strong></td> 
   <td><strong>Nombre/clave de propiedad</strong></td> 
   <td><strong>Requerido</strong></td> 
   <td><strong>Tipo de datos</strong></td> 
   <td><strong>Tipo de propiedad</strong><br /> </td> 
   <td><strong>Descripción</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Principal/Evento</em></strong></td> 
   <td>GUID de evento</td> 
   <td>event.guid</td> 
   <td>recomendado</td> 
   <td>cadena</td> 
   <td>UUID</td> 
   <td>ID único que identifica la instancia de un evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fecha y hora de recopilación del evento</td> 
   <td>event.coll_dts</td> 
   <td>opcional</td> 
   <td>cadena</td> 
   <td>timestamp - UTC</td> 
   <td>Fecha y hora de recopilación</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fecha y hora del evento (inicio)</td> 
   <td>event.dts_start</td> 
   <td>recomendado</td> 
   <td>cadena</td> 
   <td>timestamp - UTC</td> 
   <td>Hora de inicio del evento. Si no se ha especificado, se asume que la hora del evento es la hora a la que el servidor lo recibió</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fecha y hora del evento (final)</td> 
   <td>event.dts_end</td> 
   <td>opcional</td> 
   <td>cadena</td> 
   <td>timestamp - UTC</td> 
   <td>Fecha y hora de finalización del evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Flujo de trabajo</td> 
   <td>event.workflow</td> 
   <td>recomendado</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Nombre del flujo de trabajo (Pantallas)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoría DMe principal</td> 
   <td>event.category</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Categoría principal (ESCRITORIO, MÓVIL, WEB, PROCESO, SDK, SERVICIO, ECOSISTEMA): agrupación de tipos de eventos: <strong>Reproductor enviado</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subcategoría</td> 
   <td>event.subcategory</td> 
   <td>recomendado</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Subcategoría: sección de un flujo de trabajo o área de una pantalla, etc. (Archivos recientes, archivos CC, creaciones móviles, etc.).</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de evento/acción</td> 
   <td>event.type</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Tipo de evento (procesar, hacer clic, pellizcar, zoom): acción del usuario principal</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subtipo</td> 
   <td>event.subtype</td> 
   <td>recomendado</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Subtipo de evento (crear, actualizar, eliminar, publicar, etc.): más detalles de la acción del usuario</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sin conexión</td> 
   <td>event.offline</td> 
   <td>opcional</td> 
   <td>booleano</td> 
   <td> </td> 
   <td>El evento se generó mientras la acción estaba sin conexión/en línea (verdadero/falso)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente de usuario</td> 
   <td>event.user_agent</td> 
   <td>recomendado (propiedades web)</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Agente de usuario</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Idioma/configuración regional</td> 
   <td>event.language</td> 
   <td>recomendado</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>La configuración regional del usuario es una cadena basada en las convenciones de etiquetado de idiomas de RFC 3066 (por ejemplo, en-US, fr-FR o es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID de dispositivo</td> 
   <td>event.device_guid</td> 
   <td>opcional</td> 
   <td>cadena<br /> </td> 
   <td>UUID</td> 
   <td>Identifica el GUID del dispositivo (por ejemplo, ID de equipo o hash de dirección IP + máscara de subred + ID de red + agente de usuario): aquí se envía el nombre de usuario del reproductor generado en el momento del registro.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Recuento</td> 
   <td>event.count</td> 
   <td>opcional</td> 
   <td>número</td> 
   <td> </td> 
   <td>Número de veces que se ha producido el evento: la duración del vídeo se envía</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valor</td> 
   <td>event.value</td> 
   <td>opcional</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Valor del evento (por ejemplo, configuración activada/desactivada)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>necesario para AA</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Compatibilidad de Adobe Analytics con Nombre de página personalizado</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>opcional</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>URL de la propiedad web o del esquema móvil: debe incluir una URL completa</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Código de error</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Código de error</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de error</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Tipo de error</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descripción del error</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Descripción del error<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Producto de origen/original</em></strong></td> 
   <td>Nombre</td> 
   <td>source.name</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Nombre de la aplicación (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versión</td> 
   <td>source.version</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Versión de firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Plataforma</td> 
   <td>source.platform</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Dispositivo</td> 
   <td>source.device</td> 
   <td>obligatorio con excepciones</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Nombre del reproductor</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versión del SO</td> 
   <td>source.os_version</td> 
   <td>obligatorio con excepciones</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Versión de O/S</td> 
  </tr>
  <tr>
   <td><strong><em>Contenido</em></strong></td> 
   <td>Acción</td> 
   <td>content.action</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>La dirección URL del recurso, incluida la representación reproducida</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de mime</td> 
   <td>content.mimetype</td> 
   <td>opcional</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>Tipo MIME del contenido</td> 
  </tr>
  <tr>
   <td><strong><em>Transacción</em></strong></td> 
   <td>Número de transacción</td> 
   <td>trn.number</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td>UUID</td> 
   <td>ID único que se adhiere preferiblemente a UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descripción del producto</td> 
   <td>trn.product</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>La URL del recurso (excluida la representación)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Cantidad</td> 
   <td>trn.quantity</td> 
   <td>Requerido</td> 
   <td>cadena</td> 
   <td> </td> 
   <td>La duración de la reproducción</td> 
  </tr>
 </tbody>
</table>
