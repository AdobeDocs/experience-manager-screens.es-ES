---
title: Administración del tráfico de red
description: La página describe la configuración de red estándar y cómo administrar el tráfico de red.
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# Administración del tráfico de red {#managing-network-traffic}

Una configuración de red puede tener varias estructuras. En esta sección se describen las configuraciones de red más habituales y los enfoques generalizados seguidos dentro de una Organización.

En esta guía se destaca una introducción a los servidores proxy seguida de las diversas estructuras de red que se configuran en diferentes organizaciones.

>[!NOTE]
>
>**Requisitos de red de AEM Screens**
>
>Los AEM Screens se comunican directamente con AEM como Cloud Service, por lo que es necesario establecer una conexión estable entre los dos nodos. Los servidores de seguridad son absolutamente obligatorios para el acceso a Internet comercial y, como cliente, debe comprender qué puertos de comunicación deben abrirse en estos servidores de seguridad y otros componentes de red relacionados con la seguridad informática.

## Información general sobre servidores proxy {#proxy-servers}

Una conexión a Internet depende del uso de un servidor proxy. Un servidor proxy es un equipo dedicado o un sistema de software que se ejecuta en un equipo que actúa como intermediario entre un dispositivo de extremo, como un equipo, y otro servidor desde el que un usuario o cliente solicita un servicio. El servidor proxy puede existir en el mismo equipo que un servidor de seguridad o en un servidor independiente, que reenvía las solicitudes a través del servidor de seguridad.

Una ventaja de un servidor proxy es que su caché puede servir a todos los usuarios. Si se solicitan con frecuencia uno o más sitios de Internet, es probable que estén en la caché del proxy y esto mejore aún más el tiempo de respuesta del usuario. Un proxy también puede registrar sus interacciones, que se pueden utilizar para solucionar problemas.

Cuando un servidor proxy recibe una solicitud de un recurso de Internet (como una página Web o al conectarse a un editor de AEM), explora su caché local de direcciones URL anteriormente llamadas. Si encuentra la página, la devuelve al usuario sin reenviar la solicitud a Internet. Si la página no está en la caché, el servidor proxy (actúa como cliente) en nombre del usuario y solicita la página al servidor de Internet. Cuando se devuelve el contenido, el servidor proxy relaciona su contenido con la solicitud original y la reenvía al usuario.

## Explicación de la configuración de red estándar {#network-setups}

Para implementar una configuración de red, debe consultar los siguientes escenarios con sus fortalezas y detalles de implementación.

Esta guía destaca cuatro tipos diferentes de configuraciones de red dentro de una organización:

* **[Red de Internet directa (cableada/inalámbrica)](/help/using/direct-internet-network.md)**
* **[Red móvil directa](/help/using/mobile-network.md)**
* **[Red móvil con enrutador de datos móvil y componentes de red activos](/help/using/mobile-network-router.md)**
* **[Red corporativa cerrada (cableada/inalámbrica)](/help/using/enclosed-corporate-network.md)**

La siguiente tabla describe los diferentes tipos de configuraciones de red con ventajas y desventajas:

| Configuración de red | Ventajas | Desventajas |
|--- |--- |--- |
| **Red de Internet directa (cableada/inalámbrica)** | Fácil y directo a<br>SetUpBuena opción para<br>instalaciones de tamaño medio o mayorLa red dedicada se puede<br>encapsularPocos puntos de<br>falloRelativamente<br>barataBuena escalabilidad | Plan de datos de Internet obligatorio |
| **Red móvil directa** | Fácil de<br>configurarBuena opción para<br>instalaciones de tamaño medio o más grandesBuena<br>escalabilidadPantallas encapsuladas | Conexión a Internet obligatoria |
| **Red móvil con enrutador de datos móvil y componentes de red activos** | Fácil de<br>configurarBuena opción para<br>instalaciones de tamaño medio o grandesLa red dedicada se puede<br>encapsular pocos puntos de<br>fallaRelativamente<br>barataBuena escalabilidad | Plan de datos de Internet obligatorio |
| **Red corporativa cerrada (cableada/inalámbrica)** | Alta flexibilidad y<br>escalabilidadAlta seguridad debido a las diferentes líneas de<br>defensa<br>Redes encapsuladasFácil de monitorear y<br>mantenerConfiable | Complicado y<br>costosoRecomendado para especialistas en redes o integradores de sistemas |