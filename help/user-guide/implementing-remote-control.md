---
title: Implementación del control remoto
description: Obtenga información acerca de la función de control remoto de Screens en AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Uso del control remoto de Screens {#implementing-remote-control}

La función de control remoto facilita el acceso a la IU de administración, al conmutador de canales o a funciones como Borrar caché y volver a cargar. Además, proporciona un método para ver la versión local del firmware y la información del sistema en el reproductor. Esta capacidad es especialmente útil porque puede resultar difícil conectar un mouse. O bien, puede operar en dispositivos de producción que estén fuera del alcance y aún más si el reproductor ha perdido la conexión con AEM. También resulta útil cuando se utiliza Samsung RMS, ya que la diferencia de resolución puede dificultar la localización y apertura de la interfaz de usuario del administrador con un ratón.

## Combinaciones de teclas comunes de control remoto {#using-common-remote-control}

En todos los reproductores, puede utilizar las siguientes combinaciones de teclas en el control remoto de Screens:

1. Alternar IU de administración: CTRL + 1
1. Conmutador de canales de alternancia - CTRL + 2
1. Borrar caché: CTRL + ALT + 3
1. Volver a cargar el reproductor: CTRL + 4

## Combinaciones de teclas de control remoto específicas de Tizen {#using-tizen-remote-control}

Específico del reproductor Tizen, puede utilizar el mando a distancia del hardware o el mando a distancia del software disponible en Samsung RMS para acceder a estas funciones:

1. A - Alternar la IU de administración
1. B - Conmutador de canal de conmutación
1. C - Borrar caché
1. D - Recargar reproductor

## Más notas de uso {#using-additional-remote-control}

1. Con la IU de administración abierta, puede utilizar las flechas arriba y abajo para navegar por las pestañas y ver información en ellas.
1. Con el conmutador de canales abierto, puede utilizar las teclas de flecha arriba y abajo para desplazarse por los canales. También puede presionar la tecla `Enter` (o el botón situado en el centro de las flechas del control remoto) para cambiar de canal.

El diagrama siguiente ilustra el uso de la tecla en un control remoto Samsung:
![imagen](assets/tizen/remote.png)

>[!NOTE]
>Si establece los valores de configuración del dispositivo de enableAdminUI o enableOSD en false, el control remoto no conmuta la interfaz de usuario de administración y el conmutador de canales. No puede utilizar las teclas de flecha para desplazarse por la interfaz de usuario de administración o los canales. Sin embargo, aún puede borrar la caché y volver a cargar el reproductor. Puede desactivar la función de control remoto si alguna de las combinaciones de teclado entra en conflicto con el contenido interactivo mediante este código:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
