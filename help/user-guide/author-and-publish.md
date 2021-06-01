---
title: Configuración de autor y publicación en AEM Screens
seo-title: Configuración de autor y publicación en AEM Screens
description: La arquitectura de AEM Screens se parece a una arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor AEM y luego se rereplica en varias instancias de publicación. Siga esta página para aprender a configurar la creación y publicación para AEM Screens.
seo-description: La arquitectura de AEM Screens se parece a una arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor AEM y luego se rereplica en varias instancias de publicación. Siga esta página para aprender a configurar la creación y publicación para AEM Screens.
feature: Administración de Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 2%

---


# Configuración de autor y publicación en AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página destaca los siguientes temas:

* **Configuración de instancias de autor y publicación**
* **Configuración de la topología de publicación**
* **Administración de publicación: Envío de actualizaciones de contenido desde el autor a la publicación en el dispositivo**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y publicación, debe tener conocimientos previos de:

* **Topología AEM**
* **Creación y administración de proyectos de AEM Screens**
* **Proceso de registro de dispositivos**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

>[!IMPORTANT]
>
>Si desea utilizar más de una instancia de publicación con Dispatcher, debe actualizar el archivo dispatcher.any en su Dispatcher. Consulte [Habilitación de sesiones adhesivas](dispatcher-configurations-aem-screens.md#enable-sticky-session) para obtener más información.

## Configuración de instancias de Autor y Publicación {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para obtener más información sobre la descripción general de la arquitectura de autor y publicación, y cómo se crea el contenido en una instancia de autor AEM y luego se rereplica en varias instancias de publicación, consulte [Información general de la arquitectura de autor y publicación](author-publish-architecture-overview.md).

En la siguiente sección se explica cómo configurar los agentes de replicación en la topología de autor y publicación.

Puede configurar un ejemplo sencillo en el que aloje un autor y dos instancias de publicación:

* Autor —> localhost:4502
* Publicar 1 (pub1) —> localhost:4503
* Publicar 2 (pub2) —> localhost:4504

## Configuración de agentes de replicación en Author {#setting-replication-agents}

Para crear agentes de replicación, debe aprender a crear un agente de replicación estándar.

Hay 3 agentes de replicación necesarios para Screens:

1. **Agente de replicación predeterminado  ***(especificado*** como agente de replicación estándar**)
1. **Agente de replicación de Screens**
1. **Agente de replicación inversa**

### Paso 1: Creación de un agente de replicación predeterminado {#step-creating-a-default-replication-agent}

Siga los pasos a continuación para crear un agente de replicación predeterminado:

1. Vaya a su instancia de AEM —> icono de martillo —> **Operaciones** —> **Configuración**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Seleccione **Replication** en el árbol de navegación izquierdo.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Seleccione **Agents on author** en la carpeta **Replication** y haga clic en **New** para crear un nuevo agente de replicación estándar.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Introduzca **Title** y **Name** para crear el agente de replicación y haga clic en **Create**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Haga clic con el botón derecho en el agente de replicación y haga clic en **Open** para editar la configuración.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Haga clic en **Editar** para abrir el cuadro de diálogo **Configuración del agente** para introducir los detalles.

   >[!NOTE]
   >
   >El usuario debe marcar **Enabled** para habilitar el agente de replicación. Debe marcar esta opción en Predeterminado, Screens y Reverse Replication Agents.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Vaya a la pestaña **Transport** e introduzca **URI**, **User** y **Password**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >También puede copiar y cambiar el nombre de un agente de replicación predeterminado existente.


#### Creación de agentes de replicación estándar {#creating-standard-replication-agents}

1. Crear un agente de replicación estándar para pub1 (el agente predeterminado listo para usar ya debe estar configurado) (por ejemplo, *https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. Cree un agente de replicación estándar para pub2. Puede copiar el agente de rep para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte. (por ejemplo, *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### Creación de agentes de replicación de Screens {#creating-screens-replication-agents}

1. Cree el agente de replicación de AEM Screens para pub1. De serie, existe un agente de replicación Screens llamado Screens que apunta al puerto 4503. Debe habilitarse.
1. Cree un agente de replicación de AEM Screens para pub2. Copie el agente de replicación de Screens para pub1 y cambie el puerto para que apunte a 4504 para pub2.

#### Creación de agentes de replicación inversa de Screens {#creating-screens-reverse-replication-agents}

1. Cree un agente de replicación inversa estándar para pub1.
1. Cree un agente de replicación inversa estándar para pub2. Puede copiar el agente de rep inverso para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte.

## Configuración de la topología de publicación {#setting-up-publish-topology}

### Paso 1: Configurar Apache Sling Oak Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Configurar el descubrimiento basado en Apache Sling Oak para todas las instancias de publicación en la topología

Para cada instancia de publicación:

1. Ir a `https://<host>:<port>/system/console/configMgr`
1. Seleccione la configuración **Apache Sling Oak-Based Discovery Service**.
1. Actualizar URL del conector de topología: agregue direcciones URL de todas las instancias de publicación de participación que sean:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **Lista** de lista blanca del conector de topología: adaptarse a direcciones IP o subredes que abarcan instancias de publicación de participación
1. Habilitar **bucles locales de parada automática**

La configuración debe ser idéntica para cada instancia de publicación y el bucle local de parada automática evita un bucle infinito.

#### Paso 2: Verificar topología de publicación {#step-verify-publish-topology}

Para cualquiera de las instancias de publicación, vaya a `https://:/system/console/topology`. Debería ver cada instancia de publicación representada en la topología en **Conectores de topología salientes**.

#### Paso 3: Configuración del clúster de artemis ActiveMQ {#step-setup-activemq-artemis-cluster}

Este paso le permite crear una contraseña cifrada para el clúster de ActiveMQ Artemis.
El usuario y la contraseña del clúster de todas las instancias de publicación de la topología deben ser idénticos. La contraseña de la configuración de ActiveMQ Artemis debe cifrarse. Dado que cada instancia tiene su propia clave de cifrado, es necesario utilizar el soporte técnico de Crypto para crear una cadena de contraseña cifrada. A continuación, la contraseña cifrada se utilizará en la configuración OSGi para ActiveMQ.

En cada instancia de publicación:

1. En la consola OSGi, vaya a **MAIN** —> **Crypto Support** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`).
1. Escriba la contraseña de texto sin formato deseada (igual para todas las instancias) en **Texto sin formato**
1. Haga clic en **Protect**.
1. Copie el valor **Texto protegido** en el bloc de notas o en el editor de texto. Este valor se utilizará en la configuración OSGi para ActiveMQ.

Dado que cada instancia de publicación tiene de forma predeterminada claves criptográficas únicas, debe realizar este paso en cada instancia de pub y guardar la clave única para la siguiente configuración.

>[!NOTE]
>
>La contraseña debe comenzar y terminar con llaves. Por ejemplo:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Paso 4: Activar el clúster de ActiveMQ Artemis {#step-activate-activemq-artemis-cluster}

En cada instancia de publicación:

1. Vaya al administrador de configuración OSGi `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. Seleccione la configuración **Apache ActiveMQ Artemis JMS Provider**
1. Actualice lo siguiente:

   * ***Contraseña*** del clúster: usar valor cifrado del paso anterior por cada instancia respectiva
   * ***Temas***:  `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verificar el clúster de ActiveMQ Artemis {#verify-activemq-artemis-cluster}

Siga los pasos a continuación en cada instancia de publicación:

1. Vaya a la consola OSGi -> Principal > Artemis ActiveMQ `https://localhost:4505/system/console/mq`.
1. Compruebe y compruebe para ver los puertos de otras instancias en Información del clúster > Topología > nodos=2, miembros=2.
1. Enviar un mensaje de prueba (parte superior de la pantalla en Información del agente)
1. Introduzca los siguientes cambios en los campos:

   1. **Destino**: /com.adobe.cq.screens/devTestTopic
   1. **Texto**: Hello World
   1. Vea el archivo error.log de cada instancia para ver que el mensaje se envió y recibió en el clúster

>[!NOTE]
>
>La navegación a la consola OSGi puede tardar unos segundos después de guardar la configuración en el paso anterior. También puede consultar el archivo error.log para obtener más información.

Por ejemplo, la siguiente imagen aparece en una configuración correcta de ActiveMQ Artemis Server.

Si no ve la siguiente configuración desde */system/console/mq*, vaya a */system/console/mq* y haga clic en **Restart** para reiniciar el agente.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Eliminar el requisito de encabezado del referente {#remove-referrer-header-requirement}

Siga los pasos de cada instancia de publicación:

1. Vaya a la **Consola OSGi** > **Administrador de configuración**
1. Seleccione **Filtro de referente de Apache Sling**
1. Actualizar configuración y **marcar Permitir vacío**

### Configuración de la instancia de autor y publicación {#configuring-author-and-publish-instance}

Una vez configurada la topología de publicación, debe configurar las instancias de autor y publicación para ver los resultados prácticos de la implementación:

>[!NOTE]
>
>**Requisitos previos**
>
>Para comenzar con este ejemplo, cree un nuevo proyecto de AEM Screens seguido de la creación de una ubicación, visualización y canal en el proyecto. Añada contenido al canal y asigne el canal a una pantalla.

#### Paso 1: Inicio de un reproductor AEM Screens (dispositivo) {#step-starting-an-aem-screens-player-device}

1. Abra una nueva ventana del navegador.
1. Vaya al reproductor Screens utilizando el *navegador web*, es decir,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` o inicie la aplicación de AEM Screens. Cuando abra el dispositivo, verá el estado de este como no registrado.

>[!NOTE]
>
>Puede abrir un reproductor de AEM Screens con la aplicación de AEM Screens que descargó o con el explorador web.

#### Paso 2: Registro de un dispositivo en el autor {#step-registering-a-device-on-author}

1. Vaya a `https://localhost:4502/screens.html/content/screens/we-retail` o seleccione el proyecto y vaya a Dispositivos > Administrador de dispositivos.
1. Seleccione **Registrar dispositivo**.
1. Haga clic en **Device Registration** para ver el dispositivo.
1. Seleccione el dispositivo que desea registrar y haga clic en **Registrar dispositivo**.
1. Compruebe el código de registro y haga clic en **Validar**.
1. Introduzca un título para el dispositivo y haga clic en **Register**.

#### Paso 3: Asignación del dispositivo para mostrar {#step-assigning-the-device-to-display}

1. Haga clic **Asignar pantalla** en el cuadro de diálogo del paso anterior.
1. Seleccione la ruta de visualización del canal en la carpeta **Ubicaciones**.
1. Haga clic en **Asignar**.
1. Haga clic en **Finish** para completar el proceso y ahora el dispositivo está asignado.

Compruebe el reproductor y verá el contenido que agregó en el canal.

#### Paso 4: Configuración del dispositivo de publicación para publicar instancias {#step-publishing-device-configuration-to-publish-instances}

**Verificación del dispositivo**

Antes de realizar los pasos siguientes, asegúrese de verificar el ID del dispositivo. Para comprobarlo, busque el ID del dispositivo en el CRXDE Lite, con la ruta como */home/users/screens/we-retail/device*.

Siga los pasos a continuación para replicar el usuario del dispositivo:

1. Vaya a la página de administración del usuario (p. ej.: `https://localhost:4502/useradmin`
1. Busque el grupo **screens-device-master**
1. Haga clic con el botón derecho en el grupo y haga clic en **Activar**

>[!CAUTION]
>
>No active author-publish-screens-service porque es un usuario del sistema, utilizado por el trabajo de autor.

También puede activar el dispositivo desde la consola de administración de dispositivos. Complete los siguientes pasos:

1. Vaya al proyecto Screens —> **Dispositivos**.
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.
1. Seleccione el dispositivo y haga clic **Activate** en la barra de acciones, como se muestra en la figura siguiente.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Alternativamente, una vez que haya activado el dispositivo, también puede editar o actualizar la URL del servidor haciendo clic en **Editar URL del servidor** en la barra de acciones, como se muestra en la figura siguiente y los cambios se propagarán al reproductor AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Lista de comprobación de publicación {#publishing-check-list}

Los siguientes puntos resumen la lista de comprobación de publicaciones:

* *Usuario de dispositivo de Screens* : se almacena como usuario AEM y se activa desde  **Herramientas**  >  **Seguridad**  >  **Usuarios**. Al usuario se le añadirá el prefijo &quot;screens&quot; con una cadena serializada larga.

* *Proyecto* : el proyecto de AEM Screens.
* *Ubicación* : ubicación a la que está conectado el dispositivo.
* *Canal(s)* : uno o más canales que se muestran en la ubicación.
* *Programación* : si utiliza una programación, asegúrese de que se publica
* *Ubicación, programaciones y carpeta de canal* : si los recursos correspondientes están dentro de una carpeta.

Siga los pasos a continuación para comprobar el comportamiento de autor/publicación:

1. Actualizar contenido de canal en la instancia de autor
1. Realizar **Administrar publicación** para publicar nuevos cambios en todas las instancias de publicación
1. Pulse **Activar** para activar el dispositivo desde **Administrador de dispositivos**
1. **Editar** URL desde la URL de instancia de autor a una de las URL de instancias de publicación
1. Compruebe que el contenido del canal actualizado se muestra en el reproductor AEM Screens
1. Repita estos pasos con una instancia de publicación diferente


#### Paso 5: Señalar el dispositivo para publicar la instancia en el panel de administración {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Vea la IU de administración desde el reproductor Screens, pulse durante mucho tiempo en la esquina superior izquierda para abrir el menú Administración, en el reproductor AEM Screens táctil o con un ratón.
1. Haga clic en la opción **Configuration** del panel lateral.
1. Cambie la instancia de autor para publicar la instancia en **Server**.

Vea los cambios en el reproductor de AEM Screens.

También puede actualizar o editar la URL del servidor desde la consola de administración de dispositivos siguiendo los pasos siguientes:

1. Vaya al proyecto de AEM Screens y seleccione la carpeta **Devices** .
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.
1. Seleccione el dispositivo y haga clic en **Edit server URL** en la barra de acciones, como se muestra en la figura siguiente y los cambios se propagarán al reproductor AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

La función **Administrar publicación** le permite enviar actualizaciones de contenido del autor para publicarlas en el dispositivo. Puede publicar/cancelar la publicación de contenido para todo el proyecto de AEM Screens o solo para uno de sus canales, ubicación, dispositivo, aplicación o programación. Para obtener más información sobre esta función, consulte [Actualización de contenido bajo demanda](on-demand-content.md).


