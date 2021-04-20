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
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 43%

---


# Uso de AEM Screens Player {#working-with-aem-screens-player}

Puede administrar el contenido del canal y otras configuraciones en el Reproductor de AEM Screens.

>[!NOTE]
>
>Presione ***Ctrl + Cmd + F*** para salir del modo de pantalla completa del reproductor AEM Screens para OS X.

Una vez asigne un canal a una visualización, el reproductor AEM Screens muestra el contenido. Puede configurar las opciones de configuración del reproductor mediante las preferencias de la IU de administración (desde el panel) o desde el reproductor en sí mismo.

## Utilizar el panel del dispositivo {#using-the-device-dashboard}

Puede configurar las preferencias del dispositivo desde el panel del dispositivo, el cual está disponible a través de la instancia de creación de AEM.

1. Vaya al panel del dispositivo desde el proyecto; por ejemplo, ***Probar proyecto*** —> ***Dispositivos***.

   Seleccione **Dispositivos** y **Administrador de dispositivos** en la barra de acciones.

   ![imagen_1-66](assets/chlimage_1-66.png)

1. Haga clic en el dispositivo para abrir el panel del dispositivo.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Compruebe el panel **PREFERENCIAS**. Puede habilitar/deshabilitar la **IU de administración** y el **conmutador de canales** para su reproductor desde estas dos opciones.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### IU de administración {#the-admin-ui}

Al habilitar la **IU de administración** en el panel de preferencias, el usuario puede abrir la configuración de administración desde el reproductor Screens. Además, si desactiva esta opción del panel del dispositivo, el usuario no puede abrir la IU de administración desde el reproductor.

Para ver la administración de IU desde el reproductor Screens, pulse de forma prolongada la esquina inferior izquierda para abrir el menú de administración en el reproductor AEM Screens con función táctil, o use el ratón. Muestra información después de completar el registro y cargar los canales.

>[!NOTE]
>
>Además, puede ver el tiempo de actividad de la aplicación del reproductor AEM Screens para comprobar el estado de la aplicación.

![Chlimage_1-3](assets/chlimage_1-3.gif)

#### Acceso a las opciones del menú de configuración {#configuration-options}

Puede actualizar las configuraciones si selecciona la opción **Configuration** en el menú lateral, como se muestra en la figura siguiente:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

El menú Configuración le permite modificar las siguientes opciones:

* Restablezca **Firmware**, **Preferencias** o **A Factory** desde este cuadro de diálogo.

* Especifique el número máximo de archivos de registro que se guardarán para un reproductor AEM Screens en **Max No. de archivos de registro para mantener**.

* Habilite o deshabilite **Admin Menu**, **Channel Switcher** y **Activity UI** para el reproductor Screens.

   Si la **Interfaz de usuario de actividad** está habilitada desde el menú **Configuration**, el reproductor de AEM Screens muestra las *notificaciones de actividad del reproductor* en la esquina superior derecha del reproductor, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>La opción **Actualizar firmware** solo funciona en el Cordova, como los reproductores de Android.

>[!NOTE]
>
>Se recomienda deshabilitar la **IU de administración** en Implementaciones de producción.

#### Acceso a las opciones del menú Caché de contenido {#content-cache-options}

Puede borrar la caché de los canales y aplicaciones desde la IU de administración del reproductor AEM Screens.

Seleccione **Caché de contenido** del raíl lateral para actualizar la caché.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### El conmutador de canales {#the-channel-switcher}

Al habilitar **Channel Switcher** en el panel de preferencias, el usuario puede abrir la selección/configuración de canal desde el reproductor Screens.

Además, si desactiva esta opción del panel del dispositivo, el usuario no puede controlar las preferencias del canal del reproductor Screens.

Puede cambiar y controlar las opciones de configuración del canal desde el reproductor Screens.

Para ver el conmutador de canales del reproductor, pulse de forma prolongada la esquina inferior izquierda para abrir el conmutador de canales que le permitirá cambiar entre canales y otras características.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>También puede activar o desactivar el menú de administración y el conmutador de canales del reproductor, desde el reproductor Screens.
>
>(Consulte *Cambiar preferencias del reproductor Screens* tal como se indica en la sección siguiente).

