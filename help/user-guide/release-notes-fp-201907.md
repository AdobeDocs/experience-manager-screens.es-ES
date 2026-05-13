---
title: Notas de la versión del paquete de funciones 201907
description: Obtenga información acerca del paquete de funciones 201907 de AEM Screens lanzado el 31 de julio de 2019.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
TQID: https://experienceleague.adobe.com/fbTrzAj52dW2JuRe-6InIkh-dT52Au9pGgoAEjR7WW8
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 378
ht-degree: 2%

---

# Notas de la versión del paquete de funciones 201907 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>Adobe recomienda actualizar a la última versión de Adobe Experience Manager (AEM). AEM Screens proporciona compatibilidad de mantenimiento para la plataforma Screens de AEM 6.3.

AEM Screens ha lanzado el paquete de funciones 5 de AEM 6.4.5 y el paquete de funciones 1 de AEM 6.5.1 con los siguientes detalles.

## Fecha de lanzamiento {#release-date}

La fecha de lanzamiento del paquete de funciones 201907 de AEM Screens es el 31 de julio de 2019.

### Novedades {#what-s-new}

* **El Déclencheur de datos genera cambios de recursos en un canal de AEM Screens**

El reproductor cambia a un canal que muestra información de emergencia. El sistema de emergencia envía esta información cuando recibe un evento. El canal se reproduce exclusivamente hasta que termine la situación de emergencia.


Consulte el caso de uso [Canal de emergencia](emergency-channel.md) para la implementación.

* **Segmentación habilitada para componentes asincrónicos

Ahora se puede habilitar la segmentación para los recursos utilizados en el proyecto de AEM Screens.

Para obtener más información sobre cómo habilitar el direccionamiento para los recursos en el proyecto de AEM Screens, consulte [Configuración de ContextHub en AEM Screens](configuring-context-hub.md).

Después de configurar ContextHub para el proyecto de AEM Screens, siga diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

**[Activación objetivo de inventario comercial](retail-inventory-activation.md)**

**[Activación de temperatura en el centro de viajes](local-temperature-activation.md)**

**[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**

* **Mejoras en los controladores de actualizaciones**

El controlador de actualización ahora analiza los fragmentos de experiencia y recopila cualquier imagen, vídeo o producto asociado a él.

* **Lanzamientos**

Los lanzamientos permiten a los autores de contenido crear versiones futuras de los canales. Con la ayuda de Lanzamientos, los autores pueden obtener una vista previa de cada canal del lanzamiento y deben poder iniciar una solicitud de revisión. El grupo de aprobadores recibe una notificación y puede aprobar o rechazar la solicitud. Cuando se llega a la fecha de lanzamiento, el contenido se reproduce en los dispositivos.
Consulte [Lanzamientos](launches.md) para obtener más información.

* **Configuraciones sin conexión en fragmentos de experiencias**

Ahora puede agregar configuraciones sin conexión (bibliotecas del lado del cliente y archivos estáticos) al configurar el Fragmento de experiencia de Screens. Consulte [Uso de fragmentos de experiencias](experience-fragments-in-screens.md) para obtener más información.

### Reproductores de AEM Screens publicados

Los siguientes reproductores de AEM Screens están disponibles para el paquete de funciones 5 de AEM 6.4.5 y el paquete de funciones 1 de AEM 6.5.1:

* ChromeOS
* Windows
* Android™

#### Descargas del reproductor AEM Screens

Para descargar el Reproductor de AEM Screens más reciente y obtener más información sobre las correcciones de errores, consulte [Descargas del Reproductor de AEM Screens](https://download.macromedia.com/screens/).
