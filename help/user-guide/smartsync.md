---
title: Transición de ContentSync a SmartSync
seo-title: Transición de ContentSync a SmartSync
description: Siga esta página para conocer la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
seo-description: Siga esta página para conocer la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 112aa2a89578243bad49e61839d781e0f29893b4
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# Transición de ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

Esta sección proporciona información general sobre la función SmartSync y cómo minimiza la carga/almacenamiento del servidor y el tráfico de red para reducir los costes.

## Información general {#overview}

SmartSync es el mecanismo más reciente utilizado por AEM Screens. Sirve como reemplazo del método actual utilizado para almacenar en caché canales sin conexión y entregarlos al reproductor.

Se ejecuta tanto en el lado del servidor como en el lado del cliente.

**En el servidor**:

* El contenido de los canales, incluidos los recursos, se almacena en caché en */var/contentsync*.
* La caché se expone a los reproductores mediante un manifiesto que describe el contenido disponible para una visualización.

**En el lado** del cliente:

* Player actualiza su contenido en función del manifiesto generado anteriormente.

### Ventajas de utilizar SmartSync {#benefits-of-using-smartsync}

La función SmartSync ofrece una serie de ventajas para el proyecto de AEM Screens. Permite

* Reducción drástica de los requerimientos de tráfico de red y almacenamiento del lado del servidor
* El reproductor descarga los recursos de forma inteligente solo si el recurso falta o se cambia
* Optimizaciones de almacenamiento del lado del servidor y del lado del cliente

>[!NOTE]
>
>Adobe recomienda encarecidamente utilizar los proyectos de SmartSync para AEM Screens.

## Migración de ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Si ya ha instalado AEM 6.3 Feature Pack 5 y AEM 6.4 Feature Pack 3, puede activar SmartSync para los recursos para mejorar el uso del espacio en disco. Para habilitar SmartSync, siga la sección siguiente para la transición de ContentSync a SmartSync, habilitando SmartSync.
>
>SmartSync está disponible para Screens Player con servidores compatibles con AEM 6.4.3 FP3.
>
>Consulte Descargas [](https://download.macromedia.com/screens/) de AEM Screens Player para descargar el último reproductor. La siguiente tabla describe la versión mínima del reproductor requerida para cada plataforma:

| **Plataforma** | **Versión mínima del reproductor admitida** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

Siga los pasos a continuación para la transición de ContentSync a SmartSync:

1. La migración de ContentSync a SmartSync requiere borrar la caché de ContentSync antes de activar SmartSync.

   Vaya a la consola ContentSync desde su instancia mediante el vínculo ***https://localhost:4502/libs/cq/contentsync/content/console.html*** y haga clic en **Borrar caché**, como se muestra en la figura siguiente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Se debe borrar toda la caché de contenido antes de utilizar SmartSync por primera vez.

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Configuración de la consola web de Adobe Experience Manager **se abre. Busque *offlinecontentservice*.

   Para buscar la propiedad **Screens Offline Content Service** , pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Haga clic en **Guardar** para habilitar la propiedad **Screens Offline Content Services** y, por tanto, utilice SmartSync para pantallas AEM.
1. Una vez que haya habilitado SmartSync, debe navegar hasta el proyecto y hacer clic en **Actualizar contenido** sin conexión *(en la barra de acciones),* como se muestra en la figura siguiente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)