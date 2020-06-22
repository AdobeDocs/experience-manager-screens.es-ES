---
title: Comprender los servidores proxy
seo-title: Comprender los servidores proxy
description: La página describe los servidores proxy
seo-description: La página describe los servidores proxy
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Introducción a la configuración de red estándar {#intro-standard-networks}

Una configuración de red puede tener varias estructuras. En esta sección se proporciona una visión general de las estructuras de red implementadas en un entorno. Hay diferentes configuraciones que a veces se implementan desde cero.

Esta sección resalta una introducción a los servidores proxy seguida de las diferentes estructuras de red que están configuradas con diferentes organizaciones.

## Servidores proxy {#proxy-servers}

Un servidor proxy es un equipo dedicado o un sistema de software que se ejecuta en un equipo que actúa como intermediario entre un dispositivo de extremo, como un equipo, y otro servidor desde el que un usuario o cliente solicita un servicio. El servidor proxy puede existir en el mismo equipo que un servidor de seguridad o en un servidor independiente, que reenvía las solicitudes a través del servidor de seguridad.

Una ventaja de un servidor proxy es que su caché puede servir a todos los usuarios. Si se solicitan con frecuencia uno o más sitios de Internet, es probable que estén en la caché del proxy, lo que mejorará el tiempo de respuesta del usuario. Un proxy también puede registrar sus interacciones, lo que puede resultar útil para solucionar problemas.

## Explicación de la configuración de red {#network-setups}

Para implementar una configuración de red, debe consultar los siguientes escenarios con pros y contras.

Existen tres tipos principales de configuraciones de red:

1. Configuración de acceso a Internet
1. Configuración de red móvil
1. Configuración de red corporativa adjunta

La siguiente tabla describe los diferentes tipos de configuraciones de red con ventajas y desventajas:

<table>
 <tbody>
  <tr>
   <td><strong>Configuración de red</strong></td>
   <td><strong>Ventajas</strong></td>
   <td><strong>Desventajas</strong></td>
  </tr>
  <tr>
   <td><strong>Configuración de acceso a Internet</strong></td>
   <td>Fácil y directo a SetUp<br>Buena opción para instalaciones<br>Dedicated Network de tamaño medio o mayor se puede encapsular<br>Pocos puntos de falla<br>Relativamente barata<br>Buena escalabilidad</td>
   <td>Plan de datos de Internet adecuado obligatorio</td>
  </tr>
    <tr>
   <td><strong>Configuración de red móvil</strong></td>
   <td>Fácil y directo a SetUp<br>Buena opción para instalaciones<br>Dedicated Network de tamaño medio o mayor se puede encapsular<br>pocos puntos de falla<br>Relativamente barata<br>Buena escalabilidad</br></td>
   <td>Se requiere una conexión a Internet adecuada</td>
  </tr>
    <tr>
   <td><strong>Red corporativa adjunta</strong></td>
   <td>Gran flexibilidad y escalabilidad<br>Alta seguridad gracias a las diferentes líneas de redes<br>encapsuladas de defensa<br>Fácil de monitorear y mantener<br>confiable</td>
   <td>Se recomiendan especialistas en red complicados y caros<br>o integradores de sistemas</td>
  </tr>
  </tr>
 </tbody>
</table>


