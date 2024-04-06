---
title: Aspectos básicos de la publicidad dinámica para [!UICONTROL AEM Screens]
description: Conozca los conceptos básicos de un proyecto de señalización digital.
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Aspectos básicos de un proyecto de señalización digital {#basics-digital-signage}

Antes de sumergirse en las prácticas recomendadas de implementación de AEM Screens, es importante pensar en el proyecto como un proyecto de señalización digital, en lugar de como un desarrollo de software tradicional.

Esta sección contiene recomendaciones sobre los principales elementos clave que son esenciales antes de la implementación de un proyecto de AEM Screens.

## Elementos clave en la señalización digital {#key-elements}

El *Elementos clave* en un proyecto de señalización digital son:

![](/help/assets/Elements-Revised.png)

La definición de los elementos clave es esencial antes de implementar un proyecto de señalización digital:

1. **Hardware**

   Hardware define qué componentes de hardware son ideales para la implementación de proyectos de señalización digital:
   * ¿Tiene el dispositivo espacio de almacenamiento suficiente para ejecutar todas las variaciones de las experiencias sin conexión?
   * ¿Ha permitido el tipo y la longitud del cable de vídeo? ¿Y el dispositivo admite ambas resoluciones deseadas (HD, FullHD, `4K`, etc.) y códecs de vídeo que planeo implementar (h.264, h.265, etc.)
   * Uso de alambre de cobre físico
   * Tamaño de las pantallas
   * Número de pantallas
      * Orientación
      * proporción de aspecto
      * preferencia de resolución

1. **Conectividad**

   La conectividad enfatiza en las siguientes preguntas:
   * ¿Conectado en red (móvil o wi-fi) o independiente?
      * ¿Debe permitir actualizaciones de contenido USB?
      * ¿Debe permitir la recopilación de datos de uso?

1. **Instalación**

   La instalación incluye:
   * Muestra: horizontal o vertical
   * ¿Cómo se monta la pantalla?
      * Vertical frente a horizontal
      * Vivienda completa
      * Placa de cubierta
   * Compatibilidad con sujeciones
   * Personal: responsable de instalar el equipo y conectarlo a la red
   * ¿A qué distancia está la fuente de energía del accesorio?
   * ¿A qué distancia está el panel físico del dispositivo real?

1. **Contenido**

   El contenido incluye:
   * ¿Zona única o zona múltiple?
      * ¿Cuántos recursos de medios hay en pantalla al mismo tiempo?
      * ¿Cuántas páginas hay para las aplicaciones interactivas?
      * Definición del bucle de IU
      * ¿Contenido basado en datos?
   * Control de versión

1. **Interactivo**

   La comunicación interactiva incluye:
   * ¿Tipo de pantalla táctil preferido (resistiva, capacitiva, multitáctil)?
      * Pulsación de botón
      * Gesto
   * Activación de datos (E/S)
      * Envío/recepción de comandos en serie (cierre de contactos, PLC, etc.)
      * Los datos entrantes aparecen en la pantalla (RSS) o en el contenido de los déclencheur
      * RFID/NFC/Bluetooth/iBeacon
      * Servicios externos (tiempo, tráfico)

1. **Entorno**

   Environment hace hincapié en:
   * ¿Mostrar ubicación?
      * Interior frente a exterior
      * Fuera del alcance o directamente expuesto
   * ¿Necesidad de temperatura especial?
   * ¿A prueba de vándalos?
   * ¿Alta luz ambiental? ¿Contrastes fuertes?

1. **Mantenimiento**

   El mantenimiento hace hincapié en:

   * ¿Se requieren las guías de instalación y las guías del usuario?
   * ¿Está configurando (programando) el dispositivo antes del envío?
   * ¿Debe capturar cada número de serie con fines de seguimiento?
   * ¿Hay alguna necesidad de alimentación de reserva (fuente de alimentación ininterrumpida)?
   * ¿Cómo se implementan las actualizaciones del sistema? ¿Y cómo se monitorizan los dispositivos de forma remota? ¿Se requiere una solución de MDM?
