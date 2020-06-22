---
title: Acceso directo a Internet
description: Acceso directo a Internet
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Acceso directo a Internet {#direct-internet-access}

La Configuración de acceso directo a Internet contiene un punto de acceso de entrada para el acceso a Internet a fin de llegar a los AEM cloud services a los que los AEM Screens deben conectarse.

Las comunicaciones estándar de puertos para AEM Screens son:
* `http (TCP Port 80)`
O bien,
* `ssl-secured https (TCP Port 443)`

Los puertos pueden variar debido a la configuración de la configuración dedicada de AEM. Dentro de este SetUp, todos los dispositivos están conectados directamente a su router de Internet como se muestra en la figura a continuación.

![](/help/assets/direct-access-2.png)

La configuración también incluye un acceso a Internet por parte de cualquier Proveedor de servicio de Internet (ISP) y su línea de Internet. La mayoría de los ISP proporcionan un router de Internet que abarca el módem de Internet, el conmutador de red, el punto de acceso WIFI, el cortafuegos y otras funcionalidades de red (según el fabricante y el modelo).

>[!NOTE]
>**Sugerencia para la resolución de problemas **>Si los AEM Screens no se conectan correctamente y muestran el contenido esperado:
>
>1. Compruebe el servidor de seguridad del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
>1. Asegúrese de que todos los puertos necesarios están permitidos e inténtelo de nuevo.


## Requisitos para configurar la red de acceso directo {#requirements-direct}

La configuración de red de acceso directo puede separarse lógicamente en dos bloques. Bloque de conexión WAN/exterior/Internet y red LAN/área local interna.

### Conexión WAN/Internet {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de red ya descrita, proporciona un ancho de banda suficiente para operar AEM Screens sin problemas y sin problemas. En detalle, &quot;suficiente&quot; depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes WIFI invitadas.
Tenga en cuenta que todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y que el ancho de banda suele disminuir linealmente mientras se agregan más consumidores/equipos a la red.

### Conexión LAN {#lan-connection}

El rendimiento de la LAN, además de la accesibilidad de la red ya descrita, ofrece un ancho de banda suficiente para operar AEM Screens sin problemas y sin problemas. En estos días, la red LAN suele coincidir al menos con una red de 100 MBit/seg, por lo que debe haber suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema.
En caso de que se prevea una solución WIFI para conectar la pantalla a Internet Link, se recomienda utilizar como mínimo estándares WIFI modernos como IEEE 802.11g. Este estándar admite conexiones de hasta 54 Mbit. Cualquier norma *más reciente* como 802.11h-n es de mejor calidad. Si se requiere un Repetidor WIFI, recomendamos encarecidamente las tecnologías de punto de acceso WIFI Mesh como Google Nest Mesh WIFI o similar.
Otras tecnologías de repetición WiFi acaban en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

Los AEM Screens ofrecen una gran ventaja a los usuarios de publicidad dinámica. Está descargando y guardando localmente todos los archivos multimedia necesarios, como imágenes y vídeos. Debido a este concepto, el tráfico de red principal se produce en caso de que haya contenido nuevo para mostrarse en una pantalla específica.
Para una operación normal, por ejemplo, si se ha definido una lista de reproducción que no cambia muy a menudo durante el día, se oferta una operación cercana a la independiente de la red, una vez que todos los archivos se han guardado en el reproductor.
Para aquellos casos de uso en los que hay más interacciones con sensores u otros activadores y el contenido es muy dinámico, una conexión de red rápida y confiable es esencial para una reacción inmediata a la pantalla a fin de garantizar la mejor experiencia posible del cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red:

![](/help/assets/download-times-direct.png)

>[!NOTE]
>La información le permite vista del consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Así que cada una de esas solicitudes suman y extienden el tiempo de descarga.