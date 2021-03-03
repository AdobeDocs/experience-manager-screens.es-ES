---
title: Uso de MDM o EMM para aprovisionar de forma masiva Android Player
seo-title: Aprovisionamiento masivo de Android Player mediante EMM o MDM
description: Siga esta página para obtener más información sobre el aprovisionamiento masivo de Reproductor de Android mediante EMM o MDM
translation-type: tm+mt
source-git-commit: f94eac66b6372e9f3e4cfc28693c4ba61d1b9ab1
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Aprovisionamiento masivo de Android Player mediante Enterprise Mobility Management {#bulk-provisioning}

Al implementar el reproductor de Android de forma masiva, resulta tedioso registrar manualmente cada reproductor con AEM. Es muy recomendable utilizar una solución EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron o Samsung Knox para aprovisionar y administrar su implementación de forma remota. El reproductor Android de AEM Screens es compatible con la configuración de la aplicación EMM estándar del sector para permitir el aprovisionamiento remoto. Siga los siguientes pasos para aprovisionar sus reproductores de forma masiva.

## Implementación del aprovisionamiento masivo de Android Player mediante Enterprise Mobility Management {#implementation}

Siga los pasos a continuación para permitir el aprovisionamiento masivo en Android Player:

1. Asegúrese de que su dispositivo Android sea compatible con los servicios de Google Play.
1. Inscríbase sus dispositivos de reproductor Android con su solución EMM favorita compatible con Appconfig.
1. Inicie sesión en la consola de EMM y extraiga la aplicación del reproductor AEM Screens de Google Play.
1. Seleccione la configuración administrada (u opción relacionada).
1. Ahora debería ver una lista de las opciones del reproductor que se pueden configurar (como servidor y código de registro masivo).
1. Configure estos parámetros y guarde e implemente la directiva en los dispositivos.

   >[!NOTE]
   >Los dispositivos deben recibir la aplicación junto con la configuración y apuntar al servidor AEM correcto con la configuración seleccionada. Si decide configurar el código de registro masivo y lo mantiene igual que configurado en AEM, el reproductor debe poder registrarse automáticamente. Si ha configurado una visualización predeterminada, también puede descargar y mostrar algún contenido predeterminado (que se puede cambiar posteriormente según sea conveniente).

Además, debe consultar al proveedor de EMM acerca de la compatibilidad con AppConfig . Los más populares, como [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) y [Samsung Knox&lt;a> 11/> admiten este estándar del sector.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)


