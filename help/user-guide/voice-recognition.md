---
title: Reconocimiento de voz en AEM Screens
description: La página describe la función de reconocimiento de voz en AEM Screens.
translation-type: tm+mt
source-git-commit: b7d7d4ec200d3eb7cd7bac4253c8664e5bd4de81
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---


# Reconocimiento de voz en AEM Screens {#voice-recognition}

>[IMPORTANTE]
>**Información de privacidad importante**
>Al utilizar la función Reconocimiento de voz, siga todas las directrices legales y éticas aplicables para su región (incluido, entre otras cosas, el envío de un aviso visible a los usuarios finales de que el reproductor está utilizando el Reconocimiento de voz). Adobe Inc., no recibe, almacena ni procesa ninguna información relacionada con la voz. Los reproductores de AEM Screens utilizan la API de voz web estándar integrada en el motor de navegación. Entre bastidores, se envía una forma de onda de su discurso a los servidores de Google para la conversión de voz a texto y este texto coincide con el reproductor con las palabras clave configuradas.
>
>Consulte el documento técnico Privacidad de [Google en la API](https://www.google.com/chrome/privacy/whitepaper.html#speech) de voz web para obtener más información.


## Información general {#overview}

La función de reconocimiento de voz permite cambiar el contenido de un canal de AEM Screens impulsado por la interacción de voz.

Un autor de contenido puede configurar una pantalla para que esté habilitada para voz. El propósito de esta función es permitir que los clientes utilicen la voz como método para interactuar con sus pantallas. Algunos casos de uso similares incluyen la búsqueda de recomendaciones de productos en tiendas, pedidos de artículos de menú en restaurantes y restaurantes. Esta función aumenta la accesibilidad para los usuarios y puede mejorar considerablemente la experiencia del cliente.


>[!NOTE]
>El hardware del reproductor debe admitir la entrada de voz, como un micrófono.

>[!IMPORTANT]
> La función de reconocimiento de voz solo está disponible en reproductores de Chrome y Electron.

## Implementación del reconocimiento de voz {#implementing}


Para implementar el reconocimiento de voz en su proyecto de AEM Screens, debe habilitar el reconocimiento de voz para la visualización y asociar cada canal con una etiqueta única para activar una transición de canal.

En la sección siguiente se describe cómo activar y utilizar la función Reconocimiento de voz en un proyecto de AEM Screens.

### Configuración del proyecto {#setting-up}

Antes de utilizar la función de reconocimiento de voz, asegúrese de que tiene un proyecto y un canal con contenido configurado para el proyecto.

1. En el siguiente ejemplo se muestra un proyecto de demostración denominado **VoiceDemo** y tres canales de secuencia **Main**, **ColdDrinks** y **HotDrinks**, como se muestra en la figura siguiente.

   ![image](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo crear un canal o agregar contenido a un canal, consulte [Creación y administración de Canales](/help/user-guide/managing-channels.md)

1. Navegue hasta cada uno de los canales y agregue contenido. Por ejemplo, vaya a **VoiceDemo** —> **Canales** —> **Principal** y seleccione el canal. Haga clic en **Editar** en la barra de acciones para abrir el editor y agregar contenido (imágenes/vídeos) según sus necesidades. Del mismo modo, agregue contenido tanto a **ColdDrinks** como al canal **HotDrinks** .

   Los canales ahora contienen recursos (imágenes), como se muestra en las figuras siguientes.

   **Principal**:

   ![image](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![image](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![image](assets/voice-recognition/vr-2.png)

### Configuración de etiquetas para Canales {#setting-tags}

Una vez que haya agregado contenido a sus canales, debe desplazarse a cada uno de los canales y agregar las etiquetas apropiadas que activarían el reconocimiento de voz.

Siga los pasos a continuación para agregar etiquetas a su canal:

1. Navegue hasta cada uno de los canales y agregue contenido. Por ejemplo, vaya a **VoiceDemo** —> **Canales** —> **Principal** y seleccione el canal.

1. Click **Properties** from the action bar.

   ![image](assets/voice-recognition/vr-5.png)

1. Vaya a la ficha **Conceptos básicos** y seleccione una etiqueta existente en el campo **Etiquetas** o cree una nueva.

   Puede crear una nueva etiqueta escribiendo un nuevo nombre para la etiqueta y la `return` tecla de visita, como se muestra en la figura siguiente:

   ![image](assets/voice-recognition/vr-6.png)

   O bien,

   Puede crear etiquetas a partir de la instancia de AEM de antemano para el proyecto y seleccionarlas también. Una vez que siga los pasos explicados en [Creación de etiquetas](#creating-tags), puede seleccionar la etiqueta desde la ubicación y agregarla a su canal, como se muestra en la figura siguiente:

   ![image](assets/voice-recognition/vr-tag1.png)

1. Haga clic en **Guardar y cerrar** una vez que haya terminado.

Del mismo modo, agregue la etiqueta titulada como **activo** al canal **HotDrinks** .

#### Creación de etiquetas {#creating-tags}

Siga los pasos a continuación para crear etiquetas:

1. Vaya a la instancia de AEM.
1. Haga clic en las herramientas —> **Etiquetado**.
   ![image](assets/voice-recognition/vr-7.png)
1. Haga clic en **Crear** —> **Crear Área de nombres**.
   ![image](assets/voice-recognition/vr-7.png)
1. Escriba el nombre del proyecto, por ejemplo: **VoiceDemo** y haga clic en Crear.
1. Seleccione el proyecto **VoiceDemo** y haga clic en **Crear etiqueta** en la barra de acciones.
1. Haga clic en **Enviar**.


### Asignación de Canales a una visualización y activación del reconocimiento de voz {#channel-assignment}

1. Cree una pantalla en la carpeta **Ubicaciones** , como se muestra en la figura siguiente.

   ![image](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Asigne los canales **Principal**, **Refrescos** y **Bebidas** calientes **a su** pantalla de vestíbulo.

1. Defina las siguientes propiedades en cada uno de los canales, mientras asigna el canal.

   | **Nombre del canal** | **Prioridad** | **Eventos admitidos** |
   |---|---|---|
   | Principal | 2 | Carga inicial, Pantalla inactiva, Temporizador |
   | HotDrinks | 1 | Interacción del usuario |
   | ColdDrinks | 1 | Interacción del usuario |

   >[!NOTE]
   >
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Una vez que haya asignado canales a una pantalla, navegue hasta la **pantalla del vestíbulo** y seleccione la pantalla. Seleccione **Propiedades** en la barra de acciones.

1. Vaya a la ficha **Mostrar** y active la opción **Voz habilitada** en **Contenido**.

   ![image](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >Es obligatorio activar la función de reconocimiento de voz desde la pantalla.

#### Visualización del contenido en Chrome Player {#viewing-content}

Una vez completados los pasos anteriores, puede registrar el dispositivo cromado y vista de la salida.

>[!NOTE]
>Consulte Registro [](device-registration.md) del dispositivo para obtener información sobre cómo registrar un dispositivo en un reproductor de AEM Screens.

Este ejemplo muestra la salida en un reproductor Chrome.

![newimage](assets/voice-recognition/voice-video.gif)












