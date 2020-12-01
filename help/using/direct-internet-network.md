---
title: Acceso directo a Internet
description: Acceso directo a Internet
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Red de Internet directa (cableada/inalámbrica) {#direct-internet-access}

La red de Internet directa contiene un punto de acceso de entrada para el acceso a Internet a fin de llegar a los servicios de nube de AEM a los que AEM Screens debe conectarse.

Los puertos estándar para la comunicación con AEM Screens son:
* `ssl-secured https (TCP Port 443)`

   <br>O bien,</br>

* `http (TCP Port 80)`, si su caso de uso particular no requiere ese nivel de seguridad.

Los puertos pueden variar debido a la configuración de la configuración de AEM dedicada. Dentro de este SetUp, todos los dispositivos están conectados directamente a su router de Internet como se muestra en la figura a continuación.

![](/help/assets/direct-access-2.png)

La configuración también incluye un acceso a Internet por parte de cualquier Proveedor de servicio de Internet (ISP) y su línea de Internet. La mayoría de los ISP proporcionan un router de Internet que abarca el módem de Internet, el conmutador de red, el punto de acceso Wi-Fi, el cortafuegos y otras funciones de red (según el fabricante y el modelo).

## Conexión de AEM Screens Player a Direct Internet Access {#connecting-aem-screens-players}

Siga los pasos a continuación para garantizar la conexión adecuada de los reproductores de pantalla AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla AEM está conectado a la red del router.
1. Pruebe la conexión a Internet llamando a una dirección URL en el navegador del sistema.

   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de la red.Existen básicamente dos opciones para una conexión de red correcta:
   >* DHCP
   >* Configuración manual de IP


1. Asegúrese de que la configuración del adaptador de red coincide con la configuración del enrutador y compruebe si no se alcanza la cantidad máxima de direcciones IP disponibles en la red.

1. Compruebe si el router está correctamente conectado a la red de área amplia ISP (enlace de Internet). Esto también se puede identificar mediante un LED de señal en los routers estándar.
1. Si la llamada mediante URL se realiza correctamente, puede continuar instalando el AEM Screens y registrarse. Inicio AEM Screens.

   >[!NOTE]
   >**Sugerencia para la resolución de problemas**
   >Si AEM Screens no se conecta correctamente y no se muestra el contenido esperado:
   >
   >1. Compruebe el servidor de seguridad del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
   >1. Asegúrese de que todos los puertos necesarios están permitidos.


## Configuración de la red de acceso directo {#requirements-direct}

La Red de Internet Directa está lógicamente separada en dos bloques:

* Red de área amplia

* Red de área local

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, es proporcionar un ancho de banda suficiente para operar AEM Screens.

** Suficiente depende del número de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, computadoras o redes Wi-Fi de invitados.

>[!NOTE]
>
>Todos los dispositivos mencionados anteriormente tienen un acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente cuando se agregan más consumidores o equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la Red de área local (LAN), además de la accesibilidad de la red, proporciona suficiente ancho de banda para operar AEM Screens.

La red LAN suele coincidir al menos con una red de 100 Mbps, por lo que hay suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema.
En caso de que se prevea una solución Wi-Fi para conectar AEM Screens a Internet Link, se recomienda utilizar como mínimo estándares Wi-Fi modernos como `IEEE 802.11g`. Este estándar admite conexiones de hasta 54 Mbps. Cualquier *nuevo* estándar como `802.11h-n` es de mejor calidad.

>[!NOTE]
>
>Si se requiere un repetidor Wi-Fi, se recomienda encarecidamente un punto de acceso Wi-Fi en malla como Google Nest Mesh Wi-Fi o similar. Otras tecnologías de repetición Wi-Fi acaban en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo que se muestra en una pantalla específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día: oferta una operación cercana a una red independiente, una vez que todos los archivos se hayan guardado en el reproductor.

En situaciones en las que hay más interacciones con sensores o activadores y contenido dinámico, es esencial una conexión de red rápida y fiable para una reacción inmediata a la pantalla a fin de garantizar la mejor experiencia posible para el cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>
>La información le permite vista del consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y extienden el tiempo de descarga.

![](/help/assets/download-times-direct.png)

