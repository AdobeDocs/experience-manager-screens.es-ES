---
title: Servicio de notificaciones de AEM Screens
seo-title: AEM Screens Notifications Service
description: Siga esta página para obtener más información acerca de cómo supervisar la actividad de los dispositivos.
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Servicio de notificaciones de AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Servicio de notificaciones de AEM Screens***, describe la función donde se puede monitorizar la actividad del dispositivo.

Esta sección trata los siguientes temas:

* **Información general**
* **Configuración de correo electrónico**
* **Notificación por correo electrónico**
* **Ejemplo de caso de uso**

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens AEM AEM solo está disponible si ha instalado el paquete de funciones 3 de 6.3.2 o el paquete de funciones 1 de Screens de 6.3.2 o de 6.4.1.
>
>Para obtener acceso a este paquete de funciones, debe ponerse en contacto con el Soporte técnico de Adobe y solicitar acceso. Una vez que tenga los permisos necesarios, puede descargarlo desde Package Share.

## Información general {#overview}

***Servicio de notificaciones de AEM Screens*** AEM , permite a los administradores recibir un correo electrónico si un reproductor de pantallas de pantalla de la aplicación no hace ping durante un periodo de tiempo configurable.

Este servicio se puede configurar en la consola web de OSGi.

## Configuración de correo electrónico {#configuring-email-settings}

Siga los pasos a continuación para configurar las opciones de notificación por correo electrónico:

1. Abrir **Configuración de la consola web Adobe Experience Manager**.
1. Abrir **Servicio de supervisión del correo electrónico del dispositivo Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina los siguientes campos para configurar los ajustes del correo electrónico:

   **Ruta de dispositivos** Introduzca la ruta de los proyectos de Screens que desea monitorizar. El camino suele ser `/home/users/screens/<Name of your project>`.

   Por ejemplo, si el proyecto es **We.Retail**, utilizará la ruta del proyecto como ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Especifique la ruta del proyecto, donde se encuentran los usuarios del dispositivo.

   **Frecuencia de programación** Especifique la hora (por ejemplo, 5:00 p. m. o 17:00) o la frecuencia en horas (por ejemplo, 1) a las que este monitor debe enviar correos electrónicos.

   **Tiempo de espera de ping** Esto especifica el intervalo en minutos tras el cual un dispositivo debe considerarse no accesible.

   **Servidor SMTP** Especifica el servidor SMTP que se utiliza para enviar correos electrónicos.

   **Puerto SMTP** Introduzca el puerto SMTP.

   **Usar TLS** Seguridad de la capa de transporte (TLS) permite utilizar una comunicación segura con el servidor SMTP.

   Se recomienda utilizar TLS para una conexión segura con servidores de correo corporativos. Consulte con su administrador de correo los valores apropiados.

   **nombre de usuario** Especifique el nombre de usuario para enviar correos electrónicos.

   **contraseña** Especifique la contraseña para enviar correos electrónicos.

   **Destinatario** Especifique la dirección de correo electrónico del destinatario.

   >[!NOTE]
   >
   >Solo puede escribir una dirección de correo electrónico. Para enviar un correo electrónico masivo, cree un grupo o una lista de distribución con los usuarios relevantes.

1. Clic **Guardar** para configurar la actividad del monitor mediante un correo electrónico para el dispositivo AEM Screens.

## Notificación por correo electrónico {#email-notification}

Una vez que haya configurado las notificaciones por correo electrónico, recibirá una notificación por correo electrónico que contendrá el vínculo al dispositivo real del que se informa de inactividad.

Al acceder a ese vínculo, accederá directamente al panel del dispositivo.

Los correos electrónicos solo se enviarán si hay al menos un dispositivo que no ha hecho ping durante el tiempo de espera de ping especificado y sigue sin hacerlo en el momento de generar el correo electrónico.

### Casos de uso de ejemplo {#example-use-cases}

El siguiente ejemplo describe algunos escenarios como referencia para configurar las propiedades del servicio de supervisión de correo electrónico del dispositivo de Screens.

**Escenario 1**:

Si establece la frecuencia de programación en 1:00 a. m. y el tiempo de espera de ping en 60, si el dispositivo Screens no hace ping entre las 12:00 p. m. y hasta la 1:00 p. m., recibirá una notificación por correo electrónico que confirmará la inactividad del dispositivo.

**Escenario 2**:

Si establece la frecuencia de programación como 1 y el tiempo de espera de ping como 60, si el dispositivo Screens no hace ping entre una vez en cualquier momento del día en particular, recibirá una notificación por correo electrónico que confirma la inactividad del dispositivo.
