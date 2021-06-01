---
title: Transición de ContentSync a SmartSync
seo-title: Transición de ContentSync a SmartSync
description: Siga esta página para obtener más información sobre la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
seo-description: Siga esta página para obtener más información sobre la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: Administración de Screens
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---


# Transición de ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

En esta sección se proporciona información general sobre la función SmartSync y cómo minimiza la carga/almacenamiento del servidor y el tráfico de red para reducir los costes.

## Información general {#overview}

SmartSync es el mecanismo más reciente utilizado por AEM Screens. Sirve como reemplazo del método actual utilizado para almacenar en caché los canales sin conexión y entregarlos al reproductor.

Se ejecuta en el lado del servidor y en el lado del cliente.

**En el servidor**:

* El contenido de los canales, incluidos los recursos, se almacena en caché en */var/contentsync*.
* La caché se expone a los reproductores a través de un manifiesto que describe el contenido disponible para una visualización.

**En el lado** del cliente:

* El reproductor actualiza su contenido en función del manifiesto generado anteriormente.

### Beneficios del uso de SmartSync {#benefits-of-using-smartsync}

La función SmartSync ofrece una serie de ventajas a su proyecto de AEM Screens. Permite

* Reducción drástica del tráfico de red y de los requisitos de almacenamiento del lado del servidor
* El reproductor descarga los recursos de forma inteligente solo si el recurso falta o se cambia
* Optimizaciones de almacenamiento de información del lado del servidor y del lado del cliente

>[!NOTE]
>
>Adobe recomienda encarecidamente usar SmartSync para proyectos de AEM Screens.

## Migración de ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Si ya ha instalado AEM 6.3 Feature Pack 5 y AEM 6.4 Feature Pack 3, puede habilitar SmartSync para recursos para mejorar el uso del espacio en disco. Para habilitar SmartSync, siga la sección siguiente para pasar de ContentSync a SmartSync, habilitando SmartSync.
>
>SmartSync está disponible para Screens Player con servidores compatibles AEM 6.4.3 FP3.
>
>Consulte [Descargas del reproductor de AEM Screens](https://download.macromedia.com/screens/) para descargar el reproductor más reciente. La siguiente tabla describe la versión mínima del reproductor necesaria para cada plataforma:

| **Plataforma** | **Versión mínima del reproductor compatible** |
|---|---|
| Android | 3,3,72 |
| Sistema operativo Chrome | 1,0,136 |
| Windows | 1,0,136 |

Siga los pasos a continuación para pasar de ContentSync a SmartSync:

1. La migración de ContentSync a SmartSync requiere la limpieza de la caché de ContentSync antes de activar SmartSync.

   Vaya a la consola ContentSync desde su instancia mediante el enlace ***https://localhost:4502/libs/cq/contentsync/content/console.html*** y haga clic en **Borrar caché**, como se muestra en la figura siguiente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Toda la caché de contenido debe borrarse antes de usar SmartSync por primera vez.

1. Vaya a **Configuración de la consola web de Adobe Experience Manager** mediante AEM instancia —> icono de martillo —> **Operaciones** —> **Consola web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Se abre la** configuración de la consola web de Adobe Experience Manager. Busque *offlinecontentservice*.

   Para buscar la propiedad **Screens Offline Content Service**, presione **Command+F** para **Mac** y **Control+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Haga clic en **Guardar** para habilitar la propiedad **Screens Offline Content Services** y, por lo tanto, utilice SmartSync para AEM Screens.
1. Una vez que haya habilitado SmartSync, debe navegar hasta el proyecto y hacer clic en **Actualizar contenido sin conexión** *(en la barra de acciones),* como se muestra en la figura siguiente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)