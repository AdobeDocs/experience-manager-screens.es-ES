---
title: Red corporativa incluida
description: Red corporativa incluida
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Red corporativa cerrada (inalámbrica/cableada) {#enclosed-corporate-networks}

La configuración de red corporativa cerrada es aplicable a empresas más pequeñas, grandes y empresariales. Teóricamente puede ser más complejo y la configuración lógica se muestra en la figura siguiente.

![](/help/using/assets/enclosed-network-1.png)


## Conexión de AEM Screens Player a Direct Internet Access {#connecting-aem-screens-players}

Siga los pasos a continuación para garantizar la conexión adecuada de los reproductores de pantalla AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla AEM esté conectado a la red de enrutadores.
1. Pruebe la conexión a Internet llamando a una dirección URL en el explorador del sistema.

   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de la red. Básicamente hay dos opciones para una conexión de red adecuada:
   >* DHCP
   >* Configuración IP manual


1. Asegúrese de que la configuración del adaptador de red coincide con la configuración del enrutador y compruebe si no se alcanza la cantidad máxima de direcciones IP disponibles en la red.

1. Compruebe si el router está correctamente conectado a la red de área amplia del ISP (enlace de Internet). Esto también se puede identificar utilizando un LED de señal en los routers estándar.
1. Si la llamada a la URL se realiza correctamente, puede continuar instalando AEM Screens y registrarse. Inicie AEM Screens.

   >[!NOTE]
   >**Sugerencia de resolución de problemas**
   >Si AEM Screens no se conecta correctamente y el contenido esperado no se muestra:
   >
   >1. Compruebe en el firewall del router de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
   >1. Asegúrese de que todos los puertos necesarios estén permitidos.


## Configuración de redes corporativas incluidas {#requirements-enclosed-networks}

La configuración de red corporativa adjunta puede separarse lógicamente en dos bloques:

* Red de área amplia (WAN)
* Red de área local interna (LAN).

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, debe proporcionar un ancho de banda suficiente para operar las actualizaciones de contenido de AEM Screens sin problemas.
*El* ancho de banda suficiente depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes Wi-Fi invitadas.

>[!NOTE]
>
>Todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente cuando se agregan más consumidores o equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la red de área local (LAN), además de la accesibilidad de la red, debe proporcionar un ancho de banda suficiente para operar las actualizaciones de contenido de AEM Screens sin problemas.

La red LAN dentro de las organizaciones corporativas es por lo general de al menos 1000 MBit/seg de red, por lo que hay suficiente ancho de banda para conectar muchos dispositivos con buen rendimiento al sistema. Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red.

Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso/enrutador a Internet.

### Otros detalles de redes corporativas {#other-networks}

Las redes corporativas tienen varios dispositivos conectados, están separados en varias subredes y tienen conexiones a Internet redundantes o multiplexadas para proporcionar un rendimiento suficiente para miles de accesos simultáneos.
Este esquema se simplifica y se adapta a la mayoría de los casos a los entornos disponibles para el cliente.

Si se prevé una solución Wi-Fi para conectar Screens al Internet Link, se recomienda utilizar estándares Wi-Fi modernos como mínimo `IEEE 802.11g`. Este estándar admite conexiones de hasta 54 Mbps. Cualquier *más reciente* estándar como `802.11h-n` es de mejor calidad. Si se requiere un repetidor Wi-Fi, recomendamos encarecidamente Mesh Wi-Fi tecnologías de puntos de acceso como Google Nest Mesh Wi-Fi o similares.
Otras tecnologías de repetición Wi-Fi terminan en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo que mostrar en una pantalla específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día ofrece una operación casi independiente de la red, una vez que todos los archivos se han guardado en el reproductor.

En los escenarios en los que hay más interacciones con sensores o déclencheur y contenido dinámico, es esencial una conexión de red rápida y fiable para una reacción inmediata en la pantalla a fin de garantizar la mejor experiencia del cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>La información le permite ver el consumo de cada dispositivo de la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y amplían el tiempo de descarga.

![](/help/using/assets/enclosed-network-download.png)
