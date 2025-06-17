---
title: Configuración de instancias de autor y publicación en AEM Screens
description: Obtenga información sobre cómo configurar una instancia de autor y una instancia de publicación para AEM Screens.
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1939'
ht-degree: 0%

---


# Configuración de instancias de autor y publicación en AEM Screens {#configuring-author-and-publish-in-aem-screens}

En esta página se destacan los siguientes temas:

* **Configuración de instancias de autor y publicación**
* **Configurando la topología de publicación**
* **Administración de publicaciones: entrega de actualizaciones de contenido del autor para su publicación en el dispositivo**

## Requisitos previos {#prerequisites}

Antes de empezar a usar los servidores de creación y publicación, debe tener conocimientos previos de lo siguiente:

* **Topología de AEM**
* **Creación y administración de un proyecto de AEM Screens**
* **Proceso de registro de dispositivo**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este paquete de funciones, póngase en contacto con el Soporte técnico de Adobe y solicite acceso. Una vez que tenga permiso, puede descargarlo desde Package Share.

>[!IMPORTANT]
>
>Si desea utilizar más de una instancia de publicación con Dispatcher, actualice Dispatcher. Consulte [Habilitación de sesiones duraderas](dispatcher-configurations-aem-screens.md#enable-sticky-session).

## Configuración de instancias de autor y publicación {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para obtener más información sobre la descripción general de la arquitectura de creación y publicación y cómo se crea el contenido en una instancia de autor de AEM y, a continuación, se replica mediante reenvío en varias instancias de publicación, consulte [Información general sobre la arquitectura de creación y publicación](author-publish-architecture-overview.md).

En la siguiente sección se explica cómo configurar agentes de replicación en las topologías Autor y Publicación.

Puede configurar un ejemplo sencillo, en el que aloje una instancia de autor y dos instancias de publicación:

* Autor > localhost:4502
* Publicar 1 (pub1) > localhost:4503
* Publicar 2 (pub2) > localhost:4504

## Configuración de agentes de replicación en Autor {#setting-replication-agents}

Para crear agentes de replicación, aprenda a crear un agente de replicación estándar.

Hay tres agentes de replicación necesarios para Screens:

1. **Agente de replicación predeterminado &#x200B;***(especificado como&#x200B;*** agente de replicación estándar**)
1. **Agente de replicación de Screens**
1. **Agente de replicación inversa**

### Paso 1: Crear un agente de replicación predeterminado {#step-creating-a-default-replication-agent}

Siga los pasos a continuación para crear un agente de replicación predeterminado:

1. Vaya a la instancia de AEM > hammer icon > **Operaciones** > **Configuración**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Haga clic en **Replicación** en el árbol de navegación izquierdo.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Haga clic en **Agentes de autor** de la carpeta **Replicación** y haga clic en **Nuevo** para crear un nuevo agente de replicación estándar.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Escriba **Title** y **Name** para poder crear el agente de replicación y, a continuación, haga clic en **Crear**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Haga clic con el botón derecho en el agente de replicación y haga clic en **Abrir** para editar la configuración.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Haga clic en **Editar**.

1. En el cuadro de diálogo **Configuración del agente**, escriba los detalles.

   >[!NOTE]
   >
   >El usuario debe marcar **Enabled** para habilitar el agente de replicación. Marque esta opción en Agentes predeterminados, de Screens y de replicación inversa.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Vaya a la pestaña **Transporte** e introduzca el **URI**, **Usuario** y **Contraseña**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >También puede copiar y cambiar el nombre de un agente de replicación predeterminado existente.


#### Crear agentes de replicación estándar {#creating-standard-replication-agents}

1. Cree un agente de replicación estándar para pub1 (ya debe estar configurado un agente predeterminado). Por ejemplo, *`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`*
1. Cree un agente de replicación estándar para pub2. Puede copiar como agente de replicación para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte. Por ejemplo, *`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`*.

#### Crear agentes de replicación de Screens {#creating-screens-replication-agents}

1. Cree un agente de replicación de AEM Screens para pub1. De forma predeterminada, hay un agente de replicación de Screens denominado que señala al puerto 4503. Actívelo.
1. Cree un agente de replicación de AEM Screens para pub2. Copie el agente de replicación de Screens para pub1 y cambie el puerto a 4504 para pub2.

   >[!NOTE]
   >Para obtener información sobre cómo configurar los agentes de replicación de Screens, consulte [Configuración del agente de replicación de Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/configure-screens-replication).

#### Crear agentes de replicación inversa de Screens {#creating-screens-reverse-replication-agents}

1. Cree un agente de replicación inversa para pub1.
1. Cree un agente de replicación inversa para pub2. Puede copiar el agente de replicación inversa para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte.

## Configuración de la topología de publicación {#setting-up-publish-topology}

### Paso 1: Configuración de Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Configure el descubrimiento basado en Oak de Apache Sling para todas las instancias de publicación de la topología

Para cada instancia de publicación:

1. Navegue hasta `https://<host>:<port>/system/console/configMgr`
1. Haga clic en **Configuración del servicio de detección basado en Apache Sling Oak**.
1. Actualizar URL del conector de topología: añada las URL de todas las instancias de publicación participantes que sean:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Lista** del conector de topología `Whitelist`: adapte a direcciones IP o subredes que abarquen todas las instancias de publicación. Asegúrese de `whitelist` la IP/nombre de host de todas las instancias de publicación sin el número de puerto.

1. Habilitar **Bucles locales de detención automática**

La configuración debe ser idéntica para cada instancia de publicación y el bucle local de parada automática evita un bucle infinito.

#### Paso 2: Verificar La Topología De Publicación {#step-verify-publish-topology}

Para cualquiera de las instancias de publicación, vaya a `https://:/system/console/topology`. Debería ver cada instancia de publicación representada en la topología en **Conectores de topología de salida**.

#### Paso 3: Configurar el clúster de ActiveMQ Artemis {#step-setup-activemq-artemis-cluster}

Este paso le permite crear una contraseña cifrada para el clúster de ActiveMQ Artemis.
El usuario y la contraseña de clúster de todas las instancias de publicación de la topología deben ser idénticos. La contraseña de la configuración de ActiveMQ Artemis debe estar cifrada. Dado que cada instancia tiene su propia clave de cifrado, es necesario utilizar la compatibilidad con cifrado para crear una cadena de contraseña cifrada. A continuación, la contraseña cifrada se puede utilizar en la configuración OSGi para ActiveMQ.

En cada instancia de publicación:

1. En la consola OSGi, vaya a **MAIN** > **Crypto Support** (`https://<host>:<port>/system/console/crypto`).
1. Escriba la contraseña de texto sin formato que desee (la misma para todas las instancias) en **Texto sin formato**
1. Haga clic en **Proteger**.
1. Copie el valor **Texto protegido** en un bloc de notas o editor de texto. Este valor se puede utilizar en la configuración OSGi para ActiveMQ.

Dado que cada instancia de publicación, de forma predeterminada, tiene claves criptográficas únicas, realice este paso en cada instancia de publicación y guarde la clave única para la siguiente configuración.

>[!NOTE]
>
>La contraseña debe comenzar y finalizar con llaves. Por ejemplo:
>&#x200B;>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Paso 4: Activar el clúster de ActiveMQ Artemis {#step-activate-activemq-artemis-cluster}

En cada instancia de publicación:

1. Vaya al Administrador de configuración OSGi `https://<host>:<port>/system/console/configMgr`
1. Haga clic en **Apache ActiveMQ Artemis JMS Provider** Configuración
1. Actualice lo siguiente:

   * ***Contraseña de clúster***: use el valor cifrado del paso anterior por cada instancia respectiva
   * ***Temas***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Comprobar clúster de elementos ActiveMQ {#verify-activemq-artemis-cluster}

Siga los pasos a continuación en cada instancia de publicación:

1. Vaya a la consola OSGi > Principal > Elementos de ActiveMQ `https://localhost:4505/system/console/mq`.
1. Compruebe y marque para ver los puertos de otras instancias en Información de clúster > Topología > nodes=2, members=2.
1. Enviar un mensaje de prueba (parte superior de la pantalla en Información de Broker)
1. Introduzca los siguientes cambios en los campos:

   1. **Destino**: /com.adobe.cq.screens/devTestTopic
   1. **Texto**: Hello World
   1. Vea el `error.log` de cada instancia para poder ver que el mensaje se envió y recibió en todo el clúster.

>[!NOTE]
>
>La navegación a la consola OSGi puede tardar unos segundos después de guardar la configuración en el paso anterior. También puede comprobar el error.log para obtener más detalles.

Por ejemplo, la siguiente imagen se muestra si la configuración de ActiveMQ Artemis Server se ha realizado correctamente.

Si no ve la siguiente configuración de */system/console/mq*, vaya a */system/console/mq* y haga clic en **Reiniciar** para reiniciar el agente.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Quitar requisito de encabezado de referente {#remove-referrer-header-requirement}

Siga los pasos de cada instancia de publicación:

1. Vaya a la **consola OSGi** > **Administrador de configuración**
1. Haga clic en **Filtro de referente de Apache Sling**
1. Actualizar configuración y **comprobar Permitir vaciado**

### Configuración de instancias de autor y publicación {#configuring-author-and-publish-instance}

Una vez configurada la topología de publicación, configure las instancias de autor y publicación para ver los resultados prácticos de la implementación:

>[!NOTE]
>
>**Requisitos previos**
>
>Para empezar con este ejemplo, cree un proyecto de AEM Screens seguido de la creación de una ubicación, una visualización y un canal en el proyecto. Añada contenido al canal y asigne el canal a una pantalla.

#### Paso 1: Inicio de un reproductor de AEM Screens (dispositivo)

1. Inicie una ventana independiente del explorador.
1. Vaya al reproductor de Screens con el *explorador web*, es decir`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`, o inicie la aplicación de AEM Screens. Cuando abra el dispositivo, observe que su estado no está registrado.

>[!NOTE]
>
>Puede abrir un Reproductor de AEM Screens con la aplicación de AEM Screens que descargó o con el explorador web.

#### Paso 2: Registrar un dispositivo en Author {#step-registering-a-device-on-author}

1. Vaya a `https://localhost:4502/screens.html/content/screens/we-retail` o haga clic en el proyecto y vaya a Dispositivos > Administrador de dispositivos.
1. Haga clic en **Registrar dispositivo**.
1. Haga clic en **Registro de dispositivo**.
1. Haga clic en el dispositivo que desea registrar y, a continuación, haga clic en **Registrar dispositivo**.
1. Compruebe el código de registro y, a continuación, haga clic en **Validar**.
1. Escribe un título para el dispositivo y haz clic en **Registrar**.

#### Paso 3: Asignar el dispositivo a la pantalla {#step-assigning-the-device-to-display}

1. Haga clic en **Asignar pantalla** en el cuadro de diálogo del paso anterior.
1. Haga clic en la ruta de visualización del canal desde la carpeta **Ubicaciones**.
1. Haga clic en **Asignar**.
1. Haga clic en **Finalizar** para completar el proceso y ahora se asignará el dispositivo.

Compruebe el reproductor y observe el contenido que ha agregado en el canal.

#### Paso 4: Publicar la configuración del dispositivo en instancias de publicación {#step-publishing-device-configuration-to-publish-instances}

**Verificar el dispositivo**

Siga los pasos a continuación para replicar el usuario del dispositivo:

1. Navegue hasta la página de administración de usuarios. Por ejemplo, `https://localhost:4502/useradmin`.
1. Busque el grupo **`screens-devices-master`**.
1. Haga clic con el botón derecho en el grupo y haga clic en **Activar**.

>[!CAUTION]
>
>No active author-publish-screens-service porque es un usuario del sistema utilizado por el trabajo de autor.

También puede activar el dispositivo desde la Consola de administración de dispositivos. Complete los siguientes pasos:

1. Vaya a su proyecto de Screens > **Dispositivos**.
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.
1. Haga clic en el dispositivo y luego en **Activar** en la barra de acciones, como se muestra en la figura siguiente.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, una vez activado el dispositivo, también puede editar o actualizar la URL del servidor. En la barra de acciones, haga clic en **Editar URL del servidor**, como se muestra en la figura siguiente. Los cambios se propagarán al Reproductor de AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Publicar lista de comprobación {#publishing-check-list}

Los siguientes puntos resumen la lista de comprobación de publicación:

* *Usuario de dispositivo Screens*: esta información se almacena como usuario de AEM y se puede activar desde **Herramientas** > **Seguridad** > **Usuarios**. Al usuario se le agrega el prefijo &quot;screens&quot; con una cadena serializada larga.

* *Proyecto* - El proyecto de AEM Screens.
* *Ubicación* - Ubicación a la que está conectado el dispositivo.
* *Canales*: uno o más canales que se están mostrando en la ubicación.
* *Programación*: si utiliza una programación, asegúrese de que se publique.
* *Ubicación, horarios y carpeta del canal*: si los recursos correspondientes están dentro de una carpeta.

Siga los pasos a continuación para verificar el comportamiento de creación y publicación:

1. Actualizar parte del contenido del canal en la instancia de autor.
1. Realice **Administrar publicación** para publicar nuevos cambios en todas las instancias de publicación.
1. Haga clic en **Activar** para habilitar el dispositivo desde **Administrador de dispositivos**.
1. Seleccione **Editar URL** de la URL de instancia de autor a una de las URL de instancias de publicación.
1. Compruebe que el contenido actualizado del canal se muestra en el reproductor de AEM Screens.
1. Repita estos pasos con una instancia de publicación diferente.


#### Paso 5: Dirija el dispositivo a la instancia de publicación en el panel de administración {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Vea la interfaz de usuario de administración desde el reproductor de Screens; mantenga pulsada la esquina superior izquierda para poder abrir el menú Administración, en el reproductor de AEM Screens táctil o con un ratón.
1. Haga clic en la opción **Configuración** en el panel lateral.
1. Cambie la instancia de autor a la instancia de publicación en **Server**.

Vea los cambios en el Reproductor de AEM Screens.

También puede actualizar o editar la URL del servidor desde la consola de administración de dispositivos, para hacerlo, siga estos pasos:

1. Vaya al proyecto de AEM Screens y haga clic en la carpeta **Dispositivos**.
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.
1. Haga clic en el dispositivo y, a continuación, en la barra de acciones, haga clic en **Editar URL del servidor**, como se muestra en la figura siguiente. Los cambios se propagarán al Reproductor de AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

La característica **`Manage Publication`** le permite enviar actualizaciones de contenido de Autor a Publish en el dispositivo. Puede publicar/cancelar la publicación del contenido de todo el proyecto de AEM Screens o solo de uno de los canales, la ubicación, el dispositivo, la aplicación o una programación. Para obtener más información acerca de esta característica, consulte [Actualización de contenido bajo demanda](on-demand-content.md).

## Solucionar problemas de sugerencias {#troubleshoot-tips}

Siga esta sección para obtener respuestas a las preguntas frecuentes relacionadas con la configuración de autor y publicación.

### Cómo añadir un Redireccionamiento de https a http después del registro inicial y la asignación? {#add-redirect}

**Solución** - Establecer `Proxy/Load Balancer Connection in the Jetty configuration` en `true`.

### ¿Cómo actualizar el contenido sin conexión y los problemas de descarga del reproductor con los recursos fuera de `/content/dam/projects/<project>`? {#update-offline-content}

**Solución**: proporcione permisos de lectura para el usuario de servicio de actualización sin conexión en lotes y el grupo `screens-devices-master` para todos los `/content/dam` o los recursos específicos que desee usar, si desea que sean más restrictivos.

### ¿Cómo se resuelven los errores del Agente de replicación de Screens? {#replication-agent}

**Solución** - Asegúrese de que no ha marcado la opción Usar para replicación inversa en la configuración del agente. El agente de replicación de Screens no se puede usar como agente de replicación inversa y el ámbito de esta función es reenviar comandos de dispositivo de Autor a Publicar.