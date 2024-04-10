---
title: Introducción a [!UICONTROL AEM Screens]
description: Esta página es una sección introductoria de AEM Screens
exl-id: 11781e0b-0aca-4d08-aaad-87a7aaf28c24
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 58%

---

# Introducción a AEM Screens {#introduction}

**AEM Pantallas (Adobe Experience Manager) de** es una solución de señalización digital que le permite crear, publicar y reproducir experiencias digitales dinámicas e interactivas. Implica diferentes tipos de pantallas de visualización &quot;in-situ&quot; de forma conjunta con una estrategia de marketing digital omnicanal completa.

AEM Screens permite crear:

* **tableros de menús digitales específicos**
* **recomendaciones de productos**
* **imágenes que incluyan representaciones de estilo de vida de fondo**

Además, Screens proporciona muchas aplicaciones únicas para clientes y empleados en función del dominio en el que se implementan, como:

* **visualizaciones interactivas**
* **creación de sistemas de información destinados a orientar a los usuarios**
* **promoción de la marca**
* **adición de un plus de ambiente a su entorno**

La creación y gestión de una red de señalización digital mediante AEM Screens es sencilla e intuitiva. Una aplicación de reproducción aloja los canales de contenido creados por clientes o socios de implementación para AEM Screens. *Ubicaciones* administre una jerarquía de ubicaciones predefinida y contenga pantallas. Cada *pantalla* tiene un panel que muestra diferentes dispositivos y pantallas. El contenido de AEM Screens se administra en *canales*. El *reproductor de AEM Screens* procesa el contenido presente en los canales y lo muestra en pantallas.



>[!NOTE]
>
>Para obtener información detallada sobre las distintas funciones de desarrollo y administración de un proyecto de AEM Screens, consulte **[Guía del usuario de AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction)**.

## AEM SITES y AEM SCREENS {#aem-sites-screens}

>[!NOTE]
>
>Si su equipo de implementación tiene experiencia trabajando con aplicaciones de AEM Sites, es importante comprender la diferencia entre AEM Sites y AEM Screens.

AEM Screens proporciona una plataforma unificada de creación y reproducción para implementar contenido en dispositivos de señalización digital en espacios públicos. Si bien el autor de la experiencia debería esforzarse por mantener la coherencia en la web y en los canales &quot;in-situ&quot;, hay algunas diferencias que se deberían señalar.

* **Tiempo de espera**: Normalmente, las páginas web están diseñadas para proporcionar una gran cantidad de información que se puede consumir durante un tiempo relativamente más largo. Por el contrario, las experiencias digitales &quot;in-situ&quot; deben anticipar las necesidades del usuario y proporcionar indicaciones claras y concisas sobre cómo y por qué este debería interactuar con la pantalla. Esto da como resultado experiencias más específicas, depuradas y contextuales.

* **Distancia de visualización**: las distancias de visualización son más largas o más lejos que la distancia de visualización habitual que los usuarios experimentan con un sitio web. Como resultado, el tamaño del texto debería ser, por norma general, mayor. Además, el espaciado entre el texto, las imágenes y otro contenido complementario debería someterse a pruebas en función del tamaño de pantalla previsto y la ubicación en el espacio físico.

* **Persistencia**: no se debe permitir que el estado de la conexión del dispositivo de reproducción influya en la experiencia digital del usuario. El reproductor debe diseñarse para que esta experiencia sea estable y pueda mostrarse siempre, independientemente del estado de conexión del dispositivo de reproducción.

* **Segmentación de bucles de medios**: Configurar cada dispositivo de reproducción para que tenga su propio segmento de bucle garantiza que el contenido localizado se pueda crear, publicar y reproducir fácilmente dentro de la experiencia digital general. Los activos de medios incluidos en los canales de secuencias incrustadas se agregan al segmento de bucle anterior y ofrecen la oportunidad de segmentar un segmento de bucle de medios para cada grupo de ubicaciones.

* **Experiencias interactivas** AEM SPA : se puede crear y enviar una aplicación táctil y de quiosco en un canal de Screens mediante el editor de segmentos de pantalla y el editor de segmentos de pantalla de la aplicación de escritorio de la aplicación de escritorio de. Se recomienda aplicar propiedades de diseño omnicanal coherentes, un temporizador de inactividad para restablecer la experiencia y una llamada a la acción clara para las tareas que la aplicación pueda ejecutar. La página de destino debe constar de elementos digitales clave diseñados para transmitir valor, atraer al usuario a la pantalla y pedirle que interactúe con esta.

AEM Screens proporciona un marco para implementar contenido en dispositivos físicos. El contenido se asigna a los canales en Screens, que pueden contener contenido multimedia o aplicaciones de pantalla táctil. Dentro de este marco, una aplicación de AEM Sites podría entregarse como contenido a través de un canal.

Antes de enviarse a un canal en Screens, se debe dar formato a un sitio de AEM para que su uso se adapte a las dimensiones del dispositivo de visualización para el que está destinado.

>[!NOTE]
>Muchos componentes de AEM Sites no son compatibles con AEM Screens. AEM Screens incluye muchos de sus propios componentes de forma predeterminada, lo que le permite crear experiencias digitales sin necesidad de recurrir a la personalización. Si los requisitos del proyecto lo permiten, utilice la funcionalidad integrada de AEM Screens siempre que sea posible.
