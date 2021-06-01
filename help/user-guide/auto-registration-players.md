---
title: Registro automático de reproductores
seo-title: Registro automático de reproductores
description: Siga esta página para obtener más información sobre el registro automático de reproductores con pantallas AMS/On-Prem.
feature: Administración de pantallas, reproductores
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Registro automático de reproductores {#auto-registration}

El registro masivo de miles de jugadores manualmente puede volverse muy complicado y añade tiempo y costo. Para simplificar este proceso, la función de registro masivo le permite especificar una clave previamente compartida en AEM que se puede aprovisionar en un reproductor a través de un archivo de configuración o una solución de administración de dispositivos móviles (MDM).

## Implementación del registro automático de reproductores {#bulk-registering-implementation}

Siga los pasos a continuación para implementar el registro automático de reproductores:

1. Inicie sesión en la instancia de AEM, seleccione el proyecto de pantallas de AEM y haga clic en **Propiedades** en la barra de acciones.
1. Seleccione la pestaña **Advanced** para ver la sección **Device registration** .

1. Especifique un código de registro automático en el campo **Bulk registration code** y una visualización predeterminada opcional en **Default display assign** para asignarlo al reproductor que se registró automáticamente.
   >[!NOTE]
   >Introduzca un código de su elección y seleccione una visualización predeterminada si es necesario.

   ![image](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Proporcione a sus reproductores la URL del servidor y el código de registro adecuados mediante un MDM o un archivo JSON de configuración.

   >[!NOTE]
   >Consulte la página de implementación del reproductor específico de su sistema operativo (OS) para obtener más información. También puede utilizar la IU de administrador para introducir el código de registro.

1. Si el atributo `registrationKey` coincide con el configurado en AEM, el reproductor se registrará automáticamente y si se configura una visualización predeterminada, el contenido se descargará y reproducirá.

   ![image](/help/user-guide/assets/auto-registration/auto-register2.png)

## Prácticas recomendadas de seguridad {#security-best-practices}

Siga esta sección para considerar algunas de las prácticas recomendadas de seguridad:

* Para garantizar que el código de registro no se vea comprometido, configúrelo en AEM justo antes de iniciar el registro masivo y, cuando termine, borre ese campo y guarde en AEM.

* Puede configurar la ruta `/bin/screens/registration` para que solo sea accesible desde intervalos de IP conocidos si es posible.

* Considere utilizar un MDM para aprovisionar el reproductor con la configuración .

* Utilice siempre `HTTPS` y no `HTTP` para la comunicación del reproductor con AEM.

   >[!NOTE]
   >Actualmente, la asignación de visualización predeterminada solo funciona para el registro masivo y no para el registro manual sin un código de registro.