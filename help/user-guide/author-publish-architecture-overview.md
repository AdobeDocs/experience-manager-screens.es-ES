---
title: Información general sobre la arquitectura de creación y publicación
seo-title: Información general sobre la arquitectura de creación y publicación
description: La arquitectura de AEM Screens se parece a una arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor AEM y luego se rereplica en varias instancias de publicación. Siga esta página para obtener más información sobre la arquitectura de autor y publicación.
seo-description: La arquitectura de AEM Screens se parece a una arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor AEM y luego se rereplica en varias instancias de publicación. Siga esta página para obtener más información sobre la arquitectura de autor y publicación.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administración de Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 3%

---

# Información general sobre la arquitectura de creación y publicación {#author-and-publish-architectural-overview}

Esta página destaca los siguientes temas:

* **Introducción a servidores de publicación**
* **Información general de arquitectura**
* **Proceso de registro**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y publicación, debe tener conocimientos previos de:

* **Topología AEM**
* **Creación y administración de proyectos de AEM Screens**
* **Proceso de registro de dispositivos**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Introducción {#introduction}

La arquitectura de AEM Screens se parece a una arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor AEM y luego se rereplica en varias instancias de publicación. Los dispositivos AEM Screens ahora se pueden conectar a un conjunto de servidores de publicación AEM mediante el equilibrador de carga. Se pueden agregar varias instancias de publicación AEM para seguir escalando el conjunto de servidores de publicación.

*Por ejemplo*, un autor de contenido de AEM Screens emite un comando en el sistema de creación para un dispositivo concreto que está configurado para interactuar con un conjunto de servidores de publicación o un autor de contenido de AEM Screens que obtiene información sobre dispositivos configurados para interactuar con entornos de publicación.

El diagrama siguiente ilustra los entornos de autor y publicación.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Diseño arquitectónico {#architectural-design}

Hay cinco componentes arquitectónicos que facilitan esta solución:

* ***Duplicación de*** contenido del autor para publicarlo para que lo muestren los dispositivos

* ****** Reproducir el contenido binario de la publicación (recibido de los dispositivos) al autor
* ****** Envío de comandos del autor para publicar mediante API de REST específicas
* ****** Mensajería entre instancias de publicación para sincronizar actualizaciones y comandos de información del dispositivo
* ****** Polinización por parte del autor de instancias de publicación para obtener información del dispositivo a través de API de REST específicas

### Replicación (reenvío) de contenido y configuraciones  {#replication-forward-of-content-and-configurations}

Los agentes de replicación estándar se utilizan para replicar el contenido del canal de pantallas, las configuraciones de ubicación y las configuraciones de dispositivos. Esto permite a los autores actualizar el contenido de un canal y, opcionalmente, pasar por algún tipo de flujo de trabajo de aprobación antes de publicar actualizaciones del canal. Se debe crear un agente de replicación para cada instancia de publicación en el conjunto de servidores de publicación.

El diagrama siguiente ilustra el proceso de replicación:

![screen_shot_2019-03-04at3935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Se debe crear un agente de replicación para cada instancia de publicación en el conjunto de servidores de publicación.

### Comandos y agentes de replicación de Screens  {#screens-replication-agents-and-commands}

Se crean agentes de replicación específicos de Screens personalizados para enviar comandos desde la instancia Autor al dispositivo AEM Screens. Las instancias de AEM Publish sirven como intermediario para reenviar estos comandos al dispositivo.

Esto permite a los autores seguir administrando el dispositivo, como, por ejemplo, enviar actualizaciones del dispositivo y tomar capturas de pantalla del entorno de creación. Los agentes de replicación de AEM Screens tienen una configuración de transporte personalizada, como los agentes de replicación estándar.

### Mensajería entre instancias de publicación  {#messaging-between-publish-instances}

En muchos casos, un comando solo está pensado para enviarse a un dispositivo una sola vez. Sin embargo, en una arquitectura de publicación equilibrada de carga es desconocido a qué instancia de publicación se está conectando el dispositivo.

Por lo tanto, la instancia de autor envía el mensaje a todas las instancias de publicación. Sin embargo, solo se debe retransmitir un solo mensaje al dispositivo. Para garantizar la mensajería correcta, debe realizarse alguna comunicación entre instancias de publicación. Esto se logra utilizando *Apache ActiveMQ Artemis*. Cada instancia de publicación se coloca en una Topología acoplada de forma flexible mediante el servicio de detección de Sling basado en Oak y ActiveMQ está configurado para que cada instancia de publicación pueda comunicarse y crear una sola cola de mensajes. El dispositivo Screens sondea el conjunto de servidores de publicación a través del equilibrador de carga y recoge el comando de la parte superior de la cola.

### Replicación inversa {#reverse-replication}

En muchos casos, tras un comando, se espera algún tipo de respuesta del dispositivo Screens para reenviarla a la instancia de autor. Para lograr este AEM se utiliza ***Reverse replication***.

* Cree un agente de replicación inversa para cada instancia de publicación, similar a los agentes de replicación estándar y a los agentes de replicación de pantallas.
* Una configuración del iniciador de flujo de trabajo escucha los nodos modificados en la instancia de publicación y, a su vez, déclencheur un flujo de trabajo para colocar la respuesta del dispositivo en la bandeja de salida de la instancia de publicación.
* Una replicación inversa en este contexto solo se utiliza para datos binarios (como, archivos de registro y capturas de pantalla) proporcionados por los dispositivos. Los datos no binarios se recuperan mediante sondeo.
* La replicación inversa sondeada desde la instancia de autor de AEM recupera la respuesta y la guarda en la instancia de autor.

### Sondeo de instancias publicadas  {#polling-of-publish-instances}

La instancia de autor debe poder sondear los dispositivos para obtener un latido y conocer el estado de un dispositivo conectado.

Dispositivos que hacen ping en el equilibrador de carga y se enrutan a una instancia de publicación. A continuación, la instancia de publicación expone el estado del dispositivo a través de una API de publicación servida en **api/screens-dcc/device/static** para todos los dispositivos activos y en **api/screens-dcc/Devices/&lt;device_id>/status.json** para un solo dispositivo.

La instancia de autor sondea todas las instancias de publicación y combina las respuestas de estado del dispositivo en un solo estado. El trabajo programado que sondea en author es `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` y se puede configurar en función de una expresión cron.

## Registro {#registration}

El registro sigue originándose en la instancia de autor de AEM. El dispositivo AEM Screens apunta a la instancia de autor y se completa el registro.

Una vez registrado un dispositivo en el entorno de creación, la configuración del dispositivo y las asignaciones de canal/programación se replican en las instancias de publicación de AEM. A continuación, la configuración del dispositivo AEM Screens se actualiza para que apunte al equilibrador de carga delante del conjunto de AEM de publicación. Se trata de una configuración única, una vez que el dispositivo Screens se conecta correctamente al entorno de publicación, puede seguir recibiendo comandos procedentes del entorno de creación y no debería ser necesario conectar el dispositivo Screens al entorno de creación directamente.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Pasos siguientes {#the-next-steps}

Una vez que haya comprendido el diseño arquitectónico de la configuración de autor y publicación en AEM Screens, consulte [Configuración de autor y publicación para AEM Screens](author-and-publish.md) para obtener más información.
