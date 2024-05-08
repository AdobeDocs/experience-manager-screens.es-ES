---
title: Configuración y solución de problemas de reproducción de vídeo
description: Aprenda a depurar y solucionar problemas de la reproducción de vídeo en su canal para AEM Screens.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# Configuración y solución de problemas de reproducción de vídeo {#video-playback-configuration-and-troubleshooting}

Al cargar un vídeo en DAM y añadirlo a su canal, puede encontrar problemas en los que el vídeo podría no reproducirse en el reproductor de AEM Screens.

Las siguientes secciones describen cómo depurar y solucionar problemas de la reproducción de vídeo en el canal.

## Representaciones DAM {#dam-renditions}

AEM Después de cargar el vídeo en el canal, debería empezar a crear algunas representaciones para él. Puede ver los vídeos en Recursos.

Para ver el vídeo:

1. Vaya al vídeo, por ejemplo `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Haga clic en el vídeo, expanda el menú superior izquierdo y haga clic en **Representaciones**.

Debe haber diferentes representaciones (una MP4 o M4V).

AEM Si no hay ninguna representación, asegúrese de que tiene ffmpeg instalado en el sistema operativo donde se está ejecutando la.

>[!CAUTION]
>
>AEM Si no hay ninguna representación, asegúrese de que tiene ffmpeg instalado en el sistema operativo donde se está ejecutando la.
>
>Clic [aquí](https://www.ffmpeg.org/download.html) para instalar ffmpeg.

## Recursos de vídeo {#video-assets}

Si no ve un atributo de fuente en el vídeo, puede ser que el vídeo no se haya transcodificado. Si el vídeo se transcodifica correctamente, aparece en el panel, como se muestra en los siguientes ejemplos:

Compruebe que ffmpeg está instalado y los perfiles de vídeo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Comprobación del perfil de vídeo {#checking-video-profile}

1. Vaya a **Perfil de vídeo**, es decir, `http://localhost:4502/etc/dam/video.html` y haga clic en **Cargar vídeo de prueba**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Cargue un vídeo de prueba y haga clic en **Ok** para que pueda comenzar la transcodificación.

   Si el vídeo transcodificado falla, expanda la salida ffmpeg para comprender cualquier error en la salida de la consola de ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Además, si el vídeo se transcodifica correctamente, puede descargar el archivo transcodificado.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Asegúrese de dar tiempo suficiente para que el vídeo se transcodifique (debe mostrar la nueva etiqueta en lugar del procesamiento) antes de agregarlo a cualquier canal.

### Comprobación del perfil con un componente de vídeo {#checking-profile-with-a-video-component}

Compruebe la lista de perfiles del diseño de página si el componente de vídeo no está configurado correctamente.

1. Vaya al canal y haga clic en **Diseño** modo.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Haga clic en el vídeo y abra **Editar** diálogo. Abra el **Perfiles** pestaña.

   >[!NOTE]
   >Haga clic en diferentes perfiles (el perfil H.264 de &quot;alta calidad&quot; como mínimo debe estar allí).

### Comprobación del vídeo en el reproductor web {#checking-the-video-in-the-web-player}

Utilice el **Reproductor web** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` para validar la reproducción en navegadores (Chrome y Safari). Chrome se utiliza en dispositivos Android™ mientras que Safari es el navegador OS X y iOS.

Si el vídeo no se ejecuta en Safari, tampoco se ejecuta en los reproductores de OS X y iOS. Es probable que se trate de un problema de codificación, por lo que el vídeo debe volver a codificarse.

Para utilizar un flujo de trabajo DAM para crear representaciones FullHD, haga lo siguiente:

1. Vaya a *administrador de modelo de flujo de trabajo* es decir `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Haga clic en **Actualizar recurso de Screens** modelo.
1. Clic **Iniciar flujo de trabajo** de la barra de acciones.
1. Desde el **Ejecutar flujo de trabajo** , haga clic en el recurso de vídeo en la **Carga útil**.
1. Clic **Ejecutar**.

>[!NOTE]
>
>Espere un poco para crear las representaciones, pero después de unos segundos/minutos (depende del tamaño del vídeo), vuelva a cargar el reproductor web en Safari.

#### Indicador de directiva de reproducción automática de resolución de problemas {#troubleshooting-autoplay-policy-flag}

En caso de que el Reproductor de AEM Screens capte el vídeo pero no se muestre, solucione el problema del indicador de la directiva de reproducción automática.

Siga los pasos a continuación para solucionar el problema de indicador de política de reproducción automática de Google:

1. Vaya a ***chrome://flags/#autoplay-policy***
1. Cambiar **Política de reproducción automática** de **Predeterminado** hasta **no se requiere ningún gesto del usuario**

1. Vuelva a iniciar el explorador web y actualice el reproductor

>[!NOTE]
>
>Para obtener más información sobre las prácticas recomendadas para las buenas experiencias de usuario con las nuevas políticas de reproducción automática en Chrome, consulte la documentación de *Cambios de directiva de reproducción automática* en `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronización de vídeo entre varios reproductores {#syncing-video-across-multiple-players}

Para reproducir vídeos sincrónicamente en varios dispositivos, debe utilizar la estrategia absoluta para la secuencia de la que forma parte el vídeo.

#### Requisitos  {#requirements}

* 2 o más reproductores idénticos
* hardware idealmente similar
* topología de red idéntica (los reproductores están conectados a un servidor NTP que alinea sus relojes internos del sistema)

#### Configuración de la estrategia absoluta {#setting-up-the-absolute-strategy}

La estrategia absoluta:

* Calcula una hora de anclaje (medianoche del día actual).
* Calcula la duración de la secuencia (suma de la duración de todos sus elementos).
* En cualquier momento, calcula qué elemento se debe reproducir actualmente y el siguiente resolviendo la secuencia _remaining_tiempo = (current_time - anchor_time) % sequence_duration.

Siga los pasos a continuación para configurar una estrategia absoluta:

1. Vaya al autor del canal y haga clic en el componente de secuencia como se muestra en la figura siguiente.
1. Abra su cuadro de diálogo de configuración.
1. Edite el **Estrategia** y agregue absoluta.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >El sistema operativo de los reproductores debe tener el mismo reloj.

**Alineación de relojes en OS X** Siga los pasos a continuación para alinear los relojes en OS X:

1. Abrir **Fecha y hora** preferencias en cada cuadro de OS X
1. Marque **Establecer fecha y hora automáticamente**
1. Pegue el valor 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com en el menú desplegable o simplemente ejecute *sudo ntpdate -u -v 0.pool.ntp.org*
1. Inicio de los más de 2 jugadores

Puede tomar algún tiempo antes de que los jugadores comiencen una nueva secuencia alineada.
