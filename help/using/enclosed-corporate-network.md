---
title: Red corporativa adjunta
description: Red corporativa adjunta
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Red corporativa cerrada (por cable/inalámbrica) {#enclosed-corporate-networks}

La configuración de red corporativa adjunta es aplicable a las empresas más pequeñas, grandes y empresariales. En teoría, puede ser más complejo y la configuración lógica se muestra en la figura siguiente.

![](/help/using/assets/enclosed-network-1.png)


## Conexión del Reproductor de AEM Screens al acceso directo a Internet {#connecting-aem-screens-players}

AEM Siga los pasos a continuación para asegurarse de que la conexión de los reproductores de pantalla de la pantalla de la es correcta en esta configuración:

1. AEM Asegúrese de que cada uno de los reproductores de pantalla de la pantalla está conectado a la red de enrutadores.
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


## Configuración de Redes Corporativas Cerradas {#requirements-enclosed-networks}

La configuración de red corporativa adjunta se puede separar lógicamente en dos bloques:

* Red de área extensa (WAN)
* Red de área local (LAN) interna.

### Red de área amplia {#wan-connection}

El rendimiento de la conexión a Internet, además de la accesibilidad de la red, debe proporcionar suficiente ancho de banda para gestionar las actualizaciones de contenido de AEM Screens sin problemas.
*Ancho de banda suficiente* AEM depende de la cantidad de pantallas conectadas y del uso de otros consumidores dentro de la red, como smartphones, tabletas, cajeros, ordenadores o redes Wi-Fi de invitados.

>[!NOTE]
>
>Todos los dispositivos tienen un acceso simultáneo a la conexión a Internet y el ancho de banda disminuye linealmente cuando se agregan más consumidores o equipos a la red.

### Red de área local {#lan-connection}

El rendimiento de la red de área local (LAN), además de la accesibilidad de la red, debe proporcionar suficiente ancho de banda para que las actualizaciones de contenido de AEM Screens funcionen sin problemas.

La red LAN dentro de las organizaciones corporativas suele ser de al menos 1000 MBit/seg. de red, de modo que haya suficiente ancho de banda para conectar muchos dispositivos con buen rendimiento al sistema. Al utilizar otros componentes de red activos, es obligatorio que todos coincidan con los requisitos de ancho de banda de la red.

Por ejemplo, los componentes de red deben coincidir al menos con el estándar de 100 Mbps y con el ancho de banda proporcionado por la especificación de acceso a Internet/enrutador.

### Características de otras redes corporativas {#other-networks}

Las redes corporativas tienen varios dispositivos conectados, están separadas en varias subredes y tienen conexiones a Internet redundantes o multiplexadas para proporcionar un rendimiento suficiente para muchos miles de accesos simultáneos.
Este esquema se simplifica y se adapta, en la mayoría de los casos, a los entornos disponibles para el cliente.

Si se prevé una solución Wi-Fi para conectar Screens al Internet Link, se recomienda utilizar estándares Wi-Fi modernos como `IEEE 802.11g` como mínimo. Este estándar admite conexiones de hasta 54 Mbps. Cualquiera *más reciente* Estándares como `802.11h-n` son de mejor calidad. Si se requiere un repetidor de Wi-Fi, recomendamos encarecidamente tecnologías de punto de acceso Wi-Fi Mesh como Google Nest Mesh Wi-Fi o similares.
Otras tecnologías de repetición de Wi-Fi terminan en una pérdida masiva de ancho de banda en la red general.

## Descarga de medios y recursos {#download}

AEM Screens ofrece una gran ventaja a los usuarios de señalización digital. Descarga y guarda localmente todos los archivos multimedia necesarios, como imágenes y vídeos. El tráfico de red principal se produce cuando hay contenido nuevo para mostrar en una visualización específica.

Para operaciones normales, por ejemplo, una lista de reproducción definida que se actualiza con frecuencia durante el día, ofrece una operación cercana a la red independiente, una vez que todos los archivos se han guardado en el reproductor.

En escenarios donde hay más interacciones con sensores o déclencheur y contenido dinámico, una conexión de red rápida y confiable es esencial para una reacción de pantalla inmediata que garantice la mejor experiencia de cliente posible.

En la tabla siguiente se proporciona información general sobre los datos clave de conectividad de red.

>[!NOTE]
>La información permite ver el consumo de cada dispositivo en la red que solicita y descarga una fuente de Internet. Cada una de estas solicitudes añade y amplía el tiempo de descarga.

![](/help/using/assets/enclosed-network-download.png)
