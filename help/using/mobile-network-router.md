---
title: Red móvil con el enrutador de datos móvil y componentes de red activos
description: La página describe la red móvil con el enrutador de datos móvil y los componentes de red activos
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Red móvil con el enrutador de datos móvil y componentes de red activos {#mobile-network-setup}

Adobe AEM Screens Los reproductores también pueden conectarse mediante redes móviles o celulares que ejecuten al menos una red 3G.

En AEM Screens, el contenido necesario se descarga físicamente en el controlador del reproductor o en el equipo y se almacena correctamente en el sistema operativo subyacente. Por lo tanto, el ancho de banda dado solo afecta a los tiempos de descarga iniciales y a las actualizaciones de contenido, y no influye en el rendimiento de la reproducción regular de las pantallas.

La ventaja de esta configuración es que el router móvil se puede colocar en un lugar optimizado para garantizar la mejor cobertura de red disponible. Este lugar suele estar en una posición elevada y abierta, con el menor número posible de estructuras de hormigón o metal circundantes.
AEM Esta configuración proporciona flexibilidad a los usuarios de pantalla de la pantalla de la pantalla de la pantalla porque no se requiere una línea fija para conectarse a AEM Screens. También es interesante para configuraciones efímeras o móviles.

El diagrama siguiente muestra la configuración de Red móvil con el enrutador de datos móvil y los componentes de red activos. Contiene un acceso a Internet de cualquiera de los controladores AEM Screens mediante acceso directo a Internet mediante un propio enlace de datos 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Conexión del Reproductor de AEM Screens a la red móvil con el enrutador de datos móvil y los componentes de red activos {#connecting-aem-screens-players}

AEM Siga los pasos a continuación para asegurarse de que la conexión de los reproductores de pantalla de la pantalla de la es correcta en esta configuración:

La configuración asigna un acceso a Internet para cada controlador de AEM Screens mediante el acceso directo a Internet mediante un vínculo de datos dedicado 3/4/5G.

1. Asegúrese de que el enrutador de datos móvil está conectado correctamente a la red de datos móviles como se indica en el sistema operativo. AEM Además, asegúrese de que cada uno de los reproductores de pantalla de la pantalla de la red de enrutadores está conectado a la red de la pantalla de la pantalla de la red de la red de la red de la red de la red.
1. Pruebe la conexión a Internet llamando a una dirección URL en el explorador del sistema.

   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de red. Básicamente hay dos opciones para una conexión de red adecuada:
   >* DHCP
   >* Configuración manual de IP

1. Asegúrese de que la configuración del adaptador de red coincida con la configuración del enrutador.

1. Compruebe si el enrutador está conectado correctamente a la red de área ancha (vínculo a Internet) del proveedor de servicios Internet. Puede comprobarlo con un LED de señal en los enrutadores estándar.
1. Si la llamada URL se realiza correctamente, puede continuar instalando AEM Screens y registrarse. Inicie AEM Screens.

   >[!TIP]
   >Es posible que la conexión de AEM Screens no funcione correctamente. No se muestra el contenido esperado. En estos casos, compruebe el firewall del enrutador de Internet si existen restricciones con respecto a `TCP/IP Port 80/443`.


## Configuración de la red móvil con el enrutador de datos móvil y los componentes de red activos {#requirements-direct}

La configuración de red se puede separar lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de red ya descrita, debe proporcionar suficiente ancho de banda para realizar descargas de contenido de AEM Screens sin problemas.

*Suficiente* depende del número de dispositivos AEM Screens conectados. También depende del uso de otros consumidores dentro de la red, como smartphones, tablets, cajeros, computadoras o redes Wi-Fi de invitados.
Tenga en cuenta que todos los dispositivos tienen acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente al tiempo que añade más consumidores/equipos a la red.
Además de la conexión de red teórica específica, debe garantizarse que la cobertura del router móvil sea al menos *bueno*. Además, el plan mensual subyacente tiene que cubrir suficiente capacidad de datos y ancho de banda para servir a todos los clientes conectados dentro de la LAN conectada.

En la tabla siguiente se destacan las redes de datos con su ancho de banda estándar:

| Red de datos | Ancho de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | De 1000 a 10000 Mbps |

A la hora de considerar qué red de datos debe utilizarse, Adobe recomienda responder a las siguientes preguntas:

* ¿Cuántos clientes están conectados al enrutador?
* ¿Cuántos cambios de contenido se esperan y cuáles son los tamaños de archivo promedio?

>[!NOTE]
>
>El paquete de datos necesario debe ser al menos de:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Para la carga inicial de archivos multimedia mientras se integran nuevos reproductores, es necesario esperar una mayor cantidad de datos y un mayor tiempo de descarga. También se refleja en los supuestos anteriores. Una red 4G con *bueno* La cobertura y los datos ilimitados deben coincidir con las instalaciones más comunes de esta Configuración de red.


### Red de área local {#lan-connection}

El rendimiento de la LAN, además de la ya descrita accesibilidad de la red, tiene que proporcionar suficiente ancho de banda para operar las descargas de contenido de AEM Screens sin problemas. En estos días, la red LAN suele coincidir con una red de 100 Mb/s, por lo que debe haber suficiente ancho de banda para conectar al sistema muchos dispositivos con buen rendimiento. Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red.

Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet/enrutador.

Si se prevé una solución Wi-Fi para conectar la pantalla al Internet Link, se recomienda utilizar estándares Wi-Fi modernos como IEEE `802.11g` como mínimo. Este estándar admite conexiones de hasta 54 Mbps. Cualquiera *más reciente* Estándares como `802.11h-n` son de mejor calidad. Si se requiere un repetidor de Wi-Fi, Adobe recomienda tecnologías de punto de acceso Wi-Fi Mesh como Google Nest Mesh Wi-Fi o similares.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una ventaja significativa a los usuarios de señalización digital. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeo. Debido a este concepto, el tráfico de red principal se produce en el caso de que haya contenido nuevo para mostrar en una pantalla específica.
Para un funcionamiento normal, al tener una lista de reproducción definida que no se actualiza con frecuencia, ofrece una operación casi independiente de la red cuando todos los archivos se guardan en el reproductor.
En los casos de uso en los que hay más interacciones con sensores u otros Déclencheur y el contenido es dinámico, una conexión de red rápida y fiable es esencial para una reacción de pantalla inmediata. Garantiza la mejor experiencia del cliente posible.
Las siguientes tablas ofrecen una buena descripción general de lo que significan los datos clave de conectividad de red para el rendimiento que se puede esperar y los tiempos de espera potenciales.

>[!NOTE]
>
>Toda la información se refiere al consumo de cada dispositivo en la red solicitando y descargando una fuente de Internet. Cada una de estas solicitudes suma y amplía el tiempo de descarga.

![](/help/using/assets/mobile-router-download.png)
