---
title: Red corporativa adjunta
description: Red corporativa adjunta
translation-type: tm+mt
source-git-commit: 31a6b202cae200e43e87db1df4e60f6f9d75c1bf
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Redes corporativas incluidas {#enclosed-corporate-networks}

La configuración de red corporativa adjunta se aplica a las empresas más pequeñas, grandes y empresariales. En teoría, puede ser más complejo, pero la configuración lógica siempre es como se muestra a continuación en un ejemplo simplificado.

## Requisitos para la configuración de redes corporativas cerradas {#requirements-enclosed-networks}

La configuración de red corporativa adjunta puede separarse lógicamente en dos bloques. Bloque de conexión WAN/exterior/Internet y red LAN/área local interna.

### Conexión WAN/Internet {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de red ya descrita, proporciona un ancho de banda suficiente para que las pantallas AEM funcionen correctamente y sin problemas.
En detalle, &quot;suficiente&quot; depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes WIFI invitadas.
Tenga en cuenta que todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y que el ancho de banda suele disminuir de forma lineal a la vez que se agregan más consumidores/equipos a la red.

### Conexión LAN {#lan-connection}

El rendimiento de la LAN, además de la accesibilidad de la red ya descrita, proporciona un ancho de banda suficiente para operar AEM Screens de forma agradable y fluida. En estos días, la red LAN dentro de las organizaciones corporativas suele coincidir al menos con una red de 1000 MBit/seg, por lo que debe haber suficiente ancho de banda para conectar muchos dispositivos con buen rendimiento al sistema. Mientras se utiliza otro componente de red activo, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red. Por ejemplo: los componentes de red deben coincidir al menos con el estándar de 1000 Mbit/s y coincidir con el ancho de banda proporcionado por la especificación de acceso a Internet/router.

### Otros aspectos específicos de las redes corporativas {#other-networks}

Normalmente, las redes corporativas tienen una carga de dispositivos conectados, pueden estar separadas en varias subredes y pueden tener conexiones a Internet redundantes o multiplexadas para proporcionar un rendimiento suficiente para miles de accesos simultáneos.
El esquema anterior se simplifica y se ajusta en la mayoría de los casos al entorno disponible para el cliente.
En caso de que se prevea una solución WiFI para conectar la pantalla a Internet Link, se recomienda utilizar como mínimo estándares WIFI modernos como IEEE 802.11g. Este estándar admite conexiones de hasta 54 Mbit. Cualquier norma &quot;más reciente&quot; como 802.11h-n es de mejor calidad. Si se requiere un repetidor WIFI, recomendamos encarecidamente la tecnología Mesh WIFI Accespoint como Google Nest Mesh WIFI o similar.
Otras tecnologías de repetición WiFi acaban en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de publicidad dinámica. Está descargando y guardando localmente todos los archivos multimedia necesarios, como imágenes y vídeo. Debido a este concepto, el tráfico de red principal se produce en caso de que haya contenido nuevo para mostrarse en una pantalla específica.
Para el funcionamiento normal, por ejemplo, si se ha definido una lista de reproducción que no se cambia muy a menudo durante el día, se oferta una operación cercana a la independiente de la red, una vez que todos los archivos se han guardado en el reproductor. Para aquellos casos de uso en los que hay más interacciones con Sensores u otros Triggers y el contenido es muy dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata a fin de garantizar la mejor experiencia posible para el cliente.

Las siguientes tablas oferta una buena visión general de lo que significan los datos clave de conectividad de red para el rendimiento que se puede esperar y los posibles tiempos de espera.

Toda la información debe considerarse como el consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Así que cada una de esas solicitudes suman y extienden el tiempo de descarga.