---
title: Administración del tráfico de red
description: La página describe las configuraciones de red estándar y cómo administrar el tráfico de red.
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# Administración del tráfico de red {#managing-network-traffic}

Una configuración de red puede tener varias estructuras. En esta sección se describen las configuraciones de red y los enfoques generalizados más habituales que se siguen dentro de una Organización.

Esta guía destaca una introducción a los servidores proxy seguida de las diversas estructuras de red configuradas dentro de diferentes organizaciones.

>[!NOTE]
>**Requisitos de red de AEM Screens**
>AEM Screens se comunica directamente con el AEM como Cloud Service, por lo que es necesario establecer una conexión estable entre los dos nodos. Los cortafuegos son absolutamente obligatorios para el acceso a Internet comercial y como cliente debe comprender qué puertos de comunicación se necesitan para abrirse en estos cortafuegos y otros componentes de red relacionados con la seguridad de TI.

## Información general sobre los servidores proxy {#proxy-servers}

Una conexión a Internet depende del uso de un servidor proxy. Un servidor proxy es un equipo dedicado o un sistema de software que se ejecuta en un equipo que actúa como intermediario entre un dispositivo de extremo, como un equipo, y otro servidor desde el que un usuario o cliente solicita un servicio. El servidor proxy puede existir en el mismo equipo que un servidor de firewall o en un servidor independiente, que reenvía las solicitudes a través del servidor de seguridad.

Una ventaja de un servidor proxy es que su caché puede servir a todos los usuarios. Si uno o más sitios de Internet se solicitan con frecuencia, es probable que estén en la caché del proxy y esto mejora aún más el tiempo de respuesta del usuario. Un proxy también puede registrar sus interacciones, que pueden utilizarse para solucionar problemas.

Cuando un servidor proxy recibe una solicitud de un recurso de Internet (como una página Web o al conectarse a un Editor de AEM), analiza su caché local de direcciones URL anteriormente llamadas. Si encuentra la página, la devuelve al usuario sin reenviar la solicitud a Internet. Si la página no está en la caché, el servidor proxy (actúa como cliente) en nombre del usuario y solicita la página desde el servidor en Internet. Cuando se devuelve el contenido, el servidor proxy lo relaciona con la solicitud original y la reenvía al usuario.

## Información sobre la configuración de red estándar {#network-setups}

Para implementar una configuración de red, debe consultar las siguientes situaciones con sus puntos fuertes y detalles de implementación.

Esta guía destaca cuatro tipos diferentes de configuraciones de red dentro de una organización:

* **[Red directa de Internet (cableada/inalámbrica)](/help/using/direct-internet-network.md)**
* **[Red móvil directa](/help/using/mobile-network.md)**
* **[Red móvil con enrutador de datos móvil y componentes de red activa](/help/using/mobile-network-router.md)**
* **[Red corporativa cerrada (inalámbrica/cableada)](/help/using/enclosed-corporate-network.md)**

La siguiente tabla describe los diferentes tipos de configuraciones de red con ventajas y desventajas:

| Configuración de red | Ventajas | Desventajas |
|--- |--- |--- |
| **Red directa de Internet (cableada/inalámbrica)** | Fácil y directo a SetUp<br>Buena opción para instalaciones de tamaño mediano o mayor<br>Red dedicada se puede encapsular<br>Pocos puntos de fallo<br>Relativamente barato<br>Buena escalabilidad | Plan de datos obligatorio de Internet |
| **Red móvil directa** | Fácil de configurar<br>Buena opción para instalaciones de tamaño medio o más grandes<br>Buena escalabilidad<br>Pantallas encapsuladas | Conexión a Internet obligatoria |
| **Red móvil con enrutador de datos móvil y componentes de red activa** | Fácil de configurar<br>Buena opción para instalaciones de tamaño medio o más grandes<br>La red dedicada se puede encapsular<br>Pocos puntos de error<br>Relativamente barato<br>Buena escalabilidad | Plan de datos obligatorio de Internet |
| **Red corporativa cerrada (inalámbrica/cableada)** | Alta flexibilidad y escalabilidad<br>Altamente segura debido a diferentes líneas de defensa<br>Redes encapsuladas<br>Fácil de monitorizar y mantener<br>Fiable | Complicado y costoso<br>Recomendado para especialistas en redes o integradores de sistemas |
