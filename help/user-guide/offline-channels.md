---
title: Canales sin conexión
seo-title: Canales sin conexión
description: 'El reproductor AEM Screens ofrece compatibilidad con canales sin conexión gracias a la tecnología ContentSync. Siga esta página para obtener más información sobre los controladores de actualización y la activación de la configuración sin conexión para un canal.  '
seo-description: 'El reproductor AEM Screens ofrece compatibilidad con canales sin conexión gracias a la tecnología ContentSync. Siga esta página para obtener más información sobre los controladores de actualización y la activación de la configuración sin conexión para un canal.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---


# Canales sin conexión {#offline-channels}

El reproductor Screens proporciona compatibilidad con los canales sin conexión gracias a la tecnología ***ContentSync***.

Los reproductores utilizan un servidor http local para ofrecer el contenido descomprimido.

Cuando un canal está configurado para ejecutarse *en línea*, el reproductor proporciona los recursos del canal accediendo al servidor de AEM, pero cuando el canal está configurado para ejecutar *offline*, el reproductor sirve los recursos del canal desde un servidor http local.

El flujo de trabajo del proceso es el siguiente:

1. Analizar las páginas deseadas
1. Recopilar todos los recursos relacionados
1. Empaquete todo en un archivo zip
1. Descargue el zip y extráigalo localmente
1. Mostrar copia local del contenido

## Actualizar controladores {#update-handlers}

El ***ContentSync*** utiliza controladores de actualización para analizar y recopilar todas las páginas y recursos necesarios para un proyecto específico. AEM Screens utiliza los siguientes controladores de actualización:

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
   <td>canales</td> 
   <td>recopila un canal</td> 
   <td>extensión: extensión del recurso para recopilar<br /> [pathSuffix='']: sufijo que se agregará a la ruta de acceso del canal<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>recopilar la biblioteca de cliente especificada</td> 
   <td>[extension='']: puede ser css o js, para recopilar solo el primero o solo el segundo</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>recopilar las representaciones de recursos</td> 
   <td>[renditions=[]]: lista de representaciones que desea recopilar. El valor predeterminado es la representación original</td> 
  </tr>
  <tr>
   <td>copia</td> 
   <td>copiar la estructura especificada de la ruta</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Prueba de la configuración de ContentSync {#testing-contentsync-configuration}

Siga los pasos a continuación para probar la configuración de ContentSync:

1. Abra `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Seleccione la configuración en la lista
1. Haga clic en Borrar caché
1. Haga clic en Actualizar caché
1. Haga clic en Descargar completo
1. Extraer el archivo zip
1. Iniciar un servidor local en la carpeta extraída
1. Abra la página de inicio y compruebe el estado de la aplicación

## Habilitación de la configuración sin conexión para un canal {#enabling-offline-config-for-a-channel}

Siga los pasos a continuación para habilitar la configuración sin conexión para un canal:

1. Inspect indica el contenido del canal y comprueba si se solicita desde una instancia de AEM (en línea).

   ![imagen_1-24](assets/chlimage_1-24.png)

1. Vaya al panel del canal y haga clic en **...** en el panel **INFORMACIÓN DE CANAL** para cambiar las propiedades.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Vaya a las propiedades del canal y asegúrese de que la casilla de verificación está desactivada en la pestaña **Channel**. Haga clic en **Guardar y cerrar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes de que el contenido se implemente correctamente en el dispositivo, haga clic en **Actualizar contenido sin conexión**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   El estado **Offline** en **PROPERTIES** también se actualiza en consecuencia.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect el contenido del canal y compruebe si se solicita desde la caché del reproductor local.

   ![imagen_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Para obtener más información sobre la plantilla para controladores de recursos sin conexión personalizados y los requisitos mínimos en `pom.xml` para ese proyecto específico, consulte [Plantilla para controladores personalizados](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) en **Desarrollo de un componente personalizado para AEM Screens**.