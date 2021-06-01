---
title: Acceso directo a Internet
description: Acceso directo a Internet
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Red de Internet directa (inalámbrica/cableada) {#direct-internet-access}

La Red de Internet directa contiene un punto de acceso de entrada para el acceso a Internet a fin de llegar a los servicios de nube de AEM a los que AEM Screens debe conectarse.

Los puertos estándar para la comunicación de AEM Screens son:
* `ssl-secured https (TCP Port 443)`

   <br>O bien,</br>

* `http (TCP Port 80)`, si su caso de uso en particular no requiere ese nivel de seguridad.

Los puertos pueden variar debido a la configuración de la configuración AEM dedicada. Dentro de este SetUp, todos los dispositivos están conectados directamente a su enrutador de Internet como se muestra en la figura siguiente.

![](/help/assets/direct-access-2.png)

La configuración también incluye un acceso a Internet por parte de cualquier proveedor de servicios de Internet (ISP) y su línea de Internet. La mayoría de los ISP proporcionan un router de Internet que cubre el módem de Internet, el conmutador de red, el punto de acceso Wi-Fi, el firewall y otras funcionalidades de red (dependiendo del fabricante y el modelo).

## Conexión de AEM Screens Player a Direct Internet Access {#connecting-aem-screens-players}

Siga los pasos a continuación para garantizar la conexión adecuada de los reproductores de pantalla AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla AEM esté conectado a la red del router.
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


## Configuración de la red de acceso directo {#requirements-direct}

La Red de Internet Directa está lógicamente separada en dos bloques:

* Red de área amplia

* Red de área local

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet además de la accesibilidad de la red es proporcionar suficiente ancho de banda para operar AEM Screens.

** Suficiente depende del número de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes Wi-Fi de invitados.

>[!NOTE]
>
>Todos los dispositivos mencionados anteriormente tienen un acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente cuando se agregan más consumidores o equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la red de área local (LAN), además de la accesibilidad de la red, proporciona suficiente ancho de banda para operar AEM Screens.

La red LAN suele coincidir al menos con una red de 100 Mbps, por lo que hay suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema.
En caso de que se prevea una solución Wi-Fi para conectar AEM Screens a Internet Link, se recomienda utilizar estándares Wi-Fi modernos como mínimo `IEEE 802.11g`. Este estándar admite conexiones de hasta 54 Mbps. Cualquier *más reciente* estándar como `802.11h-n` es de mejor calidad.

>[!NOTE]
>
>Si se requiere un repetidor Wi-Fi, se recomienda un punto de acceso Wi-Fi Mesh como Google Nest Mesh Wi-Fi o similar. Otras tecnologías de repetición Wi-Fi terminan en una pérdida masiva de ancho de banda en toda la red.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo que mostrar en una pantalla específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día ofrece una operación casi independiente de la red, una vez que todos los archivos se han guardado en el reproductor.

En los escenarios en los que hay más interacciones con sensores o déclencheur y contenido dinámico, es esencial una conexión de red rápida y fiable para una reacción inmediata en la pantalla a fin de garantizar la mejor experiencia del cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>
>La información le permite ver el consumo de cada dispositivo de la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y amplían el tiempo de descarga.

![](/help/assets/download-times-direct.png)

