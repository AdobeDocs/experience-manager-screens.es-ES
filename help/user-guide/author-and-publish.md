---
title: Configuración del autor y la publicación en AEM Screens
seo-title: Configuración del autor y la publicación en AEM Screens
description: La arquitectura de AEM Screens se asemeja a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se reenvía a varias instancias de publicación. Siga esta página para obtener información sobre cómo configurar el autor y la publicación para AEM Screens.
seo-description: La arquitectura de AEM Screens se asemeja a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se reenvía a varias instancias de publicación. Siga esta página para obtener información sobre cómo configurar el autor y la publicación para AEM Screens.
translation-type: tm+mt
source-git-commit: 235aa979543455882c72fa262cf7320c4298de5e
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 2%

---


# Configuración del autor y la publicación en AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página resalta los siguientes temas:

* **Configuración de instancias de creación y publicación**
* **Configuración de la topología de publicación**
* **Administración de publicación: Envío de actualizaciones de contenido desde el autor a la publicación en el dispositivo**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y publicación, debe tener conocimientos previos de:

* **Topología AEM**
* **Creación y administración de proyectos de AEM Screens**
* **Proceso de registro del dispositivo**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

>[!IMPORTANT]
>
>Si desea utilizar más de una instancia de publicación con dispatcher, debe actualizar el archivo dispatcher.any en el distribuidor. Consulte [Activación de sesiones adhesivas](dispatcher-configurations-aem-screens.md#enable-sticky-session) para obtener más detalles.

## Configuración de instancias de creación y publicación {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para obtener más información sobre la descripción general de la arquitectura de creación y publicación y sobre cómo se crea el contenido en una instancia de autor AEM y, a continuación, se repite en varias instancias de publicación, consulte [Información general de la arquitectura de creación y publicación](author-publish-architecture-overview.md).

En la siguiente sección se explica cómo configurar los agentes de replicación en la topología de creación y publicación.

Puede configurar un ejemplo sencillo en el que aloje a un autor y dos instancias de publicación:

* Autor —> localhost:4502
* Publish 1 (pub1) —> localhost:4503
* Publish 2 (pub2) —> localhost:4504

## Configuración de agentes de replicación en Author {#setting-replication-agents}

Para crear agentes de replicación, debe aprender a crear un agente de replicación estándar.

Existen 3 agentes de replicación que se necesitan para las pantallas:

1. **Agente de replicación predeterminado  ***(especificado*** como agente** de replicación estándar)
1. **Agente de replicación de pantallas**
1. **Agente de replicación inversa**

### Paso 1: Creación de un Agente de replicación predeterminado {#step-creating-a-default-replication-agent}

Siga los pasos a continuación para crear un agente de replicación predeterminado:

1. Vaya a su instancia de AEM —> icono de martillo —> **Operaciones** —> **Configuración**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Seleccione la **Replicación** en el árbol de navegación izquierdo.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Seleccione los **agentes en el autor** en la carpeta **Replicación** y haga clic en **Nuevo** para crear un nuevo agente de replicación estándar.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Introduzca los **Título** y **Nombre** para crear el agente de replicación y haga clic en **Crear**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Haga clic con el botón secundario en el agente de replicación y haga clic en **Abrir** para editar la configuración.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Haga clic en **Editar** para abrir el cuadro de diálogo **Configuración del agente** para introducir los detalles.

   >[!NOTE]
   >
   >El usuario debe comprobar **Habilitado** para habilitar el agente de replicación. Debe marcar esta opción en Predeterminado, Pantallas y Agentes de replicación inversa.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Vaya a la ficha **Transporte** e introduzca el **URI**, **Usuario** y **Contraseña**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >También puede copiar y cambiar el nombre de un agente de replicación predeterminado existente.


#### Creación de Agentes de Replicación Estándar {#creating-standard-replication-agents}

1. Crear un agente de replicación estándar para pub1 (el agente predeterminado listo para usar ya debería estar configurado) (por ejemplo, *https://&lt;hostname>:4503/bin/received?sling:authRequestLogin=1*)
1. Cree un agente de replicación estándar para pub2. Puede copiar el agente de rep para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte. (por ejemplo, *https://&lt;hostname>:4504/bin/received?sling:authRequestLogin=1*)

#### Creación de agentes de replicación de pantallas {#creating-screens-replication-agents}

1. Cree un agente de replicación de AEM Screens para pub1. De manera predeterminada, existe un agente de replicación de pantallas denominado Screens que apunta al puerto 4503. Esto debe habilitarse.
1. Cree un agente de replicación de AEM Screens para pub2. Copie el agente de replicación de Screens para pub1 y cambie el puerto para que señale a 4504 para pub2.

#### Creación de agentes de replicación inversa de pantallas {#creating-screens-reverse-replication-agents}

1. Cree un agente de replicación inversa estándar para pub1.
1. Cree un agente de replicación inversa estándar para pub2. Puede copiar el agente de rep inverso para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte.

## Configuración de la topología de publicación {#setting-up-publish-topology}

### Paso 1: Configurar Apache Sling Oak Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Configure el descubrimiento basado en Apache Sling Oak para todas las instancias de Publish en la topología

Para cada instancia de publicación:

1. Ir a `https://<host>:<port>/system/console/configMgr`
1. Seleccione **Configuración del servicio de detección basado en roble Apache Sling**.
1. Actualizar direcciones URL del conector de topología: agregue direcciones URL de todas las instancias de publicación de participación que sean:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **Conector de topología Lista** blanca: adaptarse a las IP o subredes que cubren instancias de publicación de participación
1. Habilitar **bucles locales de detención automática**

La configuración debe ser idéntica para cada instancia de publicación y el bucle local de parada automática evita un bucle infinito.

#### Paso 2: Verificar topología de publicación {#step-verify-publish-topology}

Para cualquiera de las instancias de publicación, navegue a `https://:/system/console/topology`. Debe ver cada instancia de publicación representada en la topología en **Conectores de topología salientes**.

#### Paso 3: Configurar el clúster de artemis ActiveMQ {#step-setup-activemq-artemis-cluster}

Este paso le permite crear una contraseña cifrada para el clúster de ActiveMQ Artemis.
El usuario y la contraseña del clúster de todas las instancias de publicación de la topología deben ser idénticos. Es necesario cifrar la contraseña de la configuración de Artemis de ActiveMQ. Dado que cada instancia tiene su propia clave de cifrado, es necesario utilizar la compatibilidad con criptografía para crear una cadena de contraseña cifrada. Luego se utilizará la contraseña cifrada en la configuración OSGi para ActiveMQ.

En cada instancia de publicación:

1. En la Consola OSGi, navegue a **MAIN** —> **Compatibilidad con criptografía** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`).
1. Escriba la contraseña de texto sin formato deseada (igual para todas las instancias) en **Texto sin formato**
1. Haga clic en **Protect**.
1. Copie el valor **Texto protegido** en el bloc de notas o editor de texto. Este valor se utilizará en la configuración OSGi para ActiveMQ.

Dado que cada instancia de publicación tiene claves criptográficas únicas de forma predeterminada, debe realizar este paso en cada instancia de pub y guardar la clave única para la siguiente configuración.

>[!NOTE]
>
>La contraseña debe inicio y terminar con llaves. Por ejemplo:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Paso 4: Activar el clúster de artemis ActiveMQ {#step-activate-activemq-artemis-cluster}

En cada instancia de publicación:

1. Vaya al administrador de configuración OSGi `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. Seleccione **Configuración del proveedor de JMS Apache ActiveMQ Artemis**
1. Actualice lo siguiente:

   * ***Contraseña*** del clúster: (utilice un valor cifrado del paso anterior por instancia respectiva)
   * ***Temas***: {name: &#39;comandos&#39;, dirección: &#39;com.adobe.cq.screens.command&#39;, maxConsumers: 50}

#### Verificar el clúster de artemis ActiveMQ {#verify-activemq-artemis-cluster}

Siga los pasos a continuación en cada instancia de Publish:

1. Vaya a la Consola OSGi -> Principal > Artemis ActiveMQ `https://localhost:4505/system/console/mq`.
1. Compruebe y verifique la vista de los puertos de otras instancias en Información del clúster > Topología > nodos=2, miembros=2.
1. Enviar un mensaje de prueba (en la parte superior de la pantalla, en Información del agente)
1. Introduzca los siguientes cambios en los campos:

   1. **Destino**: /com.adobe.cq.screen/devTestTopic
   1. **Texto**: Hola a todos
   1. Vista el error.log de cada instancia para ver que el mensaje se ha enviado y recibido en todo el clúster

>[!NOTE]
>
>La navegación a la consola OSGi puede tardar unos segundos después de guardar la configuración en el paso anterior. También puede consultar el archivo error.log para obtener más detalles.

Por ejemplo, la siguiente imagen se muestra cuando se configura correctamente ActiveMQ Artemis Server.

Si no ve la siguiente configuración desde */system/console/mq*, desplácese hasta */system/console/mq* y haga clic en **Restart** para reiniciar el agente.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Eliminar el requisito de encabezado de remitente del reenvío {#remove-referrer-header-requirement}

Siga los pasos de cada instancia de Publish:

1. Vaya a la **Consola OSGi** > **Administrador de configuración**
1. Seleccione **Filtro de Remitente del reenvío Sling de Apache**
1. Actualice config y **marque Permitir vacío**

### Configuración de la instancia de creación y publicación {#configuring-author-and-publish-instance}

Una vez configurada la topología de publicación, debe configurar las instancias de creación y publicación para vista de los resultados prácticos de la implementación:

>[!NOTE]
>
>**Requisitos previos**
>
>Para comenzar con este ejemplo, cree un nuevo proyecto de AEM Screens seguido de una ubicación, visualización y canal en el proyecto. Añada contenido al canal y asigne el canal a una pantalla.

#### Paso 1: Inicio de un reproductor de AEM Screens (dispositivo) {#step-starting-an-aem-screens-player-device}

1. Abra una nueva ventana del navegador.
1. Vaya al reproductor de pantallas con el *navegador web*, es decir,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` o inicie la aplicación de AEM Screens. Cuando abra el dispositivo, verá el estado de este como no registrado.

>[!NOTE]
>
>Puede abrir un reproductor de AEM Screens con la aplicación de AEM Screens que ha descargado o con el navegador web.

#### Paso 2: Registro de un dispositivo en el autor {#step-registering-a-device-on-author}

1. Vaya a `https://localhost:4502/screens.html/content/screens/we-retail` o seleccione el proyecto y vaya a Dispositivos > Administrador de dispositivos.
1. Seleccione **Registrar dispositivo**.
1. Haga clic en **Registro del dispositivo** para vista del dispositivo.
1. Seleccione el dispositivo que desea registrar y haga clic en **Registrar dispositivo**.
1. Verifique el código de registro y haga clic en **Validar**.
1. Escriba un título para el dispositivo y haga clic en **Registrar**.

#### Paso 3: Asignación del dispositivo para mostrar {#step-assigning-the-device-to-display}

1. Haga clic en **Asignar visualización** en el cuadro de diálogo del paso anterior.
1. Seleccione la ruta de visualización del canal en la carpeta **Ubicaciones**.
1. Haga clic en **Asignar**.
1. Haga clic en **Finalizar** para completar el proceso y ahora se asigna el dispositivo.

Comprueba tu reproductor y verás el contenido que agregaste en tu canal.

#### Paso 4: Configuración del dispositivo de publicación para publicar instancias {#step-publishing-device-configuration-to-publish-instances}

**Verificación del dispositivo**

Antes de realizar los pasos a continuación, asegúrese de comprobar el ID del dispositivo. Para comprobarlo, busque la identificación del dispositivo en el CRXDE Lite, con la ruta como */home/users/screen/we-Retail/devices*.

Siga los pasos a continuación para replicar el usuario del dispositivo:

1. Vaya a la página de administración del usuario (p. ej.: `https://localhost:4502/useradmin`
1. Buscar el grupo **screen-devices-master**
1. Haga clic con el botón secundario en el grupo y haga clic en **Activar**

>[!CAUTION]
>
>No active author-publish-screen-service ya que es un usuario del sistema, utilizado por el trabajo del autor.

También puede activar el dispositivo desde la consola de administración de dispositivos. Complete los siguientes pasos:

1. Vaya a su proyecto de Pantallas —> **Dispositivos**.
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.
1. Seleccione el dispositivo y haga clic en **Activar** en la barra de acciones, como se muestra en la figura siguiente.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, una vez activado el dispositivo también puede editar o actualizar la dirección URL del servidor haciendo clic en **Editar dirección URL del servidor** desde la barra de acciones, como se muestra en la figura siguiente y los cambios se propagarán al reproductor de AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Lista de comprobación de publicación {#publishing-check-list}

Los siguientes puntos resumen la lista de comprobación de publicación:

* *Usuario*  de dispositivo de pantallas: se almacena como usuario AEM y se activa desde  **Herramientas** >  **Seguridad** >  **Usuarios**. Al usuario se le añadirá el prefijo &quot;screen&quot; con una cadena serializada larga.

* *Proyecto* : el proyecto de AEM Screens.
* *Ubicación* : ubicación a la que está conectado el dispositivo.
* *Canales* : uno o más canales que se muestran en la ubicación
* *Programación* : si se utiliza una programación, asegúrese de que se publique
* *Ubicación, Programas y Carpeta*  de Canal, si los recursos correspondientes están dentro de una carpeta.

Siga los pasos a continuación para comprobar el comportamiento de autor y publicación:

1. Actualizar contenido de canal en la instancia de creación
1. Realice **Administrar publicación** para publicar nuevos cambios en todas las instancias de publicación
1. Pulse **Activar** para activar el dispositivo desde **Administrador de dispositivos**
1. **Editar** URL desde la URL de la instancia de autor a una de las URL de instancias de publicación
1. Compruebe que el contenido de canal actualizado se muestra en el reproductor de AEM Screens
1. Repita estos pasos con una instancia de publicación diferente


#### Paso 5: Señalar la instancia de dispositivo para publicar en el panel de administración {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Haga una vista de la IU de administración desde el reproductor de Pantallas, mantenga presionada la tecla en la esquina superior izquierda para abrir el menú Administración, en el reproductor de AEM Screens táctil habilitado o con un ratón.
1. Haga clic en la opción **Configuración** del panel lateral.
1. Cambie la instancia de autor para publicar una instancia en **Server**.

Vista los cambios en el reproductor de AEM Screens.

También puede actualizar o editar la URL del servidor desde la consola de administración de dispositivos siguiendo los pasos siguientes:

1. Vaya a su proyecto de AEM Screens y seleccione la carpeta **Devices**.
1. Haga clic en **Administrador de dispositivos** en la barra de acciones.
1. Seleccione el dispositivo y haga clic en **Editar URL del servidor** en la barra de acciones, como se muestra en la figura siguiente y los cambios se propagarán al reproductor de AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

La función **Administrar publicación** le permite enviar actualizaciones de contenido del autor para publicarlas en el dispositivo. Puede publicar/cancelar la publicación de contenido para todo el proyecto de AEM Screens o solo para uno de sus canales, ubicaciones, dispositivos, aplicaciones o programaciones. Para obtener más información sobre esta función, consulte [On-Demand Content Update](on-demand-content.md).


