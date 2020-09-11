---
title: Lista de comprobación de seguridad para AEM Screens
seo-title: Lista de comprobación de seguridad para AEM Screens
description: La página describe la lista de comprobación de seguridad para AEM Screens
seo-description: La página describe la lista de comprobación de seguridad para AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 1%

---


# Consideraciones de seguridad del sistema para AEM Screens {#security-checklist}

>[!IMPORTANT]
>Se trata de un recurso Git interno.

Esta página resalta las consideraciones de seguridad del sistema para AEM Screens.


## Documento técnico para la seguridad de AEM Screens {#white-paper}

Esta sección describe el documento técnico. (Documento técnico pendiente adjunto)


## Preguntas más frecuentes sobre AEM Screens Security {#faqs-screens}

Las siguientes preguntas más frecuentes asumen una arquitectura de reproductor autenticada y registrada usando HTTPS como protocolo de comunicación entre reproductor y AEM Server.

### FAQ 1 {#faq1}

¿Se puede volver a enrutar el tráfico del reproductor a un servidor malintencionado e indicar que descargue y reproduzca contenido multimedia malintencionado?

**Respuesta**

No es posible porque la conexión HTTP identifica ambos extremos de la conexión y la cifra. Si tratas de estar en el medio e interceptarlo, solo ves contenido cifrado, y si tratas de suplantar al servidor, el reproductor te rechazará porque tu certificado es diferente.


### FAQ 2 {#faq2}

¿Debo usar HTTP o HTTP?

**Respuesta**

Utilice HTTP. Esto es imprescindible si le preocupa la seguridad. Con HTTPs la comunicación se encripta entre reproductor y servidor, e interceptar el contenido o modificarlo será casi imposible.


### FAQ 3 {#faq3}

En una descarga de contenido, ¿hay algún tipo de firma del contenido o hash?

**Respuesta**

Cada recurso está firmado (SHA) por el servidor y luego validado por el reproductor para el mismo hash para garantizar la integridad.
Si el hash no coincide, intentamos volver a validar 3 veces. Después de 3 intentos, consideramos que el comando download no es válido.


### FAQ 4 {#faq4}

¿AEM Server es seguro?

**Respuesta**

Ans 4. Si está en AMS, nos encargamos de toda la seguridad del servidor utilizando las mismas funciones que Sitios o Recursos.


### FAQ 5 {#faq5}

¿Es seguro el dispositivo?

**Respuesta**

Un reproductor físicamente comprometido puede ser teóricamente manipulado para reproducir cualquier contenido. También se puede conectar el reproductor y conectar un dispositivo USB/HDMI.

Por lo tanto, se recomienda poner los dispositivos fuera del alcance, preferiblemente en un contenedor seguro, con el cableado también asegurado. También deshabilite los puertos remotos IR.

Si el sistema operativo del dispositivo no se actualiza con regularidad, el sistema operativo puede quedar expuesto a agujeros de seguridad y permitir ataques remotos a través de la red.

>[!NOTE]
>
>Se recomienda instrumentar los dispositivos con capacidades de control y actualización remota decentes (escritorio remoto, solución MDM, etc.). También se recomienda utilizar una red privada, no expuesta a la WIFI pública, por ejemplo.


### FAQ 6 {#faq6}

¿Cómo intentaría un hacker comprometer a un jugador?

**Respuesta**

La única forma de poner en peligro un dispositivo reproductor es:

1. comprometa el DNS a suplantar el servidor en su nombre de host, y
1. compromiso
   1. el servidor de certificados para suplantar el servidor
   1. y suplantar el certificado en el lado del cliente

>[!IMPORTANT]
>Incluso si un dispositivo está en peligro, puede revocar fácilmente sus credenciales para que ya no pueda conectarse a AEM.





