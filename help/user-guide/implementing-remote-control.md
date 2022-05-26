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
source-git-commit: a256f624c4b647deb4cee7668665ad7b576932e7
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Uso del control remoto de Screens  {#implementing-remote-control}

La función de control remoto facilita el acceso a la IU de administración, al conmutador de canales o a funciones como Borrar caché y recargar. Además, le proporciona un método para ver la versión de firmware local y la información del sistema en el reproductor. Esto es especialmente útil porque puede ser difícil conectar un ratón y operar en dispositivos de producción que están fuera de alcance y aún más si el reproductor ha perdido la conexión con AEM. Esto también resulta útil cuando se utiliza Samsung RMS porque la diferencia de resolución puede dificultar la localización y apertura de la IU de administración con un ratón.

## Combinaciones de teclas de control remoto común {#using-common-remote-control}

En todos los reproductores puede utilizar las siguientes combinaciones de teclas en el control remoto de Screens:

1. Alternar IU de administración: CTRL + 1
1. Alternar conmutador de canales - CTRL + 2
1. Borrar caché - CTRL + ALT + 3
1. Volver a cargar reproductor - CTRL + 4

## Combinaciones de teclas de control remoto específicas de Tizen {#using-tizen-remote-control}

Específicamente para el reproductor Tizen, puede utilizar el mando a distancia del hardware o el software remoto disponible en Samsung RMS para acceder a estas funciones:

1. A: Alternar la interfaz de usuario del administrador
1. B: Alternar conmutador de canal
1. C: Borrar caché
1. D: Recargar reproductor

## Notas de uso adicionales {#using-additional-remote-control}

1. Con la interfaz de usuario de administración abierta, puede utilizar las flechas arriba y abajo para desplazarse por las pestañas y ver información en las pestañas.
1. Con el conmutador de canales abierto, puede utilizar las teclas de flecha arriba y abajo para navegar por los canales y puede pulsar la tecla Intro (o el botón del centro de las flechas del mando a distancia) para cambiar de canal.

El diagrama siguiente ilustra el uso de claves en un remoto de Samsung:
![image](assets/tizen/remote.png)

>[!NOTE]
>Si establece los valores de configuración del dispositivo enableAdminUI y/o enableOSD en false, el control remoto no cambiará la IU de administración ni el conmutador de canales. Tampoco podrá utilizar las teclas de flecha para navegar por la IU o los canales de administración. Sin embargo, aún puede borrar la caché y volver a cargar el reproductor. Puede desactivar la función de control remoto si alguna de las combinaciones de teclas entra en conflicto con el contenido interactivo mediante este código:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
