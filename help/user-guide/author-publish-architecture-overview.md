---
title: Descripción general de la arquitectura de creación y publicación
seo-title: Descripción general de la arquitectura de creación y publicación
description: La arquitectura de AEM Screens se asemeja a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se reenvía a varias instancias de publicación. Siga esta página para obtener más información sobre cómo crear y publicar información general de la arquitectura.
seo-description: La arquitectura de AEM Screens se asemeja a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se reenvía a varias instancias de publicación. Siga esta página para obtener más información sobre cómo crear y publicar información general de la arquitectura.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 3%

---


# Descripción general de la arquitectura de creación y publicación {#author-and-publish-architectural-overview}

Esta página resalta los siguientes temas:

* **Introducción a los servidores de publicación**
* **Información general de arquitectura**
* **Proceso de registro**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y publicación, debe tener conocimientos previos de:

* **Topología AEM**
* **Creación y administración de proyectos de AEM Screens**
* **Proceso de registro del dispositivo**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Introducción {#introduction}

La arquitectura de AEM Screens se asemeja a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se reenvía a varias instancias de publicación. Los dispositivos AEM Screens ahora se pueden conectar a un conjunto de servidores de publicación AEM mediante equilibrador de carga. Se pueden agregar varias instancias de publicación AEM para continuar escalando el conjunto de publicaciones.

*Por ejemplo*, un autor de contenido de AEM Screens emite un comando en el sistema de creación para un dispositivo concreto configurado para interactuar con un conjunto de servidores de publicación o un autor de contenido de AEM Screens que obtiene información sobre dispositivos configurados para interactuar con los conjuntos de servidores de publicación.

El diagrama siguiente ilustra los entornos de autor y publicación.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Diseño arquitectónico {#architectural-design}

Existen cinco componentes arquitectónicos que facilitan esta solución:

* ***Replicar contenido*** del autor para publicarlo para su visualización por dispositivos

* ***Reversión*** del contenido binario replicado de la publicación (recibido de dispositivos) al autor
* ***Envío*** de comandos del autor para la publicación mediante API de REST específicas
* ***Mensajería*** entre instancias de publicación para sincronizar actualizaciones y comandos de información del dispositivo
* ***Encuesta*** del autor de instancias de publicación para obtener información del dispositivo a través de API de REST específicas

### Replicación (avanzada) de contenido y configuraciones  {#replication-forward-of-content-and-configurations}

Los agentes de replicación estándar se utilizan para replicar contenido de canal de pantallas, configuraciones de ubicación y configuraciones de dispositivos. Esto permite a los autores actualizar el contenido de un canal y, opcionalmente, pasar por algún tipo de flujo de trabajo de aprobación antes de publicar actualizaciones de canal. Se debe crear un agente de replicación para cada instancia de publicación en el conjunto de servidores de publicación.

El diagrama siguiente ilustra el proceso de replicación:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Se debe crear un agente de replicación para cada instancia de publicación en el conjunto de servidores de publicación.

### Screens Replication Agent and Commands  {#screens-replication-agents-and-commands}

Las pantallas personalizadas crean agentes de replicación específicos para enviar comandos de la instancia Autor al dispositivo AEM Screens. Las instancias de AEM Publish sirven de intermediario para reenviar estos comandos al dispositivo.

Esto permite a los autores seguir administrando el dispositivo, como enviar actualizaciones del dispositivo y tomar capturas de pantalla del entorno del autor. Los agentes de replicación de AEM Screens tienen una configuración de transporte personalizada, como los agentes de replicación estándar.

### Mensajería entre instancias de publicación  {#messaging-between-publish-instances}

En muchos casos, un comando solo se envía a un dispositivo una vez. Sin embargo, en una arquitectura de publicación con equilibrio de carga se desconoce a qué instancia de publicación se conecta el dispositivo.

Por lo tanto, la instancia de creación envía el mensaje a todas las instancias de Publish. Sin embargo, solo se debe retransmitir un solo mensaje al dispositivo. Para garantizar la correcta mensajería, es necesario realizar alguna comunicación entre instancias de publicación. Esto se logra usando *Apache ActiveMQ Artemis*. Cada instancia de publicación se coloca en una Topología acoplada de forma flexible mediante el servicio de detección de Sling basado en Oak y ActiveMQ se configura para que cada instancia de publicación pueda comunicarse y crear una sola cola de mensajes. El dispositivo Screens sondea el conjunto de servidores de publicación mediante el equilibrador de carga y recoge el comando desde la parte superior de la cola.

### Replicación inversa {#reverse-replication}

En muchos casos, después de un comando, se espera que el dispositivo Screens envíe algún tipo de respuesta a la instancia del autor. Para lograr este AEM se utiliza la replicación ****** inversa.

* Cree un agente de replicación inversa para cada instancia de publicación, similar a los agentes de replicación estándar y a los agentes de replicación de pantallas.
* Una configuración del iniciador de flujo de trabajo escucha los nodos modificados en la instancia de publicación y, a su vez, activa un flujo de trabajo para colocar la respuesta del dispositivo en la bandeja de salida de la instancia de publicación.
* Una replicación inversa en este contexto solo se utiliza para datos binarios (como archivos de registro y capturas de pantalla) proporcionados por los dispositivos. Los datos no binarios se recuperan mediante sondeo.
* La replicación inversa sondeada desde la instancia de creación de AEM recupera la respuesta y la guarda en la instancia de creación.

### Encuesta de instancias de publicación  {#polling-of-publish-instances}

La instancia de creación debe poder sondear los dispositivos para obtener un latido y conocer el estado de mantenimiento de un dispositivo conectado.

Dispositivos que hacen ping al equilibrador de carga y se dirigen a una instancia de publicación. A continuación, la instancia de publicación expone el estado del dispositivo mediante una API de publicación servida en **api/screen-dcc/devices/static** para todos los dispositivos activos y api/screen-dcc/devices/&lt;device_id>/status.json **** para un solo dispositivo.

La instancia de autor sondea todas las instancias de publicación y combina las respuestas de estado del dispositivo en un solo estado. El trabajo programado que sondea en el autor se configura `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` y se puede configurar en función de una expresión cron.

## Registro {#registration}

El registro sigue originándose en la instancia de autor AEM. AEM Screens Device apunta a la instancia de creación y se ha completado el registro.

Una vez que se ha registrado un dispositivo en el entorno de creación, la configuración del dispositivo y las asignaciones de canal/programación se replican en las instancias de publicación de AEM. A continuación, la configuración del dispositivo AEM Screens se actualiza para que apunte al equilibrador de carga delante de la granja de AEM. Se trata de una configuración única, una vez que el dispositivo de pantallas se conecta correctamente al entorno de publicación, puede seguir recibiendo comandos procedentes del entorno de creación y no debería ser necesario conectar el dispositivo de pantallas directamente al entorno de creación.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Pasos siguientes {#the-next-steps}

Una vez que haya comprendido el diseño arquitectónico de la configuración de creación y publicación en AEM Screens, consulte [Configuración de creación y publicación para AEM Screens](author-and-publish.md) para obtener más información.
