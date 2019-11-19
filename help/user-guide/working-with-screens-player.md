---
title: Uso de AEM Screens Player
seo-title: Uso del reproductor Screens
description: Consulte esta página para obtener más información sobre el reproductor Screens. También se explica la IU de administración y el conmutador del canal.
seo-description: Consulte esta página para obtener más información sobre el reproductor Screens. También se explica la IU de administración y el conmutador del canal.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Working with AEM Screens Player {#working-with-aem-screens-player}

Puede administrar el contenido del canal y otros ajustes en AEM Screens Player.

>[!NOTE]
>
>Presione ***Ctrl + Cmd + F**para salir del modo de pantalla completa del reproductor AEM Screens para OS X.*

Una vez asigne un canal a una visualización, el reproductor AEM Screens muestra el contenido. Puede configurar las opciones de configuración del reproductor mediante las preferencias de la IU de administración (desde el panel) o desde el reproductor en sí mismo.

## Utilizar el panel del dispositivo {#using-the-device-dashboard}

Puede configurar las preferencias del dispositivo desde el panel del dispositivo, el cual está disponible a través de la instancia de creación de AEM.

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Haga clic en el dispositivo para abrir el panel del dispositivo.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Check the **PREFERENCES** panel. You can enable/disable the **Admin UI** and **Channel Switcher** for your player from these two options.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### IU de administración {#the-admin-ui}

Enabling the **Admin UI** from the preferences panel allows the user to open the admin settings from the Screens Player. Además, si desactiva esta opción del panel del dispositivo, el usuario no puede abrir la IU de administración desde el reproductor.

Para ver la administración de IU desde el reproductor Screens, pulse de forma prolongada la esquina inferior izquierda para abrir el menú de administración en el reproductor AEM Screens con función táctil, o use el ratón. Muestra información después de completar el registro y cargar los canales.

>[!NOTE]
>
>Además, puede ver el tiempo de actividad de la aplicación del reproductor AEM Screens para comprobar el estado de la aplicación.

![climage_1-3](assets/chlimage_1-3.gif)

Si selecciona la opción **Configuración** en el menú lateral, también puede restablecer **Firmware**, **Preferencias** o **A fábrica** desde este cuadro de diálogo.

Además, puede especificar el número máximo de archivos de registro que se guardarán para un reproductor de AEM Screens en el número **máximo. de los archivos de registro que se van a conservar**. Consulte la captura de pantalla de abajo para obtener más detalles.

>[!NOTE]
>
>La opción **Actualizar firmware** solo funciona en el Cordova, como reproductores de Android.

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Puede borrar la caché de los canales y aplicaciones desde la IU de administración del reproductor AEM Screens.

Seleccione **Caché de contenido** del raíl lateral para actualizar la caché.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### El conmutador de canales {#the-channel-switcher}

Enabling the **Channel Switcher** from the preferences panel allows the user to open the channel selection/settings from the Screens Player.

Además, si desactiva esta opción del panel del dispositivo, el usuario no puede controlar las preferencias del canal del reproductor Screens.

Puede cambiar y controlar las opciones de configuración del canal desde el reproductor Screens.

Para ver el conmutador de canales del reproductor, pulse de forma prolongada la esquina inferior izquierda para abrir el conmutador de canales que le permitirá cambiar entre canales y otras características.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>También puede activar o desactivar el menú de administración y el conmutador de canales del reproductor, desde el reproductor Screens.
>
>(Consulte *Cambiar preferencias del reproductor Screens* tal como se indica en la sección siguiente).

### Preferencias de administración del reproductor AEM Screens {#managing-preferences-from-the-aem-screens-player}

También puede cambiar las opciones de configuración de la administración de IU y el conmutador de canales desde el mismo reproductor.

Siga estos pasos para cambiar las preferencias del reproductor:

1. Mantenga pulsado el botón en el lado superior izquierdo del canal inactivo para abrir el panel de administración.
1. Navigate to **Configuration** from the left action menu.
1. Enable/disable configuration for **Admin UI** or **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solución de problemas del reproductor AEM Screens {#troubleshooting-aem-screens-player}

Puede solucionar varios problemas relacionados con el reproductor AEM Screens (hardware y software):

| **Problemas** | **Recomendaciones** |
|---|---|
| El almacenamiento del reproductor está lleno | Eliminar archivos innecesarios |
| Reproductor perdido red | Utilice el cable Cat-5/Cat-6. Para Wi-Fi, reduzca la distancia desde el router al dispositivo reproductor |
| Se bloqueó AEM Screens Player | Se recomienda disponer de una aplicación de vigilancia que garantice que AEM Screens Player siempre se ejecute |
| Configuración perdida de AEM Screens Player | Comprobar la conexión con el servidor AEM |
| AEM Screens Player no se inicia automáticamente después de reiniciar o reiniciar el reproductor | Comprobación de la carpeta de inicio del sistema operativo o del procedimiento de inicialización |
| AEM Screens Player muestra contenido incorrecto o anterior | Comprobar conexión de red |

### Actualizaciones para el reproductor AEM Screens {#updates-for-aem-screens-player}

Existen dos tipos de actualizaciones para el reproductor AEM Screens:

| **Método** | **Detalles** | **a través de Remote** | **Automatizado** | **0 Tiempo de inactividad** |
|---|---|---|---|---|
| Actualización de firmware | Se aplica en reproductores instalados existentes mediante un comando remoto. Después de actualizar el reproductor, se volverá a cargar automáticamente con el contenido existente. | Sí | Personalizado | Casi - 1-3 segundos |
| Actualizaciones del shell del reproductor | Se trata de un nuevo ejecutable que se implementará en el Reproductor. Esta opción requiere que se copie de forma remota un nuevo binario en el reproductor, parar la versión que se esté ejecutando en ese momento e iniciar la nueva versión. Esto podría requerir volver a descargar la carga previa de los paquetes. | Sí (mediante shell remoto) | Personalizado | No |

## Directrices de selección de hardware para el dispositivo reproductor {#hardware-selection-guidelines-for-player-device}

La siguiente sección proporciona las directrices de selección de hardware para un proyecto de pantallas:

* Utilice siempre componentes de ***categoría comercial*** o ***industrial*** tanto para el reproductor de PC como para el panel de visualización o el proyector.

* Siempre interactúes con proveedores que sirven al mercado de la publicidad dinámica.
* Consideremos siempre factores ambientales como la temperatura ambiente y la humedad relativa.
* Revise siempre los requisitos de alimentación y el acondicionamiento de alimentación.
* Revise cuidadosamente las necesidades de rendimiento y los puertos de E/S requeridos para la aplicación.

La siguiente tabla resume las configuraciones de hardware con casos de uso típicos de un proyecto de AEM Screens:

<table>
 <tbody>
  <tr>
   <td>Configuración del reproductor</td>
   <td>Procesador</td>
   <td>Memoria</td>
   <td>SSD de almacenamiento</td>
   <td>GPU</td>
   <td>Mostrar</td>
   <td>E/S</td>
   <td>Casos de uso habituales</td>
  </tr>
  <tr>
   <td>Básico</td>
   <td>Procesador Intel® Atom de doble núcleo, i3 o de cuatro núcleos básico</td>
   <td><p>4 GB de memoria</p> <p>2 MB de caché</p> </td>
   <td><p>・ChromeOS 32 GB</p> <p>・Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> Ethernet/inalámbrico,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Bucle estándar de pantalla completa<br /> </li>
     <li>Partición de día</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Estándar</td>
   <td>Procesador Intel® Core i5 de cuatro núcleos</td>
   <td><p>8 GB de memoria</p> <p>4 MB de caché</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840 x 2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/inalámbrico,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Contenido dinámico de origen único</li>
     <li>Interactivo simple</li>
     <li>1-3 diseños de zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzado</td>
   <td>Cuatro núcleos con hipersubprocesos, procesador Intel® Core i7</td>
   <td><p>16 GB de memoria</p> <p>8 MB de caché</p> </td>
   <td>256 GB</td>
   <td>GPU de gráficos dedicados</td>
   <td>3840 x 2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / inalámbrico,<br /> 4 x USB</td>
   <td>
    <ul>
     <li>4 o más zonas de contenido, reproducción de vídeo simultáneo</li>
     <li>Interactivo de varias páginas</li>
     <li>Desencadenadores de datos de varias fuentes</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
