---
title: Configuración de ContextHub en AEM Screens
seo-title: Configuración de ContextHub en AEM Screens
description: Siga esta página para obtener información sobre ContextHub en el motor de determinación de objetivos y definir el almacén de datos con el fin de cambiar el contenido del activador de datos.
seo-description: Siga esta página para obtener información sobre ContextHub en el motor de determinación de objetivos y definir el almacén de datos con el fin de cambiar el contenido del activador de datos.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 15afec3ed9ffdcfc918c13376af2b20f9a61ab8e
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---


# Configuración de ContextHub en AEM Screens {#configuring-contexthub-in-aem-screens}

En esta sección se hace hincapié en la creación y administración de cambios de recursos basados en datos mediante un almacén de datos.

## Términos clave {#key-terms}

Antes de entrar en los detalles de la creación y administración de canales impulsados por el inventario en su proyecto de AEM Screens, debe conocer algunos de los términos clave que son importantes y relevantes para los distintos escenarios.

**Marca** Se refiere a la descripción del proyecto de alto nivel.

**Área** hace referencia al nombre de proyecto de AEM Screens, como la publicidad digital y la publicidad dinámica

**Actividad** Define la categoría de la regla, como por ejemplo, controlado por inventario, por el tiempo, por disponibilidad del departamento, etc.

**Audiencia** Define la regla.

**Segmento** Se refiere a la versión del recurso que se va a reproducir para la regla dada, como si la temperatura es inferior a 50 grados centígrados, la pantalla muestra una imagen de un café caliente o una bebida fría.

