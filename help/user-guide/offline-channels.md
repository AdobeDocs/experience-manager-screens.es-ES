---
title: Canales sin conexión
description: Obtenga más información acerca de cómo el Reproductor de AEM Screens proporciona compatibilidad sin conexión para canales mediante el uso de la tecnología ContentSync.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Canales sin conexión {#offline-channels}

El reproductor Screens proporciona compatibilidad sin conexión para los canales mediante el uso de la tecnología ***ContentSync***.

Los reproductores utilizan un servidor http local para proporcionar el contenido descomprimido.

AEM Cuando un canal está configurado para ejecutar *en línea*, el reproductor sirve los recursos del canal al acceder al servidor de. Sin embargo, cuando el canal está configurado para ejecutar *offline*, el reproductor proporciona los recursos de canal desde un servidor http local.

El flujo de trabajo para el proceso es el siguiente:

1. Analice las páginas que desee.
1. Recopilar todos los recursos relacionados.
1. Empaquete todo en un archivo zip.
1. Descargue el zip y extráigalo localmente.
1. Mostrar una copia local del contenido.

## Actualizar controladores {#update-handlers}

***ContentSync*** usa controladores de actualización para analizar y recopilar todas las páginas y recursos necesarios para un proyecto específico. AEM Screens utiliza los siguientes controladores de actualización:

### Opciones comunes {#common-options}

* *tipo*: el tipo de controlador de actualización que se va a utilizar
* *ruta*: ruta al recurso
* *[targetRootDirectory]*: carpeta de destino en el archivo zip

<table>
 <tbody>
  <tr>
   <td><strong>Tipo</strong></td> 
   <td><strong>Descripción</strong></td> 
   <td><strong>Opciones</strong></td> 
  </tr>
  <tr>
   <td><code>channels</code></td> 
   <td>recopila un canal</td> 
   <td>extensión: extensión del recurso que se va a recopilar<br /> [pathSuffix='']: sufijo que se va a agregar a la ruta de acceso del canal <br /> </td> 
  </tr>
  <tr>
   <td><code>clientlib</code></td> 
   <td>recopilar la biblioteca de cliente especificada</td> 
   <td>[extension='']: puede ser css o js, para recopilar solo el primero o solo el segundo</td> 
  </tr>
  <tr>
   <td><code>assetrenditions</code></td> 
   <td>recopilar las representaciones de recursos</td> 
   <td>[renditions=[]]: lista de representaciones que recopilar. Valores predeterminados de la representación original</td> 
  </tr>
  <tr>
   <td><code>copy</code></td> 
   <td>copiar la estructura especificada de la ruta</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Probando configuración de ContentSync {#testing-contentsync-configuration}

Siga los pasos a continuación para probar la configuración de ContentSync:

1. Abra `https://localhost:4502/libs/cq/contentsync/content/console.html`.
1. Haga clic en la configuración en la lista.
1. Haga clic en **Borrar caché**.
1. Haga clic en **Actualizar caché**.
1. Haga clic en **Descargar completo**.
1. Extraiga el archivo zip.
1. Inicie un servidor local en la carpeta extraída.
1. Abra la página de inicio y compruebe el estado de la aplicación.

## Habilitar la configuración sin conexión para un canal {#enabling-offline-config-for-a-channel}

Siga los pasos a continuación para habilitar la configuración sin conexión para un canal:

1. Inspect AEM el contenido del canal y compruebe si se solicita desde una instancia de (en línea).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Vaya al panel de canales.
1. Haga clic en **...** en el panel **INFORMACIÓN DEL CANAL**.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Vaya a las propiedades del canal.
1. En la ficha (Canal), asegúrese de que la casilla de verificación esté deshabilitada y luego haga clic en **Guardar y cerrar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes de implementar el contenido correctamente en el dispositivo, haga clic en **Actualizar contenido sin conexión**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   El estado de **Sin conexión** en **PROPIEDADES** también se actualiza en consecuencia.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect el contenido del canal y compruebe si se solicita desde la caché del reproductor local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Obtenga información acerca de la plantilla para controladores de recursos sin conexión personalizados. Además, obtenga más información acerca de los requisitos mínimos de `pom.xml` para el proyecto. Vea [Plantilla para controladores personalizados](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) en **Desarrollo de un componente personalizado para AEM Screens**.
