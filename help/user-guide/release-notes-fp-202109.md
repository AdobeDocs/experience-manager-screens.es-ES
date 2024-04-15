---
title: Notas de la versión del paquete de funciones 202109
description: Obtenga información acerca del paquete de funciones 202109 de AEM Screens lanzado el 23 de septiembre de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 1%

---

# Notas de la versión del paquete de funciones 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>El Adobe recomienda actualizar a la última versión de Adobe Experience Manager AEM (). AEM Screens AEM proporciona soporte de mantenimiento para la plataforma Screens de 6.3.

## Disponibilidad {#availability}

AEM Screens AEM ha lanzado el paquete de funciones 9 de la versión 6.5.

Puede descargar el paquete de funciones más reciente para la versión 6.5.9 de AEM Screens en [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a **Adobe Experience Manager** pestaña y busque **Screens** para obtener el último paquete de funciones titulado **AEM Pantallas FP9 de 6.5**.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del AEM Screens Feature Pack 202109 es el 23 de septiembre de 2021.

### Novedades {#what-is-new}

* **Compatibilidad con miniaturas para vídeos**

  Ahora se admite la compatibilidad con miniaturas para vídeos en AEM Screens. Un autor de contenido define una miniatura para los vídeos, de modo que la imagen se utilice como marcador de posición. También prueban correctamente la reproducción y la segmentación del contenido, mientras que el equipo correspondiente finaliza el vídeo real. La imagen también se puede utilizar en caso de que falle la reproducción del vídeo.
Consulte [Compatibilidad con miniaturas para vídeos](/help/user-guide/thumbnail-support.md) para obtener más información.

* **Monitorización de reproducción básica**

  AEM Screens ahora admite la monitorización básica de la reproducción. El reproductor ahora informa de varias métricas de reproducción con cada ping (el valor predeterminado es de 30 segundos). En función de las métricas, detecta varios casos extremos (experiencia atascada, pantalla en blanco, problema de programación, etc.). Esta función permite que el equipo supervise de forma remota si un reproductor está reproduciendo el contenido correctamente y mejora la reacción a pantallas en blanco o experiencias rotas en el campo. También reduce el riesgo de mostrar una experiencia rota al usuario final.
Consulte [Monitorización de reproducción básica](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring) para obtener más información.

* **Actualizaciones del informe de asignación de contenido**

  El informe de asignación de contenido ahora está optimizado y mejorado con una experiencia de usuario mejorada. El informe descargable muestra entidades mejoradas relacionadas con el reproductor, como ubicaciones, visualizaciones y dispositivos en una pestaña de hoja de cálculo, y la información del proveedor de contenido, como canales y recursos en otra pestaña.
Consulte [Informe de asignación de contenido](/help/user-guide/content-assignment-report.md) para obtener más información.

* **Representaciones adaptables**

  Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente.

  Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Consulte [Representaciones adaptables: Información general de arquitectura y configuraciones](/help/user-guide/adaptive-renditions.md) para obtener más información.

  Además, como autor de contenido de AEM Screens, puede configurar sus recursos para que utilicen representaciones adaptables. También puede migrar los dispositivos de redes grandes para que utilicen esta función en sus canales de AEM Screens. Consulte [Uso de representaciones adaptables en AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obtener más información.

* **Compatibilidad con manifiestos de la versión 3**

  Ahora puede configurar Dispatcher para la versión de manifiesto v3. Para habilitar el manifiesto v3, haga lo siguiente:

   * Borre todos los trabajos de contenido sin conexión pendientes tanto en la creación como en la publicación.

      * Vaya al CRXDE Lite en Autor y Publicación.

      * Seleccione Herramientas > Consulta.

      * En la consulta, utilice `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * Esto enumera cualquier trabajo de contenido sin conexión que se esté ejecutando o esté pendiente en la cola.

      * Espere hasta que no haya más trabajos de contenido sin conexión devueltos desde la consulta.

   * Deshabilitar ContentSync en `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Habilitar SmartSync en `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Actualice Dispatcher.

   * Actualizar componente personalizado.


   * Consulte [Configurar Dispatcher para la versión 3 del manifiesto](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) para obtener más información.
   * Si utiliza componentes personalizados como parte de manifiestos de la versión 3, consulte [Plantilla para controladores personalizados](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Correcciones de errores {#bug-fixes}

**Lado del reproductor**

* Se han resuelto errores de almacenamiento en caché de archivos reemplazando recursos por representaciones.

* Los reproductores ahora solo exponen las representaciones de recursos si la asignación de representaciones está presente.

* Ping mejorado para volver a autenticar si la respuesta no es un archivo JSON válido.

* Los nombres o roles de los canales numéricos provocaban una pantalla en blanco.

* Descargar representaciones optimizadas mediante SmartSync.

* Se ha transformado la asignación en una lista de claves de representación.

* Acceso eliminado a `cmd.exe` y `reg.exe` en el reproductor de windows.

* Un reproductor debe informar de su último evento de reproducción correcta.

* Un reproductor debe informar de su estado de reproducción.

* El reproductor no vuelve a descargar los recursos cuando `ALL` Se ha borrado la caché.

* Como administrador de reproductor, ahora puede elegir un nombre de reproductor.

* La eliminación de la asignación del canal de la pantalla no se refleja en el reproductor.

* Si el reproductor se vuelve a cargar mientras se descarga la actualización del canal, el reproductor ignora la actualización.

* El componente de página incrustada ahora respeta el evento táctil.

* Ahora se admite el aprovisionamiento remoto del reproductor Tizen.

**Lado del servidor**

* El vídeo de destino no se muestra
* Condiciones de carrera en la difusión de datos de visualización a las subsecuencias.

* La vista previa de canal no funciona para canales que contienen vídeos.

* Modo de vista previa que muestra en blanco para el canal de pantalla dividida.

* Las miniaturas de vídeo se muestran en blanco con las representaciones adaptables habilitadas.

* Actualizar automáticamente el manifiesto de canal si se publica la página a la que se hace referencia.

* Los dispositivos eliminados ahora no bloquean la cola de replicación de Screens.

* El manifiesto no contenía contenido de destino ni páginas incrustadas de Sites. Esto se ha corregido.

* Ahora se agrega un nuevo componente de imagen principal al manifiesto de canal.

* Ahora se admite la descarga de representaciones optimizadas mediante SmartSync.

* Reproducir la representación optimizada para todos los recursos.

* Se ha agregado compatibilidad con varios tipos de proveedores de contenido

* La estrategia de reproducción de secuencias incrustadas se ha dañado y esto se ha corregido.

* Manifiesto sin conexión mediante el parámetro de solicitud `wcmmode` para la entrada html, lo que la hace inalmacenable en caché.

* La secuencia incrustada dinámica vacía a veces provocaba que la pantalla estuviera en blanco.

* El reproductor ahora informa de su estado de reproducción.

* Se estaba reproduciendo el vídeo en `Tiny mode` y no se reproduce como vídeo de pantalla completa en el dispositivo, y el problema se ha corregido.

### Reproductores de AEM Screens publicados

Los siguientes reproductores de AEM Screens AEM se incluyen en el paquete de funciones 9 de la versión 6.5 de:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Descargas del reproductor AEM Screens

Para descargar el último reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/index.html)**.
