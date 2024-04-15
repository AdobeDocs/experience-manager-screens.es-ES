---
title: Información general y configuraciones de la arquitectura de representaciones adaptables
description: Obtenga información acerca de la descripción general de la arquitectura y las configuraciones en CRXDE Lite para representaciones adaptables en AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 3%

---

# Representaciones adaptables: Información general de arquitectura y configuraciones {#adaptive-renditions}

## Introducción {#introduction}

Las representaciones adaptables permiten a los dispositivos seleccionar automáticamente la mejor representación para un dispositivo en función de las reglas definidas por el cliente. Los dispositivos descargan y reproducen automáticamente la representación más adecuada de un recurso en función de estas reglas, lo que permite a los clientes centrarse únicamente en diseñar el *main* experiencia.

## Objetivo {#objective}

Como desarrollador de AEM Screens, ahora puede configurar representaciones de recursos específicas del dispositivo para que se descarguen y reproduzcan automáticamente sin tener que crear todas las variaciones de contenido manualmente. Configure las representaciones adaptables para que un autor de contenido pueda utilizar esta función en un canal de AEM Screens.

## Información general de la arquitectura {#architectural-overview}

Las representaciones adaptables se basan en la idea de tener varias representaciones de un recurso con el nombre según una convención de nombres específica. La decisión de reproducir una representación específica se toma mediante la evaluación de expresiones de consulta de medios que solo se pueden resolver en dispositivos con las capacidades esperadas.

La capacidad de tener un patrón de nomenclatura de representación asociado define una regla de asignación de representación, como vertical u horizontal, como se muestra en la figura siguiente. Después de calcular todas las expresiones disponibles, el reproductor Screens recopila los patrones de nomenclatura correspondientes a las reglas coincidentes. Los patrones se utilizan para encontrar las representaciones correctas durante la reproducción de la secuencia buscando los patrones en los nombres de representación.

![imagen](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Adición de la propiedad de asignación de representación al proyecto de Pantallas {#rendition-mapping-new}

Para habilitar la función Representaciones adaptables, deben estar presentes las siguientes reglas de asignación y la Configuración según el contexto (CA) debe poder resolverse en canales y pantallas.

>[!NOTE]
>Para obtener más información sobre las configuraciones según el contenido, consulte [aquí](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Siga los pasos a continuación para configurar la configuración:

1. Vaya a **CRXDE Lite**. Compruebe si el **rendition-mapping** La configuración de existe en `/conf/screens/sling:configs/rendition-mapping`, como se muestra en la figura siguiente.

   >![imagen](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si ha instalado el paquete de funciones más reciente 202109, verá el **rendition-mapping** estructura de nodos previamente rellenada en `/conf/screens/sling:configs/rendition-mapping` en CRXDE Lite. Consulte [Notas de la versión del paquete de funciones 202109](/help/user-guide/release-notes-fp-202109.md) para obtener más información sobre el último paquete de funciones.
   >Para los proyectos existentes, asegúrese de que el proyecto de Pantallas tenga el **rendition-mapping** configuración asociada. Consulte [Agregar una asignación de representación a un proyecto existente](#rendition-mapping-existing) para obtener más información.

### Agregar una propiedad de asignación de representación a un proyecto existente {#rendition-mapping-existing}

1. Vaya a **CRXDE Lite**.

1. Defina explícitamente la asociación de representación y asignación agregando `sling:configRef` propiedad que señala a `/conf/screens` al nodo de contenido del proyecto, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Adición de reglas de asignación de representación {#add-rendition-mapping-rules}

Siga los pasos a continuación para agregar un nodo en Asignación de representación:

1. Vaya a esta ruta `/conf/screens/sling:configs/rendition-mapping` de **CRXDE Lite**.
1. Cree un nodo en **rendition-mapping**. Clic con el botón derecho **rendition-mapping** y seleccione **Crear** > **Crear nodo**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Introduzca el **Nombre** para la regla de asignación, como **regla1** y el nodo **Tipo** as **`nt:unstructured`** in **Crear nodo** Cuadro de diálogo. Seleccionar **OK**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Agregue la propiedad expression con el valor que contiene la expresión de consulta.

   >[!NOTE]
   >Consulte [Uso de sintaxis de consulta de medios](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) para obtener más información.

   Seleccionar **regla1** que ha creado y escriba **expresión** in **Nombre** y **(orientación:horizontal)** in **Valor**, como se muestra a continuación. Seleccione **Añadir**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Agregue la propiedad pattern con el valor que contiene el patrón de nomenclatura de representación.

   >[!NOTE]
   >El valor definido en la propiedad pattern coincide con la nueva representación de recursos y se selecciona, si la expresión se evalúa como true.

   Para añadir la propiedad pattern, seleccione **regla1** que ha creado y escriba **pattern** in **Nombre** y **horizontal** in **Valor**, como se muestra a continuación. Seleccione **Añadir**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Seleccionar **Guardar todo** y observe las propiedades bajo el nodo creado en **rendition-mapping**.

   ![imagen](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Pasos siguientes {#next-steps}

Después de agregar propiedades y reglas de asignación de representación, como autor de contenido, puede configurar los recursos. Para ello, utilice representaciones adaptables y también migre los dispositivos de redes grandes para utilizar esta función en los canales de AEM Screens. Consulte [Uso de representaciones adaptables en AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obtener más información.
