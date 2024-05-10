---
title: Lista de comprobación de seguridad para AEM Screens
description: Obtenga más información acerca de la lista de comprobación de seguridad de AEM Screens.
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Consideraciones de seguridad del sistema para AEM Screens {#security-checklist}

>[!IMPORTANT]
>Un recurso de Git interno.

Esta página resalta las Consideraciones de seguridad del sistema para AEM Screens.


## Documentación técnica sobre la seguridad de AEM Screens {#white-paper}

En esta sección se describe el documento técnico. (Documento adjunto a la documentación técnica pendiente)


## Preguntas frecuentes sobre la seguridad de AEM Screens {#faqs-screens}

Las siguientes preguntas frecuentes suponen una arquitectura de reproductor autenticada y registrada. AEM Utiliza HTTPS como protocolo de comunicación entre el reproductor y el servidor de.

### FAQ 1 {#faq1}

¿Se puede redirigir el tráfico del reproductor a un servidor malintencionado e instruirlo para que descargue y reproduzca contenido multimedia malintencionado?

**Respuesta**

No es posible porque la conexión HTTP identifica ambos extremos de la conexión y la cifra. Si intenta estar en el medio e interceptarlo, solo verá contenido encriptado. Si intenta suplantar al servidor, el reproductor le rechazará porque el certificado es diferente.


### FAQ 2 {#faq2}

¿Debo usar HTTP o HTTP?

**Respuesta**

Utilice HTTP. Este protocolo es obligatorio si le preocupa la seguridad. Con HTTP, la comunicación se cifra entre el reproductor y el servidor, y es imposible interceptar el contenido o modificarlo.


### FAQ 3 {#faq3}

En una descarga de contenido, ¿hay algún tipo de firma del contenido o hash?

**Respuesta**

El servidor firma todos los recursos (SHA). A continuación, el reproductor lo valida para el mismo hash a fin de garantizar la integridad.
Si el hash no coincide, el software intenta revalidarlo tres veces. Después de tres intentos, el comando de descarga se considera no válido.


### PREGUNTAS FRECUENTES 4 {#faq4}

AEM ¿Es seguro el servidor?

**Respuesta**

Si está en AMS, el software se encarga de toda la seguridad del servidor mediante las mismas funciones que Sites o Assets.


### PREGUNTAS FRECUENTES 5 {#faq5}

¿Es seguro el dispositivo?

**Respuesta**

En teoría, un reproductor físicamente comprometido puede manipularse para reproducir cualquier contenido. También puede desconectar el reproductor y conectar una memoria USB/HDMI.

Ponga los dispositivos fuera del alcance, preferiblemente en un contenedor seguro, con el cableado asegurado también. Deshabilite también cualquier puerto remoto IR.

Si el sistema operativo del dispositivo no se actualiza con regularidad, el sistema operativo puede quedar expuesto a agujeros de seguridad y permitir ataques remotos a través de la red.

>[!NOTE]
>
>Se recomienda instrumentar los dispositivos con capacidades decentes de actualización y control remotos (escritorio remoto, solución MDM, etc.). También se recomienda utilizar una red privada, no expuesta al WIFI público, por ejemplo.


### PREGUNTAS FRECUENTES 6 {#faq6}

¿Cómo intentaría un hacker comprometer a un jugador?

**Respuesta**

La única manera de comprometer un dispositivo de reproducción es:

1. comprometer el DNS para suplantar al servidor en este nombre de host, y,
1. avenencia
   1. el certificado del lado del servidor para suplantar al servidor
   1. y suplantar el certificado del lado del cliente

>[!IMPORTANT]
>AEM Incluso si un dispositivo está en peligro, puede revocar fácilmente sus credenciales para que ya no se pueda conectar a la red de dispositivos de forma que pueda volver a conectarse a la interfaz de usuario de la red de la red de seguridad de su dispositivo.





