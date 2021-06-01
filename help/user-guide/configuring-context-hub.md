---
title: Configuración de ContextHub en AEM Screens
seo-title: Configuración de ContextHub en AEM Screens
description: Siga esta página para obtener más información sobre ContextHub en el motor de determinación de objetivos y definir el almacén de datos con el fin de modificar el contenido del déclencheur de datos.
seo-description: Siga esta página para obtener más información sobre ContextHub en el motor de determinación de objetivos y definir el almacén de datos con el fin de modificar el contenido del déclencheur de datos.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: Desarrollo de pantallas
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 1%

---


# Configuración de ContextHub en AEM Screens {#configuring-contexthub-in-aem-screens}

En esta sección se hace hincapié en la creación y administración de cambios de recursos impulsados por datos mediante un almacén de datos.

## Términos clave {#key-terms}

Antes de entrar en los detalles de creación y administración de canales impulsados por inventario en su proyecto de AEM Screens, debe conocer pocos de los términos clave que son importantes y relevantes para los diferentes escenarios.

**** MarcaSe refiere a la descripción del proyecto de alto nivel.

**** AreaHace referencia al nombre del proyecto de AEM Screens, como la publicidad dinámica

**** ActividadDefine la categoría de regla como, por ejemplo, impulsada por el inventario, por el tiempo, por la disponibilidad del departamento, etc.

**** AudienceDefine la regla.

**** SegmentSe refiere a la versión del recurso que se va a reproducir para la regla dada, como si la temperatura es inferior a 50 grados centígrados, la pantalla muestra una imagen de un café caliente o, en caso contrario, una bebida fría.

