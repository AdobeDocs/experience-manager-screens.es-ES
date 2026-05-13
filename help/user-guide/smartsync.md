---
title: Transición de ContentSync a SmartSync
description: Obtenga más información sobre esa función de SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
TQID: https://experienceleague.adobe.com/hxV3PSzivkechOrO-jmc0NfJ8OH8LccD4-VBXUv8EtE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 452
ht-degree: 1%

---

# Transición de ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

Esta sección proporciona información general sobre la función SmartSync y cómo minimiza la carga/almacenamiento del servidor y el tráfico de red para reducir los costes.

## Información general {#overview}

SmartSync es el último mecanismo utilizado por AEM Screens. Sirve como reemplazo del método actual utilizado para almacenar en caché los canales sin conexión y entregarlos al reproductor.

Se ejecuta tanto en el lado del servidor como en el lado del cliente.

**En el servidor**

* El contenido de los canales, incluidos los recursos, se almacena en caché en *`/var/contentsync`*.
* La caché se expone a los reproductores mediante un manifiesto que describe el contenido disponible para una visualización.

**En el lado del cliente**

* El reproductor actualiza su contenido en función del manifiesto generado anteriormente.

### Ventajas de usar SmartSync {#benefits-of-using-smartsync}

La función SmartSync proporciona varios beneficios a su proyecto de AEM Screens, como los siguientes:

* Reducción drástica del tráfico de red y de los requisitos de almacenamiento del lado del servidor.
* El reproductor descarga recursos de forma inteligente solo si el recurso falta o ha cambiado.
* Optimizaciones de almacenamiento del lado del servidor y del lado del cliente.

>[!NOTE]
>
>Adobe recomienda utilizar SmartSync para proyectos de AEM Screens.

## Migración de ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Si ya ha instalado el paquete de funciones 5 de AEM 6.3 y el paquete de funciones 3 de AEM 6.4, puede habilitar SmartSync para los recursos a fin de mejorar el uso del espacio en disco. Para habilitar SmartSync, siga la sección siguiente para pasar de ContentSync a SmartSync, habilitando así SmartSync.
>
>SmartSync está disponible para Screens Player con servidores compatibles AEM 6.4.3 FP3.
>
>Consulte [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/) para descargar el reproductor más reciente. En la tabla siguiente se describe la versión mínima del reproductor necesaria para cada plataforma:

| **Plataforma** | **Versión Mínima Del Reproductor Admitida** |
|---|---|
| Android™ | 3.3.72 |
| SO CHROME | 1.0.136 |
| Windows | 1.0.136 |

Siga los pasos a continuación para pasar de ContentSync a SmartSync:

1. La migración de ContentSync a SmartSync requiere borrar la caché de ContentSync antes de activar SmartSync.

   Vaya a la consola de ContentSync desde su instancia mediante el vínculo ***https://localhost:4502/libs/cq/contentsync/content/console.html*** y haga clic en **Borrar caché**, como se muestra en la figura siguiente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Se debe borrar toda la caché de contenido antes de utilizar SmartSync por primera vez.

1. Vaya a la **configuración de la consola web de Adobe Experience Manager** mediante AEM instance > hammer icon > **Operaciones** > **Consola web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Se abre la configuración de la consola web de Adobe Experience Manager**. Busque *offlinecontentservice*.

   Para buscar la propiedad **Screens Offline Content Service**, presione **Comando+F** para **Mac** y **Control+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Haga clic en **Guardar** para habilitar la propiedad de **Screens Offline Content Services** y, por lo tanto, use SmartSync para AEM Screens.
1. Cuando haya habilitado SmartSync, vaya al proyecto y haga clic en **Actualizar contenido sin conexión** *(de la barra de acciones),*, como se muestra en la figura siguiente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
