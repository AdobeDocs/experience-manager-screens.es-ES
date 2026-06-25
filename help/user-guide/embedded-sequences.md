---
title: Secuencias incrustadas
description: Obtenga información sobre las secuencias incrustadas de los canales que permiten agregar componentes al canal principal. O bien, reutilice el contenido de un canal diferente e incrústelo en el canal principal.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
TQID: https://experienceleague.adobe.com/NK6M9ShPUQdDQQvgx7kD9c4uvfKjy61wJ6jSH0gB17E
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: ba4275ba-c29a-4197-90dc-5a633402ca3cid: d4878390-3838-4e80-8cb3-33bc1a01ea16id: d8a4be83-7d41-47be-b4a6-f8f3d35cacebid: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 811
ht-degree: 0%

---

# Secuencias incrustadas {#embedded-sequences}

>[!IMPORTANT]
>Este contenido es válido para AEM on-premise/AMS (AEM 6.5LTS y AEM 6.5). Para el contenido de AEM as a Cloud Service Screens, consulte la [guía de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Con ***Secuencias incrustadas***, en el caso de los canales, un usuario puede agregar componentes en el canal principal y también reutilizar el contenido de un canal diferente e incrustarlo en el canal principal.

## Adición de secuencias incrustadas {#adding-embedded-sequences}

Tiene la opción de añadir los siguientes componentes al canal de secuencia:

* Secuencia integrada
* Secuencia integrada dinámica

>[!NOTE]
>
>Para obtener más información sobre el uso de otros componentes en el proyecto de Screens, consulte [Agregar componentes a un canal](adding-components-to-a-channel.md).

### Añadir una secuencia incrustada {#adding-an-embedded-sequence}

Puede añadir una secuencia incrustada al canal. Una secuencia incrustada es otro canal que incluye recursos como imágenes o vídeos. Añadir una secuencia incrustada permite al usuario agregar la secuencia a un canal mediante ***Ruta del canal***.

>[!NOTE]
>***Ruta de acceso al canal*** define una referencia explícita al canal.
>Para obtener más información acerca de *Ruta del canal*, consulte [Asignación del canal](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia incrustada al canal:

1. Haga clic en el canal en el que desee incrustar una página. Por ejemplo, **`We.Retail`En tienda** > **Canales** > **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones.
1. En el modo de editor, haga clic en el icono de componentes de la barra lateral izquierda para añadir la página incrustada. Arrastre y suelte la **secuencia incrustada** en el editor.
1. Haga doble clic en el componente **Secuencia incrustada** para que pueda agregar el canal al canal de secuencia original.
1. Haga clic en **Ruta de canal** del canal.
1. Haga clic en **Duración (milisegundos)** para el canal incrustado en la ficha **Secuencia**. De manera predeterminada, la duración se establece en **-1**, lo que significa que el canal incrustado se está ejecutando completamente. Si el usuario especifica una duración, la subsiguiente se interrumpe (es decir, se corta) a la hora especificada.

1. Establezca la **Estrategia de reproducción medida** en **normal**.

De manera predeterminada, se establece en **normal**. Establecer el valor en **normal** (Reproducir todos los elementos) significa que la subsiguiente se ejecuta completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento**. Ese valor solo muestra un elemento de la subsiguiente en cada ejecución. Por ejemplo, el primer elemento del primer bucle y el segundo elemento del segundo bucle.

>[!IMPORTANT]
>
>Asigne el canal que se utiliza en la secuencia incrustada a la misma visualización.
>
>Siga los pasos a continuación después de agregar una secuencia incrustada al canal desde los pasos anteriores:
>
>1. Vaya a la pantalla y haga clic en la pantalla desde la carpeta **Ubicaciones**.
>1. Haga clic en **Tablero** en la barra de acciones.
>1. En el panel de visualización, haga clic en **+ Asignar canales** de los **CANALES ASIGNADOS y PANELES PROGRAMADOS** para poder abrir el **cuadro de diálogo Asignación de canales**.
>
>1. Haga clic en la ruta del canal que utilizó en la secuencia incrustada, en **Ruta del canal**.
>1. Asegúrese de que **Priority** sea inferior al canal principal.
>
>1. No haga clic en **Eventos compatibles**.
>1. Haga clic en **Guardar** cuando haya terminado.
>

El siguiente ejemplo muestra la adición de una secuencia incrustada (**Canal inactivo - Noche**) a un canal existente (**Canal inactivo**).

![nuevo2](assets/new2.gif)

### Adición de una secuencia incrustada dinámica {#adding-a-dynamic-embedded-sequence}

Puede añadir una secuencia incrustada dinámica al canal. Una secuencia incrustada dinámica es similar a una secuencia incrustada, pero permite al usuario seguir una jerarquía en la que los cambios/actualizaciones realizados en un canal se propagan a otro en relación. Sigue una jerarquía principal-secundario y también incluye recursos como imágenes o vídeos. Añadir una secuencia dinámica permite al usuario añadir un canal por función de canal.

>[!NOTE]
>
>***Rol del canal*** define el contexto de la visualización.
>
>Para obtener más información sobre *la función del canal*, consulte [Asignación del canal](channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia incrustada al canal:

1. Haga clic en el canal en el que desee incrustar una secuencia dinámica. Por ejemplo, **`We.Retail`En tienda** > **Canales** > **Canal inactivo**.

1. Haga clic en **Editar** en la barra de acciones.
1. En el modo de editor, haga clic en el icono de componentes de la barra lateral izquierda para añadir la secuencia incrustada dinámica. Arrastre y suelte la **secuencia incrustada** **dinámica** en el editor.

1. Haga doble clic en el componente **Secuencia incrustada** **dinámica** para que pueda agregar la página al canal de secuencia.

1. Escriba el **Rol de asignación de canal**.
1. Establezca la **Estrategia de reproducción medida** en **normal**. De manera predeterminada, se establece en **normal**. Establecer el valor en **normal** (Reproducir todos los elementos) significa que la subsiguiente se ejecuta completamente en cada ciclo de la secuencia principal. El otro valor posible es **Reproducir un solo elemento**. Ese valor solo muestra un elemento de la subsiguiente en cada ejecución. Por ejemplo, el primer elemento del primer bucle y el segundo elemento del segundo bucle.

1. Haga clic en **Duración (milisegundos)** en la ficha **Secuencia** para el canal incrustado en la secuencia.

![más reciente](assets/latest.gif)
