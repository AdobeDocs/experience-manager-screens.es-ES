---
title: Configuraciones de la plataforma AEM
seo-title: AEM Platform Configurations
description: AEM La página describe las configuraciones de plataforma de la
seo-description: The page describes AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 21%

---

# Configuraciones de la plataforma AEM  {#platform-configurations}

>[!NOTE]
>
>AEM La parte interesada habitual de esta actividad es un implementador de.

AEM Siga las secciones a continuación para configurar las configuraciones de plataforma de la para comenzar con AEM Screens.

## Configuraciones del servidor {#server-configurations}

Para configurar el servidor, consulte [Configuraciones del servidor](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Autor-Publicar {#author-publish}

Para configurar la creación y publicación, consulte [Configuración de autor y publicación en AEM Screens](https://helpx.adobe.com/es/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Si solo hay un autor y una publicación, solo tiene que seguir los pasos que se describen en **Configuración de agentes de replicación en Autor** en la página [Configuración de autor y publicación en AEM Screens](https://helpx.adobe.com/es/experience-manager/6-5/screens/using/author-and-publish.html).

## Configuraciones de Dispatcher {#dispatcher-configurations}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager. El uso de Dispatcher de AEM también le permitirá proteger el servidor AEM de ataques. Por lo tanto, puede aumentar la seguridad de su instancia de AEM mediante Dispatcher y un servidor web de clase empresarial.

Consulte **[Configuraciones de Dispatcher para AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** que resalta las directrices para configurar dispatcher para un proyecto de AEM Screens.

## Instalación de FMpeg y representaciones de vídeo {#installing-ffmpeg}

Instale FFMpeg siguiendo los pasos para el sistema operativo apropiado (normalmente RHEL):

1. Si instala habilitando EPEL y RPMFusion, puede instalar todos los códecs de gstreamer para ampliar la compatibilidad con las conversiones FFmpeg
1. Si el códec AAC está marcado como experimental, las conversiones ffmpeg fallarán. AEM AEM Para evitar esto, agregue -stricto -2 a los perfiles de vídeo (/etc/dam/video en 6.3 y se mueva a /libs/settings/dam/video en 6.4), en la versión 6.4.
   >[!NOTE]
   >
   > Tenga en cuenta que -strict -2 debe ser los últimos parámetros en la lista de parámetros. AEM Además, en la versión 6.4 de, debe copiar los nodos en */libs/settings/dam/video* hasta */conf/global/settings/dam/video* como se menciona en [Representaciones de vídeo](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Compruebe que se están produciendo conversiones de vídeo y que se están creando representaciones.

## Restricciones de contraseña {#password-restrictions}

AEM La política de contraseña de la debe deshabilitarse en la instancia de AMS. Esto se puede configurar de forma alternativa en la consola web mediante el servicio de dispositivos de Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte **Restricciones de contraseña** sección en[Configuración de autor y publicación en AEM Screens](https://helpx.adobe.com/es/experience-manager/6-5/screens/using/author-and-publish.html)

## Configuración de los entornos {#setting-up-environments}

Instale y ejecute las versiones más actuales de los siguientes paquetes para su versión de Adobe Experience Manager AEM ():

* Paquete de servicio de AEM
* Paquete de funciones de Screens
* Paquete de correcciones acumulativas de AEM 

Además de lo anterior, identifique cualquier paquete de desarrollo (por ejemplo, componentes principales de WCM) o kits de herramientas de terceros (por ejemplo, SAP Hybris) que sean necesarios.
Instale los mismos paquetes de software en los entornos de desarrollo local. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Si las configuraciones del servidor no coinciden, se crearán problemas al implementar y probar.

>[!NOTE]
>
>Para instalar el último paquete de funciones para AEM Screens, consulte [Notas de versión](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Configuración de ACL {#setting-up-acls}

La configuración de ACL explica cómo separar proyectos para que cada individuo o equipo administre su propio proyecto.

Consulte [Configuración de ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) para obtener más información.
