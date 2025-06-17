---
title: Configuraciones de la plataforma AEM
description: La página describe las configuraciones de la plataforma AEM
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# Configuraciones de la plataforma AEM {#platform-configurations}

>[!NOTE]
>
>Una parte interesada típica de esta actividad es un implementador de AEM.

Empiece a usar AEM Screens siguiendo las secciones que se indican a continuación para configurar las configuraciones de la plataforma AEM

## Configuraciones del servidor {#server-configurations}

Para establecer configuraciones de servidor, consulte [Configuraciones de servidor](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Autor-Publicar {#author-publish}

Ver [Configuración de autor y publicación en AEM Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Si solo hay un autor y una publicación, solo puede seguir los pasos de **Configuración de agentes de replicación en el autor** en la página [Configuración de autor y publicación en AEM Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

## Configuraciones de Dispatcher {#dispatcher-configurations}

Dispatcher es la herramienta de equilibrio de carga y almacenamiento en caché de Adobe Experience Manager. El uso de Dispatcher de AEM también le permitirá proteger el servidor AEM de ataques. Por lo tanto, puede aumentar la seguridad de su instancia de AEM mediante Dispatcher con un servidor web de clase empresarial.

Consulte **[Configuraciones de Dispatcher para AEM Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** que resalta las directrices para configurar Dispatcher para un proyecto de AEM Screens.

## Instalación de FMpeg y representaciones de vídeo {#installing-ffmpeg}

Instale FFMpeg siguiendo los pasos para el sistema operativo apropiado (normalmente RHEL):

1. Si instala habilitando EPEL y RPMFusion, puede instalar todos los códecs de gstreamer para ampliar la compatibilidad con las conversiones FFmpeg
1. Si el códec AAC está marcado como experimental, las conversiones ffmpeg fallan. Para evitar este problema, agregue `-strict -2` a los perfiles de vídeo (`/etc/dam/video` en AEM 6.3 y mueva a `/libs/settings/dam/video in AEM 6.4`)

   >[!NOTE]
   >
   >`-strict -2` debe ser el último parámetro de la lista de parámetros. Además, en AEM 6.4, copie los nodos en */libs/settings/dam/video* a */conf/global/settings/dam/video* como se menciona en [Representaciones de vídeo](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Compruebe que se están produciendo conversiones de vídeo y que se están creando representaciones.

## Restricciones de contraseña {#password-restrictions}

La política de contraseñas de AEM debe deshabilitarse en la instancia de AMS. También se puede configurar de forma alternativa en la consola web mediante el servicio para dispositivos Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte la sección **Restricciones de contraseña** en[Configuración de autor y publicación en AEM Screens](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configuración de los entornos {#setting-up-environments}

Instale y ejecute las versiones más actuales de los siguientes paquetes para su versión de Adobe Experience Manager (AEM):

* AEM Service Pack
* Screens Feature Pack
* Paquete de correcciones acumulativas de AEM

Además de lo anterior, identifique cualquier paquete de desarrollo (por ejemplo, WCM Core
componentes) o kits de herramientas de terceros (por ejemplo, SAP Hybris) necesarios.
Instale los mismos paquetes de software en su entorno de desarrollo local. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Las configuraciones de servidor no coincidentes crean problemas al implementar y probar.

>[!NOTE]
>
>Para instalar el paquete de funciones más reciente para AEM Screens, consulte [Notas de la versión](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Configuración de ACL {#setting-up-acls}

La configuración de ACL explica cómo separar proyectos para que cada individuo o equipo administre su propio proyecto.

Consulte [Configuración de ACL](https://experienceleague.adobe.com/es/docs/experience-manager-screens/user-guide/administering/setting-up-acls) para obtener más información.
