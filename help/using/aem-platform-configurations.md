---
title: AEM Configuraciones de plataforma de
description: AEM La página describe las configuraciones de plataforma de la
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 3%

---

# AEM Configuraciones de plataforma de  {#platform-configurations}

>[!NOTE]
>
>AEM Un inversor habitual de esta actividad es un implementador de.

Empiece a usar AEM Screens AEM siguiendo las secciones que se indican a continuación para configurar configuraciones de plataforma de la

## Configuraciones del servidor {#server-configurations}

Para configurar el servidor, consulte [Configuraciones del servidor](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Autor-Publicar {#author-publish}

Consulte [Configuración de autor y publicación en AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Si solo hay un autor y una publicación, solo debe seguir los pasos que se describen en **Configuración de agentes de replicación en Autor** in [Configuración de autor y publicación en AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) página.

## Configuraciones de Dispatcher {#dispatcher-configurations}

Dispatcher es la herramienta de almacenamiento en caché y equilibrio de carga de Adobe Experience Manager. El uso de Dispatcher de AEM también le permitirá proteger el servidor AEM de ataques. AEM Por lo tanto, puede aumentar la seguridad de la instancia de mediante Dispatcher con un servidor web de clase empresarial.

Consulte **[Configuraciones de Dispatcher para AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** que resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.

## Instalación de FMpeg y representaciones de vídeo {#installing-ffmpeg}

Instale FFMpeg siguiendo los pasos para el sistema operativo apropiado (normalmente RHEL):

1. Si instala habilitando EPEL y RPMFusion, puede instalar todos los códecs de gstreamer para ampliar la compatibilidad con las conversiones FFmpeg
1. Si el códec AAC está marcado como experimental, las conversiones ffmpeg fallan. Para evitar esto, agregue `-strict -2` AEM AEM a los perfiles de vídeo (/etc/dam/video en la versión 6.3 de y se movió a /libs/settings/dam/video en la versión 6.4).

   >[!NOTE]
   >
   >El `-strict -2` debe ser el último parámetro de la lista de parámetros. AEM Además, en la versión 6.4, copie los nodos en */libs/settings/dam/video* hasta */conf/global/settings/dam/video* como se menciona en [Representaciones de vídeo](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Compruebe que se están produciendo conversiones de vídeo y que se están creando representaciones.

## Restricciones de contraseña {#password-restrictions}

AEM La política de contraseña de la debe deshabilitarse en la instancia de AMS. Esto se puede configurar de forma alternativa en la consola web mediante el servicio de dispositivos de Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte **Restricciones de contraseña** sección en[Configuración de autor y publicación en AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configuración de los entornos {#setting-up-environments}

Instale y ejecute las versiones más actuales de los siguientes paquetes para su versión de Adobe Experience Manager AEM ():

* AEM Paquete de servicio de
* Paquete de funciones de Screens
* AEM Paquete de correcciones acumulativas de

Además de lo anterior, identifique cualquier paquete de desarrollo (por ejemplo, componentes principales de WCM) o kits de herramientas de terceros (por ejemplo, SAP Hybris) que sean necesarios.
Instale los mismos paquetes de software en su entorno de desarrollo local. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Las configuraciones de servidor no coincidentes crean problemas al implementar y probar.

>[!NOTE]
>
>Para instalar el paquete de funciones más reciente para AEM Screens, consulte [Notas de versión](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Configuración de ACL {#setting-up-acls}

La configuración de ACL explica cómo separar proyectos para que cada individuo o equipo administre su propio proyecto.

Consulte [Configuración de ACL](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls) para obtener más información.
