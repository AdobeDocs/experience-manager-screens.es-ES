---
title: Red móvil directa
description: La página describe la configuración de red móvil directa
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---


# Red móvil directa {#mobile-network-setup}

AEM Screens Los reproductores también pueden conectarse mediante redes móviles o móviles que ejecuten al menos una red 3G.

Dentro de los AEM Screens, el contenido requerido se descarga físicamente al controlador del reproductor o al Equipo y se almacena correctamente dentro del sistema operativo subyacente. De este modo, el ancho de banda determinado solo afecta a los tiempos de descarga iniciales y no influye en el rendimiento de los monitores.

Conexión de reproductores de AEM Screens con una conexión móvil 3/4/5G a su proveedor de datos de Mobile Service. La ventaja de esta configuración es que el router móvil se puede colocar en un punto optimizado para garantizar la mejor cobertura de red disponible. Normalmente se encuentra en una posición elevada y abierta con la menor construcción de hormigón o metal que sea posible.

Este SetUp permite a los usuarios de pantalla de AEM una buena flexibilidad, ya que no se requiere una conexión fija para conectar AEM Screens.

![](/help/using/assets/direct-mobile-1.png)

## Conexión de AEM Screens Player a una red móvil directa {#connecting-aem-screens-players}

Siga los pasos a continuación para conectar los reproductores de pantalla de AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla de AEM está conectado a la red de routers.

1. Pruebe la conexión a Internet llamando a una dirección URL en el navegador del sistema.

   >[!NOTE]
   >Si aparece un mensaje de error, compruebe la configuración de la red.Existen básicamente dos opciones para una conexión de red correcta:
   >* DHCP
   >* Configuración manual de IP


1. Asegúrese de que la configuración del adaptador de red coincide con la configuración del router.
1. Compruebe si el router está correctamente conectado a la red de área amplia ISP (enlace de Internet). Normalmente, esto también se puede identificar mediante un LED de señal en los routers estándar.

1. En caso de que la llamada mediante URL se realice correctamente, puede continuar instalando los AEM Screens y registrarlos según corresponda. AEM Screens de Inicio.

   >[!NOTE]
   >**Sugerencia para la resolución de problemas**
   >Si los AEM Screens no se conectan correctamente y no muestran el contenido esperado:
   >
   >1. Compruebe el servidor de seguridad del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
   >1. Asegúrese de que todos los puertos necesarios están permitidos.



## Requisitos para configurar la configuración de la red móvil {#requirements-direct}

La configuración de red se puede separar lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, proporciona un ancho de banda suficiente para que los AEM Screens funcionen bien y sin problemas.

*Suficiente* depende de la cantidad de pantallas de AEM conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes WIFI invitadas.
Tenga en cuenta que todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y que el ancho de banda suele disminuir linealmente mientras se agregan más consumidores/equipos a la red.
Además de la conexión de red teórica específica que debe estar asegurada, que la cobertura del router móvil es al menos &quot;buena&quot; (consulte el Manual del router móvil). Además, el plan mensual subyacente tiene que cubrir suficiente capacidad de datos y ancho de banda suficiente para atender a todos los clientes conectados dentro de la LAN conectada.

Las redes de datos proporcionan ancho de banda estándar con:

**3G**
* 42 Mbps

**4G**
* 150 Mbps

**5G**
* 1000 Mbps-10000 Mbps

Al considerar qué red de datos debe utilizarse, se recomienda responder a las siguientes preguntas:

* ¿Cuántos clientes están conectados al router?

* ¿Cuántos cambios de contenido se esperan y cuáles son los tamaños de archivo promedio?

>[!NOTE]
>El Paquete de datos necesario debe ser al menos:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Asegúrese de que hay suficiente búfer.
>Para la carga inicial de archivos multimedia, por ejemplo, mientras se integran nuevos reproductores, se debe esperar una mayor cantidad de datos y un mayor tiempo de descarga, que se reflejarán en los supuestos anteriores.Una red 4G con *buena* cobertura y datos *ilimitados* debe coincidir con las instalaciones más comunes de esta configuración de red.


### Red de área local {#lan-connection}

El rendimiento de la LAN, además de la accesibilidad de la red ya descrita, ofrece un ancho de banda suficiente para operar AEM Screens sin problemas y sin problemas. En estos días, la red LAN suele coincidir al menos con una red de 100 Mbps, por lo que debe haber suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema. Mientras se utiliza otro componente de red activo, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red. Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet/enrutador.

## Descarga de medios y recursos {#download}

Los AEM Screens ofrecen una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeo. Debido a este concepto, el tráfico de red principal se produce en caso de que haya contenido nuevo para mostrarse en una pantalla específica.
Para una operación normal, por ejemplo, una lista de reproducción definida que no se cambia muy a menudo durante el día, esto oferta una operación cercana a una red independiente, una vez que todos los archivos se han guardado en el reproductor.
Para aquellos casos de uso en los que hay más interacciones con Sensores u otros Triggers y el contenido es muy dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata a fin de garantizar la mejor experiencia posible para el cliente.

La siguiente tabla proporciona una visión general de lo que significan los datos clave de conectividad de red para el rendimiento que se puede esperar y los tiempos de espera potenciales.
>[!NOTE]
>Toda la información se refiere al consumo de cada dispositivo de la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y extienden el tiempo de descarga.

![](/help/using/assets/download-times-mobile.png)



