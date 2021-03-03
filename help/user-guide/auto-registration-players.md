---
title: Registro automático de reproductores
seo-title: Registro automático de reproductores
description: Siga esta página para obtener más información sobre el registro automático de reproductores con pantallas AMS/On-Prem.
translation-type: tm+mt
source-git-commit: f94eac66b6372e9f3e4cfc28693c4ba61d1b9ab1
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Registro automático de reproductores {#auto-registration}

El registro masivo de miles de jugadores manualmente puede volverse muy complicado y añade tiempo y costo. Para simplificar este proceso, la función de registro masivo le permite especificar una clave previamente compartida en AEM que se puede aprovisionar en un reproductor a través de un archivo de configuración o una solución de administración de dispositivos móviles (MDM).

## Implementación del registro automático de reproductores {#bulk-registering-implementation}

Siga los pasos a continuación para implementar el registro automático de reproductores:

1. Inicie sesión en la instancia de AEM, seleccione el proyecto de AEM screens y haga clic en las propiedades y en la pestaña Avanzadas .
1. Debería ver una sección de registro masivo en la que puede especificar un código de registro masivo y una pantalla predeterminada opcional para asignarlo al reproductor que se registró por lotes
1. Introduzca un código de su elección y seleccione una pantalla predeterminada si es necesario
1. Proporcione a sus reproductores la URL del servidor y el código de registro adecuados mediante un MDM o un archivo JSON de configuración. Consulte la página de implementación del reproductor específico de su sistema operativo para obtener detalles exactos. También puede utilizar la IU de administrador para introducir el código de registro.
1. Si el atributo `registrationKey` coincide con el configurado en AEM, el reproductor se registrará automáticamente y si se configura una visualización predeterminada, el contenido se descargará y reproducirá.

## Prácticas recomendadas de seguridad {#security-best-practices}

Siga esta sección para considerar algunas de las prácticas recomendadas de seguridad:

* Para garantizar que el código de registro no se vea comprometido, configure el código en AEM justo antes de iniciar el registro masivo y, cuando termine, borre ese campo y guárdelo en AEM.

* Se puede configurar que la ruta de registro `/bin/screens/`solo se puede acceder desde rangos de IP conocidos si es posible.

* Considere utilizar un MDM para aprovisionar el reproductor con la configuración .

* Utilice siempre `HTTPS` y no `HTTP` para la comunicación del reproductor con AEM.

   >[!NOTE]
   >Actualmente, la asignación de visualización predeterminada solo funciona para el registro masivo y no para el registro manual sin un código de registro.