El diagrama siguiente proporciona una representación visual de cómo coinciden las configuraciones de ContextHub con la actividad, la audiencia y los canales.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condiciones previas {#preconditions}

Antes de empezar a configurar las configuraciones de ContextHub para un proyecto de AEM Screens, debe configurar Google Sheets (con fines de demostración).

>[!IMPORTANT]
>
>Google Sheets se utiliza en el siguiente ejemplo como sistema de base de datos de ejemplo desde el que se recuperan los valores y solo con fines educativos. Adobe no aprueba el uso de Google Sheets para entornos de producción.
>
>Para obtener más información, consulte [Obtener clave de API](https://developers.google.com/maps/documentation/javascript/get-api-key) en la documentación de Google.

## Paso 1: Configuración de un almacén de datos {#step-setting-up-a-data-store}

Puede configurar el almacén de datos como un evento de E/S local o como un evento de base de datos local.

En el siguiente ejemplo de déclencheur de datos de nivel de recurso se muestra un evento de base de datos local que configura un almacén de datos como una hoja de Excel que le permite utilizar configuraciones de ContextHub y la ruta de acceso de segmentos al canal de AEM Screens.

Una vez que haya configurado correctamente la hoja de google, por ejemplo, como se muestra a continuación:

![image](/help/user-guide/assets/context-hub/context-hub1.png)

La siguiente validación es lo que verá al comprobar la conexión introduciendo los dos valores *google sheet ID* y *API key* en el formato siguiente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>El ejemplo específico que se muestra a continuación muestra las hojas de google como un almacén de datos que generará un déclencheur del cambio de recursos si el valor es superior a 100 o inferior a 50.

## Paso 2: Configuración de configuraciones de almacén {#step-setting-store-configurations}

1. **Navegación a ContextHub**

   Vaya a la instancia de AEM y haga clic en el icono de herramientas en la barra lateral izquierda. Haga clic en **Sitios** —> **ContextHub**, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creación de una nueva configuración de la tienda de ContextHub**

   1. Vaya al contenedor de configuración denominado **screens**.

   1. Haga clic en **Crear** > **Crear contenedor de configuración** e introduzca el título como **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** Vaya a  **ContextHubDemo**  >  **** **Configuración de CreateContentHub** y haga clic en  **Guardar**.

      >[!NOTE]
      > Después de hacer clic en **Guardar**, aparecerá en la pantalla **Configuración de ContextHub**.

   1. En la pantalla **Configuración de ContextHub**, haga clic en **Crear** > **Configuración del almacén de ContentHub..**

      ![image](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >Como parte de AEM paquete de funciones 4 o AEM 6.4 Feature Pack 8 de 6.5, los clientes deben actualizar `/conf/screens/settings/cloudsettings` a `sling:Folder`.
      >
      >Complete los siguientes pasos:
      >
      >1. Vaya al CRXDE Lite y, a continuación, a `/conf/screens/settings/cloudsettings`.
      >1. Compruebe si `cloudsettings jcr:primaryType` está en `sling:Folder`. Si el `jcr:primaryType` no está en `sling:folder`, siga los siguientes pasos.
      >1. Haga clic con el botón derecho en `/conf/screens/settings` y cree un nuevo nodo con *name* como **cloudsettings1** y *Type* como **sling:Folder** y guarde los cambios.
      >1. Mueva todos los nodos de `/conf/screens/settings/cloudsettings` a `cloudsettings1`.
      >1. Elimine `cloudsettings` y guarde.
      >1. Cambie el nombre de `cloudsettings1` a `cloudsettings` y guárdelo.
      >1. Ahora debe observar que /conf/screens/settings/cloudsettings tiene `jcr:primaryType` como `sling:Folder`.

      >
      >Debe seguir estos pasos en la creación y publicación antes o después de la actualización.

   1. Introduzca **Title** como **Google Sheets**, **Store Name** como **googlesheets** y **Store Type** como **contexthub.generic-jsonp** y haga clic en &lt;a9/ 12/>Siguiente **.**

      >[!CAUTION]
      >Si utiliza Adobe Experience Manager (AEM) 6.4, introduzca el **Título de configuración** como **hojas de gafas** y el **Tipo de almacén** como **contexthub.generic-jsonp**.

      ![image](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Introduzca la configuración json específica. Por ejemplo, puede utilizar el siguiente json para fines de demostración y hacer clic en **Guardar** y verá la configuración de la tienda titulada como **Google Sheets** en la configuración de ContextHub.

      >[!IMPORTANT]
      >Asegúrese de reemplazar el código por su *&lt;ID de hoja>* y *&lt;clave de API>* que obtuvo al configurar las hojas de Google.

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
      En el código de ejemplo anterior, **pollInterval** define la frecuencia con la que se actualizan los valores (en ms).
      Reemplace el código por su *&lt;Sheet ID>* y *&lt;API Key>* que obtuvo al configurar las hojas de Google.

      >[!CAUTION]
      Si crea las configuraciones de la tienda Google Sheets fuera de la carpeta global (por ejemplo, en su propia carpeta de proyecto), la segmentación no funcionará de forma predeterminada.


1. **Configuración de la segmentación de tiendas**

   1. Vaya a **Configuración del almacén de ContentHub.** y cree otra configuración de tienda en el contenedor de configuración de pantallas y establezca los  **** títulos  **segmentation-contexthub**,  **Store** Nameas  **** segmentationy  **Store** Typeas  **aem.segmentation**.

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Haga clic en **Siguiente** y luego en **Guardar**.

      >[!NOTE]
Debe omitir el proceso de definición del json y dejarlo en blanco.


## Paso 3: Configuración de segmentos en la audiencia {#setting-up-audience}

1. **Creación de segmentos en audiencias**

   1. Vaya desde la instancia de AEM a **Personalization** > **Audiences** > **screens**.

   1. Haga clic en **Crear** > **Crear segmento de Context Hub.** Se abre el  **cuadro de** diálogo Nuevo segmento de ContextHub.

   1. Introduzca **Title** como **Higherthan50** y haga clic en **Create**. Del mismo modo, cree otro segmento con el título **Lower than50**.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Seleccione el segmento **Higherthan50** y haga clic en **Properties** en la barra de acciones.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Seleccione la pestaña **Personalization** en **Segment Properties**. Configure la **Ruta de ContextHub** en `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` y **Ruta de segmentos** en `/conf/screens/settings/wcm/segments` y haga clic en **Guardar**, como se muestra en la figura siguiente.

      ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Del mismo modo, también configure la **Ruta de acceso de ContextHub** y la **Ruta de segmentos** para el segmento **Menor que50**.

## Paso 4: Configuración de marca y área {#setting-brand-area}

Siga los pasos a continuación para crear una marca en sus actividades y en el área bajo la marca:

1. **Creación de una marca en actividades**

   1. Vaya desde la instancia de AEM a **Personalization** > **Activities**.

   1. Haga clic en **Crear** > **Crear marca**.

   1. Seleccione **Marca** en el asistente **Crear página** y haga clic en **Siguiente**.

   1. Introduzca **Title** como **ScreensBrand** y haga clic en **Create**. La marca ahora se crea como se muestra a continuación.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema conocido:
Para agregar un área, elimine el patrón de la dirección URL, como
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creación de un área en su marca**

   Siga los pasos a continuación para crear un área en la marca:

   1. Haga clic en **Crear** y, a continuación, en **Crear área**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Seleccione **Área** en el asistente **Crear página** y haga clic en **Siguiente**.

   1. Introduzca **Title** como **ScreensValue** y haga clic en **Create**.
Se creará un área en la marca.

## Paso 5: Creación de segmentos en una actividad {#step-setting-up-audience-segmentation}

Una vez que haya configurado un almacén de datos y definido su actividad (marca y área), siga los pasos a continuación para crear segmentos en su actividad.

1. **Creación de segmentos en actividades**

   1. Vaya desde la instancia de AEM a **Personalization** > **Activities** > **ScreensBrand** >**ScreensValue**.

   1. Haga clic en **Crear** > **Crear actividad.** Se  **abre el** Asistente para configurar actividades.

   1. Introduzca el **Título** como **ValueCheck50** y **Nombre** como **valorCheck50**. Seleccione **Targeting engine** como **ContextHub (AEM)** en la lista desplegable y haga clic en **Next**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Haga clic en **Agregar experiencia** en el **Asistente para configurar actividades**.

   1. En **Audiences**, seleccione **Higherthan50** y haga clic en **Agregar experiencia** e introduzca el **Título** como **mayor que50** **Nombre** como **mayor que 50**. Haga clic en **Ok**.

   1. En **Audiencias**, seleccione **Inferior a 50** y haga clic en **Agregar experiencia** e introduzca el **Título** como **inferior a 50** **Nombre** como **a12/>menor que50**. Haga clic en **Ok**.

      ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Haga clic en **Siguiente** y luego en **Guardar**. **La actividad ValueCheck50**  ahora se crea y configura.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Paso 5: Edición de segmentos en Audiencias{#editing-audience-segmentation}

1. **Edición de segmentos**

   1. Vaya desde la instancia de AEM a **Personalization** > **Audiences** > **screens**.

   1. Seleccione el segmento **Higherthan50** y haga clic **Editar** en la barra de acciones.

   1. Arrastre y suelte la **Comparación: Propiedad: componente Value** al editor.

   1. Haga clic en el icono de llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor**.

   1. Seleccione **googlesheets/value/1/0** en la lista desplegable de **Property name**.

      >[!NOTE]
Las  **hojas de google/value/1/0**  hacen referencia a la fila 2 y a la columna tal como se rellenan en las hojas de google de la figura siguiente:

      ![image](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Seleccione **Operator** como **bueno-than** en el menú desplegable.

   1. Introduzca el **Value** como **70**.

      >[!NOTE]
      El AEM valida los datos de la hoja de Google mostrando el segmento como verde.

      ![image](/help/user-guide/assets/context-hub/context-hub18.png)
   Del mismo modo, edite los valores de las propiedades en **Lower than50**.

   1. Arrastre y suelte la **Comparación: Propiedad: componente Value** al editor.

   1. Haga clic en el icono de llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor**.

   1. Seleccione **googlesheets/value/1/0** en la lista desplegable de **Property name**.

   1. Seleccione **Operator** como **less-than** en el menú desplegable.

   1. Introduzca el **Value** como **50**.



## Activación de la orientación en canales {#step-enabling-targeting-in-channels}

Siga los pasos a continuación para habilitar la segmentación en sus canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación mediante el uso de **DataDrivenChannel** creado en un canal de AEM Screens.

1. Seleccione el canal **TargetChannel** y haga clic en **Properties** en la barra de acciones.

   ![image](/help/user-guide/assets/context-hub/context-hub19.png)

1. Seleccione la pestaña **Personalization** para configurar las configuraciones de ContextHub.

   1. Establezca la **Ruta de ContextHub** en `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` y **Ruta de segmentos** en `/conf/screens/settings/wcm/segments` y haga clic en **Guardar**.

   1. Haga clic en **Guardar y cerrar**.

      >[!NOTE]
      Utilice ContextHub y la ruta Segments, donde inicialmente guardó las configuraciones y segmentos de Context Hub.

      ![image](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Desplácese y seleccione el canal **TargetChannel** y haga clic en **Editar** en la barra de acciones.

      >[!NOTE]
      Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

      ![image](/help/user-guide/assets/context-hub/context-hub21.png)

## Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para su proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por los datos desempeñan un papel vital en diferentes industrias:

1. **[Activación de destino de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de la temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**
