---
title: Red móvil con enrutador de datos móvil y componentes de red activa
description: La página describe la red móvil con el enrutador de datos móvil y los componentes de red activa
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---


# Red móvil con enrutador de datos móvil y componentes de red activa {#mobile-network-setup}

Los reproductores AEM Screens de Adobe también pueden conectarse utilizando redes móviles o móviles que ejecuten al menos una red 3G.

Dentro de AEM Screens, el contenido requerido se descarga físicamente al controlador o equipo del reproductor y se almacena correctamente dentro del sistema operativo subyacente. Por lo tanto, el ancho de banda dado solo afecta a los tiempos de descarga inicial, así como a las actualizaciones de contenido, y no influye en el rendimiento de la reproducción regular de las pantallas.

La ventaja de esta configuración es que el router móvil puede colocarse en un punto optimizado para garantizar la mejor cobertura de red disponible. Normalmente se encuentra en una posición elevada y abierta, con la menor cantidad posible de construcciones de hormigón o metal alrededor.
Esta configuración permite a los usuarios de Pantalla AEM flexibilidad, ya que no se requiere ninguna línea fija para conectarse a AEM Screens. Esto es particularmente interesante para configuraciones efímeras o móviles.

El diagrama siguiente muestra la configuración de la red móvil con el enrutador de datos móvil y los componentes de red activa y contiene el acceso a Internet de cualquiera de los controladores de AEM Screens mediante el acceso directo a Internet mediante un vínculo de datos 3/4/5G propio.

![](/help/using/assets/mobile-network-1.png)

## Conexión del reproductor AEM Screens a la red móvil con el enrutador de datos móvil y los componentes de red activa {#connecting-aem-screens-players}

Siga los pasos a continuación para garantizar la conexión adecuada de los reproductores de pantalla AEM en esta configuración:

La configuración asigna un acceso a Internet para cada controlador de AEM Screens mediante el acceso directo a Internet mediante un vínculo de datos 3/4/5G específico.

1. Asegúrese de que el enrutador de datos móvil esté correctamente conectado a la red de datos móviles, tal como se indica en el sistema operativo, y que cada uno de los reproductores de pantalla AEM esté conectado a la red de enrutadores.
1. Pruebe la conexión a Internet llamando a una dirección URL en el explorador del sistema.
   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de la red. Básicamente hay dos opciones para una conexión de red adecuada:
   >* DHCP
   >* Configuración IP manual


1. Asegúrese de que la configuración del adaptador de red coincida con la configuración del router.

1. Compruebe si el router está correctamente conectado a la red de área amplia del ISP (enlace de Internet). Esto también se puede identificar utilizando un LED de señal en los routers estándar.
1. Si la llamada a la URL se realiza correctamente, puede continuar instalando AEM Screens y registrarse. Inicie AEM Screens.

   >[!NOTE]
   >**Sugerencia de resolución de problemas**
   >Si AEM Screens no se conecta correctamente y el contenido esperado no se muestra, compruebe en el cortafuegos del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.


## Configuración de la red móvil con el enrutador de datos móvil y los componentes de red activa {#requirements-direct}

La configuración de red puede separarse lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de red ya descrita, debe proporcionar un ancho de banda suficiente para realizar descargas de contenido de AEM Screens sin problemas.

** Suficiente depende de la cantidad de dispositivos de pantallas de AEM conectados y del uso de otros consumidores dentro de la red, como Smartphones, tabletas, cajeros, ordenadores o redes Wi-Fi de invitados.
Tenga en cuenta que todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y que el ancho de banda suele estar disminuyendo linealmente mientras se agregan más consumidores/equipos a la red.
Además de la conexión de red teórica específica, debe asegurarse que la cobertura del router móvil sea al menos &quot;buena&quot;. Además, el plan mensual subyacente tiene que cubrir suficiente capacidad de datos y ancho de banda suficiente para atender a todos los clientes conectados dentro de la LAN conectada.

La siguiente tabla resalta las redes de datos con su ancho de banda estándar:

| Red de datos | Ancho de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Al considerar qué red de datos debe usarse, se recomienda responder a las siguientes preguntas:

* ¿Cuántos clientes están conectados al Router?

* ¿Cuántos cambios de contenido se esperan y cuáles son los tamaños de archivo promedio?

>[!NOTE]
>
>El paquete de datos necesario debe ser al menos:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Para la carga inicial de archivos multimedia, por ejemplo, mientras se integran nuevos reproductores, se debe esperar una mayor cantidad de datos y un mayor tiempo de descarga, que se reflejarán en los supuestos anteriores. Una red 4G con *buena* cobertura y datos ilimitados debe coincidir con las instalaciones más comunes de esta configuración de red.


### Red de área local {#lan-connection}

El rendimiento de la LAN, además de la accesibilidad de la red ya descrita, debe proporcionar un ancho de banda suficiente para operar las descargas de contenido de AEM Screens sin problemas. En estos días, la red LAN suele coincidir al menos con una red de 100 Mbps, por lo que debe haber suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema. Mientras se utiliza otro componente de red activo, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red.

Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet/router.

En caso de que se prevea una solución Wi-Fi para conectar la pantalla a Internet Link, se recomienda utilizar como mínimo estándares Wi-Fi modernos como IEEE 802.11g. Este estándar admite conexiones de hasta 54 Mbps. Cualquier *nuevo* estándar como 802.11h-n es de mejor calidad. Si se requiere un repetidor Wi-Fi, recomendamos encarecidamente Mesh Wi-Fi Access-point Technologies como Google Nest Mesh Wi-Fi o similar.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeo. Debido a este concepto, el tráfico de red principal se está produciendo en caso de que haya contenido nuevo para mostrar en una pantalla específica.
Para una operación normal, por ejemplo, si se ha definido una lista de reproducción que no se actualiza con frecuencia durante el día, se ofrece una operación cercana a la red independiente, una vez que todos los archivos se han guardado en el reproductor.
Para aquellos casos de uso en los que hay más interacciones con sensores u otros Déclencheur y el contenido es muy dinámico, es esencial una conexión de red rápida y fiable para una reacción inmediata en la pantalla a fin de garantizar la mejor experiencia posible para el cliente.
Las siguientes tablas ofrecen una buena descripción general de lo que significan los datos clave de conectividad de red para el rendimiento que se puede esperar y los posibles tiempos de espera.

>[!NOTE]
>
>Toda la información se refiere al consumo de cada dispositivo de la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y amplían el tiempo de descarga.

![](/help/using/assets/mobile-router-download.png)
