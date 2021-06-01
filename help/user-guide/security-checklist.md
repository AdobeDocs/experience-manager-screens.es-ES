---
title: Lista de comprobación de seguridad
seo-title: Lista de comprobación de seguridad
description: La página describe las áreas de seguridad clave con una lista de comprobación de preguntas y consideraciones.
seo-description: La página describe la lista de comprobación de seguridad
feature: Administración de Screens
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# Lista de comprobación de seguridad de AEM Screens {#security-checklist}

La página Lista de comprobación de seguridad de AEM Screens describe las áreas de seguridad clave con una lista de preguntas y consideraciones.

## Tabla de lista de comprobación {#checklist-table}

| **Área de seguridad** | **Lista de comprobación** | **Sí/No/NA** |
|---|---|---|
| **Actualizaciones del software de AEM y Screens** | ***a.*** *¿Se ha aplicado el último paquete de servicio de Adobe Experience Manager (AEM)?* <br>***b.***  *¿Se ha aplicado el último paquete de funciones de AEM Screens?* <br>***c.*** *¿Está utilizando el software AEM Screens Player más reciente disponible de Descargas [ del Reproductor de ](https://download.macromedia.com/screens/)AEM Screens?* |
| **Seguridad física** | ***a.*** *¿Ha deshabilitado todos los puertos innecesarios?* <br>***b.***  *¿Ha protegido el cableado y el hardware?* <br>***c.*** *¿Está utilizando contenedores si corresponde?* |
| **Seguridad de red** | ***a.*** *¿Está utilizando una subred aislada para sus dispositivos de señalización?* <br>***b.***  *¿La subred aislada permite el acceso a los extremos requeridos, incluidos AEM, Adobe Analytics u otros servicios requeridos?* <br>***c.*** *¿Ha asegurado su Wi-Fi utilizando las prácticas recomendadas empresariales?* <br>***d.*** *Si utiliza la reproducción sincronizada, ¿ha permitido TCP 24503 para WebSocket solo en los dispositivos maestros?* <br>***e.*** *¿Ha desbloqueado el rango de direcciones IP de los dispositivos del reproductor para que solo los dispositivos autorizados puedan acceder al servicio de registro en el autor?* |
| **Seguridad del sistema operativo** | ***a.*** *¿Ha actualizado a la última versión del sistema operativo y aplicado todos los parches de seguridad necesarios?* <br>***b.*** *¿Ha deshabilitado todos los servicios innecesarios y ha eliminado aplicaciones innecesarias?* <br>***c.*** *¿Ha registrado el dispositivo en la administración de dispositivos para aplicar políticas empresariales?* <br>***d.*** *¿Ha bloqueado el dispositivo en un quiosco de aplicación única (reproductor)?* <br>***e.*** *¿Tiene un procedimiento operativo estándar (SOP) para instalar las actualizaciones de seguridad del sistema operativo a lo largo del tiempo?*<br>***f.*** *¿Ha seguido las prácticas recomendadas de seguridad para el sistema operativo en uso, como el software antimalware o el usuario no administrativo?* |
| **Seguridad de la aplicación** | ***a.*** *¿Ha deshabilitado la IU de administración, el conmutador de canales y la IU de actividad para la producción?* <br>***b.*** *¿Ha minimizado el nivel de registro para producción?* <br>***c.*** *¿Está usando https para conectarse a AEM?* <br>***d.*** *¿Está utilizando un certificado firmado por CA o una PKI empresarial? (no certificados con firma personal)*<br>***e.*** *¿Está utilizando TLS y no SSL v3?*<br>***f.*** *¿Está validando el token de registro en el dispositivo y AEM al registrarse?*<br> ***g.*** *¿Ha clasificado los datos que se utilizan y no existe PII o PHI en el dispositivo?*<br> ***h.*** *¿Ha clasificado los datos que se utilizan y que no existe información de identificación personal (PII) o información de salud protegida (PHI) en el dispositivo?*<br> ***i.*** *¿Ha configurado la supervisión de los correos electrónicos y dispone de una SOP para responder a la supervisión de los correos electrónicos y controlar los dispositivos que no tocan?* |
| **Control de acceso** | ***a.*** *¿Tiene un Control de acceso basado en roles (RBAC) identificado y administrado internamente?* <br>***b.*** *¿Ha seguido el principio de los menos privilegiados al proporcionar acceso a autores, administradores y jugadores mediante las prácticas recomendadas de Adobe?* |

### Descarga de la lista de comprobación de seguridad {#download-checklist}

Para descargar la lista de comprobación de seguridad de AEM Screens, haga clic [aquí](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).