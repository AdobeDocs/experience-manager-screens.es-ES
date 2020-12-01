---
title: Configuraciones de la plataforma AEM
seo-title: Configuraciones de la plataforma AEM
description: La página describe AEM configuraciones de plataforma
seo-description: La página describe AEM configuraciones de plataforma
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# Configuraciones de la plataforma AEM  {#platform-configurations}

>[!NOTE]
>
>El participante habitual de esta actividad es un implementador de AEM.

Siga las secciones a continuación para configurar AEM configuraciones de plataforma y comenzar con AEM Screens.

## Configuraciones del servidor {#server-configurations}

Para configurar configuraciones de servidor, consulte [Configuraciones de servidor](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

Para configurar la creación y publicación, consulte [Configuración del autor y la publicación en AEM Screens](https://helpx.adobe.com/es/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Si solo hay un autor y una publicación, solo tiene que seguir los pasos que se describen en **Configuración de agentes de replicación en Autor** en la página [Configuración de autor y publicación en AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html).

## Configuraciones del despachante {#dispatcher-configurations}

Dispatcher es la herramienta de almacenamiento en caché o de equilibrio de carga de Adobe Experience Manager. El uso de Dispatcher de AEM también le permitirá proteger el servidor AEM de ataques. Por lo tanto, puede aumentar la seguridad de su instancia de AEM mediante Dispatcher y un servidor web de clase empresarial.

Consulte **[Configuraciones del despachante para AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** que resalta las pautas para configurar el despachante para un proyecto de AEM Screens.

## Instalación de representaciones de FFMpeg y video {#installing-ffmpeg}

Instale FFMpeg siguiendo los pasos para el sistema operativo correspondiente (normalmente RHEL):

1. Si realiza la instalación activando EPEL y RPMFusion, puede instalar todos los códecs de gstreaming para ampliar la compatibilidad con las conversiones de FFmpeg
1. Si el códec AAC está marcado como experimental, las conversiones ffmpeg fallarán. Para evitar esta adición -estricta -2 a los perfiles de video (/etc/dam/video en AEM 6.3 y movido a /libs/settings/dam/video en AEM 6.4)
   >[!NOTE]
   >
   > Tenga en cuenta que -estricto -2 debe ser el último parámetro en la lista de parámetros. Además, en AEM 6.4, debe copiar los nodos en */libs/settings/dam/video* a */conf/global/settings/dam/video* como se menciona en [Representaciones de video](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Compruebe que se están produciendo conversiones de vídeo y que se están creando representaciones.

## Restricciones de contraseña {#password-restrictions}

La directiva de contraseñas de AEM debe deshabilitarse en la instancia de AMS. Esto se puede configurar de forma alternativa en la consola web mediante el servicio de dispositivo Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte la sección **Restricciones de contraseña** en[Configuración de autor y publicación en AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Configuración de los Entornos {#setting-up-environments}

Instale y ejecute las versiones más recientes de los siguientes paquetes para su versión de Adobe Experience Manager (AEM):

* Paquete de servicio de AEM
* Paquete de funciones para pantallas
* Paquete de correcciones acumulativas de AEM 

Además de lo anterior, identifique los paquetes de desarrollo (por ejemplo, WCM Core
) o juegos de herramientas de terceros (por ejemplo, SAP Hybris) que sean necesarios.
Instale los mismos paquetes de software en sus entornos de desarrollo locales. Indique a su cliente que adopte la misma configuración en todos sus servidores de control de calidad, fase y producción. Las configuraciones de servidor no coincidentes generarán problemas al implementar y probar.

>[!NOTE]
>
>Para instalar el paquete de funciones más reciente para AEM Screens, consulte [Notas de la versión](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Configuración de ACL {#setting-up-acls}

La configuración de las ACL explica cómo segregar proyectos para que cada individuo o equipo gestione su propio proyecto.

Consulte [Configuración de ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) para obtener más detalles.
