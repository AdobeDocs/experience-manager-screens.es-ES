---
title: Uso del Reproductor de Chrome como extensión
description: Obtenga información acerca de la instalación del reproductor de Chrome como extensión de explorador para AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Uso del reproductor de Chrome como extensión {#using-chrome-player}

El reproductor ChromeOS se puede instalar como complemento del explorador de Chrome en modo de desarrollador sin necesidad de un dispositivo de reproductor de Chrome real.

>[!CAUTION]
>
> Se recomienda utilizar el reproductor de Chrome como extensión para solucionar problemas en demostraciones rápidas, depuraciones y problemas con los clientes. No utilice este mecanismo para implementaciones de producción que requieran el modo quiosco y administración central.

Siga esta página para obtener información acerca de la instalación del reproductor de Chrome como extensión de explorador.

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar el reproductor de Chrome más reciente.

1. Descomprima y guárdelo en el disco.

1. Abra el explorador Chrome, haga clic en el menú de 3 puntos y, a continuación, haga clic en **Más herramientas** de **Extensiones** en la esquina superior derecha o vaya directamente a `chrome://extensions`.

1. Encienda el modo **Desarrollador** desde la esquina superior derecha.

1. Haga clic en **Cargar desempaquetado** en la esquina superior izquierda y cargue el reproductor de Chrome descomprimido.

1. Compruebe el complemento del reproductor de Chrome de AEM Screens si está disponible en la lista de extensiones.

1. Abra una nueva pestaña y haga clic en el icono Aplicaciones desde la esquina superior izquierda, o navegue directamente a `chrome://apps`.

1. Haga clic en **Complemento de AEM Screens** para iniciar el reproductor de Chrome.

   >[!NOTE]
   >
   > De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **Esc** para salir del modo de pantalla completa.


## Sugerencias de depuración avanzada {#advanced-debugging-tips}

1. Cuando el reproductor haya descargado contenido localmente, puede examinar el contenido descargado localmente yendo a `http://localhost:24502`.

   >[!NOTE]
   >
   > Si la URL mencionada anteriormente no funciona, significa que el reproductor no tiene asignada una pantalla o que el contenido no se ha descargado correctamente. Compruebe la pestaña de red del JSON de configuración del reproductor para ver si el reproductor obtiene los detalles correctos y para cualquier problema de red en la descarga.

1. Haga clic con el botón derecho e inspeccione tres capas del reproductor de Chrome.
   **Contenido de depuración**: haga clic con el botón derecho e inspeccione el contenido para depurar el contenido en ejecución (debería haber un solo elemento llamado &quot;Inspect&quot; en el menú contextual)

   **Depurar firmware**: Abra la interfaz de usuario del administrador, haga clic con el botón secundario e inspeccione para depurar el código del firmware (reproductor). (Debe haber una opción para inspeccionar e inspeccionar la página de fondo y simular un reinicio del explorador).

   **Depurar página de fondo**: abra la interfaz de usuario del administrador, haga clic con el botón secundario e inspeccione la página de fondo (para servicios en segundo plano como el servidor http).

## Actualización de la extensión del reproductor {#upgrading-player}

Siga los pasos a continuación para actualizar la extensión del reproductor si se publica una nueva versión. También puede seguir las instrucciones a continuación para probar los escenarios de actualización:

1. Cierre todas las instancias de Chrome y reproductor en ejecución
1. Cambie el nombre de la carpeta antigua por archivos de reproductor
1. Extraiga el nuevo zip en la misma ubicación que la carpeta antigua
1. Inicie Chrome y vaya a `chrome://extensions`
1. Compruebe el icono del reproductor y haga clic en el botón de actualización o recarga
