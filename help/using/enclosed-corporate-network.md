---
title: Red corporativa adjunta
description: Red corporativa adjunta
translation-type: tm+mt
source-git-commit: eaeea4933be708beca0628438e6cef6142a0490f
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---


# Redes corporativas cerradas (cableadas/inalámbricas) {#enclosed-corporate-networks}

La configuración de red corporativa adjunta se aplica a empresas más pequeñas, grandes y empresariales. En teoría, puede ser más complejo y la configuración lógica se muestra en la figura siguiente.

![](/help/using/assets/enclosed-network-1.png)


## Conexión de AEM Screens Player a Direct Internet Access {#connecting-aem-screens-players}

Siga los pasos que se describen a continuación para garantizar la conexión adecuada de los reproductores de pantalla de AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla de AEM está conectado a la red de routers.
1. Pruebe la conexión a Internet llamando a una dirección URL en el navegador del sistema.

   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de la red.Existen básicamente dos opciones para una conexión de red correcta:
   >* DHCP
   >* Configuración manual de IP


1. Asegúrese de que la configuración del adaptador de red coincide con la configuración del enrutador y compruebe si no se alcanza la cantidad máxima de direcciones IP disponibles en la red.

1. Compruebe si el router está correctamente conectado a la red de área amplia ISP (enlace de Internet). Esto también se puede identificar mediante un LED de señal en los routers estándar.
1. Si la llamada mediante URL se realiza correctamente, puede continuar instalando los AEM Screens y registrándose. AEM Screens de Inicio.

   >[!NOTE]
   >**Sugerencia para la resolución de problemas**
   >Si los AEM Screens no se conectan correctamente y no se muestra el contenido esperado:
   >
   >1. Compruebe el servidor de seguridad del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
   >1. Asegúrese de que todos los puertos necesarios están permitidos.


## Requisitos para la configuración de redes corporativas cerradas {#requirements-enclosed-networks}

La configuración de red corporativa adjunta puede separarse lógicamente en dos bloques:

* Red de área amplia (WAN)
* Red de área local interna (LAN).

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, es proporcionar un ancho de banda suficiente para que los AEM Screens funcionen bien y sin problemas.
*El ancho de banda* suficiente depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes de Wi-Fi invitadas.

>[!NOTE]
>Todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente cuando se agregan más consumidores o equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la Red de área local (LAN), además de la accesibilidad de la red, es proporcionar un ancho de banda suficiente para operar AEM Screens sin problemas.

La red LAN dentro de las organizaciones corporativas es generalmente de al menos 1000 MBit/seg., de modo que hay suficiente ancho de banda para conectar muchos dispositivos con buen rendimiento al sistema. Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red.

Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 1000 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet/enrutador.

### Otros aspectos específicos de las redes corporativas {#other-networks}

Las redes corporativas tienen una serie de dispositivos conectados, están separados en varias subredes y tienen conexiones a Internet redundantes o multiplexadas para proporcionar un rendimiento suficiente para miles de accesos simultáneos.
Este esquema se simplifica y se adapta a la mayoría de los casos a los entornos disponibles para el cliente.

En caso de que se prevea una solución Wi-Fi para conectar Pantallas a Internet Link, se recomienda usar como mínimo estándares de Wi-Fi modernos `IEEE 802.11g` . Este estándar admite conexiones de hasta 54 Mbps. Cualquier norma *nueva* como `802.11h-n` es de mejor calidad. Si se requiere un Repetidor Wi-Fi, recomendamos encarecidamente las tecnologías de puntos de acceso Wi-Fi Mesh como Google Nest Mesh Wi-Fi o similar.
Otras tecnologías de repetición Wi-Fi acaban en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

Los AEM Screens ofrecen una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo que se muestra en una pantalla específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día: oferta una operación cercana a una red independiente, una vez que todos los archivos se hayan guardado en el reproductor.

En situaciones en las que hay más interacciones con sensores o activadores y contenido dinámico, es esencial una conexión de red rápida y fiable para una reacción inmediata a la pantalla a fin de garantizar la mejor experiencia posible para el cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>La información le permite vista del consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y extienden el tiempo de descarga.

![](/help/using/assets/enclosed-network-download.png)