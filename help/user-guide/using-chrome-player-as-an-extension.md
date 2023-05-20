---
title: Uso del reproductor Chrome como extensión
seo-title: Using Chrome Player as an Extension
description: Siga esta página para obtener más información sobre la instalación del reproductor de Chrome como extensión del explorador.
seo-description: null
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Uso del reproductor Chrome como extensión {#using-chrome-player}

El reproductor ChromeOS se puede instalar como complemento del explorador Chrome en el modo de desarrollador sin requerir el dispositivo de reproductor Chrome real.

>[!CAUTION]
>
> Se recomienda utilizar el reproductor Chrome como extensión para solucionar problemas en demostraciones rápidas, depuraciones y también para solucionar problemas de los clientes. Este mecanismo no debe utilizarse para implementaciones de producción que requieran modo de quiosco y administración central.

Siga esta página para obtener más información sobre la instalación del reproductor de Chrome como extensión del explorador.

1. Clic [aquí](https://download.macromedia.com/screens/) para descargar el último reproductor de Chrome.

1. Descomprima y guárdelo en el disco.

1. Abra el navegador Chrome, haga clic en el menú de 3 puntos y seleccione **Más herramientas** de **Extensiones** situado en la esquina superior derecha o navegue directamente a `chrome://extensions`.

1. Encienda el **Desarrollador** modo desde la esquina superior derecha.

1. Haga clic en **Cargar desempaquetado** desde la esquina superior izquierda y cargue el reproductor Chrome sin comprimir.

1. Compruebe el complemento AEM Screens Chrome Player si está disponible en la lista de extensiones.

1. Abra una pestaña nueva y haga clic en el icono Aplicaciones desde la esquina superior izquierda o navegue directamente a `chrome://apps`.

1. Haga clic en **Complemento de AEM Screens** para iniciar Chrome Player.
   >[!NOTE]
   >
   > De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Prensa **esc** para salir del modo de pantalla completa.


## Sugerencias de depuración avanzada {#advanced-debugging-tips}

1. Una vez que el reproductor ha descargado contenido localmente, puede examinar el contenido descargado localmente accediendo a `http://localhost:24502`.

   >[!NOTE]
   >
   > Si la URL mencionada anteriormente no funciona, significa que el reproductor no tiene asignada una pantalla o que el contenido no se ha descargado correctamente. Compruebe la pestaña de red del JSON de configuración del reproductor para ver si el reproductor obtiene los detalles correctos y para cualquier problema de red en la descarga.

1. Puede hacer clic con el botón derecho e inspeccionar tres capas del reproductor cromado
   **Depuración de contenido**: haga clic con el botón derecho e inspeccione el contenido para depurar el contenido en ejecución (debe haber un solo elemento llamado &quot;Inspect&quot; en el menú contextual)

   **Depurar firmware**: abra la interfaz de usuario de administración y, a continuación, haga clic con el botón derecho e inspeccione para depurar el código del firmware (reproductor) (debe haber una opción para inspeccionar la página en segundo plano y simular el reinicio del explorador)

   **Depurar página de fondo**: abra la IU de administración, haga clic con el botón derecho e inspeccione la página de fondo (para servicios en segundo plano como el servidor http)

## Actualización de la extensión del reproductor {#upgrading-player}

Siga los pasos a continuación para actualizar la extensión del reproductor si se publica una nueva versión. También puede seguir las instrucciones a continuación para probar los escenarios de actualización:

1. Cierre todas las instancias de Chrome y reproductor en ejecución
1. Cambie el nombre de la carpeta antigua por archivos de reproductor
1. Extraiga el nuevo zip en la misma ubicación que la carpeta antigua
1. Inicie Chrome y vaya a `chrome://extensions`
1. Compruebe el icono del reproductor y haga clic en el botón Actualizar o volver a cargar
