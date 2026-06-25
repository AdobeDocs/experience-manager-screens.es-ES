---
title: Administración del tráfico de red
description: La página describe las Configuraciones de red estándar y cómo administrar el tráfico de red.
exl-id: b6d8f4a3-fca2-4556-9455-b9e27b138154
TQID: https://experienceleague.adobe.com/toQExjYycmdyuJ18MzNczjmqjec2SQrXbnz4gxi01Tk
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 532
ht-degree: 0%

---

# Administración del tráfico de red {#managing-network-traffic}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Una configuración de red puede tener varias estructuras. En esta sección se describen las configuraciones de red y los enfoques generalizados más habituales que se siguen dentro de una organización.

En esta guía se destaca la introducción a los servidores proxy, seguida de las diversas estructuras de red configuradas en las distintas organizaciones.

>[!NOTE]
>**Requisitos de red de AEM Screens**
>AEM Screens se comunica directamente con AEM as a Cloud Service, por lo que es necesario establecer una conexión estable entre los dos nodos. Los firewalls son obligatorios para el acceso comercial a Internet. Como cliente, es importante saber qué puertos de comunicación deben abrirse en estos servidores de seguridad y en otros componentes de red relacionados con la seguridad de TI.

## Introducción a los servidores proxy {#proxy-servers}

Una conexión a Internet depende del uso de un servidor proxy. Un servidor proxy es un equipo dedicado o un sistema de software que se ejecuta en un equipo. Actúa como intermediario entre un dispositivo de extremo, como un equipo, y otro servidor desde el que un usuario o cliente solicita un servicio. El servidor proxy puede existir en el mismo equipo que un servidor de firewall o en un servidor independiente, que reenvía solicitudes a través del firewall.

Una ventaja de un servidor proxy es que su caché puede servir a todos los usuarios. Si se solicitan uno o más sitios de Internet con frecuencia, es probable que estos sitios estén en la caché del proxy. Este almacenamiento en caché mejora aún más el tiempo de respuesta del usuario. Un proxy también puede registrar sus interacciones, que se pueden utilizar para solucionar problemas.

Cuando un servidor proxy recibe una solicitud de un recurso de Internet (como una página Web o mientras se conecta a un publicador de AEM), analiza su caché local de direcciones URL antes denominadas. Si encuentra la página, la devuelve al usuario sin reenviar la solicitud a Internet. Si la página no está en la caché, el servidor proxy actúa como cliente en nombre del usuario y solicita la página desde el servidor en Internet. Cuando se devuelve el contenido, el servidor proxy lo relaciona con la solicitud original y la reenvía al usuario.

## Explicación de las configuraciones de red estándar {#network-setups}

Para implementar una Configuración de red, consulte los siguientes escenarios con sus puntos fuertes y detalles de implementación.

En esta guía se destacan cuatro tipos diferentes de configuraciones de red dentro de una organización:

* **[Red de Internet directa (por cable o inalámbrica)](/help/using/direct-internet-network.md)**
* **[Red móvil directa](/help/using/mobile-network.md)**
* **[Red móvil con el enrutador de datos móvil y componentes de red activos](/help/using/mobile-network-router.md)**
* **[Red Corporativa Cerrada (Por Cable/Inalámbrica)](/help/using/enclosed-corporate-network.md)**

En la tabla siguiente se describen los diferentes tipos de configuraciones de red con ventajas y desventajas:

| Configuración de red | Ventajas | Desventajas |
|--- |--- |--- |
| **Red de Internet directa (por cable o inalámbrica)** | Fácil y directo a SetUp<br>Buena opción para instalaciones medianas o grandes<br>La red dedicada se puede encapsular<br>Pocos puntos de error<br>Relativamente barata<br>Buena escalabilidad | Plan de datos obligatorio de Internet |
| **Red móvil directa** | Fácil de configurar<br>Buena elección para instalaciones medianas o grandes<br>Buena escalabilidad<br>Screens encapsulado | Conexión obligatoria a Internet |
| **Red móvil con el enrutador de datos móvil y componentes de red activos** | Fácil de configurar<br>Buena elección para instalaciones medianas o grandes<br>La red dedicada se puede encapsular<br>Pocos puntos de error<br>Es relativamente barata<br>Buena escalabilidad | Plan de datos obligatorio de Internet |
| **Red Corporativa Cerrada (Por Cable/Inalámbrica)** | Alta flexibilidad y escalabilidad<br>Altamente seguras gracias a las diferentes líneas de defensa<br>Redes encapsuladas<br>Fáciles de supervisar y mantener<br>Confiables | Complicado y caro<br>Recomendado para especialistas en redes o integradores de sistemas |
