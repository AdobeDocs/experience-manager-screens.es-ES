---
title: Información general sobre la arquitectura de creación y publicación
description: La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y se replica mediante reenvío en varias instancias de publicación.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Información general sobre la arquitectura de creación y publicación {#author-and-publish-architectural-overview}

En esta página se destacan los siguientes temas:

* **Introducción a los servidores de publicación**
* **Información general de arquitectura**
* **Proceso de registro**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y de publicación, debe tener conocimientos previos de lo siguiente:

* **Topología de AEM**
* **Creación y administración de un proyecto de AEM Screens**
* **Proceso de registro de dispositivo**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este paquete de funciones, póngase en contacto con el Soporte técnico de Adobe y solicite acceso. Una vez que tenga permiso, descárguelo de Package Share.

## Introducción {#introduction}

La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y se replica mediante reenvío en varias instancias de publicación. Los dispositivos de AEM Screens ahora se pueden conectar a una granja de servidores de publicación de AEM mediante un equilibrador de carga. Se pueden agregar varias instancias de publicación de AEM para seguir escalando la granja de servidores de publicación.

*Por ejemplo*, un autor de contenido de AEM Screens emite un comando en el sistema de creación de un dispositivo en particular. Ese dispositivo está configurado para interactuar con un conjunto de servidores de publicación. O bien, interactúe con un Autor de contenido de AEM Screens que obtenga información sobre los dispositivos configurados para interactuar con granjas de publicación.

El diagrama siguiente ilustra el entorno de creación y el entorno de publicación.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Diseño arquitectónico {#architectural-design}

Hay cinco componentes arquitectónicos que facilitan esta solución:

* ***Replicando contenido*** de autor a publicación para su visualización por dispositivos

* ***Invertir*** la replicación del contenido binario desde el entorno de publicación (recibido desde dispositivos) al entorno de creación.
* ***Enviando*** comandos del autor para publicar mediante API REST específicas.
* ***Mensajería*** entre instancias de publicación para sincronizar actualizaciones y comandos de información del dispositivo.
* ***Sondeo*** realizado por el autor de instancias de publicación para obtener información del dispositivo mediante API de REST específicas.

### Replicación (reenvío) del contenido y las configuraciones {#replication-forward-of-content-and-configurations}

Los agentes de replicación estándar se utilizan para replicar el contenido del canal de AEM Screens, las configuraciones de ubicación y las configuraciones de dispositivo. Esta funcionalidad permite a los autores actualizar el contenido de un canal y, opcionalmente, pasar por algún tipo de flujo de trabajo de aprobación antes de publicar actualizaciones de canal. Se debe crear un agente de replicación para cada instancia de publicación de la granja de servidores de publicación.

El diagrama siguiente ilustra el proceso de replicación:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Se debe crear un agente de replicación para cada instancia de publicación de la granja de servidores de publicación.

### Agentes y comandos de replicación de Screens {#screens-replication-agents-and-commands}

Los agentes de replicación específicos de Screens personalizados se crean para enviar comandos de la instancia de autor al dispositivo de AEM Screens. Las instancias de publicación de AEM sirven como intermediarias para reenviar estos comandos al dispositivo.

Este flujo de trabajo permite a los autores seguir administrando el dispositivo, como, por ejemplo, enviar actualizaciones de dispositivos y realizar capturas de pantalla desde el entorno de creación. Los agentes de replicación de AEM Screens tienen una configuración de transporte personalizada, como los agentes de replicación estándar.

### Mensajería entre instancias de publicación {#messaging-between-publish-instances}

A menudo, un comando solo está pensado para enviarse a un dispositivo una sola vez. Sin embargo, en una arquitectura de publicación con equilibrio de carga, la instancia de publicación a la que se conecta el dispositivo es desconocida.

Por lo tanto, la instancia de autor envía el mensaje a todas las instancias de publicación. Sin embargo, solo se debe transmitir un único mensaje al dispositivo. Para garantizar la mensajería correcta, debe haber comunicación entre instancias de publicación. Esta comunicación se logra usando *Apache ActiveMQ Artemis*. Cada instancia de publicación se coloca en una topología de correspondencia imprecisa mediante el servicio de detección de Sling basado en Oak. ActiveMQ está configurado para que cada instancia de publicación pueda comunicarse y crear una única cola de mensajes. El dispositivo AEM Screens sondea la granja de servidores de publicación de AEM a través del equilibrador de carga y toma el comando de la parte superior de la cola.

### Replicación inversa {#reverse-replication}

A menudo, después de un comando, se espera algún tipo de respuesta del dispositivo Screens para reenviarla a la instancia de autor. Para lograr este AEM se utiliza ***replicación inversa***.

* Cree un agente de replicación inversa para cada instancia de publicación, similar a los agentes de replicación estándar y a los agentes de replicación de AEM Screens.
* Una configuración del iniciador del flujo de trabajo escucha los nodos modificados en la instancia de publicación de AEM y, a su vez, déclencheur un flujo de trabajo para colocar la respuesta del dispositivo en la bandeja de salida de la instancia de publicación de AEM.
* Una replicación inversa en este contexto solo se utiliza para los datos binarios (como archivos de registro y capturas de pantalla) proporcionados por los dispositivos. Se recupera el sondeo de datos no binarios.
* El sondeo de replicación inversa de la instancia de autor de AEM recupera la respuesta y la guarda en la instancia de autor.

### Sondeo de instancias de publicación {#polling-of-publish-instances}

Las instancias de autor deben poder sondear los dispositivos para obtener un latido y conocer el estado de un dispositivo conectado.

Los dispositivos hacen ping al equilibrador de carga y se enrutan a una instancia de publicación. La instancia de publicación de AEM expone el estado del dispositivo a través de una API de publicación ofrecida en **api/screens-dcc/devices/static** para todos los dispositivos activos y en **api/screens-dcc/devices/&lt;device_id>/status.json** para un solo dispositivo.

La instancia de autor sondea todas las instancias de publicación y combina las respuestas de estado del dispositivo en un solo estado. El trabajo programado que sondea al autor es `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` y se puede configurar en función de una expresión cron.

## Registro {#registration}

El registro sigue originándose en la instancia de autor de AEM. El dispositivo AEM Screens se dirige a la instancia de autor y se completa el registro.

Después de registrar un dispositivo en el entorno de creación de AEM, la configuración del dispositivo y las asignaciones de canal/programación se replican en las instancias de publicación de AEM. La configuración del dispositivo AEM Screens se actualiza para que apunte al equilibrador de carga delante de la granja de servidores de publicación de AEM. Este acuerdo está diseñado para ser una configuración única. Una vez que el dispositivo Screens se haya conectado correctamente al entorno de publicación, puede seguir recibiendo comandos procedentes del entorno de creación. No debe ser necesario conectar directamente el dispositivo AEM Screens al entorno de creación de AEM.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Pasos siguientes {#the-next-steps}

Cuando comprenda el diseño arquitectónico de la configuración de autor y publicación en AEM Screens, consulte [Configuración de autor y publicación para AEM Screens](author-and-publish.md) para obtener más información.
