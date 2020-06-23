---
title: Introducción a la configuración de red estándar
seo-title: Introducción a la configuración de red estándar
description: La página describe la configuración de red estándar
seo-description: La página describe la configuración de red estándar
translation-type: tm+mt
source-git-commit: ae7da9c48188c3f7567d05d0e9a5a6b72383d539
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Administración del tráfico de red {#managing-network-traffic}

Una configuración de red puede tener varias estructuras. En esta sección se proporciona una visión general de las estructuras de red implementadas en un entorno. Hay diferentes configuraciones que a veces se implementan desde cero.

Esta sección resalta una introducción a los servidores proxy seguida de las diferentes estructuras de red que están configuradas con diferentes organizaciones.

>[!NOTE]
>**Requisitos de red de AEM Screens **>Los AEM Screens se comunican directamente con el Cloud Service de AEM, por lo que es necesario establecer una conexión estable entre estos dos nodos. Los servidores de seguridad son absolutamente obligatorios para el acceso a Internet comercial y el cliente necesita saber qué puertos de comunicación deben abrirse en los servidores de seguridad de los sistemas y otros componentes de red relacionados con la seguridad informática que están bajo el control del cliente.

## Servidores proxy {#proxy-servers}

Un servidor proxy es un equipo dedicado o un sistema de software que se ejecuta en un equipo que actúa como intermediario entre un dispositivo de extremo, como un equipo, y otro servidor desde el que un usuario o cliente solicita un servicio. El servidor proxy puede existir en el mismo equipo que un servidor de seguridad o en un servidor independiente, que reenvía las solicitudes a través del servidor de seguridad.

Una ventaja de un servidor proxy es que su caché puede servir a todos los usuarios. Si se solicitan con frecuencia uno o más sitios de Internet, es probable que estén en la caché del proxy, lo que mejorará el tiempo de respuesta del usuario. Un proxy también puede registrar sus interacciones, lo que puede resultar útil para solucionar problemas.

## Explicación de la configuración de red estándar {#network-setups}

Para implementar una configuración de red, debe consultar los siguientes escenarios con detalles de implementación y fortalezas.

Existen tres tipos principales de configuraciones de red:

1. [Acceso directo a Internet](/help/using/direct-internet-access.md)
1. [Red móvil directa](/help/using/mobile-network-setup.md)
1. [Red móvil con enrutador de datos móvil y componentes de red activos](/help/using/mobile-network-setup-router.md)
1. [Red corporativa adjunta](/help/using/enclosed-corporate-network.md)

La siguiente tabla describe los diferentes tipos de configuraciones de red con ventajas y desventajas:

<table>
 <tbody>
  <tr>
   <td><strong>Configuración de red</strong></td>
   <td><strong>Ventajas</strong></td>
   <td><strong>Desventajas</strong></td>
  </tr>
  <tr>
   <td><strong>Acceso directo a Internet</strong></td>
   <td>Fácil y directo a SetUp<br>Buena opción para instalaciones<br>Dedicated Network de tamaño medio o mayor se puede encapsular<br>Pocos puntos de falla<br>Relativamente barata<br>Buena escalabilidad</td>
   <td>Plan de datos de Internet adecuado obligatorio</td>
  </tr>
    <tr>
   <td><strong>Red móvil directa</strong></td>
   <td>Fácil y directo a SetUp<br>Buena opción para instalaciones de tamaño mediano o más grandes<br>Buena escalabilidadPantallas<br>encapsuladas
</td>
   <td>Se requiere una conexión a Internet adecuada</td>
  </tr>
    <tr>
<tr>
   <td><strong>Red móvil con enrutador de datos móvil y componentes de red activos</strong></td>
   <td>Fácil y directo a SetUp<br>Buena opción para instalaciones<br>Dedicated Network de tamaño medio o mayor se puede encapsular<br>pocos puntos de falla<br>Relativamente barata<br>Buena escalabilidad</br></td>
   <td>Plan de datos de Internet adecuado obligatorio</td>
  </tr>
    <tr>

<td><strong>Red corporativa adjunta</strong></td>
   <td>Gran flexibilidad y escalabilidad<br>Alta seguridad gracias a las diferentes líneas de redes<br>encapsuladas de defensa<br>Fácil de monitorear y mantener<br>confiable</td>
   <td>Se recomiendan especialistas en red complicados y caros<br>o integradores de sistemas</td>
  </tr>
  </tr>
 </tbody>
</table>


