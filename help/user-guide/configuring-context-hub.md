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
source-git-commit: 69dd2238562c00ab83e63e268515e24dee55f5ee

---


# Configuración de ContextHub en AEM Screens {#configuring-contexthub-in-aem-screens}

En esta sección se hace hincapié en la creación y administración de cambios de recursos basados en datos mediante un almacén de datos.

## Términos clave {#key-terms}

Antes de entrar en los detalles de la creación y administración de canales impulsados por el inventario en su proyecto de AEM Screens, debe conocer algunos de los términos clave que son importantes y relevantes para los distintos escenarios.

**Marca** Se refiere a la descripción del proyecto de alto nivel.

**Área** hace referencia al nombre de proyecto de AEM Screens, como la publicidad digital y la publicidad dinámica

**Actividad** Define la categoría de regla, como por ejemplo, por inventario, por tiempo, por disponibilidad del departamento, etc.

**Audiencia** Define la regla.

**Segmento** Se refiere a la versión del recurso que se va a reproducir para la regla dada, como si la temperatura es inferior a 50 grados centígrados, la pantalla muestra una imagen de un café caliente o una bebida fría.

El diagrama siguiente proporciona una representación visual de cómo las configuraciones de ContextHub coinciden con la actividad, la audiencia y los canales.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condiciones previas {#preconditions}

Antes de empezar a configurar las configuraciones de Context Hub para un proyecto de AEM Screens, debe configurar Google Sheets (para fines de demostración).

>[!CAUTION]
>
>Google Sheets se utiliza en el siguiente ejemplo como sistema de bases de datos de muestra desde donde se recuperan los valores y se utiliza únicamente con fines educativos. Adobe no acepta el uso de Google Sheets para entornos de producción.
>
>Para obtener más información, consulte [Obtener clave](https://developers.google.com/maps/documentation/javascript/get-api-key) de API en la documentación de Google.

## Paso 1: Configuración de un almacén de datos {#step-setting-up-a-data-store}

Puede configurar el almacén de datos como un evento de E/S local o como un evento de base de datos local.

### Evento de E/S local {#local-io-event}

Siga los pasos que se describen a continuación para configurar un almacén de datos, como un evento ASCII, que le permita utilizar las configuraciones de ContextHub y la ruta de segmentos al canal de AEM Screens.

### Evento de base de datos local {#local-db-event}

Siga los pasos a continuación para configurar un almacén de datos como una hoja de Excel que le permita utilizar las configuraciones de ContextHub y la ruta de segmentos al canal de AEM Screens.

1. **Navegación a ContextHub**

   Vaya a la instancia de AEM y haga clic en el icono de herramientas en la barra lateral izquierda. Haga clic en **Sitios** —> **ContextHub**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Creación de una nueva configuración de la Tienda ContextHub**

   1. Vaya a **global** > **predeterminado** > Configuración **de** ContextHub.

   1. Haga clic en **Crear** > Contenedor **** de configuración e introduzca el título como **ContextHubDemo**.

   1. **** Vaya **a** ContextHubDemo **> Configuración de la tienda** ContentHub... para abrir el asistente **Configurar**.

   1. Introduzca el **título** como hojas de **Google**, el nombre **** de la tienda como hojas de **Google** y el tipo **de** **tienda comocontexthub.generic-jsonp**

   1. Haga clic en **Siguiente**
   1. Introduzca la configuración de json específica. Por ejemplo, puede utilizar el siguiente json para fines de demostración.
   1. Haga clic en **Guardar**.

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >En el código de muestra anterior, **pollInterval** define la frecuencia con la que se actualizan los valores (en ms).
   >
   >
   >Reemplace el código por el *&lt;ID de hoja>* y *&lt;clave de API>* que buscó al configurar las hojas de Google.

   >[!CAUTION]
   Si crea las configuraciones del almacén de Google Sheets fuera de la carpeta heredada (por ejemplo, en su propia carpeta de proyecto), la segmentación no funcionará de forma predeterminada.
   En caso de que desee configurar las configuraciones de la tienda de Google Sheets fuera de la carpeta preexistente global, debe establecer el nombre **de la** tienda como **segmentación** y el tipo **de** tienda como **aem.segmentation**. Además, debe omitir el proceso de definir el archivo como se ha definido anteriormente.

1. **Creación de una marca en actividades**

   1. Vaya de la instancia de AEM a **Personalización** > **Actividades**

   1. Haga clic en **Crear** > **Crear marca**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Su marca ahora se crea como se muestra a continuación.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)


   >[!CAUTION]
   Problema conocido:
   Para agregar un área, quite el patrón de la dirección URL, como
   `https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master`

1. **Creación de un área en la marca**

   Siga los pasos a continuación para crear un área en la marca:

   1. Haga clic en **Crear** y, a continuación, en **Crear área**

   1. Select **Area** from the **Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**.
El área se creará en la actividad.

## Paso 2: Configuración de la segmentación de audiencias {#step-setting-up-audience-segmentation}

Una vez que haya configurado un almacén de datos y definido la marca, siga los pasos a continuación para configurar los segmentos de audiencia.

1. **Creación de segmentos en audiencias**

   1. Vaya de la instancia de AEM a **Personalización** > **Audiencias** > **We.Retail**.

   1. Haga clic en **Crear** > **Crear segmento de Context Hub.** Se abre el cuadro de diálogo **Nuevo segmento** de ContextHub.

   1. Enter the **Title** as **SheetA1 1** and click **Create**. Del mismo modo, cree otro segmento denominado **HojaA2 2**.

1. **Edición de segmentos**

   1. Seleccione las **hojas de segmentos A1 1** (creadas en el paso (5)) y haga clic en **Editar** en la barra de acciones.

   1. Arrastre y suelte la **comparación: Propiedad: componente de valor** al editor.
   1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor** .
   1. Seleccione **googlesheets/value/1/0** en el menú desplegable del nombre **de** propiedad.

   1. Seleccione el **operador** como **igual** en el menú desplegable.

   1. Introduzca el **valor** como **1**.
   >[!NOTE]
   AEM valida los datos de la hoja de Google mostrando el segmento como verde.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Del mismo modo, edite los valores de propiedad en **Hojas A1 2**.

   1. Arrastre y suelte la **comparación: Propiedad: componente de valor** al editor.
   1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor** .
   1. Seleccione **googlesheets/value/1/0** en el menú desplegable del nombre **de** propiedad.

   1. Seleccione el **operador** como **igual** en el menú desplegable.

   1. Introduzca el **valor** como **2**.
   >[!NOTE]
   Las reglas aplicadas en los pasos anteriores son sólo un ejemplo de cómo se configuran los segmentos para implementar los siguientes casos de uso.

## Paso 3: Activación de la determinación de objetivos en los canales {#step-enabling-targeting-in-channels}

Siga los pasos a continuación para habilitar la segmentación en los canales.

1. Vaya a uno de los canales de AEM Screens. Los siguientes pasos muestran cómo habilitar la segmentación mediante **DataDrivenRetail** creado en un canal de pantallas de AEM.

1. Seleccione el canal **DataDrivenRetail** y haga clic en **Propiedades** en la barra de acciones.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Seleccione la ficha **Personalización** para configurar las configuraciones de ContextHub.

   1. Seleccione la Ruta **de** ContextHub como **bibliotecas** > **configuración** > **configuración** de nube > **predeterminada** **** ****> Configuraciones de ContextHub y haga clic enSeleccionar.

   1. Seleccione la Ruta **de** segmentos como **conf** > **We.Retail** > **configuración** > **wcm** **** ****> segmentosy haga clic en Seleccionar.

   1. Haga clic en **Guardar y cerrar**.
   >[!NOTE]
   Utilice ContextHub y la ruta de segmentos, donde inicialmente guardó las configuraciones y los segmentos del concentrador de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navegue y seleccione **DataDrivenRetail** en **DataDrivenAssets** > **Canales** y haga clic en **Editar** en la barra de acciones.

   >[!NOTE]
   Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Una vez que haya configurado las configuraciones de ContextHub para su canal, asegúrese de seguir los pasos anteriores del 1 al 4 para los otros tres canales de secuencia también si desea seguir todos los casos de uso que se mencionan a continuación.

## Más información: Casos de uso de ejemplo {#learn-more-example-use-cases}

Después de configurar ContextHub para su proyecto de AEM Screens, puede seguir los diferentes casos de uso para comprender cómo los recursos activados por datos desempeñan un papel vital en diferentes industrias:

1. **[Activación de objetivo de inventario comercial](retail-inventory-activation.md)**
1. **[Activación de la temperatura del centro de viajes](local-temperature-activation.md)**
1. **[Activación de reserva de hospitalidad](hospitality-reservation-activation.md)**
