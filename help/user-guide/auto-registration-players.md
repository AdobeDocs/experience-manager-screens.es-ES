---
title: Registro automático de reproductores
description: Siga esta página para poder obtener más información sobre el registro automático de reproductores con pantallas AMS/On-Prem.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Registro automático de reproductores {#auto-registration}

El registro masivo de miles de jugadores manualmente puede ser engorroso y añade tiempo y costo. AEM Para simplificar este proceso, la función de registro masivo le permite especificar una clave previamente compartida en la que se puede aprovisionar en un reproductor mediante un archivo de configuración o una solución de administración de dispositivos móviles (MDM).

## Implementación del registro automático de reproductores {#bulk-registering-implementation}

Siga los pasos a continuación para implementar el registro automático de reproductores:

1. AEM Inicie sesión en la instancia de, haga clic en el proyecto de AEM Screens y en **Propiedades** de la barra de acciones.
1. Haga clic en **Avanzadas** para poder ver la pestaña **Registro de dispositivos** sección.

1. Especifique un código de registro automático en la **Código de registro en bloque** field. A continuación, una visualización predeterminada opcional en la variable **Asignación de visualización predeterminada** para asignar al reproductor que se ha registrado automáticamente.

   >[!NOTE]
   >Introduzca un código de su elección y haga clic en una pantalla predeterminada si es necesario.

   ![imagen](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Proporcione a los reproductores la URL del servidor y el código de registro adecuados mediante un archivo MDM o JSON de configuración.

   >[!NOTE]
   >Consulte la página de implementación del reproductor específico de su sistema operativo (SO) para obtener más información. También puede utilizar la IU de administración para introducir el código de registro.

1. Si la variable `registrationKey` AEM coincide con el configurado en, el reproductor se registra automáticamente y, si se configura una visualización predeterminada, ese contenido se descarga y se reproduce.

   ![imagen](/help/user-guide/assets/auto-registration/auto-register2.png)

## Prácticas recomendadas de seguridad {#security-best-practices}

En la sección siguiente se describen algunas de las prácticas recomendadas para la seguridad:

* AEM AEM Asegúrese de que el código de registro no esté en peligro: configure el código en la configuración de justo antes de iniciar el registro masivo y, cuando haya terminado, borre ese campo y guarde los cambios en la configuración de la aplicación. Haga clic en.

* Puede configurar la ruta `/bin/screens/registration` de modo que solo sea accesible desde intervalos de IP conocidos, si es posible.

* Considere la posibilidad de utilizar un MDM para aprovisionar el reproductor con la configuración.

* Usar siempre `HTTPS` y no `HTTP` AEM para que el reproductor se comunique con el.

  >[!NOTE]
  >En este momento, la asignación de visualización predeterminada solo funciona para el registro masivo. No funciona para el registro manual cuando un código de registro no está disponible.
