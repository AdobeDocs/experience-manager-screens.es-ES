---
title: Uso del reproductor Chrome como extensión
description: Obtenga información acerca de la instalación del reproductor de Chrome como extensión del explorador para AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Uso del reproductor Chrome como extensión {#using-chrome-player}

El reproductor ChromeOS se puede instalar como complemento del explorador Chrome en modo de desarrollador sin necesidad de un dispositivo de reproductor Chrome real.

>[!CAUTION]
>
> Se recomienda utilizar el reproductor Chrome como extensión para solucionar problemas en demostraciones rápidas, depuraciones y también para solucionar problemas de los clientes. No utilice este mecanismo para implementaciones de producción que requieran el modo quiosco y administración central.

Siga esta página para obtener información sobre la instalación del reproductor Chrome como extensión del explorador.

1. Clic [aquí](https://download.macromedia.com/screens/) para descargar el último reproductor de Chrome.

1. Descomprima y guárdelo en el disco.

1. Abra el explorador Chrome, haga clic en el menú de 3 puntos y seleccione **Más herramientas** de **Extensiones** en la esquina superior derecha o navegue directamente a `chrome://extensions`.

1. Encienda el **Desarrollador** de la esquina superior derecha.

1. Clic **Cargar desempaquetado** desde la esquina superior izquierda y cargue el reproductor Chrome sin comprimir.

1. Compruebe el complemento del reproductor AEM Screens Chrome si está disponible en la lista de extensiones.

1. Abra una pestaña nueva y haga clic en el icono Aplicaciones en la esquina superior izquierda, o navegue directamente a `chrome://apps`.

1. Clic **Complemento de AEM Screens** para poder iniciar el reproductor Chrome.

   >[!NOTE]
   >
   > De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Prensa **Esc** para salir del modo de pantalla completa.


## Sugerencias de depuración avanzada {#advanced-debugging-tips}

1. Cuando el reproductor haya descargado contenido localmente, puede examinar el contenido descargado localmente accediendo a `http://localhost:24502`.

   >[!NOTE]
   >
   > Si la URL mencionada anteriormente no funciona, significa que el reproductor no tiene asignada una pantalla o que el contenido no se ha descargado correctamente. Compruebe la pestaña de red del JSON de configuración del reproductor para ver si el reproductor obtiene los detalles correctos y para cualquier problema de red en la descarga.

1. Haga clic con el botón derecho e inspeccione tres capas del reproductor Chrome.
   **Depuración de contenido**: haga clic con el botón derecho e inspeccione el contenido para depurar el contenido en ejecución (debe haber un solo elemento llamado &quot;Inspect&quot; en el menú contextual)

   **Depurar firmware**: abra la IU de administración, haga clic con el botón derecho e inspeccione para depurar el código del firmware (reproductor). (Debe haber una opción para inspeccionar e inspeccionar la página de fondo y simular un reinicio del explorador).

   **Depurar página de fondo**: abra la interfaz de usuario de administración, haga clic con el botón derecho e inspeccione la página de fondo (para servicios en segundo plano como servidor http).

## Actualización de la extensión del reproductor {#upgrading-player}

Siga los pasos a continuación para actualizar la extensión del reproductor si se publica una nueva versión. También puede seguir las instrucciones a continuación para probar los escenarios de actualización:

1. Cierre todas las instancias de Chrome y reproductor en ejecución
1. Cambie el nombre de la carpeta antigua por archivos de reproductor
1. Extraiga el nuevo zip en la misma ubicación que la carpeta antigua
1. Inicie Chrome y vaya a `chrome://extensions`
1. Compruebe el icono del reproductor y haga clic en el botón de actualización o recarga
