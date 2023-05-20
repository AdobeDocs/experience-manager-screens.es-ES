---
title: Información general sobre la arquitectura de creación y publicación
seo-title: Author and Publish Architectural Overview
description: La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. AEM El contenido se crea en una instancia de autor de y, a continuación, se replica mediante reenvío en varias instancias de publicación. Siga esta página para obtener más información sobre la descripción general de la arquitectura de creación y publicación.
seo-description: AEM Screens architecture resembles a traditional AEM Sites architecture. Content is authored on an AEM author instance and then forward-replicated to multiple publish instances. Follow this page to learn more on author and publish architectural overview.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 1%

---

# Información general sobre la arquitectura de creación y publicación {#author-and-publish-architectural-overview}

En esta página se destacan los siguientes temas:

* **Introducción a los servidores de publicación**
* **Información general de la arquitectura**
* **Proceso de registro**

## Requisitos previos {#prerequisites}

Antes de empezar a usar los servidores de creación y publicación, debe tener conocimientos previos de lo siguiente:

* **AEM Topología de**
* **Creación y administración de un proyecto de AEM Screens**
* **Proceso de registro de dispositivos**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens AEM solo está disponible si ha instalado el paquete de funciones 2 de Screens de 6.4. Para obtener acceso a este paquete de funciones, debe ponerse en contacto con el Soporte técnico de Adobe y solicitar acceso. Una vez que tenga los permisos necesarios, puede descargarlo desde Package Share.

## Introducción {#introduction}

La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. AEM El contenido se crea en una instancia de autor de y, a continuación, se replica mediante reenvío en varias instancias de publicación. Los dispositivos AEM Screens AEM ahora se pueden conectar a una granja de servidores de publicación de a través del equilibrador de carga. AEM Se pueden agregar varias instancias de publicación para seguir escalando la granja de servidores de publicación.

*Por ejemplo*, un autor de contenido de AEM Screens emite un comando en el sistema de creación para un dispositivo concreto que está configurado para interactuar con un conjunto de servidores de publicación o un autor de contenido de AEM Screens que obtiene información sobre dispositivos configurados para interactuar con conjuntos de servidores de publicación.

