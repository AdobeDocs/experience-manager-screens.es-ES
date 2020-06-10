---
title: Configuración del autor y la publicación en AEM Screens
seo-title: Configuración del autor y la publicación en AEM Screens
description: La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se repite en varias instancias de publicación. Siga esta página para obtener información sobre cómo configurar el autor y la publicación para AEM Screens.
seo-description: La arquitectura de AEM Screens se parece a la arquitectura tradicional de AEM Sites. El contenido se crea en una instancia de autor de AEM y, a continuación, se repite en varias instancias de publicación. Siga esta página para obtener información sobre cómo configurar el autor y la publicación para AEM Screens.
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: 59eb6f298aa646d14445ddd6082006742fb02d62
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 2%

---


# Configuración del autor y la publicación en AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página resalta los siguientes temas:

* **Configuración de instancias de creación y publicación**
* **Configuración de la topología de publicación**
* **Administración de publicación: Envío de actualizaciones de contenido desde el autor a la publicación en el dispositivo**

## Requisitos previos {#prerequisites}

Antes de comenzar con los servidores de creación y publicación, debe tener conocimientos previos de:

* **Topología de AEM**
* **Creación y gestión de proyectos de AEM Screens**
* **Proceso de registro del dispositivo**

>[!NOTE]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4 Screens Feature Pack 2. Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Configuración de instancias de creación y publicación {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para obtener más información sobre el autor y la descripción general de la arquitectura de publicación, así como sobre cómo se crea el contenido en una instancia de autor de AEM y, a continuación, se repite en varias instancias de publicación, consulte [Creación y descripción general](author-publish-architecture-overview.md)de la arquitectura de publicación.

En la siguiente sección se explica cómo configurar los agentes de replicación en la topología de creación y publicación.

Puede configurar un ejemplo sencillo en el que aloje a un autor y dos instancias de publicación:

* Autor —> localhost:4502
* Publish 1 (pub1) —> localhost:4503
* Publish 2 (pub2) —> localhost:4504

## Configuración de agentes de replicación en el autor {#setting-replication-agents}

Para crear agentes de replicación, debe aprender a crear un agente de replicación estándar.

Existen 3 agentes de replicación que se necesitan para las pantallas:

1. **Agente de replicación predeterminado ***(especificado como***agente** de replicación estándar)
1. **Agente de replicación de pantallas**
1. **Agente de replicación inversa**

### Paso 1: Creación de un agente de replicación predeterminado {#step-creating-a-default-replication-agent}

Siga los pasos a continuación para crear un agente de replicación predeterminado:

1. Vaya a su instancia de AEM —> icono de martillo —> **Operaciones** —> **Configuración**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Seleccione **Replicación** en el árbol de navegación izquierdo.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Seleccione los **agentes del autor** en la carpeta **Replicación** y haga clic en **Nuevo** para crear un nuevo agente de replicación estándar.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Introduzca el **Título** y el **Nombre** para crear el agente de replicación y haga clic en **Crear**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Haga clic con el botón secundario en el agente de replicación y haga clic en **Abrir** para editar la configuración.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Haga clic en **Editar** para abrir el cuadro de diálogo Configuración **del** agente y especificar los detalles.

   >[!NOTE]
   >
   >El usuario debe marcar **Habilitado** para habilitar el agente de replicación. Debe marcar esta opción en Predeterminado, Pantallas y Agentes de replicación inversa.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Vaya a la ficha **Transporte** e introduzca el **URI**, el **usuario** y la **contraseña**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >También puede copiar y cambiar el nombre de un agente de replicación predeterminado existente.


#### Creación de Agentes de Replicación Estándar  {#creating-standard-replication-agents}

1. Crear un agente de replicación estándar para pub1 (el agente predeterminado ya debería estar configurado) (por ejemplo, *https://&lt;hostname>:4503/bin/received?sling:authRequestLogin=1*)
1. Cree un agente de replicación estándar para pub2. Puede copiar el agente de rep para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte. (por ejemplo, *https://&lt;hostname>:4504/bin/received?sling:authRequestLogin=1*)

#### Creación de agentes de replicación de pantallas {#creating-screens-replication-agents}

1. Cree un agente de replicación de AEM Screens para pub1. De manera predeterminada, existe un agente de replicación de pantallas denominado Screens que apunta al puerto 4503. Esto debe habilitarse.
1. Cree un agente de replicación de AEM Screens para pub2. Copie el agente de replicación de Screens para pub1 y cambie el puerto para que señale a 4504 para pub2.

#### Creación de agentes de replicación inversa de pantallas {#creating-screens-reverse-replication-agents}

1. Cree un agente de replicación inversa estándar para pub1.
1. Cree un agente de replicación inversa estándar para pub2. Puede copiar el agente de rep inverso para pub1 y actualizar el transporte que se utilizará para pub2 cambiando el puerto en la configuración de transporte.

## Configuración de la topología de publicación {#setting-up-publish-topology}

### Paso 1: Configuración de Apache Sling Oak Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Configure el descubrimiento basado en Apache Sling Oak para todas las instancias de Publish en la topología

Para cada instancia de publicación:

1. Ir a `https://<host>:<port>/system/console/configMgr`
1. Seleccione **Apache Sling Oak-Based Discovery Service** Configuration.
1. Actualizar direcciones URL del conector de topología: agregue direcciones URL de todas las instancias de publicación de participación que sean:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. Lista permitida del conector de topología: adaptarse a las IP o subredes que cubren instancias de publicación de participación
1. Habilitar bucles locales de detención **automática**

La configuración debe ser idéntica para cada instancia de publicación y el bucle local de parada automática evita un bucle infinito.

#### Paso 2: Verificar topología de publicación {#step-verify-publish-topology}

Para cualquiera de las instancias de publicación vaya a `https://:/system/console/topology`. Debe ver cada instancia de publicación representada en la topología en Conectores **de topología de** salida.

#### Paso 3: Configuración del clúster de artemis de ActiveMQ {#step-setup-activemq-artemis-cluster}

Este paso le permite crear una contraseña cifrada para el clúster de ActiveMQ Artemis.
El usuario y la contraseña del clúster de todas las instancias de publicación de la topología deben ser idénticos. Es necesario cifrar la contraseña de la configuración de Artemis de ActiveMQ. Dado que cada instancia tiene su propia clave de cifrado, es necesario utilizar la compatibilidad con criptografía para crear una cadena de contraseña cifrada. Luego se utilizará la contraseña cifrada en la configuración OSGi para ActiveMQ.

En cada instancia de publicación:

1. En la consola OSGi, navegue a **MAIN** —> Compatibilidad con **criptografía** (*https://&lt;host>:&lt;puerto>/system/console/crypto*).
1. Escriba la contraseña de texto sin formato que desee (igual para todas las instancias) en **Texto sin formato**
1. Haga clic en **Proteger**.
1. Copie el valor Texto **** protegido en el editor de texto o el bloc de notas. Este valor se utilizará en la configuración OSGi para ActiveMQ.

Dado que cada instancia de publicación tiene claves criptográficas únicas de forma predeterminada, debe realizar este paso en cada instancia de pub y guardar la clave única para la siguiente configuración.

>[!NOTE]
>La contraseña debe inicio y terminar con llaves.
>Por ejemplo:{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a6 10e}

#### Paso 4: Activar clúster de artemis ActiveMQ {#step-activate-activemq-artemis-cluster}

En cada instancia de publicación:

1. Vaya al administrador de configuración OSGi *https://&lt;host>:&lt;puerto>/system/console/configMgr*
1. Seleccione la configuración del proveedor **de JMS de** Apache ActiveMQ Artemis
1. Actualice lo siguiente:

* ***Contraseña*** del clúster: (utilice un valor cifrado del paso anterior por instancia respectiva)
* ***Temas***: {name: &#39;comandos&#39;, dirección: &#39;com.adobe.cq.screens.command&#39;, maxConsumers: 50}

#### Verificar el clúster de artemis de ActiveMQ {#verify-activemq-artemis-cluster}

Siga los pasos a continuación en cada instancia de Publish:

1. Vaya a la Consola OSGi -> Principal > Artemis ActiveMQ `[https://localhost:4505/system/console/mq`.
1. Compruebe y verifique la vista de los puertos de otras instancias en Información del clúster > Topología > nodos=2, miembros=2.
1. Enviar un mensaje de prueba (en la parte superior de la pantalla, en Información del agente)
1. Introduzca los siguientes cambios en los campos:

   1. **Destino**: /com.adobe.cq.screen/devTestTopic
   1. **Texto**: Hola a todos
   1. Vista el error.log de cada instancia para ver que el mensaje se ha enviado y recibido en el clúster

>[!NOTE]
>
>La navegación a la consola OSGI puede tardar unos segundos después de guardar la configuración en el paso anterior. También puede consultar el archivo error.log para obtener más detalles.

Por ejemplo, la siguiente imagen se muestra cuando se configura correctamente ActiveMQ Artemis Server.

Si no ve la siguiente configuración desde */system/console/mq*, vaya a */system/console/mq* y haga clic en **Reiniciar** para reiniciar el agente.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Eliminar el requisito de encabezado de remitente del reenvío {#remove-referrer-header-requirement}

Siga los pasos de cada instancia de Publish:

1. Vaya a la Consola **** OSGi > Administrador **de configuración**
1. Seleccionar el filtro de Remitente del reenvío Sling de **Apache**
1. Actualizar configuración y **marcar Permitir vacío**

### Configuración de la instancia de creación y publicación {#configuring-author-and-publish-instance}

Una vez configurada la topología de publicación, debe configurar las instancias de creación y publicación para vista de los resultados prácticos de la implementación:

>[!NOTE]
>
>**Requisitos previos**
>
>Para comenzar con este ejemplo, cree un nuevo proyecto de AEM Screens y, a continuación, cree una ubicación, una pantalla y un canal en el proyecto. Añada contenido al canal y asigne el canal a una pantalla.

#### Paso 1: Inicio de AEM Screens Player (dispositivo) {#step-starting-an-aem-screens-player-device}

1. Abra una nueva ventana del navegador.
1. Go to Screens player using the *web browser*, that is,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` or launch the AEM Screens app. Cuando abra el dispositivo, verá el estado de este como no registrado.

>[!NOTE]
>
>Puede abrir un reproductor de AEM Screens con la aplicación AEM Screens que ha descargado o con el navegador web.

#### Paso 2: Registro de un dispositivo en el autor {#step-registering-a-device-on-author}

1. Vaya a su proyecto `https://localhost:4502/screens.html/content/screens/we-retail` o selecciónelo y vaya a Dispositivos > Administrador de dispositivos.
1. Seleccione **Registrar dispositivo**.
1. Haga clic en Registro **del** dispositivo para realizar la vista del dispositivo.
1. Select the device you want to register and click **Register Device**.
1. Compruebe el código de registro y haga clic en **Validar**.
1. Escriba un título para el dispositivo y haga clic en **Registrar**.

#### Paso 3: Asignación del dispositivo para mostrar {#step-assigning-the-device-to-display}

1. Haga clic en **Asignar visualización** en el cuadro de diálogo del paso anterior.
1. Seleccione la ruta de visualización del canal en la carpeta **Ubicaciones** .
1. Click **Assign**.
1. Click **Finish** to complete the process, and now the device is assigned.

Comprueba tu reproductor y verás el contenido que agregaste en tu canal.

#### Paso 4: Configuración de dispositivo de publicación para instancias de publicación {#step-publishing-device-configuration-to-publish-instances}

**Verificación del dispositivo**

Antes de realizar los pasos a continuación, asegúrese de comprobar el ID del dispositivo. Para verificarlo, busque el ID del dispositivo en CRXDELite, con la ruta como */home/users/screen/we-Retail/devices*.

Siga los pasos a continuación para replicar el usuario del dispositivo:

1. Vaya a la página de administración del usuario (p. ej.: `https://localhost:4502/useradmin`
1. Buscar el grupo **screen-devices-master**
1. Haga clic con el botón secundario en el grupo y haga clic en **Activar**

>[!CAUTION]
>
>No active author-publish-screen-service ya que es un usuario del sistema, utilizado por el trabajo del autor.

También puede activar el dispositivo desde la consola de administración de dispositivos. Siga los pasos a continuación:

1. Vaya a su proyecto Pantallas —> **Dispositivos**.
1. Click **Device Manager** from the action bar.
1. Seleccione el dispositivo y haga clic en **Activar** en la barra de acciones, como se muestra en la figura siguiente.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, una vez activado el dispositivo también puede editar o actualizar la URL del servidor haciendo clic en **Editar URL** del servidor en la barra de acciones, como se muestra en la figura siguiente y los cambios se propagarán al reproductor de AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### lista de comprobación de publicación {#publishing-check-list}

Los siguientes puntos resumen la lista de comprobación de publicación:

* *Usuario* de dispositivo de pantallas: se almacena como usuario de AEM y se activa desde **Herramientas** > **Seguridad** > **Usuarios**. Al usuario se le añadirá el prefijo &quot;screen&quot; con una cadena serializada larga.

* *Proyecto* : proyecto de AEM Screens.
* *Ubicación* : ubicación a la que está conectado el dispositivo.
* *Canales* : uno o más canales que se muestran en la ubicación
* *Programación* : si utiliza una programación, asegúrese de que se publique
* *Ubicación, Programas y Carpeta* de Canal: si los recursos correspondientes están dentro de una carpeta.

Siga los pasos a continuación para comprobar el comportamiento de autor y publicación:

1. Actualizar contenido de canal en la instancia de creación
1. Realice **Administrar publicación** para publicar nuevos cambios en todas las instancias de publicación
1. Pulse **Activar** para activar el dispositivo desde el Administrador **de dispositivos**
1. **Editar URL** desde la URL de la instancia de autor a una de las URL de instancias de publicación
1. Verificación de la visualización del contenido de canal actualizado en el reproductor de AEM Screens
1. Repita estos pasos con una instancia de publicación diferente


#### Paso 5: Señalar la instancia de dispositivo para publicar en el panel de administración {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Haga una Vista de la IU de administración desde el reproductor de Pantallas, mantenga presionada la tecla en la esquina superior izquierda para abrir el menú Administración, en el reproductor de AEM Screens activado o con un ratón.
1. Haga clic en la opción **Configuración** del panel lateral.
1. Cambiar la instancia de autor a la instancia de publicación en **el servidor**.

Vista de los cambios en el reproductor de AEM Screens.

También puede actualizar o editar la URL del servidor desde la consola de administración de dispositivos siguiendo los pasos siguientes:

1. Vaya al proyecto de AEM Screens y seleccione la carpeta **Dispositivos** .
1. Click **Device Manager** from the action bar.
1. Seleccione el dispositivo y haga clic en **Editar URL** del servidor en la barra de acciones, como se muestra en la figura siguiente y los cambios se propagarán al reproductor de AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

La función **Administrar publicación** le permite enviar actualizaciones de contenido desde el autor para publicarlas en el dispositivo. Puede publicar/cancelar la publicación de contenido para todo el proyecto de AEM Screens o solo para uno de sus canales, ubicaciones, dispositivos, aplicaciones o programaciones. Para obtener más información sobre esta función, consulte [On-Demand Content Update](on-demand-content.md).


