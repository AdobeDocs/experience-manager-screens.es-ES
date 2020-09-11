---
title: Introducción a [!UICONTROL AEM Screens]
seo-title: Guía de prácticas recomendadas para proyectos de [!UICONTROL AEM Screens]
description: Esta página es una sección introductoria de AEM Screens
seo-description: Esta página ofrece una introducción a AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 83%

---


# Introducción a AEM Screens {#introduction}

**AEM Pantallas** (Adobe Experience Manager) es una solución de publicidad dinámica que le permite crear, publicar y reproducir experiencias digitales dinámicas e interactivas que incluyen distintos tipos de pantallas de visualización en el lugar, de manera concertada con una estrategia de marketing digital integral de canal.

AEM Screens le permite crear:

* **tableros de menús digitales específicos**
* **recomendaciones de productos**
* **imágenes que incluyan representaciones de estilo de vida de fondo**

Además, Screens proporciona muchos recursos únicos para clientes y empleados en función de su área de trabajo, como por ejemplo:

* **visualizaciones interactivas**
* **creación de sistemas de información destinados a orientar a los usuarios**
* **promoción de la marca**
* **adición de un plus de ambiente a su entorno**

La creación y gestión de una red de señalización digital mediante AEM Screens es sencilla e intuitiva. Una aplicación de reproducción aloja los canales de contenido creados por clientes o socios de implementación para AEM Screens. Las *ubicaciones* administran una jerarquía de ubicaciones predefinida y contienen pantallas. Cada *pantalla* tiene un panel que muestra diferentes dispositivos y pantallas. El contenido de AEM Screens se administra en *canales*. El *reproductor de AEM Screens* procesa el contenido presente en los canales y lo muestra en pantallas.



>[!NOTE]
>
>Para obtener información detallada sobre las distintas funciones presentes en el desarrollo y gestión de un proyecto de AEM Screens, consulte la **[Guía del usuario de AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)**.

## AEM Sites y AEM Screens {#aem-sites-screens}

>[!NOTE]
>
>Si su equipo de implementación tiene experiencia trabajando con aplicaciones de AEM Sites, es importante comprender la diferencia entre AEM Sites y AEM Screens.

AEM Screens proporciona una plataforma unificada de creación y reproducción para implementar contenido en dispositivos de señalización digital en espacios públicos. Si bien el autor de la experiencia debería esforzarse por mantener la coherencia en la web y en los canales &quot;in-situ&quot;, hay algunas diferencias que se deberían señalar.

* **Tiempo de permanencia**: normalmente, las páginas web están diseñadas para proporcionar una gran cantidad de información que se puede consumir durante un período de tiempo relativamente más largo. Por el contrario, las experiencias digitales &quot;in-situ&quot; deben anticipar las necesidades del usuario y proporcionar indicaciones claras y concisas sobre cómo y por qué este debería interactuar con la pantalla. Esto da como resultado experiencias más específicas, depuradas y contextuales.

* **Distancia de visualización**: normalmente, los usuarios tienen que distanciarse más que cuando visualizan un sitio web. Como resultado, el tamaño del texto debería ser, por norma general, mayor. Además, el espaciado entre el texto, las imágenes y otro contenido complementario debería someterse a pruebas en función del tamaño de pantalla previsto y la ubicación en el espacio físico.

* **Persistencia**: no se debe permitir que el estado de la conexión del dispositivo de reproducción influya en la experiencia digital del usuario. El reproductor debe diseñarse para que esta experiencia sea estable y pueda mostrarse siempre, independientemente del estado de conexión del dispositivo de reproducción.

* **Segmentación de bucles de medios**: configurar cada dispositivo de reproducción para que tenga su propio segmento de bucle garantiza que el contenido localizado se pueda crear, publicar y reproducir fácilmente dentro de la experiencia digital global. Los activos de medios incluidos en los canales de secuencias incrustadas se agregan al segmento de bucle anterior y ofrecen la oportunidad de segmentar un segmento de bucle de medios para cada grupo de ubicaciones.

* **Experiencias interactivas**: se puede crear y publicar una aplicación táctil y de quiosco en un canal de Screens con AEM y el editor de SPA. Se recomienda aplicar propiedades de diseño de omni-canal coherentes, un temporizador de inactividad para restablecer la experiencia y una clara llamada a acción para las tareas que la aplicación puede ejecutar. La página de destino debe constar de elementos digitales clave diseñados para transmitir valor, atraer al usuario a la pantalla y pedirle que interactúe con esta.

AEM Screens proporciona un marco para implementar contenido en dispositivos físicos. El contenido se asigna a los canales en Screens, que pueden contener contenido multimedia o aplicaciones de pantalla táctil. Dentro de este marco, una aplicación de AEM Sites podría entregarse como contenido a través de un Canal.

Antes de colocarse en un Canal en Pantallas, se debe dar formato a un AEM Sites para que se pueda utilizar en las dimensiones del dispositivo de visualización para el que está destinado.

>[!NOTE]
>Muchos componentes de AEM Sites no son compatibles con AEM Screens. AEM Screens incluye muchos de sus propios componentes de forma predeterminada, lo que le permite crear experiencias digitales sin necesidad de recurrir a la personalización. Si los requisitos del proyecto lo permiten, utilice la funcionalidad integrada de AEM Screens siempre que sea posible.
