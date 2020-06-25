---
title: Red móvil directa
description: La página describe la configuración de red móvil directa
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---


# Red móvil directa {#mobile-network-setup}

AEM Screens Los reproductores también pueden conectarse a través de redes móviles o móviles que se ejecutan al menos en una red 3G.

Dentro de los AEM Screens, el contenido requerido se descarga físicamente al controlador del reproductor o al equipo y se almacena correctamente dentro del sistema operativo subyacente. Por lo tanto, el ancho de banda determinado solo afecta a los tiempos de descarga iniciales y no influye en el rendimiento de los monitores.

La ventaja de la conexión de los reproductores AEM Screens con una conexión Cellular 3/4/5G a su proveedor de datos de servicio móvil es que el router móvil se puede colocar en un punto optimizado para garantizar la mejor cobertura de red disponible. Generalmente se encuentra en una posición elevada y abierta, con la mejor construcción de hormigón o metal que sea posible.

Este SetUp permite a los usuarios de pantalla de AEM una buena flexibilidad, ya que no se requiere una conexión fija para conectarse a AEM Screens.

El siguiente diagrama muestra la configuración de red móvil directa y consta de un segmento de conexión de red único y la conexión de cada reproductor a la red de datos móviles o móviles.

![](/help/using/assets/direct-mobile-1.png)

## Conexión de AEM Screens Player a una red móvil directa {#connecting-aem-screens-players}

Siga los pasos que se describen a continuación para garantizar la conexión adecuada de los reproductores de pantalla de AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla de AEM está conectado a la red de routers.

1. Pruebe la conexión a Internet llamando a una dirección URL en el navegador del sistema.

   >[!NOTE]
   >En caso de que reciba un mensaje de error, compruebe la configuración de la red y la comprobación cruzada si hay un vínculo de red suficiente y el servidor de seguridad del sistema operativo está configurado para permitir el acceso a la red mediante los puertos de comunicación de AEM Screens configurados.

1. Si la llamada mediante URL se realiza correctamente, puede continuar instalando los AEM Screens y registrándose. AEM Screens de Inicio.

## Requisitos para configurar la configuración de la red móvil {#requirements-direct}

La configuración de red se puede separar lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, proporciona un ancho de banda suficiente para que los AEM Screens funcionen sin problemas.

En Red móvil directa, cada reproductor está conectado con una tarjeta de datos móvil única a la red de datos del proveedor.

La siguiente tabla resalta las redes de datos con su ancho de banda estándar:

| Red de datos | Ancho de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Al considerar qué red de datos debe utilizarse, se recomienda responder a las siguientes preguntas:

La velocidad de red disponible depende del plan específico del proveedor de datos móviles y de la cobertura disponible que se alcanza en la ubicación del controlador de AEM Screens.
Al seguir esta configuración, también hay que tener en cuenta que además del ancho de banda disponible, algunos planes del proveedor de datos móviles limitan la cantidad disponible de datos que se encuentran en la conexión dentro de un período de tiempo específico. Hay que garantizar que haya suficiente capacidad en cantidad de datos y ancho de banda.
Como seguimiento, el Paquete de datos necesario debe ser al menos:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Para la carga inicial de archivos multimedia, por ejemplo, mientras se integran nuevos reproductores, se debe esperar una mayor cantidad de datos y un mayor tiempo de descarga, que se reflejarán en los supuestos anteriores.Una red 4G con *buena* cobertura y datos *ilimitados* debe coincidir con las instalaciones más comunes de esta configuración de red.

>[!NOTE]
>Un plan 3G mínimo con una buena cobertura de red debería llevar a un rendimiento de descarga aceptable para un reproductor de AEM Screens. Si sólo hay una cobertura justa disponible en una ubicación específica, debe tener en cuenta el cambio de la configuración de red general a la red [móvil con enrutador de datos móvil y componentes](/help/using/mobile-network-router.md)de red activos.


### Red de área local {#lan-connection}

El rendimiento de la Red de área local (LAN), además de la accesibilidad de la red, es proporcionar un ancho de banda suficiente para operar AEM Screens sin problemas. La red LAN suele coincidir con una red de 100 Mbps, por lo que hay suficiente ancho de banda para conectar muchos dispositivos con un buen rendimiento al sistema.

Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red. Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet o enrutador.

## Descarga de medios y recursos {#download}

Los AEM Screens ofrecen una gran ventaja a los usuarios de publicidad dinámica. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo que se muestra en una pantalla específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día: oferta una operación cercana a una red independiente, una vez que todos los archivos se hayan guardado en el reproductor.

En situaciones en las que hay más interacciones con sensores o activadores y contenido dinámico, es esencial una conexión de red rápida y fiable para una reacción inmediata a la pantalla a fin de garantizar la mejor experiencia posible para el cliente.

La siguiente tabla proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>Toda la información se refiere al consumo de cada dispositivo de la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes suman y extienden el tiempo de descarga.

![](/help/using/assets/download-times-mobile.png)



