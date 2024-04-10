---
title: Reconocimiento de voz en AEM Screens
description: La página describe la función de reconocimiento de voz en AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 2%

---

# Reconocimiento de voz en AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Información importante sobre privacidad**
>
>Al utilizar la función de reconocimiento de voz, siga todas las directrices legales y éticas aplicables en su región (incluyendo, entre otras, la notificación visible a los usuarios finales de que el reproductor está utilizando el reconocimiento de voz). Adobe Inc., no recibe, almacena ni procesa ninguna información relacionada con la voz. Los reproductores de AEM Screens utilizan la API de voz web estándar integrada en el motor de navegación. Entre bastidores, esta API envía una forma de onda de su discurso a los servidores de Google para convertirlo de voz en texto y el reproductor compara este texto con las palabras clave configuradas.
>
>Consulte [Documento técnico de privacidad de Google sobre la API de voz web](https://www.google.com/chrome/privacy/whitepaper.html#speech) para obtener más información.


La función de reconocimiento de voz permite cambiar el contenido en un canal de AEM Screens impulsado por la interacción de voz.

Un autor de contenido puede configurar una pantalla para que esté habilitada para voz. El propósito de esta función es permitir que los clientes utilicen la voz como un método para interactuar con sus pantallas. Algunos casos de uso similares incluyen encontrar recomendaciones de productos en tiendas, ordenar elementos de menú en comensales y restaurantes. Esta función aumenta la accesibilidad para los usuarios y puede mejorar en gran medida la experiencia del cliente.

>[!NOTE]
>El hardware del reproductor debe admitir entradas de voz, como un micrófono.

## Implementación del reconocimiento de voz {#implementing}

>[!IMPORTANT]
> La función de reconocimiento de voz solo está disponible en reproductores Windows y Chrome OS.

Para implementar el reconocimiento de voz en el proyecto de AEM Screens, debe habilitar el reconocimiento de voz para la pantalla y asociar cada canal con una etiqueta única para almacenar en déclencheur una transición de canal.

En la siguiente sección se describe cómo habilitar y utilizar la función de reconocimiento de voz en un proyecto de AEM Screens.

## Conmutador de canal de visualización de contenido en pantalla completa o en pantalla dividida {#sequence-channel}

Antes de usar la función de reconocimiento de voz, asegúrese de que tiene un proyecto y un canal con contenido configurado para su proyecto.

1. El siguiente ejemplo muestra un proyecto de demostración denominado **VoiceDemo** y tres canales de secuencia **Principal**, **Bebidas frías**, y **Bebidas**, como se muestra en la figura siguiente.

   ![imagen](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Para aprender a crear un canal o añadir contenido a un canal, consulte [Creación y administración de canales](/help/user-guide/managing-channels.md)

   O bien,

   Puede crear tres canales de secuencia **Principal**, **Bebidas frías**, y **Bebidas** y un canal adicional de pantallas divididas 1x2 **SplitScreen** como se muestra en la figura siguiente.

   ![imagen](assets/voice-recognition/vr-emb-1.png)

1. Vaya a cada uno de los canales y añada contenido. Por ejemplo, vaya a **VoiceDemo** > **Canales** > **Principal** y seleccione el canal. Clic **Editar** en la barra de acciones para abrir el editor y añadir contenido (imágenes/vídeos) según sus necesidades. Del mismo modo, agregue contenido a ambos **Bebidas frías** y el **Bebidas** canal.

   Los canales ahora contienen recursos (imágenes), como se muestra en las figuras siguientes.

   **Principal**:

   ![imagen](assets/voice-recognition/vr-4.png)

   **Bebidas frías**:

   ![imagen](assets/voice-recognition/vr-3.png)

   **Bebidas**:

   ![imagen](assets/voice-recognition/vr-2.png)

   Si ha añadido el canal de Pantallas divididas al proyecto, vaya a **SplitScreen** y arrastre y suelte dos secuencias incrustadas y agregue rutas a ambas. **Bebidas frías** y **Bebidas** como se muestra en la figura siguiente.
   ![imagen](assets/voice-recognition/vr-emb-6.png)


### Configuración de etiquetas para canales {#setting-tags}

Una vez que haya añadido contenido a sus canales, debe navegar a cada uno de ellos y añadir las etiquetas adecuadas que puedan déclencheur el reconocimiento de voz.

Siga los pasos a continuación para añadir etiquetas a su canal:

1. Vaya a cada uno de los canales y añada contenido. Por ejemplo, vaya a **VoiceDemo** > **Canales** > **Principal** y seleccione el canal.

1. Clic **Propiedades** de la barra de acciones.

   ![imagen](assets/voice-recognition/vr-5.png)

1. Vaya a **Conceptos básicos** y seleccione una etiqueta ya existente de la **Etiquetas** o cree uno nuevo.

   Puede crear una etiqueta nueva escribiendo un nombre nuevo para la etiqueta y la visita `return` , como se muestra en la figura siguiente:

   ![imagen](assets/voice-recognition/vr-6.png)

   O bien,

   AEM También puede crear etiquetas a partir de la instancia de de antemano para su proyecto y seleccionarlas. Una vez que haya seguido los pasos explicados en [Creación de etiquetas](#creating-tags), puede seleccionar la etiqueta de la ubicación y añadirla a su canal, como se muestra en la figura siguiente:

   ![imagen](assets/voice-recognition/vr-tag1.png)

1. Del mismo modo, agregue la etiqueta con el título **ardiente** a la **Bebidas** canal.

1. Si utiliza un canal de Pantallas divididas, añada ambas etiquetas (**ardiente** y **frío**) a la **SplitScreen** propiedades del canal, como se muestra en la figura siguiente.

   ![imagen](assets/voice-recognition/vr-emb-7.png)

1. Clic **Guardar y cerrar** una vez que haya terminado.


### Creación de etiquetas {#creating-tags}

Siga los pasos a continuación para crear etiquetas:

1. AEM Vaya a la instancia de la.

1. Haga clic en el icono de herramientas > **Etiquetado**.
   ![imagen](assets/voice-recognition/vr-7.png)

1. Clic **Crear** > **Crear área de nombres**.
   ![imagen](assets/voice-recognition/vr-tag3.png)

1. Introduzca el nombre del proyecto, por ejemplo: **VoiceDemo** y haga clic en **Crear**.

1. Seleccione el **VoiceDemo** proyecto y haga clic en **Crear etiqueta** de la barra de acciones.
   ![imagen](assets/voice-recognition/vr-tag4.png)

1. Introduzca el nombre de la etiqueta y haga clic en **Enviar**.
   ![imagen](assets/voice-recognition/vr-tag5.png)

Ahora puede utilizar estas etiquetas en su proyecto de AEM Screens.

### Asignación de canales a una pantalla y activación del reconocimiento de voz {#channel-assignment}

1. Cree una visualización en la **Ubicaciones** , como se muestra en la figura siguiente.

   ![imagen](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Asignar los canales **Principal**, **Bebidas frías**, y **Bebidas** a su **LobbyDisplay**. Además, si utiliza el **SplitScreen** canal del proyecto, asegúrese de asignarlo a la pantalla.

   >[!NOTE]
   >Si ha creado un canal de pantalla dividida, asigne la variable **SplitScreen** canal a la pantalla.

1. Establezca las siguientes propiedades en cada uno de los canales al asignar el canal.

   | **Nombre del canal** | **Prioridad** | **Eventos admitidos** |
   |---|---|---|
   | Principal | 2 | Carga inicial, pantalla inactiva, temporizador |
   | Bebidas | 1 | Interacción del usuario |
   | Bebidas frías | 1 | Interacción del usuario |
   | SplitScreen | 1 | Interacción del usuario |

   >[!NOTE]
   >
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Una vez asignados los canales a una pantalla, vaya a **LobbyDisplay** y seleccione la pantalla. Seleccionar **Propiedades** de la barra de acciones.

1. Vaya a **Mostrar** y activar **Voz habilitada** opción en **Contenido**.

   ![imagen](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >Es obligatorio activar la función de reconocimiento de voz desde la pantalla.

### Visualización del contenido en el reproductor de Chrome {#viewing-content}

Una vez completados los pasos anteriores, puede registrar el dispositivo Chrome para ver la salida.

>[!NOTE]
>Consulte [Registro de dispositivos](device-registration.md) para aprender a registrar un dispositivo en un reproductor de AEM Screens.

**Salida deseada para el canal de secuencia**

El **Principal** canal está reproduciendo su contenido, pero cuando utiliza palabras con palabra clave **ardiente** como *Me gustaría tomar una bebida caliente*, el canal comienza a reproducir el contenido del **Bebidas** canal.

Del mismo modo, si utiliza Word con una palabra clave **frío** como *Me gustaría tener algo frío*, el canal comienza a reproducir el contenido del **Bebidas frías** canal.

**Salida deseada para el canal de pantallas divididas**

El **Principal** canal está reproduciendo su contenido, pero cuando utiliza palabras con palabra clave **ardiente** y **frío** juntos, como *Me gustaría ver el menú de bebidas frías y calientes*, el canal comienza a reproducir el contenido del **SplitScreen** canal. Si usted dice *volver al menú principal*, vuelve al canal principal.
