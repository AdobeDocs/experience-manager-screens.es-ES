---
title: Conceptos básicos de señalización digital para [!UICONTROL AEM Screens]
description: Conozca los conceptos básicos de un proyecto de señalización digital.
exl-id: e3913be2-9028-4773-a034-e16924a71e04
TQID: https://experienceleague.adobe.com/w0fVaYNPs2emLyL377rLTXLZRcXd05B56FtIn3Yjoqg
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 0%

---

# Aspectos básicos de un proyecto de señalización digital {#basics-digital-signage}

Antes de sumergirse en las prácticas recomendadas de implementación de AEM Screens, es importante pensar en el proyecto como un proyecto de señalización digital, en lugar de como un desarrollo de software tradicional.

En esta sección se ofrecen recomendaciones sobre los principales elementos clave esenciales para la implementación de un proyecto de AEM Screens.

## Elementos clave en la señalización digital {#key-elements}

Los *elementos clave* de un proyecto de señalización digital son:

![](/help/assets/Elements-Revised.png)

La definición de los elementos clave es esencial antes de implementar un proyecto de señalización digital:

1. **Hardware**

   Hardware define qué componentes de hardware son ideales para la implementación de proyectos de señalización digital:
   * ¿Tiene el dispositivo espacio de almacenamiento suficiente para ejecutar todas las variaciones de las experiencias sin conexión?
   * ¿Ha permitido el tipo y la longitud del cable de vídeo? ¿Es compatible el dispositivo con las resoluciones deseadas (HD, FullHD, `4K`, etc.) y los códecs de vídeo que planeo implementar (h.264, h.265, etc.)?
   * Uso de alambre de cobre físico
   * Tamaño de las pantallas
   * Número de pantallas
      * Orientación
      * proporción de aspecto
      * preferencia de resolución

1. **Conectividad**

   La conectividad hace hincapié en las siguientes preguntas:
   * ¿Conectado en red (móvil o wi-fi) o independiente?
      * ¿Debe permitir actualizaciones de contenido USB?
      * ¿Debe permitir el uso de la recopilación de datos?

1. **Instalación**

   La instalación incluye:
   * Muestra: horizontal o vertical
   * ¿Cómo se monta la pantalla?
      * Orientación vertical u orientación horizontal
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

   El entorno hace hincapié en:
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
