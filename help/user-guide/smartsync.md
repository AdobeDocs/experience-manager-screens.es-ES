---
title: Transición de ContentSync a SmartSync
seo-title: Transitioning from ContentSync to SmartSync
description: Siga esta página para obtener más información sobre la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
seo-description: Follow this page to learn about SmartSync feature and how you can transition from ContentSync to SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# Transición de ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

Esta sección proporciona información general sobre la función SmartSync y cómo minimiza la carga/almacenamiento del servidor y el tráfico de red para reducir los costes.

## Información general {#overview}

SmartSync es el último mecanismo utilizado por AEM Screens. Sirve como reemplazo del método actual utilizado para almacenar en caché los canales sin conexión y entregarlos al reproductor.

Se ejecuta tanto en el lado del servidor como en el lado del cliente.

**Del lado del servidor**:

* El contenido de los canales, incluidos los recursos, se almacena en caché en */var/contentsync*.
* La caché se expone a los reproductores a través de un manifiesto que describe el contenido disponible para una visualización.

**Del lado del cliente**:

* El reproductor actualiza su contenido en función del manifiesto generado anteriormente.

### Ventajas de usar SmartSync {#benefits-of-using-smartsync}

La función SmartSync proporciona varias ventajas a su proyecto de AEM Screens. Permite

* Reducción drástica del tráfico de red y de los requisitos de almacenamiento del lado del servidor
* El reproductor descarga recursos de forma inteligente solo si el recurso falta o ha cambiado
* Optimizaciones del almacenamiento del lado del servidor y del lado del cliente

>[!NOTE]
>
>El Adobe recomienda encarecidamente no utilizar SmartSync para proyectos de AEM Screens.

## Migración de ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>AEM AEM Si ya ha instalado el paquete de funciones 5 de la versión 6.3 y el paquete de funciones 3 de la versión 6.4 de la versión 6.3, puede habilitar SmartSync para que los recursos mejoren el uso del espacio en disco. Para habilitar SmartSync, siga la sección siguiente para pasar de ContentSync a SmartSync, habilitando así SmartSync.
>
>AEM SmartSync está disponible para el reproductor Screens con servidores compatibles con el FP3 de la versión 6.4.3 de la aplicación.
>
>Consulte la [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/) para descargar el último reproductor. En la tabla siguiente se describe la versión mínima del reproductor necesaria para cada plataforma:

| **Plataforma** | **Versión mínima del reproductor admitida** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

Siga los pasos a continuación para pasar de ContentSync a SmartSync:

1. La migración de ContentSync a SmartSync requiere borrar la caché de ContentSync antes de activar SmartSync.

   Navegue hasta la consola de ContentSync desde la instancia mediante el vínculo ***https://localhost:4502/libs/cq/contentsync/content/console.html*** y haga clic en **Borrar caché**, como se muestra en la figura siguiente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Se debe borrar toda la caché de contenido antes de utilizar SmartSync por primera vez.

1. Vaya a **Configuración de la consola web Adobe Experience Manager** AEM vía instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Configuración de la consola web Adobe Experience Manager** abre. Buscar por *offlinecontentservice*.

   Para buscar en **Servicio de contenido sin conexión de Screens** propiedad, presione **Comando + F** para **Mac** y **Control + F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Clic **Guardar** para habilitar el **Servicios de contenido sin conexión de Screens** y, por lo tanto, utilice SmartSync para AEM Screens.
1. Una vez que haya habilitado SmartSync, debe desplazarse al proyecto y hacer clic en **Actualizar contenido sin conexión** *(de la barra de acciones),* como se muestra en la figura siguiente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
