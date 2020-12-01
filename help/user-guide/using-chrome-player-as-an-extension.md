---
title: Uso de Chrome Player como extensión
seo-title: Uso de Chrome Player como extensión
description: nulo
seo-description: nulo
translation-type: tm+mt
source-git-commit: 1753009451e4bed75eb8241bcca887f7abe2f77b
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Uso de Chrome Player como extensión {#using-chrome-player}

El reproductor ChromeOS se puede instalar como complemento Chrome Browser en el modo de desarrollador sin necesidad de un dispositivo de reproducción Chrome.

>[!CAUTION]
>
> Se recomienda utilizar Chrome Player como extensión para solucionar problemas con demostraciones rápidas, depuración y también para solucionar problemas de los clientes. Este mecanismo no debe utilizarse para implementaciones de producción que requieran el modo de quiosco y la administración central.

Siga esta página para obtener información sobre la instalación del reproductor de Chrome como extensión del navegador.

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar la versión más reciente de Chrome Player.

1. Descomprima y guárdelo en el disco.

1. Abra el navegador Chrome y haga clic en el menú de 3 puntos y seleccione **Más herramientas** de **Extensiones** ubicado en la esquina superior derecha o navegue directamente a `chrome://extensions`.

1. Active el modo **Desarrollador** desde la esquina superior derecha.

1. Haga clic en **Cargar sin empaquetar** desde la esquina superior izquierda y cargue el reproductor Chrome sin comprimir.

1. Compruebe el complemento AEM Screens Chrome Player si está disponible en la lista de extensiones.

1. Abra una nueva ficha y haga clic en el icono Aplicaciones en la esquina superior izquierda o navegue directamente a `chrome://apps`.

1. Haga clic en **Complemento de AEM Screens** para iniciar Chrome Player.
   >[!NOTE]
   >
   > De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **esc** para salir del modo de pantalla completa.


## Sugerencias de depuración avanzadas {#advanced-debugging-tips}

1. Una vez que el reproductor haya descargado contenido localmente, puede examinar el contenido descargado localmente si ingresa a `http://localhost:24502`.

   >[!NOTE]
   >
   > Si la URL mencionada anteriormente no funciona, significa que el reproductor no tiene asignada una visualización o que el contenido no se ha descargado correctamente. Compruebe la ficha de red del JSON de configuración del reproductor para ver si el reproductor obtiene los detalles correctos y si hay algún problema de red en la descarga.

1. Puede hacer clic con el botón derecho e inspeccionar tres capas del reproductor de cromo
   **Depurar contenido**: Haga clic con el botón derecho e inspeccione el contenido para depurar el contenido que se está ejecutando (debe haber un solo elemento llamado &quot;Inspect&quot; en el menú contextual)

   **Firmware** de depuración: Abra la interfaz de usuario de administración y haga clic con el botón secundario e inspeccione para depurar el código de firmware (reproductor) (debe haber una opción para inspeccionar e inspeccionar la página de fondo y simular el reinicio del explorador)

   **Depurar página** de fondo: Muestre la interfaz de usuario de administración y, a continuación, haga clic con el botón secundario e inspeccione la página de fondo (para servicios en segundo plano como http server)

## Actualización de la extensión del reproductor {#upgrading-player}

Siga los pasos a continuación para actualizar la extensión del reproductor si se ha lanzado una nueva versión del reproductor. También puede seguir las instrucciones siguientes para probar los escenarios de actualización:

1. Cerrar todas las instancias de cromo y reproductor en ejecución
1. Cambiar el nombre de la carpeta antigua con archivos de reproductor
1. Extraiga el nuevo zip en la misma ubicación que la carpeta antigua
1. Inicie Chrome y vaya a `chrome://extensions`
1. Marque el icono del reproductor y haga clic en el botón actualizar o volver a cargar