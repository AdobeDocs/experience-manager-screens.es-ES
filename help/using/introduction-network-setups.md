---
title: Introducción a la configuración de red estándar
seo-title: Introducción a la configuración de red estándar
description: La página describe la configuración de red estándar
seo-description: La página describe la configuración de red estándar
translation-type: tm+mt
source-git-commit: 77cf87cbce39a00528b2690d9689861b91e61fc5
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Administración del tráfico de red {#managing-network-traffic}

Una configuración de red puede tener varias estructuras. Esta sección describe las configuraciones de red más habituales dentro de la configuración de red de una organización.

En esta guía se destaca una introducción a los servidores proxy seguida de las diversas estructuras de red que se configuran en diferentes organizaciones.

>[!NOTE]
>**Requisitos de red de AEM Screens **>Los AEM Screens se comunican directamente con AEM como Cloud Service, por lo que es necesario establecer una conexión estable entre los dos nodos. Los servidores de seguridad son absolutamente obligatorios para el acceso a Internet comercial y, como cliente, debe comprender qué puertos de comunicación deben abrirse en servidores de seguridad y otros componentes de red relacionados con la seguridad informática.

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

<table>
 <tbody>
  <tr>
   <td><strong>Configuración de red</strong></td>
   <td><strong>Ventajas</strong></td>
   <td><strong>Desventajas</strong></td>
  </tr>
  <tr>
   <td><strong>Red de Internet directa (cableada/inalámbrica)</strong></td>
   <td>Fácil y directo a SetUp<br>Buena opción para instalaciones<br>Dedicadas de red de tamaño medio o mayor se puede encapsular<br>pocos puntos de falla<br>Relativamente barata<br>Buena escalabilidad</td>
   <td>Plan de datos de Internet obligatorio </td>
  </tr>
    <tr>
   <td><strong>Red móvil directa</strong></td>
   <td>Fácil de configurar<br>Buena opción para instalaciones de tamaño medio o grandes<br>Pantallas con capacidad de ampliación<br>Encapsuladas
</td>
   <td>Conexión a Internet obligatoria</td>
  </tr>
    <tr>
<tr>
   <td><strong>Red móvil con enrutador de datos móvil y componentes de red activos</strong></td>
   <td>Fácil de configurar<br>Buena opción para redes de tamaño medio o grandes instalaciones<br>dedicadas se pueden encapsular<br>pocos puntos de falla<br>Relativamente barata<br>Buena escalabilidad</br></td>
   <td>Plan de datos de Internet obligatorio</td>
  </tr>
    <tr>

<td><strong>Red corporativa cerrada (cableada/inalámbrica)</strong></td>
   <td>Alta flexibilidad y escalabilidad<br>Altamente segura gracias a las diferentes líneas de redes<br>encapsuladas de defensa<br>fáciles de monitorear y mantener<br>fiables</td>
   <td>Complicado y costoso<br>recomendado para especialistas en redes o integradores de sistemas</td>
  </tr>
  </tr>
 </tbody>
</table>


