---
title: Uso del Reproductor de AEM Screens
description: Obtenga información acerca de cómo trabajar con el Reproductor de AEM Screens, la IU del administrador y el conmutador de canales.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Uso del Reproductor de AEM Screens

Puede administrar el contenido del canal y otros ajustes en el Reproductor de AEM Screens.

>[!NOTE]
>
>Presione ***Ctrl+Cmd+F*** para poder salir del modo de pantalla completa para el Reproductor de AEM Screens de OS X.

Después de asignar un canal a una pantalla, el Reproductor de AEM Screens muestra el contenido. Puede configurar los ajustes del reproductor mediante las preferencias de la IU del administrador (desde el panel) o desde el propio reproductor.

## Uso del tablero de dispositivos {#using-the-device-dashboard}

AEM Puede configurar las preferencias de su dispositivo desde el panel Dispositivo, al que se puede acceder mediante la instancia de creación de la instancia de la instancia de creación de la.

1. Vaya al panel de dispositivos desde el proyecto, por ejemplo, ***Proyecto de prueba*** > ***Dispositivos***.

   Haga clic en **Dispositivos** y **Administrador de dispositivos** en la barra de acciones.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Haga clic en el dispositivo para poder abrir el tablero de dispositivos.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Compruebe el panel **PREFERENCIAS**. Puede habilitar o deshabilitar **IU de administración** y **conmutador de canal** para su reproductor desde estas dos opciones.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### La IU de administración {#the-admin-ui}

Habilitar la **IU de administración** desde el panel de preferencias permite al usuario abrir la configuración de administración desde el Reproductor de Screens. Además, si desactiva esta opción desde el panel del dispositivo, el usuario no podrá abrir la IU de administración desde el reproductor.

Para ver la IU de administración desde el Reproductor de Screens, pulse durante mucho tiempo la esquina superior izquierda para abrir el menú Administración, en el reproductor de AEM Screens táctil o con un ratón. La información se muestra una vez completado el registro y cargados los canales.

