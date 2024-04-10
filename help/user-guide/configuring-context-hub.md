---
title: Configuración de ContextHub en AEM Screens
description: Obtenga información acerca de ContextHub en el motor de segmentación para que pueda definir un almacén de datos para el cambio de contenido del déclencheur de datos.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 1%

---

# Configuración de ContextHub en AEM Screens {#configuring-contexthub-in-aem-screens}

Esta sección hace hincapié en la creación y administración de cambios de recursos impulsados por datos mediante un almacén de datos.

## Términos clave {#key-terms}

Antes de entrar en los detalles de la creación y administración de canales impulsados por el inventario en su proyecto de AEM Screens, conozca algunos de los términos clave para los diferentes escenarios.

**Marca** - Su descripción de alto nivel del proyecto.

**Área** : el nombre del proyecto de AEM Screens, como la señalización de publicidad digital

**Actividad** : define las reglas de categoría como Gobernado por inventario, Gobernado por tiempo o Gobernado por disponibilidad del departamento.

**Audiencia** - Define la regla.

**Segmento** : La versión del recurso que se reproducirá para la regla determinada. Por ejemplo, si la temperatura es inferior a 50 grados Fahrenheit, la pantalla muestra una imagen de una bebida caliente; de lo contrario, una bebida fría.

El diagrama siguiente proporciona una representación visual de cómo las configuraciones de ContextHub coinciden con la actividad, la audiencia y los canales.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condiciones previas {#preconditions}

Antes de empezar a configurar Configuraciones de ContextHub para un proyecto de AEM Screens, debe configurar Hojas de cálculo de Google (para fines de demostración).

>[!IMPORTANT]
>
>En el ejemplo siguiente, se utilizan las Hojas de cálculo de Google como sistema de base de datos de ejemplo desde el que se recuperan los valores y que es únicamente con fines educativos. El Adobe no aprueba el uso de hojas de Google para entornos de producción.
>
>Para obtener más información, consulte [Obtener clave API](https://developers.google.com/maps/documentation/javascript/get-api-key) en la documentación de Google.

## Paso 1: Configuración de un almacén de datos {#step-setting-up-a-data-store}

Puede configurar el almacén de datos como un evento de E/S local o como un evento de base de datos local.

El siguiente ejemplo de déclencheur de datos de nivel de recurso muestra un evento de base de datos local que configura un almacén de datos, como una hoja de Excel, que permite utilizar las configuraciones de ContextHub y la ruta de segmentos al canal de AEM Screens.

Después de configurar el `google` hoja correctamente, como se muestra en el ejemplo siguiente:

![imagen](/help/user-guide/assets/context-hub/context-hub1.png)

La siguiente validación es lo que se ve al comprobar la conexión introduciendo los dos valores, `*google sheet ID*` y `*API key*` en el formato siguiente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![imagen](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>El ejemplo específico siguiente muestra las hojas de cálculo de Google como un almacén de datos que déclencheur un cambio de recurso si el valor es superior a 100 o inferior a 50.

## Paso 2: Configuración de tiendas {#step-setting-store-configurations}

1. **Navegación a ContextHub**

   AEM Navegue hasta la instancia de y haga clic en el icono de herramientas de la barra lateral izquierda. Clic **Sites** > **ContextHub**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creación de una configuración de tienda de ContextHub**

   1. Vaya al contenedor de configuración titulado como **pantallas**.

   1. Seleccionar **Crear** > **Crear contenedor de configuración** e introduzca el título como **ContextHubDemo**.

      ![imagen](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navegar** hasta **ContextHubDemo** > **Crear** **Configuración de ContentHub** y haga clic en **Guardar**.

      >[!NOTE]
      > Después de seleccionar **Guardar**, se encuentra en la **Configuración de ContextHub** pantalla.

   1. Desde el **Configuración de ContextHub** pantalla, seleccione **Crear** > **Configuración de tienda de ContentHub**

   ![imagen](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >AEM AEM Como parte del paquete de funciones 4 o 8 de la versión 6.5 de la versión, los clientes deben actualizar el paquete de funciones 4 o el paquete de funciones 8 de la versión 6.4 de la versión, respectivamente `/conf/screens/settings/cloudsettings` hasta `sling:Folder`.
   >
   >Complete los siguientes pasos:
   >
   >1. Vaya a CRXDE Lite y, a continuación, a `/conf/screens/settings/cloudsettings`.
   >1. Comprobar si `cloudsettings jcr:primaryType` está en `sling:Folder`. Si la variable `jcr:primaryType` no está en `sling:folder`, continúe con los siguientes pasos.
   >1. Clic con el botón derecho `/conf/screens/settings` y cree un nodo con *name* as **`cloudsettings1`** y *Tipo* as **`sling:Folder`** y guarde los cambios.
   >1. Mueva todos los nodos debajo de `/conf/screens/settings/cloudsettings` hasta `cloudsettings1`.
   >1. Eliminar `cloudsettings` y guarde.
   >1. Cambiar nombre `cloudsettings1` hasta `cloudsettings` y guarde.
   >1. Observe que `/conf/screens/settings/cloudsettings` tiene `jcr:primaryType` as `sling:Folder`.
   >
   >Siga estos pasos en Creación y publicación antes o después de la actualización.

   1. Introduzca el **Título** as **Hojas de Google**, **Nombre del almacén** as **`googlesheets`**, y **Tipo de tienda** as **c`ontexthub.generic-jsonp`** y haga clic en **Siguiente**.

      >[!CAUTION]
      >Si utiliza Adobe Experience Manager AEM () 6.4, introduzca el **Título de configuración** as **`googlesheets`** y el **Tipo de tienda** as **c`ontexthub.generic-jsonp`**.

      ![imagen](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Introduzca la configuración json específica. Por ejemplo, puede utilizar el siguiente json para fines de demostración y seleccionar **Guardar**. Verá la configuración de la tienda titulada **Hojas de Google** en la configuración de ContextHub.

      >[!IMPORTANT]
      >Asegúrese de reemplazar el código con su `*<Sheet ID>*` y `*<API Key>*`, que recuperó al configurar las Hojas de cálculo de Google.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      >
      >En el código de ejemplo anterior, **pollInterval** define la frecuencia con la que se actualizan los valores (en milisegundos).
      >
      >Reemplace el código por su `*<Sheet ID>*` y `*<API Key>*`, que recuperó al configurar las Hojas de cálculo de Google.

      >[!CAUTION]
      >
      >Si crea las hojas de cálculo de Google y almacena configuraciones fuera de la carpeta global (por ejemplo, en su propia carpeta de proyecto), el direccionamiento no funciona de forma predeterminada.

1. **Configuración de la segmentación de tienda**

   1. Vaya a **Configuración de tienda de ContentHub** y cree otra configuración de tienda en el contenedor de configuración de AEM Screens y establezca el **Título** as **segmentation-contexthub**, **Nombre del almacén** as **segmentación** y **Tipo de tienda** as **aem.segmentation**.

      ![imagen](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Clic **Siguiente** y luego **Guardar**.

      >[!NOTE]
      >Omita el proceso de definición del json y déjelo en blanco.


## Paso 3: Configuración de segmentos en Audience Manager {#setting-up-audience}

1. **Creación de segmentos en audiencias**

   1. AEM Navegue desde la instancia de a **Personalización** > **Audiencias** > **pantallas**.

   1. Clic **Crear** > **Crear segmento de Context Hub.** El **Nuevo segmento de ContextHub** se abre el cuadro de diálogo.

   1. Introduzca el **Título** as `**Higherthan50**` y haga clic en **Crear**. Del mismo modo, cree otro segmento con el título `**Lowerthan50**`.

      ![imagen](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Seleccione el segmento `**Higherthan50**` y haga clic en **Propiedades** de la barra de acciones.
      ![imagen](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Seleccione el **Personalización** de la pestaña **Propiedades del segmento**. Configure las variables **Ruta de ContextHub** hasta `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` y **Ruta de segmentos** hasta `/conf/screens/settings/wcm/segments` y haga clic en **Guardar**, como se muestra en la figura siguiente.

   ![imagen](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Del mismo modo, configure el **Ruta de ContextHub** y **Ruta de segmentos** para `**Lowerthan50**` segmentar también.

## Paso 4: Configuración de marca y área {#setting-brand-area}

Siga los pasos a continuación para crear una marca en sus actividades y áreas bajo la marca:

1. **Creación de una marca en actividades**

   1. AEM Navegue desde la instancia de a **Personalización** > **Actividades**.

   1. Seleccionar **Crear** > **Crear marca**.

   1. Seleccionar **Marca** desde el **Crear página** y haga clic en **Siguiente**.

   1. Introduzca el **Título** as **ScreensBrand** y haga clic en **Crear**. Su marca se creará como se muestra a continuación.

      ![imagen](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problema conocido:
      >Para añadir un área, elimine la principal de la dirección URL, como
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creación de un área en la marca**

   Siga los pasos a continuación para crear un área en la marca:

   1. Seleccionar **Crear** y luego **Crear área**.

      ![imagen](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Seleccionar **Área** desde el **Crear página** asistente y seleccione **Siguiente**.

   1. Introduzca el **Título** as **ScreensValue** y seleccione **Crear**.
Se crea un área en su marca.

## Paso 5: Creación de los segmentos en una actividad {#step-setting-up-audience-segmentation}

Después de configurar un almacén de datos y definir la actividad (marca y área), siga los pasos a continuación para crear segmentos en la actividad.

1. **Creación de segmentos en actividades**

   1. AEM Navegue desde la instancia de a **Personalización** > **Actividades** > **ScreensBrand** >**ScreensValue**.

   1. Seleccionar **Crear** > **Crear actividad.** El **Asistente de configuración de actividades** abre.

   1. Introduzca el **Título** as **ValueCheck50** y **Nombre** as **valuecheck50**. Seleccione el **Motor de segmentación** as **AEM ContextHub ()** en la lista desplegable y seleccione **Siguiente**.

      ![imagen](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Seleccionar **Añadir experiencia** desde el `**Configure Activity**` asistente.

   1. Desde el **Audiencias**, seleccione la `**Higherthan50**` y seleccione **Añadir experiencia** e introduzca la variable **Título** as `**higherthan50**` **Nombre** as `**higherthan50**`. Seleccionar **Ok**.

   1. Desde el **Audiencias**, seleccione la `**Lowerthan50**` y seleccione **Añadir experiencia** e introduzca la variable **Título** as `**lowerthan50**` **Nombre** as `**lowerthan50**`. Seleccionar **Ok**.

   ![imagen](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Seleccionar **Siguiente** y luego **Guardar**. `**ValueCheck50**` la actividad se ha creado y configurado.

      ![imagen](/help/user-guide/assets/context-hub/context-hub16.png)

## Paso 5: Edición de segmentos en audiencias{#editing-audience-segmentation}

1. **Edición de segmentos**

   1. AEM Navegue desde la instancia de a **Personalización** > **Audiencias** > **pantallas**.

   1. Seleccione el segmento `**Higherthan50**`y seleccione **Editar** de la barra de acciones.

   1. Arrastre y suelte el **Comparación: propiedad/valor** al editor.

   1. Haga clic en el icono de la llave inglesa para abrir **Comparación de una propiedad con un valor** Cuadro de diálogo.

   1. Seleccionar **googlesheets/value/1/0** de la lista desplegable en **Nombre de propiedad**.

      >[!NOTE]
      > El **googlesheets/value/1/0** hace referencia a la fila 2 y a la columna como se rellenan en `google` hojas en la figura siguiente:

      ![imagen](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Seleccione el **Operador** as **greater-than** en el menú desplegable.

   1. Introduzca el **Valor** as **70**.

      >[!NOTE]
      >
      >AEM La valida los datos de la hoja de cálculo de Google mostrando el segmento como verde.

      ![imagen](/help/user-guide/assets/context-hub/context-hub18.png)

   Del mismo modo, edite los valores de propiedad en `**Lowerthan50**`.

   1. Arrastre y suelte el **Comparación: propiedad/valor** al editor.

   1. Seleccione el icono de la llave inglesa.

   1. En el **Comparación de una propiedad con un valor** , seleccione **googlesheets/value/1/0** de la lista desplegable en **Nombre de propiedad**.

   1. Seleccione el **Operador** as **less-than** en el menú desplegable.

   1. Introduzca el **Valor** as **50**.


## Habilitar la segmentación en canales {#step-enabling-targeting-in-channels}

Siga los pasos a continuación para habilitar el direccionamiento en sus canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación utilizando **DataDrivenChannel** creado en un canal de AEM Screens.

1. Seleccione el canal **TargetChannel** y haga clic en **Propiedades** de la barra de acciones.

   ![imagen](/help/user-guide/assets/context-hub/context-hub19.png)

1. Seleccione el **Personalización** para poder configurar las configuraciones de ContextHub.

   1. Configure las variables **Ruta de ContextHub** hasta `/conf/screens/settings/wcm/segments` y **Ruta de segmentos** hasta `/conf/screens/settings/wcm/segments`.
   1. Establecer marca en **ScreensBrand** en el menú desplegable y **Establecer referencia de área** hasta **ScreensValue**.

   1. Haga clic en **Guardar y cerrar**.

      >[!NOTE]
      >
      >Utilice ContextHub y la ruta de segmentos, donde guardó inicialmente las configuraciones y segmentos de Context Hub.

      ![imagen](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Desplácese y seleccione **TargetChannel** y haga clic en **Editar** de la barra de acciones.

      >[!NOTE]
      >
      >Si ha configurado todo correctamente, verá lo siguiente **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

      ![imagen](/help/user-guide/assets/context-hub/context-hub21.png)

## Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para el proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

1. **[Activación segmentada de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**
