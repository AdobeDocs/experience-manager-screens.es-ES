---
title: Lista de comprobación de seguridad
description: Obtenga información acerca de las áreas de seguridad clave de AEM Screens con una lista de comprobación de preguntas y consideraciones.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Lista de comprobación de seguridad de AEM Screens {#security-checklist}

En la página Lista de comprobación de seguridad de AEM Screens se describen las áreas de seguridad clave con una lista de comprobación de preguntas y consideraciones.

## Tabla de lista de comprobación {#checklist-table}

| **Área de seguridad** | **Lista de comprobación** | **Sí/No/No aplicable** |
|---|---|---|
| **AEM Actualizaciones de software de Pantallas y Pantallas** | **a.** *¿Se ha aplicado el Service Pack más reciente de Adobe Experience Manager AEM ()?* <br>**b.** *¿Se ha aplicado el paquete de funciones más reciente de AEM Screens?* <br>**c.** *¿Está utilizando el software AEM Screens Player más reciente disponible de? [Descargas del reproductor AEM Screens](https://download.macromedia.com/screens/)?* |
| **Seguridad física** | **a.** *¿Ha desactivado todos los puertos innecesarios?* <br>**b.** *¿Ha asegurado el cableado y el hardware?* <br>**c.** *¿Está utilizando contenedores, si corresponde?* |
| **Seguridad de red** | **a.** *¿Utiliza una subred aislada para los dispositivos de señalización?* <br>**b.** *AEM ¿Permite la subred aislada el acceso a los extremos necesarios, incluidos los servicios de red, Adobe Analytics u otros servicios necesarios?* <br>**c.** *¿Ha protegido su Wi-Fi mediante las prácticas recomendadas empresariales?* <br>**d.** *Si utiliza la reproducción sincronizada, ¿ha permitido el 24503 TCP para WebSocket únicamente en los dispositivos principales?* <br>**e.** *¿Ha desbloqueado el intervalo de direcciones IP de los dispositivos de reproducción para que solo los dispositivos autorizados puedan acceder al servicio de registro en la instancia de creación?* |
| **Seguridad del sistema operativo** | **a.** *¿Ha actualizado a la última versión del sistema operativo y ha aplicado todos los parches de seguridad necesarios?* <br>**b.** *¿Ha desactivado todos los servicios innecesarios y eliminado las aplicaciones innecesarias?* <br>**c.** *¿Ha inscrito el dispositivo en la administración de dispositivos para aplicar directivas empresariales?* <br>**d.** *¿Ha bloqueado el dispositivo en un quiosco de una sola aplicación (reproductor)?* <br>**e.** *¿Dispone de procedimientos operativos estándar (SOP) para instalar las actualizaciones de seguridad del sistema operativo a lo largo del tiempo?*<br>**f.***¿Ha seguido las prácticas recomendadas de seguridad para el sistema operativo en uso, como el software antimalware o el usuario no administrativo?* |
| **Seguridad de aplicaciones** | **a.** *¿Ha deshabilitado la IU de administración, el conmutador de canal y la IU de actividad para la producción?* <br>**b.** *¿Ha minimizado el nivel de registro para la producción?* <br>**c.** *AEM ¿Está utilizando https para conectarse a la red de trabajo de la?* <br>**d.** *¿Está utilizando un certificado firmado por la CA o una PKI empresarial? (no certificados autofirmados)*<br>**e.***¿Utiliza TLS y no SSL v3?*<br>**f.** *AEM ¿Está validando el token de registro en el dispositivo y al registrarse en el mismo*<br> **g.** *¿Ha clasificado los datos que se utilizan y que no existen PII ni PHI en el dispositivo?*<br> **h.** *¿Ha clasificado los datos que se utilizan y que no existe información de identificación personal (PII) o información médica protegida (PHI) en el dispositivo?*<br> **i.** *¿Ha configurado la monitorización de correos electrónicos? ¿Dispone de un SOP para responder a los correos electrónicos de monitorización y gestionar dispositivos que no son ping?* |
| **Control de acceso** | **a.** *¿Tiene un control de acceso basado en roles (RBAC) identificado y administrado internamente?* <br>**b.** *¿Ha seguido el principio del menor privilegio al proporcionar acceso a autores, administradores y jugadores mediante las prácticas recomendadas desde el Adobe?* |

### Descargando lista de comprobación de seguridad {#download-checklist}

Para descargar la lista de comprobación de seguridad de AEM Screens, haga clic en [aquí](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
