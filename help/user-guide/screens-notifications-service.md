---
title: Servicio de notificaciones de AEM Screens
description: Obtenga más información acerca de cómo monitorizar la actividad de los dispositivos para AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
TQID: https://experienceleague.adobe.com/9BVI-WKkjiL-vY57T-GMir-4Dll552q-30LDHF20BxU
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 538
ht-degree: 0%

---

# Servicio de notificaciones de AEM Screens{#aem-screens-notifications-service}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Servicio de notificaciones de AEM Screens*** describe la actividad del dispositivo de supervisión.

Esta sección trata los siguientes temas:

* **Información general**
* **Configurar correo electrónico**
* **Notificación por correo electrónico**
* **Ejemplo de caso de uso**

<!-- 
OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. 
-->

## Información general {#overview}

El ***servicio de notificaciones de AEM Screens*** permite a los administradores recibir un correo electrónico si un reproductor de AEM Screens no hace ping durante un tiempo configurable.

Este servicio se puede configurar en la consola web de OSGi.

## Configuración de correo electrónico {#configuring-email-settings}

Siga los pasos a continuación para configurar los ajustes de notificación por correo electrónico:

1. Abra **Configuración de la consola web de Adobe Experience Manager**.
1. Abra **Servicio de supervisión de correo electrónico del dispositivo Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina los siguientes campos para poder configurar los ajustes del correo electrónico:

   **Ruta de acceso de dispositivos**: escriba la ruta de acceso a los proyectos de Screens que desea supervisar. La ruta de acceso suele ser `/home/users/screens/<Name of your project>`.

   Por ejemplo, si su proyecto es **`We.Retail`**, utilice la ruta del proyecto como ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Especifique la ruta del proyecto, donde se encuentran los usuarios del dispositivo.

   **Frecuencia de horario**: especifique la hora (por ejemplo, 5:00 p. m. o 17:00) o la frecuencia en horas (por ejemplo, 1) a las que este monitor debe enviar correos electrónicos.

   **Tiempo de espera de ping**: este campo especifica el intervalo en minutos tras el cual se debe considerar que un dispositivo no está accesible.

   **Servidor SMTP**: especifica el servidor SMTP que se usa para enviar correos electrónicos.

   **Puerto SMTP**: introduzca el puerto SMTP.

   **Usar TLS** - Seguridad de la capa de transporte (TLS) permite usar una comunicación segura con el servidor SMTP.

   Adobe recomienda utilizar TLS para una conexión segura con servidores de correo corporativos. Consulte con su administrador de correo los valores apropiados.

   **nombre de usuario** - Especifique el nombre de usuario para enviar correos electrónicos.

   **contraseña** - Especifique la contraseña para enviar correos electrónicos.

   **Destinatario** - Especifique la dirección de correo electrónico del destinatario.

   >[!NOTE]
   >
   >Solo puede escribir una dirección de correo electrónico. Para enviar un correo electrónico masivo, cree un grupo o una lista de distribución con los usuarios relevantes.

1. Haga clic en **Guardar** para configurar la actividad del monitor mediante un mensaje de correo electrónico para el dispositivo AEM Screens.

## Notificación por correo electrónico {#email-notification}

Después de establecer la configuración de las notificaciones por correo electrónico, recibe una notificación por correo electrónico que contiene el vínculo al dispositivo real del que se informa de inactividad.

Al acceder a ese vínculo, accederá directamente al panel del dispositivo.

Los correos electrónicos solo se envían si:

* hay al menos un dispositivo que no ha hecho ping durante el tiempo de espera de ping especificado, y
* sigue sin hacer ping en el momento de generar el correo electrónico.

### Casos de uso de ejemplo {#example-use-cases}

En el siguiente ejemplo se describen algunos escenarios como referencia para configurar las propiedades del servicio de monitorización de correo electrónico de dispositivos de Screens.

**Escenario 1**

Estableció la frecuencia de horario como 1:00 a.m. y el tiempo de espera de ping como 60. A continuación, si el dispositivo AEM Screens no hace ping entre las 12:00 p.m. y las 13:00 p.m., recibirá una notificación por correo electrónico que confirmará la inactividad del dispositivo.

**Escenario 2**

Establezca la frecuencia de programación como 1 y el tiempo de espera de ping como 60. A continuación, si el dispositivo AEM Screens no hace ping a la vez en ningún momento del día en particular, recibirá una notificación por correo electrónico que confirma la inactividad del dispositivo.