El diagrama siguiente muestra cómo las configuraciones de ContextHub coinciden con la Actividad, la Audiencia y los Canales.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condiciones previas {#preconditions}

Antes de dar inicio a la configuración de Context Hub Configurations para un proyecto de AEM Screens, debe configurar Google Sheets (para fines de demostración).

>[!IMPORTANT]
>
>Google Sheets se utiliza en el siguiente ejemplo como sistema de bases de datos de muestra desde donde se recuperan los valores y se utiliza únicamente con fines educativos. Adobe no aprueba el uso de Google Sheets para entornos de producción.
>
>Para obtener más información, consulte [Obtener clave](https://developers.google.com/maps/documentation/javascript/get-api-key) de API en la documentación de Google.

## Paso 1: Configuración de un almacén de datos {#step-setting-up-a-data-store}

Puede configurar el almacén de datos como un evento de E/S local o como un evento de base de datos local.

El siguiente ejemplo de desencadenadores de datos de nivel de recurso muestra un evento de base de datos local que configura un almacén de datos como una hoja de Excel que le permite utilizar las configuraciones de ContextHub y la ruta de segmentos al canal de AEM Screens.

Una vez configurada correctamente la hoja de Google, por ejemplo:

![image](/help/user-guide/assets/context-hub/context-hub1.png)

La siguiente validación es lo que vista al comprobar la conexión introduciendo los dos valores, ID *de hoja de* Google y clave *de* API en el formato siguiente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> El ejemplo específico que se muestra a continuación muestra las hojas de Google como un almacén de datos que activará el cambio de recurso si el valor es mayor que 100 o menor que 50.

## Paso 2: Configuración de configuraciones de tienda {#step-setting-store-configurations}

1. **Navegación a ContextHub**

   Vaya a la instancia de AEM y haga clic en el icono de herramientas en la barra lateral izquierda. Haga clic en **Sitios** —> **ContextHub**, como se muestra en la figura siguiente.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creación de una nueva configuración de la Tienda ContextHub**

   1. Vaya al contenedor de configuración titulado como **pantallas**.

   1. Haga clic en **Crear** > **Crear Contenedor** de configuración e introduzca el título como **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Vaya** a **ContextHubDemo** > **Crear** la configuración **de** ContentHub y haga clic en **Guardar**.

      >[!NOTE]
      > Después de hacer clic en **Guardar** , aparecerá en la pantalla de configuración **de** ContextHub.

   1. En la pantalla de configuración **de** ContextHub, haga clic en **Crear** > Configuración de la tienda de **ContentHub.**

      ![image](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >Como parte de AEM 6.5 Feature Pack 4 o AEM 6.4 Feature Pack 8, los clientes deben actualizar `/conf/screens/settings/cloudsettings` a `sling:Folder`.
      > 
      >Siga los pasos a continuación:
      >
      >1. Vaya a CRXDE Lite y, a continuación, a `/conf/screens/settings/cloudsettings`.
      >1. Compruebe si `cloudsettings jcr:primaryType` está en `sling:Folder`. Si el `jcr:primaryType` no está en `sling:folder`, continúe con los pasos siguientes.
      > 1. Haga clic con el botón secundario en `/conf/screens/settings` y cree un nuevo nodo con el *nombre* como **cloudsettings1** y *Escriba* como **sling:Folder** y guarde los cambios.
      >1. Mueva todos los nodos debajo de `/conf/screens/settings/cloudsettings` a `cloudsettings1`.
      >1. Eliminar `cloudsettings` y guardar.
      >1. Cambie el nombre `cloudsettings1` a `cloudsettings` y guarde.
      >1. Ahora debe observar que /conf/screen/settings/cloudsettings tiene `jcr:primaryType` as `sling:Folder`.
Debe seguir estos pasos en la creación y publicación antes o después de la actualización.


   1. Introduzca el **Título** como Hojas **de** Google, Nombre **de** la tienda como **hojas de cálculo** y Tipo **de** **** **** tienda como contexthub.generic-jsonpy haga clic en Siguiente.

      >[!CAUTION]
      >Si utiliza Adobe Experience Manager (AEM) 6.4, introduzca el Título **de** configuración como hojas de **Google** y el Tipo **de** tienda como **contexthub.generic-jsonp**.

      ![image](/help/user-guide/assets/context-hub/context-hub6.png)



   1. Introduzca la configuración de json específica. Por ejemplo, puede utilizar el siguiente json para fines de demostración y hacer clic en **Guardar** , y verá la configuración de la tienda titulada como Hojas de **Google** en la configuración de ContextHub.

      >[!IMPORTANT]
      >Asegúrese de reemplazar el código por su *&lt;ID de hoja>* y *&lt;Clave de API>*, que buscó al configurar las hojas de Google.

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
      En el código de muestra anterior, **pollInterval** define la frecuencia con la que se actualizan los valores (en ms).
Reemplace el código por el *&lt;ID de hoja>* y *&lt;clave de API>* que buscó al configurar las hojas de Google.

      >[!CAUTION]
      Si crea las configuraciones del almacén de Google Sheets fuera de la carpeta global (por ejemplo, en su propia carpeta de proyecto), la segmentación no funcionará de forma predeterminada.

1. **Configuración de la segmentación de tiendas**

   1. Vaya a Configuración de **ContentHub Store.** y cree otra configuración de almacén en el contenedor de configuración de pantallas y defina el **Título** como **segmentación-contexto**, Nombre **de** tienda como **segmentación** y Tipo **de** **** almacén como aem.segmentation.

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
Debe omitir el proceso de definición del archivo y dejarlo en blanco.


## Paso 3: Configuración de segmentos en Audiencia {#setting-up-audience}

1. **Creación de segmentos en Audiencias**

   1. Vaya de la instancia de AEM a **Personalización** > **Audiencias** > **pantallas**.

   1. Haga clic en **Crear** > **Crear segmento de Context Hub.** Se abre el cuadro de diálogo **Nuevo segmento** de ContextHub.

   1. Enter the **Title** as **Higherthan50** and click **Create**. Del mismo modo, cree otro segmento con el título **Menos que 50**.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Seleccione el segmento **Higherthan50** y haga clic en **Propiedades** en la barra de acciones.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Seleccione la ficha **Personalización** en Propiedades **del segmento**. Configure la ruta **de** ContextHub en `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` y la ruta **de** segmentos en `/conf/screens/settings/wcm/segments` y haga clic en **Guardar**, como se muestra en la figura siguiente.

      ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Del mismo modo, configure también la ruta **y la ruta** de **segmentos de** ContextHub para el segmento **menor que50** .

## Paso 4: Configuración de marca y área {#setting-brand-area}

Siga los pasos a continuación para crear una marca en sus actividades y en el área bajo la marca:

1. **Creación de una marca en Actividades**

   1. Vaya de la instancia de AEM a **Personalización** > **Actividades**.

   1. Haga clic en **Crear** > **Crear marca**.

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. Su marca ahora se crea como se muestra a continuación.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema conocido:
Para agregar un área, quite el patrón de la dirección URL, como
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creación de un área en la marca**

   Siga los pasos a continuación para crear un área en la marca:

   1. Haga clic en **Crear** y, a continuación, en **Crear área**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
Se creará un área en su marca.

## Paso 5: Creación de segmentos en una Actividad {#step-setting-up-audience-segmentation}

Una vez que haya configurado un almacén de datos y definido la actividad (marca y área), siga los pasos a continuación para crear segmentos en la actividad.

1. **Creación de segmentos en Actividades**

   1. Vaya de la instancia de AEM a **Personalización** > **Actividades** > **PantallasMarca** >**ValorDePantallas**.

   1. Haga clic en **Crear** > **Crear Actividad.** Se abre el Asistente para **configurar Actividades** .

   1. Introduzca el **Título** como **ValueCheck50** y **Nombre** como **valueCheck50**. Seleccione el motor **de** Targeting como **ContextHub (AEM)** en la lista desplegable y haga clic en **Siguiente**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Haga clic en **Añadir experiencia** en el Asistente para **configurar Actividades**.

   1. En las **Audiencias**, seleccione la opción **Más alto50** y haga clic en **Añadir experiencia** e introduzca el **título** como **más alto que50** Nombrecomo más alto que **** **** 00. Click **Ok**.

   1. En las **Audiencias**, seleccione la opción **Más bajo que50** y haga clic en **Añadir experiencia** e introduzca el **Título** como **menor que50** **** **** Nombre500. Click **Ok**.

      ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **La actividad ValueCheck50** ahora se crea y configura.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Paso 5: Edición de segmentos en Audiencias{#editing-audience-segmentation}

1. **Edición de segmentos**

   1. Vaya de la instancia de AEM a **Personalización** > **Audiencias** > **pantallas**.

   1. Seleccione el segmento **Superior50** y haga clic en **Editar** en la barra de acciones.

   1. Arrastre y suelte la **comparación: Propiedad: componente de valor** al editor.

   1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor** .

   1. Seleccione **googlesheets/value/1/0** en el menú desplegable del nombre **de** propiedad.

      >[!NOTE]
Las **hojas de googleets/value/1/0** se refieren a la fila 2 y la columna tal como se rellenan en las hojas de Google en la figura siguiente:

      ![image](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Seleccione el **Operador** como **bueno que** en el menú desplegable.

   1. Introduzca el **valor** como **70**.

      >[!NOTE]
      AEM valida los datos de la hoja de Google mostrando el segmento como verde.

      ![image](/help/user-guide/assets/context-hub/context-hub18.png)
   Del mismo modo, edite los valores de propiedad en **Inferior a 50**.

   1. Arrastre y suelte la **comparación: Propiedad: componente de valor** al editor.

   1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor** .

   1. Seleccione **googlesheets/value/1/0** en el menú desplegable del nombre **de** propiedad.

   1. Seleccione el **Operador** como **menor que** en el menú desplegable.

   1. Introduzca el **valor** como **50**.



## Habilitar la determinación de objetivos en Canales {#step-enabling-targeting-in-channels}

Siga los pasos a continuación para habilitar la segmentación en sus canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación mediante **DataDrivenChannel** creado en un Canal de AEM Screens.

1. Seleccione el **TargetChannel** de canal y haga clic en **Propiedades** en la barra de acciones.

   ![image](/help/user-guide/assets/context-hub/context-hub19.png)

1. Seleccione la ficha **Personalización** para configurar las configuraciones de ContextHub.

   1. Defina la ruta **de** ContextHub en `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` y la ruta **de** segmentos en `/conf/screens/settings/wcm/segments` y haga clic en **Guardar**.

   1. Click **Save &amp; Close**.

      >[!NOTE]
      Utilice ContextHub y la ruta de segmentos, donde inicialmente guardó las configuraciones y los segmentos del concentrador de contexto.

      ![image](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navegue y seleccione el canal **TargetChannel** y haga clic en **Editar** en la barra de acciones.

      >[!NOTE]
      Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

      ![image](/help/user-guide/assets/context-hub/context-hub21.png)

## Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para su proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

1. **[Activación de objetivo de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de la temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reservación de hospitalidad](hospitality-reservation-activation.md)**
