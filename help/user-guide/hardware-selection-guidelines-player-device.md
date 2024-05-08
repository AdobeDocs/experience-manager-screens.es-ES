---
title: Directrices de selección de hardware para dispositivos de reproducción
description: Obtenga información acerca de las directrices de selección de hardware para dispositivos AEM Screens Player.
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 3%

---


# Directrices de selección de hardware para dispositivos de reproducción {#hardware-selection}

En la siguiente sección se proporcionan las directrices de selección de hardware para un reproductor de AEM Screens.

## Consideraciones importantes {#important-considerations}

* Origen siempre ***Comercial*** o ***Industrial*** Componentes de nivel superior para el reproductor de PC y el panel de visualización o el proyector.

* Póngase en contacto con los proveedores que trabajan en el mercado de la publicidad dinámica.
* Tenga siempre en cuenta factores ambientales como la temperatura ambiente y la humedad relativa.
* Revise siempre los requisitos de alimentación y el acondicionador de alimentación.
* Revise cuidadosamente las necesidades de rendimiento y los puertos de E/S necesarios para la aplicación.

## Configuraciones de hardware {#hardware-configurations}

La siguiente tabla resume las configuraciones de hardware con casos de uso típicos para un proyecto de AEM Screens:

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>Configuración del reproductor</strong></td>
   <td><strong>Procesador</strong></td>
   <td><strong>Memoria</strong></td>
   <td><strong>SSD de almacenamiento</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>Mostrar</strong></td>
   <td><strong>E/S</strong></td>
   <td><strong>Casos de uso habituales</strong></td>
  </tr>
  <tr>
   <td>Básica</td>
   <td>Procesador Intel® Atom de doble núcleo, i3 o núcleo cuádruple básico</td>
   <td><p>4 GB de memoria</p> <p>2 MB de caché</p> </td>
   <td><p>*ChromeOS de 32 GB</p> <p>*Windows de 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> Ethernet / Inalámbrico,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Bucle estándar de pantalla completa<br /> </li>
     <li>División por día</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Estándar</td>
   <td>Procesador Intel® Core™ i5 de núcleo cuádruple</td>
   <td><p>8 GB de memoria</p> <p>4 MB de caché</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / Inalámbrico,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Contenido dinámico de origen único</li>
     <li>Interactivo simple</li>
     <li>Diseños de zona 1-3</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzado </td>
   <td>Procesador Intel® Core™ i7 de núcleo cuádruple con subprocesos</td>
   <td><p>16 GB de memoria</p> <p>8 MB de caché</p> </td>
   <td>256 GB</td>
   <td>GPU gráfica dedicada</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / Inalámbrico,<br /> 4 x USB</td>
   <td>
    <ul>
     <li>4 o más zonas de contenido, reproducción de vídeo simultánea</li>
     <li>Interactivo de varias páginas</li>
     <li>Déclencheur de datos de varias fuentes</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
