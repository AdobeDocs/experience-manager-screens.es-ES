---
title: Canales sin conexión
seo-title: Canales sin conexión
description: 'El reproductor de AEM Screens proporciona compatibilidad sin conexión con los canales mediante la tecnología ContentSync. Siga esta página para obtener más información sobre los controladores de actualización y la activación de la configuración sin conexión para un canal.  '
seo-description: 'El reproductor de AEM Screens proporciona compatibilidad sin conexión con los canales mediante la tecnología ContentSync. Siga esta página para obtener más información sobre los controladores de actualización y la activación de la configuración sin conexión para un canal.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canales sin conexión {#offline-channels}

El reproductor de Pantallas ofrece compatibilidad sin conexión con los canales mediante la tecnología ***ContentSync*** .

Los reproductores utilizan un servidor http local para proporcionar el contenido sin comprimir.

Cuando se configura un canal para que se ejecute *en línea*, el reproductor proporciona los recursos del canal mediante el acceso al servidor de AEM, pero cuando el canal está configurado para ejecutarse *sin conexión*, el reproductor proporciona los recursos del canal desde un servidor http local.

El flujo de trabajo del proceso es el siguiente:

1. Analizar las páginas que desee
1. Recopilar todos los recursos relacionados
1. Empaquetar todo en un archivo zip
1. Descargue el archivo comprimido y extráigalo localmente
1. Mostrar copia local del contenido

## Controladores de actualización {#update-handlers}

ContentSync ****** utiliza controladores de actualización para analizar y recopilar todas las páginas y recursos necesarios para un proyecto específico. AEM Screens utiliza los siguientes controladores de actualización:

### Opciones comunes {#common-options}

* *type*: tipo de controlador de actualización que se va a utilizar
* *path*: ruta al recurso
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
   <td>extension: extensión del recurso para recopilar<br /> [pathSuffix='']: sufijo para agregar a la ruta del canal<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>recopilar la biblioteca de cliente especificada</td> 
   <td>[extension='']: puede ser css o js, para recopilar solo el primero o solo el segundo</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>recopilar las representaciones de recursos</td> 
   <td>[renditions=[]]: lista de representaciones que se van a recopilar. Valores predeterminados de la representación original</td> 
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

## Activación de la configuración sin conexión para un canal {#enabling-offline-config-for-a-channel}

Siga los pasos a continuación para habilitar la configuración sin conexión para un canal:

1. Inspeccione el contenido del canal y compruebe si se solicita desde una instancia de AEM (en línea).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. **Vaya al panel de canales y haga clic en**... en el **panel INFORMACIÓN** DEL CANAL para cambiar las propiedades.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Vaya a las propiedades del canal y asegúrese de que la casilla de verificación está desactivada en la ficha **Canal** . Haga clic en **Guardar y cerrar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes de que el contenido se implemente correctamente en el dispositivo, haga clic en **Actualizar contenido** sin conexión.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   El estado **Sin conexión** en **PROPERTIES** también se actualiza en consecuencia.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspeccione el contenido del canal y compruebe si se solicita desde la caché del reproductor local.

   ![chlimage_1-26](assets/chlimage_1-26.png)
