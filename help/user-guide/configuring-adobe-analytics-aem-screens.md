---
title: Configuración de Adobe Analytics con AEM Screens
seo-title: Configuración de Adobe Analytics con AEM Screens
description: 'Siga esta sección para obtener más información sobre la secuenciación y el envío de eventos personalizados con Adobe Analytics sin conexión '
seo-description: 'Siga esta sección para obtener más información sobre la secuenciación y el envío de eventos personalizados con Adobe Analytics sin conexión '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: Administering Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 11%

---


# Configuración de Adobe Analytics con AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4.2 Feature Pack 2 y AEM 6.3.3 Feature Pack 4.
>
>Para obtener acceso a cualquiera de estos Feature Packs, debe ponerse en contacto con el servicio de asistencia al Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

Esta sección cubre los siguientes temas:

* **Secuencia en Adobe Analytics con AEM Screens**
* **Envío de eventos personalizados mediante Adobe Analytics sin conexión**

## Secuencia en Adobe Analytics con AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

El ***proceso de secuenciación*** comienza con el servicio de almacenamiento de datos que activa el servicio Adobe Analytics. El contenido del canal envía eventos de Adobe Analytics con nómina, es decir, captura de prueba de datos a Windows I/O y se activan eventos de estadía. Los eventos se guardan en la base de datos de índice y se colocan más adelante en el almacén de objetos. Según la programación, el administrador lo establece, corta los datos del almacén de objetos y los transfiere aún más en el almacén de bloques. Cuando está conectado, intenta enviar la máxima cantidad de datos.

### Diagrama de secuencia {#sequencing-diagram}

En el diagrama de secuenciación siguiente se explica la integración de Adobe Analytics con AEM Screens:

![analytics_chunking](assets/analytics_chunking.png)

## Envío de eventos personalizados mediante Adobe Analytics sin conexión {#sending-custom-events-using-offline-adobe-analytics}

La siguiente tabla resume el modelo de datos estándar para los eventos. Enumera todos los campos enviados a Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Sección</strong></td> 
   <td><strong>Etiqueta de propiedad</strong></td> 
   <td><strong>Nombre de propiedad/Clave</strong></td> 
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
   <td>Cadena</td> 
   <td>UUID</td> 
   <td>ID único que identifica la instancia de un evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fecha y hora de recopilación del evento</td> 
   <td>event.coll_dts</td> 
   <td>opcional</td> 
   <td>Cadena</td> 
   <td>timestamp - UTC</td> 
   <td>Hora de la fecha de recopilación</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fecha y hora del evento (inicio)</td> 
   <td>event.dts_start</td> 
   <td>recomendado</td> 
   <td>Cadena</td> 
   <td>timestamp - UTC</td> 
   <td>Hora de la fecha de inicio del evento, si NO lo especifica, la hora del evento se asumirá como la hora en que el servidor la recibió</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fecha y hora del evento (final)</td> 
   <td>event.dts_end</td> 
   <td>opcional</td> 
   <td>Cadena</td> 
   <td>timestamp - UTC</td> 
   <td>Hora de finalización del evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Flujo de trabajo</td> 
   <td>event.workflow</td> 
   <td>recomendado</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Nombre del flujo de trabajo (Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoría principal de DMe</td> 
   <td>event.category</td> 
   <td>required</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Categoría principal (ESCRITORIO, MÓVIL, WEB, PROCESO, SDK, SERVICIO, ECOSISTEMA) - Agrupación de tipos de eventos - <strong>Enviamos Player</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subcategoría</td> 
   <td>event.subcategory</td> 
   <td>recomendado</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Subcategoría: sección de un flujo de trabajo o área de una pantalla, etc. (Archivos recientes, archivos CC, creaciones móviles, etc.).</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de evento/acción</td> 
   <td>event.type</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Tipo de evento (procesar, hacer clic, pellizcar, hacer zoom): acción principal del usuario</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subtipo</td> 
   <td>event.subtype</td> 
   <td>recomendado</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Subtipo de evento (crear, actualizar, eliminar, publicar, etc.) : Detalles adicionales de la acción del usuario</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sin conexión</td> 
   <td>event.offline</td> 
   <td>opcional</td> 
   <td>boolean</td> 
   <td> </td> 
   <td>El evento se generó mientras la acción estaba sin conexión/en línea (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente de usuario</td> 
   <td>event.user_agent</td> 
   <td>recomendado (propiedades web)</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Agente de usuario</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Idioma/configuración regional</td> 
   <td>event.language</td> 
   <td>recomendado</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>La configuración regional del usuario es una cadena basada en las convenciones de etiquetado de idiomas de RFC 3066 (por ejemplo, en-US, fr-FR o es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID del dispositivo</td> 
   <td>event.device_guid</td> 
   <td>opcional</td> 
   <td>cadena<br /> </td> 
   <td>UUID</td> 
   <td>Identifica el GUID del dispositivo (por ejemplo, ID del equipo o hash de la dirección IP + máscara de subred + ID de red + agente de usuario): Aquí enviaremos el nombre de usuario del reproductor generado en el momento del registro.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Recuento</td> 
   <td>event.count</td> 
   <td>opcional</td> 
   <td>número</td> 
   <td> </td> 
   <td>Número de veces que se ha producido el evento : aquí enviamos la duración del vídeo</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Value</td> 
   <td>event.value</td> 
   <td>opcional</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Valor del evento (por ejemplo, configuración activada/desactivada)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>requerido para AA</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Compatibilidad de Adobe Analytics con Nombre de página personalizado</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>opcional</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>URL de la propiedad web o del esquema móvil: debe incluir una URL completa</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Código de error</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Código de error</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de error</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Tipo de error</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descripción de error</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Descripción del error<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Origen/Producto original</em></strong></td> 
   <td>Nombre</td> 
   <td>source.name</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Nombre de la aplicación (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versión</td> 
   <td>source.version</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Versión del firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Plataforma</td> 
   <td>source.platform</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Dispositivo</td> 
   <td>source.device</td> 
   <td>obligatorio con excepciones</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Nombre del reproductor</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versión del SO</td> 
   <td>source.os_version</td> 
   <td>obligatorio con excepciones</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Versión O/S</td> 
  </tr>
  <tr>
   <td><strong><em>Contenido</em></strong></td> 
   <td>Acción</td> 
   <td>content.action</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>La dirección URL del recurso, incluida la representación que se reprodujo</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo Mime</td> 
   <td>content.mimetype</td> 
   <td>opcional</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>Tipo de tiempo del contenido</td> 
  </tr>
  <tr>
   <td><strong><em>Transacción</em></strong></td> 
   <td>Número de transacción</td> 
   <td>trn.number</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td>UUID</td> 
   <td>ID único que se adhiere preferentemente a UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descripción del producto</td> 
   <td>trn.product</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>La URL del recurso (excluida la representación)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Cantidad</td> 
   <td>trn.quantity</td> 
   <td>obligatorio</td> 
   <td>Cadena</td> 
   <td> </td> 
   <td>La duración de la reproducción</td> 
  </tr>
 </tbody>
</table>

