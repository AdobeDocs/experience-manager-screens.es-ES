---
title: Conceptos básicos de la señalización digital para pantallas [!UICONTROL AEM]
seo-title: Conceptos básicos de la señalización digital para pantallas [!UICONTROL AEM]
description: La guía describe los conceptos básicos de un proyecto de publicidad dinámica
seo-description: La guía describe los conceptos básicos de un proyecto de publicidad dinámica
translation-type: tm+mt
source-git-commit: 30c724ea897fd2da5300bb5cad285d460af5de40

---


# Conceptos básicos de un proyecto de comunicación digital {#basics-digital-signage}

Antes de sumergirse en las optimizaciones de implementación de AEM Screens, es importante considerar el proyecto como un proyecto de publicidad dinámica, en lugar de un desarrollo de software tradicional.

Esta sección proporciona recomendaciones sobre los principales elementos clave que son críticos antes de la implementación de un proyecto de AEM Screens.

## Elementos clave de la publicidad dinámica {#key-elements}

Los elementos *clave* de un proyecto de publicidad dinámica son:

![](/help/assets/Elements-Revised.png)

La definición de los elementos clave es esencial antes de implementar un proyecto de publicidad dinámica:

1. **Hardware**

   El hardware define qué componentes de hardware son ideales para la implementación de proyectos de publicidad dinámica:
   * ¿Dispone el dispositivo de espacio de almacenamiento suficiente para ejecutar todas las variaciones de las experiencias sin conexión?
   * ¿Hemos permitido el tipo y la longitud del cable de vídeo? ¿Admite el dispositivo las dos resoluciones deseadas (HD, FullHD, 4K, etc.)? y los códecs de vídeo que planeo implementar (h.264, h.265, etc.)
   * Uso del alambre físico de cobre
   * Tamaño de las pantallas
   * Número de pantallas
      * orientation
      * proporción de aspecto
      * preferencia de resolución

1. **Conectividad**

   La conectividad hace hincapié en las siguientes preguntas:
   * ¿Conectado en red (móvil o wi-fi) o independiente?
      * ¿Necesitamos permitir actualizaciones de contenido USB?
      * ¿Necesitamos permitir la recopilación de datos de uso?

1. **Instalación**

   La instalación incluye:
   * Muestra: horizontal o vertical
   * ¿Cómo se montará la pantalla?
      * Vertical vs. horizontal
      * Vivienda completa
      * Tapa de la tapa
   * Compatibilidad con correcciones
   * Personal: encargado de instalar el equipo y conectarlo a la red
   * ¿A qué distancia se encuentra la fuente de alimentación del aparato?
   * ¿A qué distancia está el panel físico del dispositivo real?

1. **Contenido**

   El contenido incluye:
   * ¿Zona única o Zona múltiple?
      * ¿Cuántos recursos de medios están en pantalla al mismo tiempo?
      * ¿Cuántas páginas para aplicaciones interactivas?
      * Definición del bucle de interfaz de usuario
      * ¿Contenido gobernado por datos?
   * Control de versión

1. **Interactivo**

   Interactivo incluye:
   * ¿Tipo de pantalla táctil preferido?(resistible, capacitivo, multitáctil)?
      * Pulsación de botón
      * Gesto
   * ¿Activación de datos (E/S)?
      * Envío/recepción de comandos de serie (cierre de contacto, PLC, etc.)
      * Los datos entrantes se muestran en la pantalla (RSS) o activan el contenido
      * RFID/NFC/Bluetooth/iBeacon
      * Servicios externos (tiempo, tráfico, etc.)

1. **creación**

   El entorno enfatiza en:
   * Ubicación de visualización?
      * Interior vs. Exterior
      * Fuera de alcance o directamente expuesto
   * Requisito de tiempo especial?
   * ¿Prueba de Vandal?
   * ¿Luz ambiental alta? ¿Fuertes contrastes?

1. **Mantenimiento**

   El mantenimiento enfatiza en:

   * ¿Se requieren guías de instalación o guías de usuario detalladas?
   * ¿Estamos configurando (programando) el dispositivo antes del envío?
   * ¿Es necesario capturar cada número de serie con fines de seguimiento?
   * ¿Existen requisitos de alimentación de reserva (fuente de alimentación ininterrumpida)?
   * ¿Cómo se implementan las actualizaciones del sistema? ¿Y cómo se monitorean los dispositivos de forma remota? ¿Se requiere una solución MDM?
