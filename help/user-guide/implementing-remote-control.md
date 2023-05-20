---
title: Implementación del control remoto
seo-title: Impementing the Remote Control
description: Siga esta página para obtener más información sobre la función de control remoto de Screens.
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: 6cd68194bf3128464ec368f3e7fd69d20925c3d6
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Uso del control remoto de Screens  {#implementing-remote-control}

La función de control remoto facilita el acceso a la interfaz de usuario del administrador, al conmutador de canales o a funciones como Borrar caché y volver a cargar. Además, le proporciona un método para ver la versión local del firmware y la información del sistema en el reproductor. AEM Esto es especialmente útil porque puede ser difícil conectar un ratón y operar en dispositivos de producción que están fuera de alcance y aún más si el reproductor ha perdido la conexión con el sistema de reproducción de la pantalla de inicio de la pantalla de inicio de la pantalla de inicio de la pantalla de inicio de la pantalla de inicio. Esto también resulta útil cuando se utiliza Samsung RMS, ya que la diferencia de resolución puede dificultar la localización y apertura de la interfaz de usuario del administrador con un ratón.

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

## Notas de uso adicionales {#using-additional-remote-control}

1. Con la IU de administración abierta, puede utilizar las flechas arriba y abajo para navegar por las pestañas y ver información en ellas.
1. Con el conmutador de canales abierto, puede utilizar las teclas de las flechas arriba y abajo para navegar por los canales y puede pulsar la tecla Intro (o el botón situado en el centro de las flechas del mando a distancia) para cambiar de canal.

El diagrama siguiente ilustra el uso de la tecla en un control remoto Samsung:
![imagen](assets/tizen/remote.png)

>[!NOTE]
>Si establece los valores de configuración del dispositivo de enableAdminUI o enableOSD en false, el control remoto no conmutará la interfaz de usuario de administración y el conmutador de canal. Tampoco podrá utilizar las teclas de flecha para navegar por la interfaz de usuario de administración o los canales. Sin embargo, aún puede borrar la caché y volver a cargar el reproductor. Puede desactivar la función de control remoto si alguna de las combinaciones de teclado entra en conflicto con el contenido interactivo mediante este código:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