>[!NOTE]
>
>Además, puede ver el tiempo de actividad de la aplicación del Reproductor de AEM Screens para comprobar el estado de la aplicación.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Acceso a las opciones del menú de configuración {#configuration-options}

Puede actualizar las configuraciones si hace clic en la opción **Configuración** del menú lateral, como se muestra en la figura siguiente:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

El menú Configuration permite modificar las siguientes opciones:

* Restablecer **firmware**, **preferencias** o **a fábrica** desde este cuadro de diálogo.

* Especifique el número máximo de archivos de registro que desea conservar para un Reproductor de AEM Screens en **Número máximo. de archivos de registro para conservar**.

* Habilite o deshabilite **Menú de administración**, **Cambiar canal** y **IU de actividad** para el reproductor Screens.

  Si la **IU de actividad** está habilitada desde el menú **Configuración**, el Reproductor de AEM Screens muestra *notificaciones de actividad del reproductor* en la esquina superior derecha del reproductor, como se muestra en la figura siguiente.

  ![imagen](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>La opción **Actualizar firmware** solo funciona en Cordova, como reproductores Android™.

>[!NOTE]
>
>Se recomienda deshabilitar la **IU de administración** en las implementaciones de producción.

#### Acceso a las opciones del menú Caché de contenido {#content-cache-options}

Puede borrar la caché de los canales y las aplicaciones desde la IU del administrador en el reproductor de AEM Screens.

Haga clic en **Caché de contenido** en el carril lateral para actualizar la caché.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### El conmutador de canales {#the-channel-switcher}

Al habilitar **Channel Switcher** en el panel de preferencias, el usuario podrá abrir la configuración de selección de canales desde el Reproductor de Screens.

Además, si deshabilita esta opción desde el panel del dispositivo, el usuario no podrá controlar las preferencias de canal desde el Reproductor de Screens.

Puede cambiar y controlar la configuración de su canal desde el Reproductor de Screens.

Para ver el conmutador de canales desde el reproductor, pulse durante mucho tiempo la esquina inferior izquierda para abrir el conmutador de canales que permite cambiar canales y otras funciones.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>También puede habilitar o deshabilitar el menú de administración y el conmutador de canales para el reproductor desde el Reproductor de Screens.
>
>(Consulte *Cambiar preferencias del reproductor Screens* como se menciona en la sección siguiente).

### Administración de preferencias desde el reproductor de AEM Screens

También puede cambiar la configuración de la IU de administración y el conmutador de canales desde el propio reproductor.

Para cambiar las preferencias del reproductor:

1. Pulse durante mucho tiempo en la esquina superior izquierda del canal inactivo para abrir el panel de administración.
1. Vaya a **Configuración** desde el menú de acción de la izquierda.
1. Habilite o deshabilite la configuración de **IU de administración** o **conmutador de canal**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solución de problemas del reproductor AEM Screens

Puede solucionar varios problemas asociados con el Reproductor de AEM Screens (hardware y software):

| **Problemas** | **Recommendations** |
|---|---|
| El almacenamiento del reproductor está lleno | Eliminar archivos innecesarios |
| El reproductor perdió la red | Utilice un cable Cat-5 o Cat-6. Para wifi, reduce la distancia desde el router al dispositivo de reproducción |
| Reproductor de AEM Screens bloqueado | Se recomienda tener una aplicación de vigilancia que se asegure de que el reproductor de AEM Screens siempre se ejecute |
| El Reproductor de AEM Screens perdió la configuración | AEM Comprobar la conexión con el servidor de |
| El Reproductor de AEM Screens no se inicia automáticamente después de reiniciar el Reproductor | Compruebe la carpeta de inicio del sistema operativo o el procedimiento de inicialización |
| El Reproductor de AEM Screens muestra contenido incorrecto o antiguo | Comprobar conexión de red |

### Actualizaciones del Reproductor de AEM Screens

Existen dos tipos de actualizaciones para el Reproductor de AEM Screens:

| **Método** | **Detalles** | **a través del control remoto** | **Automatizado** | **0 tiempo de inactividad** |
|---|---|---|---|---|
| Actualización de firmware | Se aplica a los reproductores instalados existentes mediante un comando remoto. Después de la actualización, el Reproductor se vuelve a cargar automáticamente con el contenido existente. | Sí | Personalizado | Casi - 1-3 segundos |
| Actualizaciones del contenedor del reproductor | Un nuevo ejecutable que se implementa en el Reproductor. Esta funcionalidad requiere que copie de forma remota el nuevo binario en el reproductor, detenga el que se está ejecutando e inicie la nueva versión. Es posible que sea necesario volver a descargar la precarga de los paquetes. | Sí (a través de shell remoto) | Personalizado | No |

## Directrices de selección de hardware para dispositivos de reproducción {#hardware-selection-guidelines-for-player-device}

En la siguiente sección se proporcionan las directrices de selección de hardware para un proyecto de Screens:

* Use siempre componentes de nivel ***Comercial*** o ***Industrial*** para reproductores de PC y paneles de pantalla o proyectores.

* Póngase en contacto con los proveedores que trabajan en el mercado de la publicidad dinámica.
* Tenga siempre en cuenta factores ambientales como la temperatura ambiente y la humedad relativa.
* Revise siempre los requisitos de alimentación y el acondicionador de alimentación.
* Revise cuidadosamente las necesidades de rendimiento y los puertos de E/S necesarios para la aplicación.

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
   <td>Básica</td>
   <td>Procesador Intel® Atom de doble núcleo, i3 o núcleo cuádruple básico</td>
   <td><p>4 GB de memoria</p> <p>2 MB de caché</p> </td>
   <td><p>*ChromeOS de 32 GB</p> <p>*Windows de 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> Ethernet / inalámbrico<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Bucle estándar de pantalla completa<br /> </li>
     <li>División por día</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Estándar</td>
   <td>Procesador Intel® Core™ i5 de núcleo cuádruple</td>
   <td><p>8 GB de memoria</p> <p>4 MB de caché</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet/inalámbrico,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Contenido dinámico de Source único</li>
     <li>Interactivo simple</li>
     <li>Diseños de zona 1-3</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzado </td>
   <td>Procesador Intel® Core™ i7 de núcleo cuádruple con subprocesos</td>
   <td><p>16 GB de memoria</p> <p>8 MB de caché</p> </td>
   <td>256 GB</td>
   <td>GPU gráfica dedicada</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet/inalámbrico,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 o más zonas de contenido, reproducción de vídeo simultánea</li>
     <li>Interactivo de varias páginas</li>
     <li>Déclencheur de datos de varias Source</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
