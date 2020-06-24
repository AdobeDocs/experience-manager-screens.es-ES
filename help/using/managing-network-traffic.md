---
title: Administración del tráfico de red
description: La página describe la configuración de red estándar y cómo administrar el tráfico de red.
translation-type: tm+mt
source-git-commit: 93cc11459e23d3eb22d865bedeb26deaf7135636
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# Administración del tráfico de red {#managing-network-traffic}

Una configuración de red puede tener varias estructuras. Esta sección describe las configuraciones de red más habituales dentro de la configuración de red de una organización.

En esta guía se destaca una introducción a los servidores proxy seguida de las diversas estructuras de red que se configuran en diferentes organizaciones.

>[!NOTE]
>
>**Requisitos de red de AEM Screens**
>
>Los AEM Screens se comunican directamente con AEM como Cloud Service, por lo que es necesario establecer una conexión estable entre los dos nodos. Los servidores de seguridad son absolutamente obligatorios para el acceso a Internet comercial y, como cliente, debe comprender qué puertos de comunicación deben abrirse en servidores de seguridad y otros componentes de red relacionados con la seguridad informática.

## Información general sobre servidores proxy {#proxy-servers}

Una conexión a Internet depende del uso de un servidor proxy. Un servidor proxy es un equipo dedicado o un sistema de software que se ejecuta en un equipo que actúa como intermediario entre un dispositivo de extremo, como un equipo, y otro servidor desde el que un usuario o cliente solicita un servicio. El servidor proxy puede existir en el mismo equipo que un servidor de seguridad o en un servidor independiente, que reenvía las solicitudes a través del servidor de seguridad.

Una ventaja de un servidor proxy es que su caché puede servir a todos los usuarios. Si se solicitan con frecuencia uno o más sitios de Internet, es probable que estén en la caché del proxy, se mejora el tiempo de respuesta del usuario. Un proxy también puede registrar sus interacciones, que se utilizan para solucionar problemas.

## Explicación de la configuración de red estándar {#network-setups}

Para implementar una configuración de red, debe consultar los siguientes escenarios con sus fortalezas y detalles de implementación.

Existen cuatro tipos principales de configuraciones de red:

1. [Red de Internet directa (cableada/inalámbrica)](/help/using/direct-internet-network.md)
1. [Red móvil directa](/help/using/mobile-network.md)
1. [Red móvil con enrutador de datos móvil y componentes de red activos](/help/using/mobile-network-router.md)
1. [Red corporativa cerrada (cableada/inalámbrica)](/help/using/enclosed-corporate-network.md)

La siguiente tabla describe los diferentes tipos de configuraciones de red con ventajas y desventajas:

| Configuración de red | Ventajas | Desventajas |
|--- |--- |--- |
| Red de Internet directa (cableada/inalámbrica) | Fácil y directo a<br>SetUpBuena opción para<br>instalaciones de tamaño medio o mayorLa red dedicada se puede<br>encapsularPocos puntos de<br>falloRelativamente<br>barataBuena escalabilidad | Plan de datos de Internet obligatorio |
| Red móvil directa | Fácil de<br>configurarBuena opción para<br>instalaciones de tamaño medio o más grandesBuena<br>escalabilidadPantallas encapsuladas | Conexión a Internet obligatoria |
| Red móvil con enrutador de datos móvil y componentes de red activos | Fácil de<br>configurarBuena opción para<br>instalaciones de tamaño medio o grandesLa red dedicada se puede<br>encapsular pocos puntos de<br>fallaRelativamente<br>barataBuena escalabilidad | Plan de datos de Internet obligatorio |
| Red corporativa cerrada (cableada/inalámbrica) | Alta flexibilidad y<br>escalabilidadAlta seguridad debido a las diferentes líneas de<br>defensa<br>Redes encapsuladasFácil de monitorear y<br>mantenerConfiable | Complicado y<br>costosoRecomendado para especialistas en redes o integradores de sistemas |
