---
title: Notas de la versión para Feature Pack 202109
description: Siga esta página para obtener información sobre el paquete de funciones 202105 de AEM Screens, publicado el 23 de septiembre de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: 375024848ed736104add828251ea494406a4f7ba
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---

# Notas de la versión para Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Se recomienda actualizar a la última versión de Adobe Experience Manager (AEM). Screens proporciona compatibilidad con el mantenimiento de AEM plataforma Screens 6.3.

## Disponibilidad {#availability}

AEM Screens ha lanzado AEM 6.5 Feature Pack 9.

Puede descargar el último paquete de funciones para la versión 6.5.9 de AEM Screens desde el [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) con su Adobe ID. Vaya a la pestaña **Adobe Experience Manager** y busque **Screens** para obtener el último feature pack titulado como **AEM 6.5 Screens FP9**.

## Fecha de la versión {#release-date}

La fecha de versión del Feature Pack 202109 de AEM Screens es el 23 de septiembre de 2021.

### Novedades {#what-is-new}

* **Compatibilidad con miniaturas para vídeos**

   Compatibilidad con miniaturas para vídeos en ahora se admite en AEM Screens. Un autor de contenido puede definir una miniatura para los vídeos, de modo que la imagen pueda utilizarse como marcador de posición y probar correctamente la reproducción y el destino del contenido, mientras el equipo adecuado está finalizando el vídeo en sí. También se puede utilizar la imagen en caso de que falle la reproducción del vídeo.
Consulte Compatibilidad con miniaturas para vídeos para obtener más información.

* **Monitorización de reproducción básica**

   AEM Screens ahora es compatible con la monitorización de reproducción básica. El reproductor ahora informará de varias métricas de reproducción con cada ping (el valor predeterminado es de 30 segundos). En función de las métricas, proporciona la capacidad de detectar varios casos extremos (experiencia atascada, pantalla en blanco, problema de programación, etc.). Esta función permite que el equipo supervise de forma remota si un reproductor está reproduciendo contenido correctamente, mejora la reacción a pantallas en blanco o experiencias rotas en el campo y disminuye el riesgo de mostrar una experiencia rota al usuario final.
Consulte Supervisión de reproducción básica para obtener más información.

* **Actualizaciones del informe de asignación de contenido**

   El informe de asignación de contenido ahora se optimiza y mejora con la experiencia del usuario mejorada. El informe descargable muestra las entidades mejoradas relacionadas con el reproductor, como ubicaciones, visualizaciones y dispositivos, en una ficha de hoja de cálculo, así como la información del proveedor de contenido, como los canales y los recursos, en otra ficha.

* **Representaciones adaptables**

   Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente.

   Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Consulte Representaciones adaptables: Información general de arquitectura y configuraciones para obtener más información.

   Además, como autor de contenido de AEM Screens, ahora puede utilizar Representaciones adaptables en su proyecto de AEM Screens y aplicar también una estrategia de migración para redes grandes. Consulte Uso de representaciones adaptables para obtener más información.

* **Compatibilidad con los manifiestos V3**

   Ahora puede configurar Dispatcher para la versión de manifiesto v3. Consulte [Configuración de Dispatcher para la versión de manifiesto v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) para obtener más información.
Además, si está utilizando componentes personalizados como parte de manifiestos v3, consulte [Plantilla para controladores personalizados](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).


### Corrección de errores {#bug-fixes}

**Lado del reproductor**

* Se han resuelto errores de almacenamiento en caché de archivos al reemplazar recursos por representaciones.

* Los reproductores ahora solo muestran las representaciones de recursos si está presente la asignación de representación.

* Ahora puede configurar alertas de demora basadas en registros de fragmento.

* ping mejorado para volver a autenticarse si la respuesta no es JSON válida.

* Los nombres y roles de canales numéricos provocaron una pantalla en blanco.

* Descargue representaciones optimizadas mediante SmartSync.

* Se ha transformado la asignación en una lista de claves de representación.

* Se ha eliminado el acceso a `cmd.exe` y `reg.exe` en el reproductor de windows.

* Un reproductor debe informar de su último evento de reproducción exitoso.

* Un reproductor debe informar de su estado de reproducción.

* El reproductor no vuelve a descargar Assets cuando se borra la caché `ALL`.

* Como administrador del reproductor, ahora puede elegir un nombre de reproductor.

* La eliminación de la asignación de canal de la visualización no se refleja en el reproductor.

* Si el reproductor se vuelve a cargar mientras se descarga la actualización del canal, el reproductor ignora la actualización.

* El componente de página integrada ahora respeta el evento táctil.

* Ahora se admite el aprovisionamiento remoto del reproductor Tizen.

**Servidor**

* El vídeo de Target no se muestra
* Condición de carrera al transmitir datos de visualización a las subsecuencias.

* La vista previa del canal no funciona para los canales que contienen vídeos.

* El modo de vista previa se muestra en blanco para el canal de pantalla dividido.

* Las miniaturas de vídeo se representan en blanco con las representaciones adaptables habilitadas.

* Actualice automáticamente el manifiesto de canal si se publica la página a la que se hace referencia.

* Los dispositivos eliminados ahora no bloquean la cola de replicación de Screens.

* El manifiesto no contenía contenido de destino ni páginas incrustadas de Sites. Esto se ha corregido.

* El nuevo componente de imagen principal ahora se agrega al manifiesto del canal.

* Ahora se admite la descarga de representaciones optimizadas mediante SmartSync.

* Reproducir la representación optimizada para todos los recursos.

* Se agregó compatibilidad con varios tipos de proveedores de contenido

* La estrategia de reproducción de secuencias incrustadas se ha interrumpido y esto se ha corregido.

* Manifiesto sin conexión utilizando el parámetro de solicitud `wcmmode` para la entrada html, lo que hace que no se pueda almacenar en caché.

* La secuencia integrada dinámica vacía a veces causaba una pantalla en blanco.

* El reproductor ahora informa de su estado de reproducción.

* El vídeo se estaba reproduciendo en `Tiny mode` y no se reproduciendo como vídeo de pantalla completa en el dispositivo, por lo que el problema se ha solucionado ahora.

### Reproductores de AEM Screens publicados {#released-aem-screens-players}

Los siguientes reproductores de AEM Screens están disponibles para AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Descargas del reproductor de AEM Screens  {#aem-screens-player-downloads}

Para descargar el último reproductor de AEM Screens y obtener más información sobre las correcciones de errores, consulte **[Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/index.html)**.