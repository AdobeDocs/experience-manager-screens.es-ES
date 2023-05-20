---
title: Acceso directo a Internet
description: Acceso directo a Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# Red de Internet directa (por cable o inalámbrica) {#direct-internet-access}

La red de Internet directa contiene un punto de acceso de entrada para acceder a Internet a fin de llegar a los servicios de nube de AEM a los que AEM Screens debe conectarse.

Los puertos estándar para la comunicación de AEM Screens son:
* `ssl-secured https (TCP Port 443)`

   <br>O bien,</br>

* `http (TCP Port 80)`, si su caso de uso particular no requiere ese nivel de seguridad.

AEM Los puertos pueden variar debido a la configuración de la configuración de la aplicación de la configuración de la plataforma de datos dedicada. En esta configuración, todos los dispositivos están conectados directamente al enrutador de Internet, como se muestra en la figura siguiente.

![](/help/assets/direct-access-2.png)

La configuración también incluye un acceso a Internet por cualquier proveedor de servicios de Internet (ISP) y su línea de Internet. La mayoría de los ISP proporcionan un enrutador de Internet que cubre el módem de Internet, el conmutador de red, el punto de acceso Wi-Fi, el cortafuegos y otras funcionalidades de red (según el fabricante y el modelo).

## Conexión del Reproductor de AEM Screens al acceso directo a Internet {#connecting-aem-screens-players}

AEM Siga los pasos a continuación para asegurarse de que la conexión de los reproductores de pantalla de la pantalla de la es correcta en esta configuración:

1. AEM Asegúrese de que cada uno de los reproductores de pantalla de la pantalla está conectado a la red del enrutador.
1. Pruebe la conexión a Internet llamando a una dirección URL en el explorador de sistemas.

   >[!NOTE]
   >En caso de que reciba un error, compruebe la configuración de red. Básicamente, hay dos opciones para una conexión de red adecuada:
   >* DHCP
   >* Configuración manual de IP


1. Asegúrese de que la Configuración del adaptador de red no coincide con la Configuración del enrutador y compruebe si no se alcanza la cantidad máxima de direcciones IP disponibles en la red.

1. Compruebe si el enrutador está conectado correctamente a la red de área ancha del ISP (vínculo a Internet). Esto también se puede identificar mediante un LED de señal en los enrutadores estándar.
1. Si la llamada URL se realiza correctamente, puede continuar instalando AEM Screens y registrarse. Inicie AEM Screens.

   >[!NOTE]
   >**Sugerencia de resolución de problemas**
   >Si AEM Screens no se conecta correctamente y no se muestra el contenido esperado:
   >
   >1. Compruebe en el cortafuegos del enrutador de Internet si hay alguna restricción con respecto a `TCP/IP Port 80/443`.
   >1. Asegúrese de que todos los puertos requeridos estén permitidos.


## Configuración de la red de acceso directo {#requirements-direct}

La red Direct Internet está separada lógicamente en dos bloques:

* Red de área amplia

* Red de área local

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, es proporcionar suficiente ancho de banda para utilizar AEM Screens.

*Suficiente* AEM depende del número de pantallas conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes Wi-Fi de invitados.

>[!NOTE]
>
>Todos los dispositivos mencionados tienen acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente cuando se añaden más consumidores o equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la red de área local (LAN), además de la accesibilidad de la red, proporciona suficiente ancho de banda para utilizar AEM Screens.

La red LAN suele coincidir con una red de 100 Mb/s, por lo que hay suficiente ancho de banda para conectar al sistema muchos dispositivos con buen rendimiento.
Si se prevé una solución Wi-Fi para conectar AEM Screens al Internet Link, se recomienda utilizar estándares Wi-Fi modernos como `IEEE 802.11g` como mínimo. Este estándar admite conexiones de hasta 54 Mbps. Cualquiera *más reciente* Estándares como `802.11h-n` son de mejor calidad.

>[!NOTE]
>
>Si se requiere un repetidor de Wi-Fi, se recomienda encarecidamente un punto de acceso Wi-Fi de malla como Google Nest Mesh Wi-Fi o similar. Otras tecnologías de repetición de Wi-Fi terminan en una pérdida masiva de ancho de banda en la red general.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de señalización digital. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo para mostrar en una visualización específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día, ofrece una operación cercana a la red independiente, una vez que todos los archivos se han guardado en el reproductor.

En escenarios donde hay más interacciones con sensores o déclencheur y contenido dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata que garantice la mejor experiencia de cliente posible.

En la tabla siguiente se proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>
>La información permite ver el consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes añade y amplía el tiempo de descarga.

![](/help/assets/download-times-direct.png)
