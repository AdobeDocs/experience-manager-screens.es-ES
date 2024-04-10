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
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 0%

---

# Uso del Reproductor de AEM Screens

Puede administrar el contenido del canal y otros ajustes en el Reproductor de AEM Screens.

>[!NOTE]
>
>Prensa ***Ctrl + Cmd + F*** para poder salir del modo de pantalla completa para el Reproductor de AEM Screens OS X.

Después de asignar un canal a una pantalla, el Reproductor de AEM Screens muestra el contenido. Puede configurar los ajustes del reproductor mediante las preferencias de la IU de administración (desde el panel) o desde el propio reproductor.

## Uso del tablero de dispositivos {#using-the-device-dashboard}

AEM Puede configurar las preferencias de su dispositivo desde el Tablero de dispositivo, al que se puede acceder mediante la instancia de creación de la.

1. Vaya al panel de dispositivos desde el proyecto, por ejemplo, ***Proyecto de prueba*** > ***Dispositivos***.

   Seleccionar **Dispositivos** y **Administrador de dispositivos** de la barra de acciones.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Haga clic en el dispositivo para poder abrir el tablero de dispositivos.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Compruebe la **PREFERENCIAS** panel. Puede habilitar/deshabilitar el **IU de administración** y **Conmutador de canales** para su reproductor a partir de estas dos opciones.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### La IU de administración {#the-admin-ui}

Activación de la **IU de administración** desde el panel de preferencias el usuario puede abrir la configuración de administración desde el reproductor de Screens. Además, si desactiva esta opción desde el panel del dispositivo, el usuario no podrá abrir la interfaz de usuario de administración desde el reproductor.

Para ver la IU de administración desde el reproductor de Screens, pulse durante mucho tiempo la esquina superior izquierda para abrir el menú Administración, en el reproductor de AEM Screens táctil o con un ratón. La información se muestra una vez completado el registro y cargados los canales.

>[!NOTE]
>
>Además, puede ver el tiempo de actividad de la aplicación del Reproductor de AEM Screens para comprobar el estado de la aplicación.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Acceso a las opciones del menú de configuración {#configuration-options}

Puede actualizar las configuraciones si selecciona la **Configuración** del menú lateral, como se muestra en la figura siguiente:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

El menú Configuration permite modificar las siguientes opciones:

* Restablecer **Firmware**, **Preferencias**, o **A Fábrica** de este cuadro de diálogo.

* Especifique el número máximo de archivos de registro que desea conservar para un reproductor de AEM Screens en **Número máximo. de archivos de registro que se van a conservar**.

* Habilitar o deshabilitar **Menú Administrador**, **Conmutador de canales**, y **IU de actividad** para el reproductor Screens.

  Si la variable **IU de actividad** está habilitado desde el **Configuración** menú, el reproductor de AEM Screens muestra el *notificaciones de actividad del reproductor* en la esquina superior derecha del reproductor, como se muestra en la figura siguiente.

  ![imagen](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>El **Actualizar firmware** solo funciona en Cordova, como reproductores de Android™.

>[!NOTE]
>
>Se recomienda que la variable **IU de administración** Deshabilitarse en las implementaciones de producción.

#### Acceso a las opciones del menú Caché de contenido {#content-cache-options}

Puede borrar la caché de los canales y las aplicaciones desde la IU del administrador en el reproductor de AEM Screens.

Seleccione el **Caché de contenido** desde el carril lateral para poder actualizar la caché.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### El conmutador de canales {#the-channel-switcher}

Activación de la **Conmutador de canales** desde el panel de preferencias el usuario puede abrir la selección/configuración de canal desde el reproductor de Screens.

Además, si desactiva esta opción desde el panel del dispositivo, el usuario no podrá controlar las preferencias de canal desde el reproductor de Screens.

Puede cambiar y controlar la configuración del canal desde el reproductor de Screens.

Para ver el conmutador de canales desde el reproductor, pulse durante mucho tiempo la esquina inferior izquierda para abrir el conmutador de canales que permite cambiar canales y otras funciones.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>También puede habilitar o deshabilitar el menú de administración y el conmutador de canales para el reproductor desde el reproductor Screens.
>
>(Consulte *Cambiar preferencias del reproductor de Screens* como se menciona en la sección siguiente).

### Administración de preferencias desde el reproductor de AEM Screens

También puede cambiar la configuración de la IU de administración y el conmutador de canales desde el propio reproductor.

Para cambiar las preferencias del reproductor:

1. Pulse durante mucho tiempo en la esquina superior izquierda del canal inactivo para abrir el panel de administración.
1. Vaya a **Configuración** en el menú de acción de la izquierda.
1. Habilitar/deshabilitar la configuración de **IU de administración** o **Conmutador de canales**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solución de problemas del reproductor AEM Screens

Puede solucionar varios problemas asociados con el Reproductor de AEM Screens (hardware y software):

| **Problemas** | **Recommendations** |
|---|---|
| El almacenamiento del reproductor está lleno | Eliminar archivos innecesarios |
| El reproductor perdió la red | Utilice un cable Cat-5/Cat-6. Para wifi, reduce la distancia desde el router al dispositivo de reproducción |
| Reproductor de AEM Screens bloqueado | Se recomienda tener una aplicación de vigilancia que se asegure de que el reproductor de AEM Screens siempre se ejecute |
| El Reproductor de AEM Screens perdió la configuración | AEM Comprobar la conexión con el servidor de |
| El Reproductor de AEM Screens no se inicia automáticamente después de reiniciar el Reproductor | Compruebe la carpeta de inicio del sistema operativo o el procedimiento de inicialización |
| El Reproductor de AEM Screens muestra contenido incorrecto/antiguo | Comprobar conexión de red |

### Actualizaciones del Reproductor de AEM Screens

Existen dos tipos de actualizaciones para el Reproductor de AEM Screens:

| **Método** | **Detalles** | **a través de Remote** | **Automatizado** | **0 Tiempo de inactividad** |
|---|---|---|---|---|
| Actualización de firmware | Se aplica a los reproductores instalados existentes mediante un comando remoto. Después de la actualización, el Reproductor se vuelve a cargar automáticamente con el contenido existente. | Sí | Personalizada | Casi - 1-3 segundos |
| Actualizaciones del contenedor del reproductor | Se trata de un nuevo ejecutable que se implementará en el Reproductor. Esto requiere copiar de forma remota el nuevo binario en el reproductor, detener el que se está ejecutando e iniciar la nueva versión. Esto puede requerir volver a descargar la precarga de los paquetes. | Sí (a través de shell remoto) | Personalizada | No |

## Directrices de selección de hardware para dispositivos de reproducción {#hardware-selection-guidelines-for-player-device}

En la siguiente sección se proporcionan las directrices de selección de hardware para un proyecto de Screens:

* Origen siempre ***Comercial*** o ***Industrial*** Componentes de nivel superior para el reproductor de PC y el panel de visualización o el proyector.

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
   <td>DVI<br /> Ethernet/Inalámbrico<br /> 2 x USB</td>
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
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Inalámbrico,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Contenido dinámico de origen único</li>
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
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Inalámbrico,<br /> 4 x USB</td>
   <td>
    <ul>
     <li>4 o más zonas de contenido, reproducción de vídeo simultánea</li>
     <li>Interactivo de varias páginas</li>
     <li>Déclencheur de datos de varias fuentes</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
