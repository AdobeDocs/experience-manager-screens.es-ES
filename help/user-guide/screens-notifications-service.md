---
title: Servicio de notificaciones de AEM Screens
seo-title: Servicio de notificaciones de AEM Screens
description: Siga esta página para obtener más información sobre cómo puede supervisar la actividad del dispositivo.
seo-description: Siga esta página para obtener más información sobre cómo puede supervisar la actividad del dispositivo.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 5%

---


# Servicio de notificaciones de AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***El servicio*** de notificaciones de AEM Screens describe la función en la que puede supervisar la actividad del dispositivo.

Esta sección abarca los siguientes temas:

* **Información general**
* **Configuración de la configuración de correo electrónico**
* **Notificación de correo electrónico**
* **Ejemplo de caso de uso**

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.3.2 Feature Pack 3 o AEM 6.4.1 Screens Feature Pack 1.
>
>Para obtener acceso a este Feature Pack, debe ponerse en contacto con la Asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.

## Información general {#overview}

***El servicio*** de notificaciones de AEM Screens permite a los administradores recibir un correo electrónico si un reproductor de pantallas de AEM no realiza ping durante un período de tiempo configurable.

Este servicio se puede configurar en la consola web OSGi.

## Configuración de la configuración de correo electrónico {#configuring-email-settings}

Siga los pasos a continuación para configurar la configuración de la notificación por correo electrónico:

1. Abra **Configuración de la consola web de Adobe Experience Manager**.
1. Abra **Servicio de supervisión de correo electrónico del dispositivo de pantallas**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina los siguientes campos para configurar la configuración del correo electrónico:

   **Ruta** de acceso de dispositivosIntroduzca la ruta a los proyectos de pantallas que desea supervisar. La ruta suele ser `/home/users/screens/<Name of your project>`.

   Por ejemplo: si su proyecto es **We.Retail**, utilizará la ruta del proyecto como ***/home/users/screen/we-Retail***.

   >[!NOTE]
   >
   >Especifique la ruta del proyecto, donde se encuentran los usuarios del dispositivo.

   **Frecuencia** de programaciónEspecifique una hora (p. ej., 5:00 pm o 17:00) o una frecuencia en horas (p. ej., 1) en la que este monitor debe enviar correos electrónicos.

   **Tiempo de** espera de pingEspecifica el intervalo en minutos después del cual se debe considerar que un dispositivo no está disponible.

   **Servidor** SMTPEspecifica el servidor SMTP que se utiliza para enviar correos electrónicos.

   **Puerto** SMTPIntroduzca el puerto SMTP.

   **Usar** TLSTransport Layer Security (TLS) le permite utilizar una comunicación segura con el servidor SMTP.

   Se recomienda utilizar TLS para una conexión segura a los servidores de correo de la empresa. Consulte con el administrador de correo los valores adecuados.

   **** usernameEspecifique el nombre de usuario para enviar correos electrónicos.

   **** passwordEspecifique la contraseña para enviar correos electrónicos.

   **** DestinatarioEspecifique la dirección de correo electrónico del destinatario.

   >[!NOTE]
   >
   >Solo puede introducir una dirección de correo electrónico. Para enviar un correo electrónico masivo, cree una lista de grupo o distribución con los usuarios relevantes.

1. Haga clic en **Guardar** para configurar la actividad del monitor mediante un correo electrónico para el dispositivo AEM Screens.

## Notificación de correo electrónico {#email-notification}

Una vez configurada la configuración para las notificaciones por correo electrónico, recibirá una notificación por correo electrónico que contendrá el vínculo al dispositivo real del que se informa la inactividad.

El acceso a ese vínculo le llevará directamente al panel del dispositivo.

Los correos electrónicos solo se enviarán si hay al menos un dispositivo que no haya anidado durante el tiempo de espera de ping dado y que aún no esté sonando en el momento de generar el correo electrónico.

### Casos de uso de ejemplo {#example-use-cases}

En el siguiente ejemplo se describen algunos escenarios para la referencia, a fin de configurar las propiedades desde el servicio de supervisión de correo electrónico de dispositivos de pantalla.

**Escenario 1**:

Si establece la frecuencia de programación como 1:00 a.m. y el tiempo de espera de ping como 60, si el dispositivo Screens no emite un ping entre las 12:00 p.m. y la 1:00 p.m., recibirá una notificación por correo electrónico que confirma la inactividad del dispositivo.

**Escenario 2**:

Si establece la frecuencia de programación como 1 y el tiempo de espera de ping como 60, si el dispositivo Screens no emite un ping de una sola vez a cualquier hora del día, recibirá una notificación por correo electrónico que confirme la inactividad del dispositivo.