El diagrama siguiente ilustra los entornos de creación y publicación.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Diseño arquitectónico {#architectural-design}

Hay cinco componentes arquitectónicos que facilitan esta solución:

* ***Duplicación de contenido*** del autor a la publicación para su visualización por dispositivos

* ***Inverso*** replicar contenido binario de la publicación (recibida desde dispositivos) al autor
* ***Enviando*** comandos del autor para publicar mediante API de REST específicas
* ***Mensajes*** entre instancias de publicación para sincronizar actualizaciones y comandos de información del dispositivo
* ***Sondeo*** por parte del autor de instancias de publicación para obtener información del dispositivo a través de API de REST específicas

### Replicación (reenvío) del contenido y las configuraciones  {#replication-forward-of-content-and-configurations}

Los agentes de replicación estándar se utilizan para replicar el contenido del canal de pantallas, las configuraciones de ubicación y las configuraciones de dispositivo. Esto permite a los autores actualizar el contenido de un canal y, opcionalmente, pasar por algún tipo de flujo de trabajo de aprobación antes de publicar actualizaciones de canal. Es necesario crear un agente de replicación para cada instancia de publicación de la granja de servidores de publicación.

El diagrama siguiente ilustra el proceso de replicación:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Es necesario crear un agente de replicación para cada instancia de publicación de la granja de servidores de publicación.

### Agentes y comandos de replicación de Screens  {#screens-replication-agents-and-commands}

Se crean agentes de replicación específicos de Pantallas personalizadas para enviar comandos de la instancia de autor al dispositivo de AEM Screens. Las instancias de publicación de AEM sirven como intermediarias para reenviar estos comandos al dispositivo.

Esto permite a los autores seguir administrando el dispositivo, como, por ejemplo, enviar actualizaciones de dispositivos y realizar capturas de pantalla desde el entorno de creación. Los agentes de replicación de AEM Screens tienen una configuración de transporte personalizada, como los agentes de replicación estándar.

### Mensajería entre instancias de publicación  {#messaging-between-publish-instances}

En muchos casos, un comando solo está pensado para enviarse a un dispositivo una sola vez. Sin embargo, en una arquitectura de publicación con equilibrio de carga, se desconoce a qué instancia de publicación se conecta el dispositivo.

Por lo tanto, la instancia de autor envía el mensaje a todas las instancias de publicación. Sin embargo, solo se debe transmitir un único mensaje al dispositivo. Para garantizar la mensajería correcta, debe haber alguna comunicación entre instancias de publicación. Esto se logra utilizando *Apache ActiveMQ Artemis*. Cada instancia de publicación se coloca en una topología de correspondencia imprecisa mediante el servicio de detección de Sling basado en Oak, y ActiveMQ se configura para que cada instancia de publicación pueda comunicarse y crear una única cola de mensajes. El dispositivo Screens sondea la granja de servidores de publicación a través del equilibrador de carga y toma el comando de la parte superior de la cola.

### Replicación inversa {#reverse-replication}

En muchos casos, después de un comando, se espera algún tipo de respuesta del dispositivo Screens para reenviarla a la instancia de autor. AEM A fin de lograr este objetivo, es preciso establecer una ***Replicación inversa*** se utiliza.

* Cree un agente de replicación inversa para cada instancia de publicación, similar a los agentes de replicación estándar y a los agentes de replicación de pantallas.
* Una configuración del iniciador del flujo de trabajo escucha los nodos modificados en la instancia de publicación y, a su vez, déclencheur un flujo de trabajo para colocar la respuesta del dispositivo en la bandeja de salida de la instancia de publicación.
* Una replicación inversa en este contexto solo se utiliza para datos binarios (como archivos de registro y capturas de pantalla) proporcionados por los dispositivos. Los datos no binarios se recuperan mediante sondeo.
* AEM La replicación inversa sondeada desde la instancia de autor de la recupera la respuesta y la guarda en la instancia de autor.

### Sondeo de instancias de publicación  {#polling-of-publish-instances}

La instancia de autor debe poder sondear los dispositivos para obtener un latido y conocer el estado de un dispositivo conectado.

Los dispositivos hacen ping al equilibrador de carga y se enrutan a una instancia de publicación. La instancia de publicación expone el estado del dispositivo a través de una API de publicación ofrecida @ **api/screens-dcc/devices/static** para todos los dispositivos activos y **api/screens-dcc/devices/&lt;device_id>/status.json** para un solo dispositivo.

La instancia de autor sondea todas las instancias de publicación y combina las respuestas de estado del dispositivo en un solo estado. El trabajo programado que sondea al autor es `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` y se pueden configurar en función de una expresión cron.

## Registro {#registration}

AEM El registro sigue originándose en la instancia de autor de la. El dispositivo AEM Screens se dirige a la instancia de autor y se completa el registro.

AEM Una vez que se ha registrado un dispositivo en el entorno de creación, la configuración del dispositivo y las asignaciones de canal/programación se replican en las instancias de publicación de la. La configuración del dispositivo AEM Screens AEM se actualiza a continuación para que apunte al equilibrador de carga situado frente a la granja de servidores de publicación de la. Se pretende que sea una configuración única, una vez que el dispositivo Screens se conecte correctamente al entorno de publicación, puede seguir recibiendo comandos procedentes del entorno de creación y no debe haber necesidad de conectar nunca directamente el dispositivo Screens al entorno de creación.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Pasos siguientes {#the-next-steps}

Una vez que haya comprendido el diseño arquitectónico de la configuración de creación y publicación en AEM Screens, consulte [Configuración de autor y publicación para AEM Screens](author-and-publish.md) para obtener más información.
