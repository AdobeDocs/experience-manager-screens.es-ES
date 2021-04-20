---
title: Uso de Chrome Player como extensión
seo-title: Uso de Chrome Player como extensión
description: Siga esta página para obtener más información sobre la instalación del reproductor Chrome como extensión del explorador.
seo-description: nulo
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---


# Uso de Chrome Player como extensión {#using-chrome-player}

El reproductor ChromeOS se puede instalar como complemento del explorador Chrome en el modo de desarrollador sin necesidad de un dispositivo de reproducción Chrome.

>[!CAUTION]
>
> Se recomienda utilizar Chrome Player como extensión para solucionar problemas en demostraciones rápidas, depuración y también para solucionar problemas de clientes. Este mecanismo no debe utilizarse para implementaciones de producción que requieran el modo de quiosco y la administración central.

Siga esta página para obtener más información sobre la instalación del reproductor Chrome como extensión del explorador.

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar la última versión de Chrome Player.

1. Descomprima y guárdelo en el disco.

1. Abra el explorador Chrome, haga clic en el menú de 3 puntos y seleccione **Más herramientas** en **Extensiones**, en la esquina superior derecha, o navegue directamente a `chrome://extensions`.

1. Active el modo **Developer** desde la esquina superior derecha.

1. Haga clic en **Cargar desempaquetado** desde la esquina superior izquierda y cargue el reproductor Chrome descomprimido.

1. Compruebe el complemento de AEM Screens Chrome Player si está disponible en la lista de extensiones.

1. Abra una nueva pestaña y haga clic en el icono Aplicaciones en la esquina superior izquierda, o navegue directamente a `chrome://apps`.

1. Haga clic en **AEM Screens Plugin** para iniciar Chrome Player.
   >[!NOTE]
   >
   > De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **esc** para salir del modo de pantalla completa.


## Sugerencias de depuración avanzadas {#advanced-debugging-tips}

1. Una vez que el reproductor haya descargado contenido localmente, puede examinar el contenido descargado localmente en `http://localhost:24502`.

   >[!NOTE]
   >
   > Si la URL mencionada anteriormente no funciona, significa que al reproductor no se le asigna una pantalla o que el contenido no se ha descargado correctamente. Compruebe la pestaña red para ver si el JSON de configuración del reproductor ha obtenido los detalles correctos y si hay algún problema de red en la descarga.

1. Puede hacer clic con el botón derecho e inspeccionar tres capas del reproductor de Chrome
   **Depurar contenido**: Haga clic con el botón derecho e inspeccione el contenido para depurar el contenido en ejecución (debe haber un solo elemento llamado &quot;Inspect&quot; en el menú contextual)

   **firmware** de depuración: Acceda a la interfaz de usuario de administración y haga clic con el botón derecho e inspeccione para depurar el código de firmware (reproductor) (debe haber una opción para inspeccionar e inspeccionar la página de fondo y simular el reinicio del explorador)

   **Depurar página** de fondo: Acceda a la interfaz de usuario de administración y haga clic con el botón derecho e inspeccione la página de fondo (para servicios en segundo plano como el servidor http)

## Actualización de la extensión del reproductor {#upgrading-player}

Siga los pasos a continuación para actualizar la extensión del reproductor si se lanza una nueva versión del mismo. También puede seguir las instrucciones que se indican a continuación para probar los escenarios de actualización:

1. Cierre las instancias de Chrome y del reproductor en ejecución
1. Cambiar el nombre de la carpeta antigua con archivos de reproductor
1. Extraiga el nuevo zip en la misma ubicación que la carpeta antigua
1. Inicie Chrome y vaya a `chrome://extensions`
1. Marque el icono del reproductor y haga clic en el botón actualizar o volver a cargar