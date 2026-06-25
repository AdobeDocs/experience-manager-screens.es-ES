---
title: Registro automático de reproductores
description: Sigue esta página para obtener más información sobre el registro automático de reproductores con AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
TQID: https://experienceleague.adobe.com/uvCRS49L6CQbah4AKFwRdhGN-pvKnTWtNMN8CnFojIQ
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 388
ht-degree: 0%

---

# Registro automático de reproductores {#auto-registration}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

El registro masivo de miles de jugadores manualmente puede ser engorroso y añade tiempo y costo. Para simplificar este proceso, la función de registro masivo le permite especificar una clave previamente compartida en AEM que se puede aprovisionar en un reproductor mediante un archivo de configuración o una solución de administración de dispositivos móviles (MDM).

## Implementación del registro automático de reproductores {#bulk-registering-implementation}

Siga los pasos a continuación para implementar el registro automático de reproductores:

1. Inicie sesión en la instancia de AEM, haga clic en el proyecto de AEM Screens y, a continuación, haga clic en **Propiedades** en la barra de acciones.
1. Haga clic en la ficha **Avanzado** para poder ver la sección **Registro de dispositivo**.

1. Especifique un código de registro automático en el campo **Código de registro en bloque**. A continuación, una pantalla predeterminada opcional en la **asignación de pantalla predeterminada** para asignar al reproductor que se ha registrado automáticamente.

   >[!NOTE]
   >Introduzca un código de su elección y haga clic en una pantalla predeterminada si es necesario.

   ![imagen](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Proporcione a los reproductores la URL del servidor y el código de registro adecuados mediante un archivo MDM o JSON de configuración.

   >[!NOTE]
   >Consulte la página de implementación del reproductor específico de su sistema operativo (SO) para obtener más información. También puede utilizar la IU de administración para introducir el código de registro.

1. Si el atributo `registrationKey` coincide con el configurado en AEM, el reproductor se registra automáticamente y, si se configura una pantalla predeterminada, ese contenido se descarga y se reproduce.

   ![imagen](/help/user-guide/assets/auto-registration/auto-register2.png)

## Prácticas recomendadas de seguridad {#security-best-practices}

En la sección siguiente se describen algunas de las prácticas recomendadas para la seguridad:

* Asegúrese de que el código de registro no esté en peligro: configure el código en AEM justo antes de iniciar el registro masivo y, cuando haya terminado, borre ese campo y guarde en AEM.

* Puede configurar la ruta de acceso `/bin/screens/registration` para que sólo sea accesible desde intervalos de IP conocidos, si es posible.

* Considere la posibilidad de utilizar un MDM para aprovisionar el reproductor con la configuración.

* Use siempre `HTTPS` y no `HTTP` para la comunicación del reproductor con AEM.

  >[!NOTE]
  >En este momento, la asignación de visualización predeterminada solo funciona para el registro masivo. No funciona para el registro manual cuando un código de registro no está disponible.
