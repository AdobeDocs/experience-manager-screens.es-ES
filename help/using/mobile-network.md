---
title: Red móvil directa
description: La página describe la configuración de Direct Mobile Network
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Red móvil directa {#mobile-network-setup}

Los reproductores AEM Screens también pueden conectarse mediante redes móviles o celulares que ejecuten al menos una red 3G.

En AEM Screens, el contenido necesario se descarga físicamente en el controlador del reproductor o en el equipo y se almacena correctamente en el sistema operativo subyacente. Por lo tanto, el ancho de banda dado solo afecta a los tiempos de descarga iniciales, así como a las actualizaciones de contenido, y no influye en el rendimiento de la reproducción regular de pantallas.

La ventaja de conectar AEM Screens Players over Cellular 3/4/5G a su proveedor de datos de servicio móvil es que el router móvil se puede colocar en un lugar optimizado para garantizar la mejor cobertura de red disponible. Esto suele ser en una posición elevada y abierta con la menor construcción de hormigón o metal que sea posible.

AEM Esta configuración permite a los usuarios de pantalla de la pantalla de la red una buena flexibilidad, ya que no se requiere conexión de línea fija para conectarse a AEM Screens. Esto es especialmente interesante para configuraciones efímeras o móviles.

El diagrama siguiente muestra la configuración de la red móvil directa y consta de un segmento de conexión de red único y la conexión de cada reproductor a la red de datos móviles o móviles.

![](/help/using/assets/direct-mobile-1.png)

## Conexión del Reproductor de AEM Screens a la red móvil directa {#connecting-aem-screens-players}

AEM Siga los pasos a continuación para asegurarse de que la conexión de los reproductores de pantalla de la pantalla de la es correcta en esta configuración:

1. AEM Asegúrese de que cada uno de los reproductores de pantalla de la pantalla está conectado a la red del enrutador.

1. Pruebe la conexión a Internet llamando a una dirección URL en el explorador de sistemas.

   >[!NOTE]
   >Si aparece un mensaje de error, compruebe la configuración de red y verifique si hay un vínculo de red suficiente y si el cortafuegos del sistema operativo está configurado para permitir el acceso a la red mediante los puertos de comunicación de AEM Screens configurados.

1. Si la llamada URL se realiza correctamente, puede continuar instalando AEM Screens y registrarse. Inicie AEM Screens.

## Configuración de una red móvil directa {#requirements-direct}

La configuración de red se puede separar lógicamente en dos bloques:

* Conexión a Internet móvil

* Red de área local

### Conexión a Internet móvil {#mobile-internet-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, proporciona suficiente ancho de banda para utilizar AEM Screens sin problemas.

En Direct Mobile Network, cada reproductor está conectado con una única tarjeta de datos móvil a la red de datos de los proveedores.

En la tabla siguiente se destacan las redes de datos con su ancho de banda estándar:

| Red de datos | Ancho de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | De 1000 a 10000 Mbps |

Al considerar qué red de datos debe utilizarse, se recomienda responder a las siguientes preguntas:

La velocidad de red disponible depende del plan específico del proveedor de datos móviles y de la cobertura disponible que se alcance en la ubicación del controlador de AEM Screens.
Si bien se sigue esta configuración, también se debe tener en cuenta que, además del ancho de banda disponible, algunos planes del proveedor de datos móviles limitan la cantidad de datos disponibles que llegan a través de la conexión en un período de tiempo específico. Debe garantizarse que haya suficiente capacidad en cantidad de datos y ancho de banda.
Como seguimiento, el paquete de datos necesario debe ser al menos de:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Para la carga inicial de archivos multimedia, por ejemplo, al integrar nuevos reproductores, se debe esperar una mayor cantidad de datos y un mayor tiempo de descarga, lo que se refleja en las suposiciones anteriores. Una red 4G con *bueno* cobertura y *ilimitado* Los datos deben coincidir con las instalaciones más comunes de esta Configuración de red.

>[!NOTE]
>Un plan 3G mínimo con una buena cobertura de red debería permitir un rendimiento de descarga aceptable para un reproductor de AEM Screens. Si solo hay una cobertura justa disponible en una ubicación específica, se debe tener en cuenta cambiar la configuración general de la red a [Red móvil con el enrutador de datos móvil y componentes de red activos](/help/using/mobile-network-router.md).


### Red de área local {#lan-connection}

El objetivo del rendimiento de la red de área local (LAN), además de la accesibilidad de la red, es proporcionar suficiente ancho de banda para que AEM Screens funcione sin problemas. La recomendación para las velocidades de red LAN es comenzar al menos en redes de 100 Mbps, de manera que haya suficiente ancho de banda para conectar muchos dispositivos con buen rendimiento al sistema.

Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red. Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por el acceso a Internet o la especificación del enrutador. De lo contrario, el ancho de banda total estará limitado por el eslabón más débil de la cadena de red.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de señalización digital. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo para mostrar en una visualización específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día, ofrece una operación cercana a la red independiente, una vez que todos los archivos se han guardado en el reproductor.

En escenarios donde hay más interacciones con sensores o déclencheur y contenido dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata que garantice la mejor experiencia de cliente posible.

En la tabla siguiente se proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>
>Toda la información se refiere al consumo de cada dispositivo en la red solicitando y descargando una fuente de Internet. Cada una de estas solicitudes añade y amplía el tiempo de descarga.

![](/help/using/assets/download-times-mobile.png)
