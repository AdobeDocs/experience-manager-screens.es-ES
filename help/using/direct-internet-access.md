---
title: Acceso directo a Internet
description: Acceso directo a Internet
translation-type: tm+mt
source-git-commit: 70dddffd46ebf1bd83b25515be548bc442e45fea
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---


# Acceso directo a Internet {#direct-internet-access}

El SetUp de Direct Internet Access contiene un punto de acceso de entrada para el acceso a Internet a fin de llegar a los AEM cloud services a los que los AEM Screens deben conectarse.

Las comunicaciones estándar de puertos para AEM Screens son:
* `http (TCP Port 80)`
O bien,
* `ssl-secured https (TCP Port 443)`

Los puertos pueden variar debido a la configuración de la configuración dedicada de AEM. Dentro de este SetUp, todos los dispositivos están conectados directamente a su router de Internet como se muestra en la figura a continuación.

![](/help/assets/direct-access-2.png)

La configuración también incluye un acceso a Internet por parte de cualquier Proveedor de servicio de Internet (ISP) y su línea de Internet. La mayoría de los ISP proporcionan un router de Internet que abarca el módem de Internet, el conmutador de red, el punto de acceso WIFI, el cortafuegos y otras funcionalidades de red (según el fabricante y el modelo).

## Conexión de AEM Screens Player a Direct Internet Access {#connecting-aem-screens-players}

Siga los pasos a continuación para conectar los reproductores de pantalla de AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla de AEM está conectado a la red de routers.
1. Pruebe la conexión a Internet llamando a una dirección URL en el navegador del sistema.

   >[!NOTE]
   >Si aparece un mensaje de error, compruebe la configuración de la red.Existen básicamente dos opciones para una conexión de red correcta:
   >* DHCP
   >* Configuración manual de IP


1. Asegúrese de que la configuración del adaptador de red coincide con la configuración del enrutador y compruebe si no se alcanza la cantidad máxima de direcciones IP disponibles en la red.

1. Compruebe si el router está correctamente conectado a la red de área amplia ISP (enlace de Internet). Normalmente, esto también se puede identificar mediante un LED de señal en los routers estándar.
1. Si la llamada mediante URL se realiza correctamente, puede continuar instalando los AEM Screens y registrarlos como corresponda. AEM Screens de Inicio.

   >[!NOTE]
   >**Sugerencia para la resolución de problemas**
   >Si los AEM Screens no se conectan correctamente y no muestran el contenido esperado:
   >
   >1. Compruebe el servidor de seguridad del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
   >1. Asegúrese de que todos los puertos necesarios están permitidos.


## Requisitos para configurar la red de acceso directo {#requirements-direct}

La configuración de red de acceso directo puede separarse lógicamente en dos bloques:

* Red de área amplia

* Red de área local

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, es proporcionar un ancho de banda suficiente para operar AEM Screens agradables y suaves.

*Suficiente* depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes WIFI invitadas.

>[!NOTE]
>Todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y el ancho de banda suele disminuir linealmente cuando se agregan más consumidores/equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la Red de área local (LAN), además de la accesibilidad de la red, proporciona un ancho de banda suficiente para operar AEM Screens sin problemas.

La red LAN suele coincidir al menos con una red de 100 MBit/seg, por lo que hay suficiente ancho de banda para conectar muchos dispositivos con buen rendimiento al sistema.
En caso de que se prevea una solución WIFI para conectar AEM Screens a Internet Link, se recomienda utilizar como mínimo estándares WIFI modernos como IEEE 802.11g. Este estándar admite conexiones de hasta 54 Mbps. Cualquier norma *más reciente* como 802.11h-n es de mejor calidad.

>[!NOTE]
>Si se requiere un Repetidor WIFI, recomendamos encarecidamente las tecnologías de punto de acceso WIFI Mesh como Google Nest Mesh WIFI o similar. Otras tecnologías de repetición WiFi acaban en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

Los AEM Screens ofrecen una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. Debido a este concepto, el tráfico de red principal se produce cuando hay contenido nuevo que se muestra en una pantalla específica.
Para una operación normal, por ejemplo, si se ha definido una lista de reproducción que no cambia muy a menudo durante el día, se oferta una operación cercana a la independiente de la red, una vez que todos los archivos se han guardado en el reproductor.
Para aquellos casos de uso en los que hay más interacciones con sensores u otros activadores y el contenido es muy dinámico, una conexión de red rápida y confiable es esencial para una reacción inmediata a la pantalla a fin de garantizar la mejor experiencia posible del cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>La información le permite vista del consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y extienden el tiempo de descarga.

![](/help/assets/download-times-direct.png)

