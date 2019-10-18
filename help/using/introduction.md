---
title: Introducción a [!UICONTROL AEM Screens]
seo-title: Guía de prácticas recomendadas para proyectos de pantallas [!UICONTROL de] AEM
description: Esta página es una sección introductoria de AEM Screens
seo-description: Esta página ofrece una introducción a AEM Screens
translation-type: tm+mt
source-git-commit: 55999ae9ead7ab8986f4dcb69b0bbaa46933c9ec

---


# Introducción a AEM Screens {#introduction}

**Las pantallas** de AEM (Adobe Experience Manager) son una solución de publicidad dinámica que le permite crear, publicar y reproducir experiencias digitales dinámicas e interactivas que incluyen distintos tipos de pantallas de visualización dentro del recinto, de manera concertada con una estrategia de marketing digital integral de canal.

AEM Screens le permite crear:

* **tableros de menús digitales dedicados**
* **recomendaciones de productos**
* **imágenes de estilo de vida de fondo**

Además, las pantallas proporcionan muchas aplicaciones únicas para clientes y empleados en función del dominio en el que se implementan, como por ejemplo:

* **visualizaciones interactivas**
* **búsqueda de formas**
* **marca**
* **agregar ambiente a su entorno**

La creación y gestión de una red de publicidad dinámica mediante AEM Screens es sencilla e intuitiva. Una aplicación de reproductor aloja los canales de contenido creados para AEM Screens por clientes o socios de implementación. *Las ubicaciones* administran una jerarquía de ubicaciones predefinida y contienen pantallas. Cada *pantalla* tiene un tablero que muestra diferentes dispositivos y pantallas. El contenido de AEM Screens se administra en *canales*. *AEM Screens Player* procesa el contenido presente en los canales en pantallas.



>[!NOTE]
>
>Para obtener información detallada sobre las distintas funciones de un proyecto de AEM Screens, consulte la Guía del usuario de **[AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)**.

## AEM Sites y AEM Screens {#aem-sites-screens}

> [!NOTE]
>
> Si su equipo de implementación tiene experiencia en el trabajo con aplicaciones de AEM Sites, es importante comprender la diferencia entre AEM Sites y AEM Screens.

AEM Screens proporciona una plataforma unificada de creación y reproducción para implementar contenido en dispositivos de publicidad dinámica en espacios públicos. Si bien el autor de la experiencia debería esforzarse por mantener la coherencia en la web y en los canales del lugar de celebración, hay algunas diferencias que cabe señalar.

* **Tiempo de espera**: Normalmente, las páginas Web están diseñadas para proporcionar una gran cantidad de información que se puede consumir durante un período de tiempo relativamente más largo. Por el contrario, las experiencias digitales en el lugar de celebración deben anticipar las necesidades del visor y proporcionar indicaciones claras y concisas sobre cómo y por qué el usuario debe participar. Esto da como resultado experiencias más específicas, depuradas y contextuales.

* **Distancia** de visualización: Las distancias de visualización generalmente son más largas o más lejanas de lo que los usuarios suelen experimentar con un sitio Web. Como resultado, el tamaño del texto debería ser normalmente mayor y el espaciado entre el texto, las imágenes y otro contenido complementario debería probarse en función del tamaño de pantalla previsto y la ubicación en el espacio físico.

* **Persistencia**: Nunca se debe permitir que el estado conectado del dispositivo del reproductor influya en la entrega o no de experiencias digitales al usuario. El reproductor debe diseñarse para que una o varias experiencias siempre persistan y se puedan entregar independientemente del estado conectado del dispositivo del reproductor.

* **Segmentación** de bucle de medios: La configuración de cada dispositivo reproductor para que tenga su propio segmento de bucle garantiza que el contenido localizado se pueda crear, publicar y reproducir fácilmente dentro de la experiencia digital global. Los recursos de medios contenidos en los canales de secuencias incrustadas se agregan al segmento de bucle anterior y ofrecen la oportunidad de segmentar un segmento de bucle de medios para cada grupo de ubicaciones.

* **Experiencias** interactivas: La aplicación táctil se puede crear y distribuir en un canal de pantallas con AEM y el editor de SPA. Se recomienda aplicar propiedades de diseño omnichannel coherentes, un temporizador de inactividad para restablecer la experiencia y una clara llamada a acción para las tareas que la aplicación puede ejecutar. La página de aterrizaje debe constar de elementos digitales clave diseñados para transmitir valor, atraer al usuario a la pantalla y pedirle que interactúe con él.

AEM Screens proporciona un marco para implementar contenido en dispositivos físicos. El contenido se asigna a los canales en pantallas, que pueden contener contenido multimedia o aplicaciones de pantalla táctil. Dentro de este marco, una aplicación de AEM Site podría entregarse como contenido a través de un canal.

Antes de colocarse en un canal en pantallas, se debe dar formato a un sitio de AEM para que se utilice en las dimensiones del dispositivo de visualización para el que está destinado.

> [!NOTE]
>
> Muchos componentes de AEM Sites no son compatibles con AEM Screens. AEM Screens incluye muchos de sus propios componentes integrados que le permiten crear experiencias digitales sin necesidad de personalizarlas. Si los requisitos del proyecto lo permiten, utilice la funcionalidad integrada de AEM Screens siempre que sea posible.
