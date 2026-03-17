---
title: Lista de comprobación de seguridad
description: Obtenga información acerca de las áreas de seguridad clave de AEM Screens con una lista de comprobación de preguntas y consideraciones.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: ad8509deaff9f90df5f6b50947f587a74e420661
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 1%

---

# Lista de comprobación de seguridad de AEM Screens {#security-checklist}

En la página Lista de comprobación de seguridad de AEM Screens se describen las áreas de seguridad clave con una lista de comprobación de preguntas y consideraciones.

## Tabla de lista de comprobación {#checklist-table}

| **Área de seguridad** | **Lista de comprobación** | **Sí/No/No** |
|---|---|---|
| **Actualizaciones de software de AEM y Screens** | **a.** *¿Se ha aplicado el Service Pack más reciente de Adobe Experience Manager (AEM)?* <br>**b.** *¿Se ha aplicado el paquete de funciones más reciente de AEM Screens?* <br>**c.** *¿Está usando el software de AEM Screens Player más reciente disponible de [Descargas de AEM Screens Player](https://download.macromedia.com/screens/)?* | |
| **Seguridad física** | **a.** *¿Ha deshabilitado todos los puertos innecesarios?* <br>**b.** *¿Ha protegido el cableado y el hardware?* <br>**c.** *¿Está usando contenedores, si corresponde?* | |
| **Seguridad de red** | **a.** *¿Está usando una subred aislada para los dispositivos de señalización?* <br>**b.** *¿Permite la subred aislada el acceso a los extremos necesarios, incluidos AEM, Adobe Analytics u otros servicios necesarios?* <br>**c.** *¿Ha protegido su Wi-Fi mediante las prácticas recomendadas empresariales?* <br>**d.** *Si utiliza la reproducción sincronizada, ¿ha permitido el 24503 TCP para WebSocket solamente en los dispositivos principales?* <br>**e.** *¿Ha desbloqueado el intervalo de direcciones IP de los dispositivos de reproducción para que solo los dispositivos autorizados puedan acceder al servicio de registro en la instancia de creación?* | |
| **Seguridad del sistema operativo** | **a.** *¿Ha actualizado a la última versión del sistema operativo y ha aplicado todos los parches de seguridad necesarios?* <br>**b.** *¿Ha deshabilitado todos los servicios innecesarios y ha eliminado las aplicaciones innecesarias?* <br>**c.** *¿Ha inscrito el dispositivo en la administración de dispositivos para aplicar directivas empresariales?* <br>**d.** *¿Ha bloqueado el dispositivo en un quiosco de una sola aplicación (reproductor)?* <br>**e.** *¿Dispone de procedimientos operativos estándar (SOP) para instalar las actualizaciones de seguridad del sistema operativo a lo largo del tiempo?*<br>**f.***¿Ha seguido las prácticas recomendadas de seguridad para el sistema operativo en uso, como software antimalware o usuario no administrativo?* | |
| **Seguridad de la aplicación** | **a.** *¿Ha deshabilitado la IU de administración, el conmutador de canal y la IU de actividad para la producción?* <br>**b.** *¿Ha minimizado el nivel de registro para la producción?* <br>**c.** *¿Está usando https para conectarse a AEM?* <br>**d.** *¿Está utilizando un certificado firmado por la CA o una PKI empresarial? (no certificados autofirmados)*<br>**e.***¿Está usando TLS y no SSL v3?*<br>**f.** *¿Está validando el token de registro en el dispositivo y en AEM al registrarse?*<br> **g.** *¿Ha clasificado los datos en uso y que no existen PII ni PHI en el dispositivo?*<br> **h.** *¿Ha clasificado los datos en uso y que no existe información de identificación personal (PII) o información médica protegida (PHI) en el dispositivo?*<br> **i.** *¿Ha configurado la monitorización de correos electrónicos? ¿Tiene un SOP para responder a los correos electrónicos de supervisión y administrar los dispositivos que no son ping?* | |
| **Control de acceso** | **a.** *¿Ha identificado y administrado internamente un control de acceso basado en roles (RBAC)?* <br>**b.** *¿Ha seguido el principio del menor privilegio al proporcionar acceso a autores, administradores y reproductores mediante las prácticas recomendadas de Adobe?* | |

### Descargar lista de comprobación de seguridad {#download-checklist}

Para descargar la lista de comprobación de seguridad de AEM Screens, haga clic [aquí](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