### Preferencias de administración del reproductor AEM Screens  {#managing-preferences-from-the-aem-screens-player}

También puede cambiar las opciones de configuración de la administración de IU y el conmutador de canales desde el mismo reproductor.

Siga estos pasos para cambiar las preferencias del reproductor:

1. Mantenga pulsado el botón en el lado superior izquierdo del canal inactivo para abrir el panel de administración.
1. Vaya a **Configuration** en el menú de acciones de la izquierda.
1. Habilite o deshabilite la configuración para **Admin UI** o **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solución de problemas del reproductor AEM Screens {#troubleshooting-aem-screens-player}

Puede solucionar varios problemas relacionados con el reproductor AEM Screens (hardware y software):

| **Problemas** | **Recomendaciones** |
|---|---|
| El almacenamiento del reproductor está lleno | Eliminación de archivos innecesarios |
| Red perdida del reproductor | Utilice el cable Cat-5/Cat-6. Para WiFi, reduzca la distancia desde el router al dispositivo de reproducción |
| AEM Screens Player se bloqueó | Se recomienda disponer de una aplicación watchdog que se asegure de que AEM Screens Player se ejecute siempre |
| Configuración perdida de AEM Screens Player | Comprobar la conexión con AEM servidor |
| AEM Screens Player no se inicia automáticamente después de reiniciar o reiniciar el reproductor | Comprobar la carpeta de inicio del sistema operativo o el procedimiento de inicialización |
| AEM Screens Player muestra contenido incorrecto o antiguo | Comprobar la conexión de red |

### Actualizaciones para el reproductor AEM Screens {#updates-for-aem-screens-player}

Existen dos tipos de actualizaciones para el reproductor AEM Screens:

| **Método** | **Detalles** | **mediante remoto** | **Automatizado** | **0 Tiempo de inactividad** |
|---|---|---|---|---|
| Actualización del firmware | Se aplica en reproductores instalados existentes a través del comando remoto. Después de actualizar el reproductor, se volverá a cargar automáticamente con el contenido existente. | Sí | Personalizado | Casi - 1-3 segundos |
| Actualizaciones del contenedor del reproductor | Se trata de un nuevo ejecutable que se implementará en el Reproductor. Esta opción requiere que se copie de forma remota un nuevo binario en el reproductor, parar la versión que se esté ejecutando en ese momento e iniciar la nueva versión. Esto podría requerir volver a descargar la carga previa de los paquetes. | Sí (a través de shell remoto) | Personalizado | No |

## Pautas de selección de hardware para el dispositivo del reproductor {#hardware-selection-guidelines-for-player-device}

La siguiente sección proporciona las directrices de selección de hardware para un proyecto de Screens:

* Siempre genere componentes de ***de grado comercial*** o ***industrial*** tanto para el reproductor de PC como para el panel de visualización o el proyector.

* Siempre interactúe con los proveedores que sirven al mercado de la publicidad dinámica.
* Consideremos siempre los factores ambientales como la temperatura ambiente y la humedad relativa.
* Revise siempre los requisitos de alimentación y el acondicionamiento de alimentación.
* Revise cuidadosamente las necesidades de performance y los puertos de E/S requeridos para la aplicación.

La siguiente tabla resume las configuraciones de hardware con casos de uso típicos para un proyecto de AEM Screens:

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
   <td>Procesador Intel® Atom de núcleo doble, i3 o de núcleo cuádruple básico</td>
   <td><p>4 GB de memoria</p> <p>2 MB de caché</p> </td>
   <td><p>・ChromeOS 32 GB</p> <p>・Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> Ethernet/inalámbrico,<br /> 2xUSB</td>
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
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Contenido dinámico de origen único</li>
     <li>Sencilla interactiva</li>
     <li>1-3 diseños de zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzado </td>
   <td>Quad Core con hipersubproceso, procesador Intel® Core i7</td>
   <td><p>16 GB de memoria</p> <p>8 MB de caché</p> </td>
   <td>256 GB</td>
   <td>GPU de gráficos dedicados</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 o más zonas de contenido, reproducción de vídeo concurrente</li>
     <li>Interactivo de varias páginas</li>
     <li>Déclencheur de datos de varias fuentes</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
