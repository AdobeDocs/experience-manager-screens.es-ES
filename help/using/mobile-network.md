---
title: Red móvil directa
description: Obtenga información acerca de la configuración de Direct Mobile Network en AEM Screens.
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Red móvil directa {#mobile-network-setup}

Los reproductores AEM Screens también pueden conectarse mediante redes móviles o celulares que ejecuten al menos una red 3G.

En AEM Screens, el contenido necesario se descarga físicamente en el controlador del reproductor o en el equipo y se almacena correctamente en el sistema operativo subyacente. Por lo tanto, el ancho de banda dado solo afecta a los tiempos de descarga iniciales y a las actualizaciones de contenido, y no influye en el rendimiento de la reproducción normal de las pantallas.

La ventaja de conectar AEM Screens Players over Cellular 3/4/5G a su proveedor de datos de servicio móvil es que el router móvil se puede colocar en un lugar optimizado. Al hacerlo, se asegura la mejor cobertura de red disponible. Esta ubicación suele estar en una posición elevada y abierta con el menor número posible de estructuras de hormigón o metal alrededor.

Esta configuración ofrece a los usuarios de AEM Screen una gran flexibilidad porque no se requiere conexión de línea fija para conectarse a AEM Screens. Este arreglo es interesante para configuraciones efímeras o móviles.

El diagrama siguiente muestra la configuración de Direct Mobile Network. Consiste en un único segmento de conexión de red y la conexión de cada reproductor a la red de datos móviles o celulares.

![](/help/using/assets/direct-mobile-1.png)

## Conexión del Reproductor de AEM Screens a la red móvil directa

Siga los pasos a continuación para garantizar la conexión adecuada de los reproductores de pantalla de AEM en esta configuración:

1. Asegúrese de que cada uno de los reproductores de pantalla de AEM esté conectado a la red del enrutador.

1. Pruebe la conexión a Internet llamando a una dirección URL en el explorador del sistema.

   >[!NOTE]
   >Si aparece un mensaje de error, compruebe la configuración de red y compruebe si hay un vínculo de red suficiente. Compruebe también que el cortafuegos del sistema operativo está configurado para permitir el acceso a la red mientras utiliza los puertos de comunicación de AEM Screens configurados.

1. En caso de que la llamada URL se realice correctamente, puede seguir instalando AEM Screens y registrarse. Inicie AEM Screens.

## Configuración de una red móvil directa {#requirements-direct}

La configuración de red se puede separar lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, proporciona suficiente ancho de banda para utilizar AEM Screens sin problemas.

En Direct Mobile Network, cada Reproductor está conectado con una única tarjeta de datos móvil a la red de datos del proveedor.

En la tabla siguiente se destacan las redes de datos con su ancho de banda estándar:

| Red de datos | Ancho de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | De 1000 a 10000 Mbps |

Al considerar qué red de datos debe utilizarse, tenga en cuenta lo siguiente:

La velocidad de red disponible depende del plan específico del proveedor de datos móviles y de la cobertura disponible que se alcance en la ubicación del controlador de AEM Screens.
Al seguir esta configuración, tenga en cuenta que, además del ancho de banda disponible, algunos planes del proveedor de datos móviles limitan la cantidad de datos disponibles que llegan a través de la conexión en un tiempo específico. Se debe garantizar que haya suficiente capacidad en los datos y en las cantidades de ancho de banda.
A continuación, el paquete de datos necesario debe ser al menos de:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Para la carga inicial de archivos multimedia mientras se integran nuevos reproductores, se debe esperar una mayor cantidad de datos y un mayor tiempo de descarga; esto se refleja en los supuestos anteriores. Una red 4G con *buena* cobertura y *ilimitado* datos debe coincidir con las instalaciones más comunes en esta configuración de red.

>[!NOTE]
>Un plan 3G mínimo con una buena cobertura de red debería llevar a un rendimiento de descarga aceptable para un reproductor AEM Screens. Si sólo hay cobertura razonable disponible en una ubicación específica, considere cambiar la configuración general de red a [Red móvil con enrutador de datos móvil y componentes de red activos](/help/using/mobile-network-router.md).


### Red de área local {#lan-connection}

El objetivo del rendimiento de la red de área local (LAN), además de la accesibilidad de la red, es proporcionar suficiente ancho de banda para que AEM Screens funcione sin problemas. La recomendación para las velocidades de red LAN es comenzar al menos en redes de 100 Mbps, de modo que haya suficiente ancho de banda para conectar al sistema muchos dispositivos con buen rendimiento.

Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red. Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por el acceso a Internet o la especificación del enrutador. De lo contrario, el ancho de banda total está limitado por el eslabón más débil de la cadena de red.

## Descarga de medios y Assets {#download}

AEM Screens ofrece una ventaja significativa a los usuarios de señalización digital. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo para mostrar en una visualización específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día, ofrece una operación cercana a la independiente de la red, una vez que todos los archivos se han guardado en el reproductor.

En escenarios donde hay más interacciones con sensores o déclencheur y contenido dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata que garantice la mejor experiencia de cliente posible.

En la tabla siguiente se proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>
>Toda la información se refiere al consumo de cada dispositivo en la red solicitando y descargando una fuente de Internet. Cada una de estas solicitudes suma y amplía el tiempo de descarga.

![](/help/using/assets/download-times-mobile.png)
