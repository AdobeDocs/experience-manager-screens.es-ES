---
title: Lista de comprobación de seguridad para AEM Screens
seo-title: Security Checklist for AEM Screens
description: En la página se describe la lista de comprobación de seguridad de AEM Screens
seo-description: The page describes Security Checklist for AEM Screens
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---


# Consideraciones de seguridad del sistema para AEM Screens {#security-checklist}

>[!IMPORTANT]
>Este es un recurso de Git interno.

Esta página resalta las Consideraciones de seguridad del sistema para AEM Screens.


## Documentación técnica sobre la seguridad de AEM Screens {#white-paper}

En esta sección se describe el documento técnico. (Documento adjunto a la documentación técnica pendiente)


## Preguntas frecuentes sobre la seguridad de AEM Screens {#faqs-screens}

AEM Las siguientes preguntas frecuentes suponen una arquitectura de reproductor autenticada y registrada que utiliza HTTPS como protocolo de comunicación entre el reproductor y el servidor de la.

### FAQ 1 {#faq1}

¿Se puede redirigir el tráfico del reproductor a un servidor malintencionado e instruirlo para que descargue y reproduzca contenido multimedia malintencionado?

**Respuesta**

No es posible porque la conexión HTTP identifica ambos extremos de la conexión y la cifra. Si intenta estar en el medio e interceptarlo, solo verá contenido encriptado y, si intenta suplantar al servidor, el reproductor le rechazará porque su certificado es diferente.


### FAQ 2 {#faq2}

¿Debo usar HTTP o HTTP?

**Respuesta**

Utilice HTTP. Esto es imprescindible si le preocupa la seguridad. Con HTTP la comunicación se cifra entre el reproductor y el servidor, e interceptar el contenido o modificarlo será prácticamente imposible.


### FAQ 3 {#faq3}

En una descarga de contenido, ¿hay algún tipo de firma del contenido o hash?

**Respuesta**

El servidor firma todos los recursos (SHA) y, a continuación, el reproductor los valida para obtener el mismo hash a fin de garantizar la integridad.
Si el hash no coincide, intentamos volver a validarlo 3 veces. Tras 3 intentos, consideramos que el comando de descarga no es válido.


### PREGUNTAS FRECUENTES 4 {#faq4}

AEM ¿Es seguro el servidor?

**Respuesta**

Ans 4. Si está en AMS, nos encargamos de toda la seguridad del servidor mediante las mismas funciones que Sites o Assets.


### PREGUNTAS FRECUENTES 5 {#faq5}

¿Es seguro el dispositivo?

**Respuesta**

En teoría, un reproductor físicamente comprometido puede manipularse para reproducir cualquier contenido. También podría simplemente enchufar el reproductor y enchufar una memoria USB/HDMI.

Por lo tanto, se recomienda poner los dispositivos fuera del alcance, preferiblemente en un contenedor seguro, con el cableado asegurado también. Deshabilite también cualquier puerto remoto IR.

Si el sistema operativo del dispositivo no se actualiza con regularidad, el sistema operativo puede quedar expuesto a agujeros de seguridad y permitir ataques remotos a través de la red.

>[!NOTE]
>
>Se recomienda instrumentar los dispositivos con capacidades decentes de actualización y control remoto (escritorio remoto, solución MDM, etc.). También se recomienda utilizar una red privada, no expuesta al WIFI público, por ejemplo.


### PREGUNTAS FRECUENTES 6 {#faq6}

¿Cómo intentaría un hacker comprometer a un jugador?

**Respuesta**

La única manera de comprometer un dispositivo de reproducción es:

1. comprometer el DNS para suplantar al servidor en su nombre de host, y,
1. avenencia
   1. el certificado del lado del servidor para suplantar al servidor
   1. y suplantar el certificado del lado del cliente

>[!IMPORTANT]
>AEM Incluso si un dispositivo está en peligro, puede revocar fácilmente sus credenciales para que ya no se pueda conectar a la red de manera que no se pueda volver a conectar a la red de manera más rápida y segura.





