---
title: Reconocimiento de voz en AEM Screens
description: La página describe la función de reconocimiento de voz en AEM Screens.
translation-type: tm+mt
source-git-commit: e355d648846034c4762ef8fdcb3e218d868044b6
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 3%

---


# Reconocimiento de voz en AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Información de privacidad importante**
>
>Al utilizar la función de reconocimiento de voz, siga todas las directrices legales y éticas aplicables para su región (incluso, entre otras cosas, para proporcionar a los usuarios finales un aviso visible de que el reproductor está utilizando el Reconocimiento de voz). Adobe Inc., no recibe, almacena ni procesa ninguna información relacionada con la voz. Los reproductores de AEM Screens utilizan la API de voz web estándar integrada en el motor de navegación. Entre bastidores, esta API envía una forma de onda de su discurso a los servidores de Google para la conversión de voz a texto y este texto coincide con el reproductor en comparación con las palabras clave configuradas.
>
>Consulte el documento técnico Privacidad de [Google en la API](https://www.google.com/chrome/privacy/whitepaper.html#speech) de voz web para obtener más información.


La función de reconocimiento de voz permite cambiar el contenido en un canal de AEM Screens impulsado por la interacción de voz.

Un autor de contenido puede configurar una pantalla para que esté habilitada para voz. El propósito de esta función es permitir que los clientes utilicen la voz como método para interactuar con sus pantallas. Algunos casos de uso similares incluyen la búsqueda de recomendaciones de productos en tiendas, pedidos de artículos de menú en restaurantes y restaurantes. Esta función aumenta la accesibilidad para los usuarios y puede mejorar considerablemente la experiencia del cliente.

>[!NOTE]
>El hardware del reproductor debe admitir la entrada de voz, como un micrófono.

## Implementación del reconocimiento de voz {#implementing}

>[!IMPORTANT]
> La función de reconocimiento de voz solo está disponible en reproductores Chrome OS y Windows.

Para implementar el reconocimiento de voz en su proyecto de AEM Screens, debe habilitar el reconocimiento de voz para la visualización y asociar cada canal con una etiqueta única para activar una transición de canal.

En la sección siguiente se describe cómo habilitar y utilizar la función de reconocimiento de voz en un proyecto de AEM Screens.

## Visualización de contenido en pantalla completa o cambio de Canal de pantalla dividida {#sequence-channel}

Antes de utilizar la función de reconocimiento de voz, asegúrese de que tiene un proyecto y un canal con contenido configurado para el proyecto.

1. En el siguiente ejemplo se muestra un proyecto de demostración denominado **VoiceDemo** y tres canales de secuencia **Main**, **ColdDrinks** y **HotDrinks**, como se muestra en la figura siguiente.

   ![image](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Para obtener información sobre cómo crear un canal o agregar contenido a un canal, consulte [Creación y administración de Canales](/help/user-guide/managing-channels.md)

   O bien,

   Puede crear tres canales de secuencia **Principal**, **ColdDrinks** y **HotDrinks**, y un canal de pantalla dividida 1x2 adicional **SplitScreen** como se muestra en la siguiente figura.

   ![image](assets/voice-recognition/vr-emb-1.png)

1. Navegue hasta cada uno de los canales y agregue contenido. Por ejemplo, vaya a **VoiceDemo** —> **Canales** —> **Principal** y seleccione el canal. Haga clic en **Editar** en la barra de acciones para abrir el editor y agregar contenido (imágenes/vídeos) según sus necesidades. Del mismo modo, agregue contenido tanto a **ColdDrinks** como al canal **HotDrinks** .

   Los canales ahora contienen recursos (imágenes), como se muestra en las figuras siguientes.

   **Principal**:

   ![image](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![image](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![image](assets/voice-recognition/vr-2.png)

   Si ha agregado el canal Dividir pantallas al proyecto, navegue hasta **SplitScreen** y arrastre y suelte dos secuencias incrustadas y agregue rutas al canal **ColdDrinks** y **HotDrinks** como se muestra en la figura siguiente.
   ![image](assets/voice-recognition/vr-emb-6.png)


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

   También puede crear etiquetas a partir de la instancia de AEM de antemano para el proyecto y seleccionarlas. Una vez que siga los pasos explicados en [Creación de etiquetas](#creating-tags), puede seleccionar la etiqueta desde la ubicación y agregarla a su canal, como se muestra en la figura siguiente:

   ![image](assets/voice-recognition/vr-tag1.png)

1. Del mismo modo, agregue la etiqueta titulada como **activo** al canal **HotDrinks** .

1. Si utiliza un canal Dividir pantallas, agregue ambas etiquetas (**caliente** y **fría**) a las propiedades del canal **SplitScreen** , como se muestra en la figura siguiente.

   ![image](assets/voice-recognition/vr-emb-7.png)

1. Haga clic en **Guardar y cerrar** una vez que haya terminado.


### Creación de etiquetas {#creating-tags}

Siga los pasos a continuación para crear etiquetas:

1. Vaya a la instancia de AEM.

1. Haga clic en el icono de herramientas —> **Etiquetado**.
   ![image](assets/voice-recognition/vr-7.png)

1. Haga clic en **Crear** —> **Crear Área de nombres**.
   ![image](assets/voice-recognition/vr-tag3.png)

1. Escriba el nombre del proyecto, por ejemplo, **VoiceDemo** y haga clic en **Crear**.

1. Seleccione el proyecto **VoiceDemo** y haga clic en **Crear etiqueta** en la barra de acciones.
   ![image](assets/voice-recognition/vr-tag4.png)

1. Escriba el nombre de la etiqueta y haga clic en **Enviar**.
   ![image](assets/voice-recognition/vr-tag5.png)

Ahora puede utilizar estas etiquetas en su proyecto de AEM Screens.

### Asignación de Canales a una visualización y activación del reconocimiento de voz {#channel-assignment}

1. Cree una pantalla en la carpeta **Ubicaciones** , como se muestra en la figura siguiente.

   ![image](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Asigne los canales **Principal**, **Refrescos** y **Bebidas** calientes **a su** pantalla de vestíbulo. Además, si utiliza el canal **SplitScreen** para su proyecto, asegúrese de asignarlo a la pantalla.

   >[!NOTE]
   >Si ha creado un canal de pantalla dividida, asigne el canal **SplitScreen** a la pantalla.

1. Defina las siguientes propiedades en cada uno de los canales, mientras asigna el canal.

   | **Nombre del canal** | **Prioridad** | **Eventos admitidos** |
   |---|---|---|
   | Principal | 2 | Carga inicial, Pantalla inactiva, Temporizador |
   | HotDrinks | 1 | Interacción del usuario |
   | ColdDrinks | 1 | Interacción del usuario |
   | SplitScreen | 1 | Interacción del usuario |

   >[!NOTE]
   >
   >Para obtener información sobre cómo asignar un canal a una pantalla, consulte [Creación y administración de pantallas](/help/user-guide/managing-displays.md).

1. Una vez que haya asignado canales a una pantalla, navegue hasta la **pantalla del vestíbulo** y seleccione la pantalla. Seleccione **Propiedades** en la barra de acciones.

1. Vaya a la ficha **Mostrar** y active la opción **Voz habilitada** en **Contenido**.

   ![image](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >Es obligatorio activar la función de reconocimiento de voz desde la pantalla.

### Visualización del contenido en Chrome Player {#viewing-content}

Una vez completados los pasos anteriores, puede registrar el dispositivo cromado para vista de la salida.

>[!NOTE]
>Consulte Registro [](device-registration.md) del dispositivo para obtener información sobre cómo registrar un dispositivo en un reproductor de AEM Screens.

**Salida deseada para el Canal de secuencia**

El canal **Principal** reproduce su contenido, pero cuando se utilizan palabras con palabras clave **calientes** como *quisiera tomar una bebida* caliente, los inicios de canal reproducen el contenido del canal **HotDrinks** .

Del mismo modo, si utiliza palabras con una palabra clave **fría** como *me gustaría tener algo frío*, los inicios de canal juegan con el contenido del canal **ColdDrinks** .

**Salida deseada para el Canal de pantallas divididas**

El canal **principal** reproduce su contenido, pero cuando se utilizan palabras con palabras clave **calientes** y **frías** como *me gustaría ver el menú para bebidas* frías y calientes, los inicios de canal reproducen el contenido del canal **SplitScreen** . Si vuelve *al menú* principal, vuelve al canal principal.





