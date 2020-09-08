---
title: Configuración y solución de problemas de la reproducción de vídeo
seo-title: Resolución de problemas de vídeos
description: null
seo-description: Siga esta página para obtener información sobre cómo solucionar problemas de vídeos. Al cargar un vídeo en el DAM y agregarlo a su canal, es posible que se produzcan problemas que el vídeo no se reproduzca en el reproductor de pantallas y en esta sección se describe cómo depurar y solucionar problemas de reproducción de vídeo en el canal.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: 6d86710a5d0a4fd1cf6c0dc46961d231b0128f95
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---


# Configuración y solución de problemas de la reproducción de vídeo {#video-playback-configuration-and-troubleshooting}

Al cargar un vídeo en el DAM y agregarlo a su canal, es posible que se produzcan problemas que impiden la reproducción del vídeo en el reproductor de pantallas.

Las siguientes secciones describen cómo depurar y solucionar problemas de reproducción de vídeo en el canal.

## Representaciones DAM {#dam-renditions}

Una vez cargado el vídeo en el canal, AEM crear algunas representaciones para él con inicio. Puede vista de los vídeos en Recursos.

Para vista del vídeo:

1. Vaya al vídeo, por ejemplo `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Haga clic en el vídeo, expanda el menú superior izquierdo y haga clic en **Representaciones**.

Debe haber distintas representaciones (MP4 o M4V).

Si no hay ninguna representación, asegúrese de que tiene instalado ffmpeg en el sistema operativo en el que se está ejecutando AEM.

>[!CAUTION]
>
>Si no hay ninguna representación, asegúrese de que tiene instalado ffmpeg en el sistema operativo en el que se está ejecutando AEM.
>
>Haga clic [aquí](https://www.ffmpeg.org/download.html) para instalar ffmpeg.

## Recursos de vídeo {#video-assets}

Si no ve un atributo de origen en video, podría ser que el vídeo no se transcodificó. Si el vídeo está codificado correctamente, aparecerá en el panel, como se muestra en la figura siguiente.

Compruebe que ffmpeg está instalado y los perfiles de vídeo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Comprobación del Perfil de vídeo {#checking-video-profile}

1. Vaya al Perfil **** Vídeo, es decir, `http://localhost:4502/etc/dam/video.html` y haga clic en **Cargar vídeo** de prueba.

   ![climage_1-3](assets/chlimage_1-3.png)

1. Cargue un vídeo de prueba y haga clic en **Aceptar** para iniciar la transcodificación.

   Si la transcodificación falla, expanda la salida ffmpeg para comprender cualquier error en la salida de la consola de ffmpeg.

   ![climage_1-4](assets/chlimage_1-4.png)

   Además, si el vídeo se transcodifica correctamente, puede descargar el archivo transcodificado.

   ![climage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Asegúrese de dar tiempo suficiente para que el vídeo se transcodifique (debe mostrar la etiqueta nueva en lugar de procesarla) antes de agregarla a cualquier canal.

### Comprobación de Perfiles con un componente de vídeo {#checking-profile-with-a-video-component}

Compruebe la lista de perfiles del diseño de página si el componente de vídeo no está configurado correctamente.

1. Vaya al canal y seleccione el modo **Diseño** .

   ![climage_1-6](assets/chlimage_1-6.png)

1. Seleccione el vídeo y abra el cuadro de diálogo **Editar** . Open the **Profiles** tab.

   >[!NOTA
   >Seleccione diferentes perfiles (debe haber al menos un perfil &quot;H.264 de alta calidad&quot;).


### Comprobación del vídeo en el reproductor web {#checking-the-video-in-the-web-player}

Utilice **Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` para validar la reproducción en navegadores (Chrome y Safari). Chrome se utiliza en dispositivos Android mientras que Safari es el explorador OSX e iOS.

Si el vídeo no se ejecuta en Safari, no se ejecutará en los reproductores OSX e iOS. Probablemente se trate de un problema de codificación y el vídeo debe volver a codificarse.

Siga estos pasos para utilizar un flujo de trabajo DAM para crear representaciones FullHD:

1. Vaya al administrador *del modelo de* flujo de trabajo, es decir, `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Seleccione el modelo **de recursos** de actualización de pantallas.
1. haga clic en Flujo de trabajo **Inicio** en la barra de acciones para abrir el cuadro de diálogo **Ejecutar flujo de trabajo** .

1. Seleccione el recurso de vídeo en la **carga útil**.
1. Haga clic en **Ejecutar**.

>[!NOTE]
>
>Deje tiempo para crear las representaciones, pero después de unos segundos/minutos (según el tamaño del vídeo), vuelva a cargar el reproductor web en Safari.

#### Resolución de problemas con el indicador de directiva de reproducción automática {#troubleshooting-autoplay-policy-flag}

En caso de que el reproductor de AEM Screens recoja el vídeo pero no lo muestre, deberá solucionar los problemas del indicador de la directiva de reproducción automática.

Siga los pasos a continuación para solucionar el problema del indicador de la política de reproducción automática de Google:

1. Vaya a ***chrome://flags/#autoplay-policy***
1. Cambiar la directiva **de** reproducción automática de **Predeterminado** a **no se requiere ningún gesto del usuario**

1. Reinicie el explorador Web y actualice el reproductor

>[!NOTE]
>
>Para obtener más información sobre las prácticas recomendadas para las buenas experiencias de los usuarios con las nuevas políticas de reproducción automática en Chrome, consulte la documentación sobre los cambios *de la política de* reproducción automática, es decir, `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronización de vídeo en varios reproductores {#syncing-video-across-multiple-players}

Para reproducir vídeos sincrónicamente en varios dispositivos, debe utilizar la estrategia absoluta para la secuencia de la que forma parte el vídeo.

#### Requisitos {#requirements}

* reproductores idénticos de 2+
* hardware similar idealmente
* topología de red idéntica (los reproductores están conectados a un servidor NTP que alinea los relojes internos del sistema)

#### Configuración de la estrategia absoluta {#setting-up-the-absolute-strategy}

La estrategia absoluta:

* calcula una hora de anclaje (medianoche del día actual)
* calcula la duración de la secuencia (suma de la duración de todo su elemento)
* en cualquier momento, calcula qué elemento debe reproducirse actualmente y el siguiente resolviendo la secuencia _remain_time = (current_time - anchor_time) % sequence_duration.

Siga los pasos a continuación para configurar una estrategia absoluta:

1. Vaya al autor del canal y seleccione el componente de secuencia como se muestra en la figura siguiente.
1. Abra el cuadro de diálogo de configuración.
1. Edite la **estrategia** y agregue absoluta.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >El SO de los jugadores debe tener el mismo reloj.

**Alineación de bloqueos en OS X** Siga los pasos a continuación para alinear los relojes en OSX:

1. Abrir preferencias **de fecha y hora** en cada cuadro OSX
1. Marcar la fecha y la hora **establecidas automáticamente**
1. Pegue el valor 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com en el menú desplegable o simplemente ejecute *sudo ntpdate -u -v 0.pool.ntp.org*
1. Inicio de los más de 2 reproductores

Es posible que tarde algún tiempo en que los reproductores inicio una nueva secuencia alineada.

