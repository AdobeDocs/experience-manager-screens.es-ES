---
title: Aspectos básicos de la señalización digital para [!UICONTROL AEM Screens]
seo-title: Aspectos básicos de la señalización digital para [!UICONTROL AEM Screens]
description: La guía describe los conceptos básicos de un proyecto de señalización digital
seo-description: La guía describe los conceptos básicos de un proyecto de señalización digital
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 2%

---


# Aspectos básicos de un proyecto de señalización digital {#basics-digital-signage}

Antes de sumergirse en las prácticas recomendadas de implementación de AEM Screens, es importante considerar el proyecto como un proyecto de señalización digital, en lugar de como un desarrollo de software tradicional.

En esta sección se ofrecen recomendaciones sobre los principales elementos clave que son esenciales antes de la implementación de un proyecto de AEM Screens.

## Elementos clave en la señalización digital {#key-elements}

Los *elementos clave* de un proyecto de señalización digital son:

![](/help/assets/Elements-Revised.png)

La definición de los elementos clave es esencial antes de implementar un proyecto de señalización digital:

1. **Hardware**

   El hardware define qué componentes de hardware son ideales para la implementación de su proyecto de señalización digital:
   * ¿Tiene el dispositivo suficiente espacio de almacenamiento para ejecutar todas las variaciones de las experiencias sin conexión?
   * ¿Hemos permitido el tipo y longitud del cable de vídeo? ¿Admite el dispositivo las dos resoluciones deseadas (HD, FullHD, 4K, etc.) y códecs de vídeo que planeo implementar (h.264, h.265, etc.)
   * Uso del alambre físico de cobre
   * Tamaño de las pantallas
   * Número de pantallas
      * orientation
      * proporción de aspecto
      * preferencia de resolución

1. **Conectividad**

   La conectividad hace hincapié en las siguientes preguntas:
   * ¿Conectado en red (celda o wi-fi) o independiente?
      * ¿necesitamos permitir actualizaciones de contenido USB?
      * ¿necesitamos permitir la recopilación de datos de uso?

1. **Instalación**

   La instalación incluye:
   * Muestra: horizontal o vertical
   * ¿Cómo se montará la pantalla?
      * Vertical frente a horizontal
      * Vivienda completa
      * Tapa
   * Compatibilidad con correcciones
   * Personal: responsable de instalar el equipo y conectarlo a la red
   * ¿A qué distancia está la fuente de alimentación de la instalación?
   * ¿A qué distancia está el panel físico del dispositivo real?

1. **Contenido**

   El contenido incluye:
   * ¿Zona única o Zona múltiple?
      * ¿Cuántos recursos de medios hay en la pantalla al mismo tiempo?
      * ¿Cuántas páginas para aplicaciones interactivas?
      * Definición del bucle de interfaz de usuario
      * ¿Contenido impulsado por datos?
   * Control de versión

1. **Interactivo**

   Interactivo incluye:
   * ¿Tipo de pantalla táctil preferido? (resistivo, capacitivo, multitáctil)?
      * Pulsación de botón
      * Gesto
   * ¿Activación de datos (E/S)?
      * Envío/recepción de comandos seriales (cierre de contacto, PLC, etc.)
      * Los datos entrantes se muestran en la pantalla (RSS) o en el contenido de déclencheur
      * RFID/NFC/Bluetooth/iBeacon
      * Servicios externos (clima, tráfico)

1. **creación**

   El entorno enfatiza en:
   * Ubicación de visualización?
      * Dentro vs. Fuera
      * Fuera de alcance o directamente expuesto
   * Requisito temporal especial?
   * ¿Prueba de vandal?
   * ¿Alta luz ambiental? ¿Fuertes contrastes?

1. **Mantenimiento**

   El mantenimiento enfatiza en:

   * ¿Se requieren guías detalladas de instalación o guías del usuario?
   * ¿Configuramos (programamos) el dispositivo antes del envío?
   * ¿Es necesario capturar cada número de serie con fines de seguimiento?
   * ¿Existen requisitos de alimentación de reserva (fuente de alimentación ininterrumpida)?
   * ¿Cómo se implementan las actualizaciones del sistema? ¿Y cómo se supervisan los dispositivos de forma remota? ¿Se requiere una solución MDM?
