---
title: Red móvil con enrutador de datos móvil y componentes de red activos
description: La página describe la red móvil con el enrutador de datos móvil y los componentes de red activos
translation-type: tm+mt
source-git-commit: d12de8de2b7bb29d85ebb0e046f2d1fd5051e928
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---


# Red móvil con enrutador de datos móvil y componentes de red activos {#mobile-network-setup}

Los reproductores de AEM Screens de Adobe también pueden conectarse mediante redes móviles o móviles que ejecuten al menos una red 3G.

Dentro de los AEM Screens, el contenido requerido se descarga físicamente al controlador del reproductor o al equipo y se almacena correctamente dentro del sistema operativo subyacente. Por lo tanto, el ancho de banda dado solo afecta a los tiempos de descarga iniciales y no influye en el rendimiento de los sistemas de visualización.

La ventaja de esta configuración es que el router móvil se puede colocar en un punto optimizado para garantizar la mejor cobertura de red disponible. Normalmente se encuentra en una posición elevada y abierta con la menor construcción de hormigón o metal que sea posible.
Este SetUp permite a los usuarios de la pantalla de AEM flexibilidad, ya que no se requiere una línea fija para conectarse a los AEM Screens.

El siguiente diagrama muestra la configuración de la red móvil con el enrutador de datos móvil y los componentes de red activos y contiene un acceso a Internet de cualquiera de los controladores de AEM Screens mediante el acceso directo a Internet mediante un vínculo de datos 3/4/5 G propio.

![](/help/using/assets/mobile-network-1.png)

## Conexión del Reproductor de AEM Screens a la red móvil con el enrutador de datos móvil y los componentes de red activos {#connecting-aem-screens-players}

Siga los pasos que se describen a continuación para garantizar la conexión adecuada de los reproductores de pantalla de AEM en esta configuración:

La configuración contiene un acceso a Internet de cualquiera de los AEM Screens Controladores por acceso directo a Internet usando su propio enlace de datos 3/4/5G.

1. Asegúrese de que el enrutador de datos móvil está correctamente conectado a la red de datos móviles, como se indica en el sistema operativo, y que cada uno de los reproductores de pantalla de AEM está conectado a la red de enrutadores.
1. Pruebe la conexión a Internet llamando a una dirección URL en el navegador del sistema.
   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de la red.Existen básicamente dos opciones para una conexión de red correcta:
   >* DHCP
   >* Configuración manual de IP


1. Asegúrese de que la configuración del adaptador de red coincide con la configuración del router.

1. Compruebe si el router está correctamente conectado a la red de área amplia ISP (enlace de Internet). También se puede identificar mediante un LED de señal en los routers estándar.
1. Si la llamada mediante URL se realiza correctamente, puede continuar instalando los AEM Screens y registrándose. AEM Screens de Inicio.

   >[!NOTE]
   >**Sugerencia para la resolución de problemas**
   >Si los AEM Screens no se conectan correctamente y no se muestra el contenido esperado:
   >
   >1. Compruebe el servidor de seguridad del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.



## Configuración de la red móvil con el enrutador de datos móvil y los componentes de red activos {#requirements-direct}

La configuración de red se puede separar lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red ya descrita, proporciona un ancho de banda suficiente para operar AEM Screens sin problemas y con buen gusto.

*Suficiente* depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes Wi-Fi de invitados.
Tenga en cuenta que todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y que el ancho de banda suele disminuir linealmente mientras se agregan más consumidores/equipos a la red.
Además de la conexión de red teórica específica que debe garantizarse, que la cobertura del router móvil es al menos &quot;buena&quot;. Además, el plan mensual subyacente tiene que cubrir suficiente capacidad de datos y ancho de banda suficiente para atender a todos los clientes conectados dentro de la LAN conectada.

La siguiente tabla resalta las redes de datos con su ancho de banda estándar:

| Red de datos | Ancho de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Al considerar qué red de datos debe utilizarse, se recomienda responder a las siguientes preguntas:

* ¿Cuántos clientes están conectados al router?

* ¿Cuántos cambios de contenido se esperan y cuáles son los tamaños de archivo promedio?

>[!NOTE]
>El Paquete de datos necesario debe ser al menos:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Para la carga inicial de archivos multimedia, por ejemplo, mientras se integran nuevos reproductores, se debe esperar una mayor cantidad de datos y un mayor tiempo de descarga, que se reflejarán en los supuestos anteriores. Una red 4G con *buena* cobertura y datos ilimitados debe coincidir con las instalaciones más comunes de esta configuración de red.


### Red de área local {#lan-connection}

El rendimiento de la LAN, además de la accesibilidad de la red ya descrita, ofrece un ancho de banda suficiente para operar AEM Screens sin problemas y sin problemas. En estos días, la red LAN suele coincidir al menos con una red de 100 Mbps, por lo que debe haber suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema. Al utilizar otro componente de red activo, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red.

Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet/enrutador.

En caso de que se prevea una solución Wi-Fi para conectar la pantalla a Internet Link, se recomienda utilizar como mínimo estándares Wi-Fi modernos como IEEE 802.11g. Este estándar admite conexiones de hasta 54 Mbps. Cualquier norma *más reciente* como 802.11h-n es de mejor calidad. Si se requiere un repetidor Wi-Fi, recomendamos encarecidamente las tecnologías de punto de acceso Wi-Fi de malla como Google Nest Mesh Wi-Fi o similar.

## Descarga de medios y recursos {#download}

Los AEM Screens ofrecen una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeo. Debido a este concepto, el tráfico de red principal se produce en caso de que haya contenido nuevo para mostrarse en una pantalla específica.
Para el funcionamiento normal, por ejemplo, si se ha definido una lista de reproducción que no se actualiza con frecuencia durante el día, se oferta una operación cercana a la red independiente, una vez que todos los archivos se hayan guardado en el reproductor.
Para aquellos casos de uso en los que hay más interacciones con Sensores u otros Triggers y el contenido es muy dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata a fin de garantizar la mejor experiencia posible para el cliente.
Las siguientes tablas oferta una buena visión general de lo que significan los datos clave de conectividad de red para el rendimiento que se puede esperar y los posibles tiempos de espera.

>[!NOTE]
>Toda la información se refiere al consumo de cada dispositivo de la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y extienden el tiempo de descarga.

![](/help/using/assets/mobile-router-download.png)



