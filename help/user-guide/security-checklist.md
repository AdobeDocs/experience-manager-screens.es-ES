---
title: Lista de comprobación de seguridad
seo-title: Lista de comprobación de seguridad
description: La página describe la lista de comprobación de seguridad
seo-description: La página describe la lista de comprobación de seguridad
translation-type: tm+mt
source-git-commit: 16361c016251a0ce0c86175eb6ef09ffb3150415
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Lista de comprobación de seguridad de AEM Screens  {#security-checklist}

La página Lista de comprobación de seguridad de AEM Screens describe las áreas de seguridad clave con una lista de preguntas y consideraciones.

## Tabla de lista de comprobación {#checklist-table}

| **Área de seguridad** | **Lista de comprobación** | **Sí/No/NA** |
|---|---|---|
| **Actualizaciones de software de AEM y Screens** | ***a.*** *¿Se ha aplicado el último Service Pack de Adobe Experience Manager (AEM)?* <br>***b.****¿Se ha aplicado el último paquete de funciones de AEM Screens?*<br>***c.*** *¿Está utilizando el software AEM Screens Player más reciente disponible en Descargas[de](https://download.macromedia.com/screens/)AEM Screens Player?* |
| **Seguridad física** | ***a.*** *¿Ha deshabilitado todos los puertos innecesarios?* <br>***b.****¿Ha asegurado el cableado y el hardware?*<br>***c.*** *¿Está utilizando algún contenedor, si corresponde?* |
| **Seguridad de red** | ***a.*** *¿Está utilizando una subred aislada para sus dispositivos de señalización?* <br>***b.****¿La subred aislada permite el acceso a los extremos requeridos, incluidos AEM, Adobe Analytics u otros servicios necesarios?*<br>***c.*** *¿Ha asegurado su Wi-Fi mediante las optimizaciones empresariales?* <br>***d.****Si utiliza la reproducción sincronizada, ¿ha permitido TCP 24503 para WebSocket únicamente en los dispositivos maestros?*<br>***e.*** *¿Ha desbloqueado el rango de intervalos de IP de los dispositivos del reproductor para que solo los dispositivos autorizados puedan acceder al servicio de registro en el autor?* |
| **Seguridad del sistema operativo** | ***a.*** *¿Ha actualizado la versión más reciente del sistema operativo y ha aplicado todos los parches de seguridad necesarios?* <br>***b.****¿Ha desactivado todos los servicios innecesarios y ha eliminado las aplicaciones innecesarias?*<br>***c.*** *¿Ha inscrito el dispositivo en la administración de dispositivos para aplicar políticas empresariales?* <br>***d.****¿Ha bloqueado el dispositivo en un quiosco de aplicación única (reproductor)?*<br>***e.*** *¿Dispone de procedimientos operativos estándar (SOP) para instalar las actualizaciones de seguridad del sistema operativo con el paso del tiempo?*<br>***f.****¿Ha seguido las prácticas recomendadas de seguridad para el sistema operativo en uso, como software antimalware o usuario no administrativo?* |
| **Seguridad de la aplicación** | ***a.*** *¿Ha desactivado la IU de administración, el Canal Switcher y la IU de Actividad para la producción?* <br>***b.****¿Ha minimizado el nivel de registro para la producción?*<br>***c.*** *¿Utiliza https para conectarse a AEM?* <br>***d.****¿Está utilizando un certificado de CA firmado o una PKI empresarial? (no certificados con firma personal)*<br>***e.****¿Está utilizando TLS y no SSL v3?*<br>*** f.****¿Está validando el token de registro en el dispositivo y en AEM al registrarse?*<br> ***g.*** *¿Ha clasificado los datos que se utilizan y que no existe PII o PHI en el dispositivo?*<br> ***h.*** *¿Ha clasificado los datos que se utilizan y que no existe información de identificación personal (PII) o información de salud protegida (PHI) en el dispositivo?*<br> ***i.*** *¿Ha configurado la supervisión de los correos electrónicos y dispone de una SOP para responder a la supervisión de los correos electrónicos y controlar los dispositivos que no hacen ping?* |
| **Control de acceso** | ***a.*** *¿Tiene un Control de acceso basado en roles (RBAC) identificado y administrado internamente?* <br>***b.****¿Ha seguido el principio de los privilegios mínimos al proporcionar acceso a autores, administradores y reproductores mediante las prácticas recomendadas de Adobe?* |

### Descarga de la lista de comprobación de seguridad {#download-checklist}

Para descargar la lista de comprobación de seguridad de AEM Screens, haga clic [aquí](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).