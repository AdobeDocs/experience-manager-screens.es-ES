---
title: Información general sobre la arquitectura de autor y Publish
description: La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. AEM El contenido se crea en una instancia de autor de y, a continuación, se replica mediante reenvío en varias instancias de publicación.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# Información general sobre la arquitectura de autor y Publish {#author-and-publish-architectural-overview}

En esta página se destacan los siguientes temas:

* **Introducción a los servidores Publish**
* **Información general de arquitectura**
* **Proceso de registro**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y de publicación, debe tener conocimientos previos de lo siguiente:

* AEM **Topología de la**
* **Creación y administración de un proyecto de AEM Screens**
* **Proceso de registro de dispositivo**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens AEM solo está disponible si ha instalado el paquete de funciones 2 de Screens de la versión 6.4 de. Para obtener acceso a este paquete de funciones, póngase en contacto con el Soporte técnico de Adobe y solicite acceso. Una vez que tenga permiso, descárguelo de Package Share.

## Introducción {#introduction}

La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. AEM El contenido se crea en una instancia de autor de y, a continuación, se replica mediante reenvío en varias instancias de publicación. Los dispositivos de AEM Screens AEM ahora se pueden conectar a una granja de servidores de publicación de mediante un equilibrador de carga. AEM Se pueden agregar varias instancias de publicación para seguir escalando la granja de servidores de publicación.

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

Los agentes de replicación específicos de Screens personalizados se crean para enviar comandos de la instancia de autor al dispositivo de AEM Screens. AEM Las instancias de Publish sirven de intermediario para reenviar estos comandos al dispositivo.

Este flujo de trabajo permite a los autores seguir administrando el dispositivo, como, por ejemplo, enviar actualizaciones de dispositivos y realizar capturas de pantalla desde el entorno de creación. Los agentes de replicación de AEM Screens tienen una configuración de transporte personalizada, como los agentes de replicación estándar.

### Mensajes entre instancias de Publish {#messaging-between-publish-instances}

A menudo, un comando solo está pensado para enviarse a un dispositivo una sola vez. Sin embargo, en una arquitectura de publicación con equilibrio de carga, la instancia de publicación a la que se conecta el dispositivo es desconocida.

Por lo tanto, la instancia de autor envía el mensaje a todas las instancias de Publish. Sin embargo, solo se debe transmitir un único mensaje al dispositivo. Para garantizar la mensajería correcta, debe haber comunicación entre instancias de publicación. Esta comunicación se logra usando *Apache ActiveMQ Artemis*. Cada instancia de publicación se coloca en una topología de correspondencia imprecisa mediante el servicio de detección de Sling basado en Oak. ActiveMQ está configurado para que cada instancia de publicación pueda comunicarse y crear una única cola de mensajes. El dispositivo AEM Screens AEM sondea la granja de servidores de publicación de la publicación mediante el equilibrador de carga y recoge el comando desde la parte superior de la cola.

### Replicación inversa {#reverse-replication}

A menudo, después de un comando, se espera algún tipo de respuesta del dispositivo Screens para reenviarla a la instancia de autor. AEM Para lograr este objetivo, se utiliza ***replicación inversa*** de la lista de distribución.

* Cree un agente de replicación inversa para cada instancia de publicación, similar a los agentes de replicación estándar y a los agentes de replicación de AEM Screens.
* AEM Una configuración del iniciador del flujo de trabajo escucha los nodos modificados en la instancia de publicación de la y, a su vez, déclencheur AEM un flujo de trabajo para colocar la respuesta del dispositivo en la bandeja de salida de la instancia de publicación de la.
* Una replicación inversa en este contexto solo se utiliza para los datos binarios (como archivos de registro y capturas de pantalla) proporcionados por los dispositivos. Se recupera el sondeo de datos no binarios.
* AEM El sondeo de replicación inversa de la instancia de autor de la recupera la respuesta y la guarda en la instancia de autor.

### Sondeo de instancias de Publish {#polling-of-publish-instances}

Las instancias de autor deben poder sondear los dispositivos para obtener un latido y conocer el estado de un dispositivo conectado.

Los dispositivos hacen ping al equilibrador de carga y se enrutan a una instancia de publicación. AEM La instancia de publicación del dispositivo expone el estado a través de una API de Publish proporcionada en **api/screens-dcc/devices/static** para todos los dispositivos activos y en **api/screens-dcc/devices/&lt;device_id>/status.json** para un solo dispositivo.

La instancia de autor sondea todas las instancias de publicación y combina las respuestas de estado del dispositivo en un solo estado. El trabajo programado que sondea al autor es `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` y se puede configurar en función de una expresión cron.

## Registro {#registration}

AEM El registro sigue originándose en la instancia de autor de la. El dispositivo AEM Screens se dirige a la instancia de autor y se completa el registro.

AEM AEM Una vez que un dispositivo se registra en el entorno de creación de la, la configuración del dispositivo y las asignaciones de canal/programación se replican en las instancias de publicación de la. A continuación, la configuración del dispositivo AEM Screens AEM se actualiza para que apunte al equilibrador de carga delante de la granja de servidores de publicación de. Este acuerdo está diseñado para ser una configuración única. Una vez que el dispositivo Screens se haya conectado correctamente al entorno de publicación, puede seguir recibiendo comandos procedentes del entorno de creación. No debe ser necesario conectar el dispositivo AEM Screens AEM directamente al entorno de creación de la.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Pasos siguientes {#the-next-steps}

Cuando comprenda el diseño arquitectónico de la configuración de autor y publicación en AEM Screens, consulte [Configuración de autor y Publish para AEM Screens](author-and-publish.md) para obtener más información.
