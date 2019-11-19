---
title: Canal controlado por inventario
seo-title: Canal controlado por inventario
description: nulo
seo-description: nulo
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canal controlado por inventario{#inventory-driven-channel}

## Introducción a los canales impulsados por inventario {#getting-started-with-inventory-driven-channels}

En esta sección se describe un ejemplo de caso de uso que hace hincapié en la creación y administración de un cambio de recurso basado en datos mediante hojas de Google.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](managing-channels.md)**
* **[Crear y administrar ubicaciones](managing-locations.md)**
* **[Crear y administrar programaciones](managing-schedules.md)**
* **[Registro de dispositivos](device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

### Terminología {#terminolgies}

Siga los términos que se mencionan a continuación y que desempeñan un papel importante en la comprensión y configuración del proyecto en los distintos casos de uso:

**Actividad** hace referencia a la categoría.

**Proyecto de área** principal

**Audiencia** Ubicación de los datos

**Marca**

**Segmento de segmento** hace referencia a un contenedor de recursos que intenta segmentar.

### Flujo básico: Configuración del proyecto {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**Requisito previo:**
>
>Antes de profundizar en los detalles de la configuración y el uso del cambio de recursos basado en datos en el proyecto, asegúrese de crear un proyecto de AEM Screens con un canal de secuencia. Con fines de demostración, se crea un proyecto denominado **DataDrivenAsset** y se agregan al proyecto canales de secuencia titulados **DataDrivenRestaurant**, **DataDrivenTextOverlay**, **DataDrivenWeather** y **DataDrivenRetail** , como se muestra en la figura siguiente.
>
>La creación de cuatro canales diferentes solo sirve para fines de demostración y para mostrar cuatro casos de uso diferentes en distintos canales. Si desea seguir solo un caso de uso como requisito, no dude en crear sólo un canal de secuencia.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

Siga las secciones a continuación para crear un proyecto de muestra sobre la creación y administración de un cambio de recurso basado en datos con Google Sheets en un proyecto de AEM Screens:

## Paso 1: Configuración de la base de datos {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets se utiliza en el siguiente sistema de bases de datos de ejemplo desde donde se recuperan los valores y se utiliza únicamente con fines educativos. Adobe no acepta el uso de Google Sheets para entornos de producción.
>
>Para obtener más información, consulte [Obtener clave](https://developers.google.com/maps/documentation/javascript/get-api-key) de API en la documentación de Google.

1. Inicie sesión en Google Docs.

   >[!NOTE]
   >
   >Debe tener una cuenta en Google Drive antes de crear una nueva hoja de Google.

1. Inicie una nueva hoja de cálculo en blanco. Agregue contenido a la hoja de Google y guárdelo. Para fines de demostración, la hoja de Google se denomina **ContextHubDemo**.
1. Haga clic en **Compartir** en la esquina superior derecha de la hoja de Google para abrir el cuadro de diálogo **Compartir con otros** . Haga clic en la opción **Avanzado** y cambie la configuración a **Activado - Cualquiera con el vínculo**, como se muestra en la figura siguiente.

   Este paso le permite acceder a los valores de la hoja de Google.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. Al hacer clic en **Guardar** en el paso anterior, se obtiene el vínculo de la hoja de Google. Guarde el clic para referencias futuras y haga clic en **Finalizado**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets se utiliza en el siguiente ejemplo con fines educativos. Adobe no acepta el uso de Google Sheets para entornos de producción.

## Paso 2: Activación de las API de REST de Google Sheets {#step-enabling-the-google-sheets-rest-apis}

Una vez configurada la hoja de Google, debe habilitar la API REST de la hoja de Google para acceder a los valores.

Para obtener información sobre cómo habilitar las API de REST para hojas de Google, consulte la documentación de las API de Google.

1. Vaya a la Consola [de API de](https://console.developers.google.com/apis/credentials)Google. Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. Introduzca el nombre **del** proyecto como **AssetChange** y haga clic en **CREAR**.
1. Una vez creado el proyecto, tendrá que configurar la clave de API. Haga clic en **Crear credenciales** y seleccione **clave de API **para generar la clave de API para el proyecto. Guarde la clave de API para referencias futuras.

   >[!NOTE]
   >
   >Este proyecto de demostración utiliza la clave gratuita de Google API. Para obtener más información, consulte los precios y las restricciones del sitio web de Google **Get API Key** .

### Verificación de la configuración de hojas de Google {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;su ID de hoja&gt;/values/Sheet1?key=&lt;su clave de API&gt;

Por ejemplo:

Si el vínculo** Google Sheets** es el *siguiente:*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`, luego el

**El Id** de hoja es: `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**La clave** de API es: `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Agregando ambos valores en la sintaxis anterior:

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Ahora debería poder ver los datos en la hoja.

## Paso 2: Configuración de AEM para recuperar el contenido de las hojas de Google {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

En la sección siguiente se describe cómo configurar Adobe Experience Manager (AEM) para recuperar contenido de las hojas de Google.

1. Vaya a la instancia de AEM y haga clic en el icono de herramientas en la barra lateral izquierda. Haga clic en **Sitios** —&gt; **ContextHub**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Crear una nueva configuración de la tienda de ContextHub**

   1. Vaya a **global** &gt; **predeterminado** &gt; Configuración **de** ContextHub.

   1. Haga clic en** Crear &gt; Contenedor de configuración **e introduzca el título como** ContextHubDemo**.

   1. **** Vaya **a** ContextHubDemo **&gt; Configuración de la tienda** ContentHub... para abrir el asistente **Configurar**
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
   >Reemplace el código por el *&lt;Id. de hoja&gt;* y *&lt;Clave de API&gt;*, que ha obtenido desde el **paso 1: Configuración de la base de datos.**

   >[!CAUTION]
   Si crea las configuraciones del almacén de Google Sheets fuera de la carpeta heredada (por ejemplo, en su propia carpeta de proyecto), la segmentación no funcionará de forma predeterminada.
   En caso de que desee configurar las configuraciones de la tienda de Google Sheets fuera de la carpeta preexistente global, debe establecer el nombre **de la** tienda como **segmentación** y el tipo **de** tienda como **aem.segmentation**. Además, debe omitir el proceso de definir el archivo como se ha definido anteriormente.

1. **Creación de una marca en actividades**

   1. Vaya de la instancia de AEM a **Personalización** &gt; **Actividades**

   1. Haga clic** Crear** &gt; **Crear marca**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Su marca ahora se crea como se muestra a continuación.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
Problema conocido:
Para agregar un área, quite el patrón de la dirección URL, como
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. Creación de un área en su marca**

   1. Haga clic en **Crear** &gt; **Crear área**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. El área se creará en la actividad.

1. **Creación de segmentos en audiencias**

   1. Vaya de la instancia de AEM a **Personalización** &gt; **Audiencias** &gt; **We.Retail**.
   1. Haga clic en **Crear** &gt; **Crear segmento** de Context Hub. Se abre el nuevo cuadro de diálogo Segmento de ContextHub.
   1. Enter the **Title** as **SheetA1 1** and click **Create**. Del mismo modo, cree otro segmento denominado **HojaA2 2**.

1. **Edición de segmentos**

   1. Seleccione las **hojas de segmentos A1 1** (creadas en el paso (5)) y haga clic en **Editar** en la barra de acciones.

   1. Arrastre y suelte la **comparación: Propiedad: componente de valor** al editor.
   1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor** .
   1. Seleccione **googlesheets/value/1/0** en el menú desplegable del nombre **de** propiedad.

   1. Seleccione el **Operador** como **Igual **en el menú desplegable.

   1. Introduzca el **valor** como **1**.
   >[!NOTE]
   AEM valida los datos de la hoja de Google mostrando el segmento como verde.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Del mismo modo, edite los valores de propiedad en **Hojas A1 2**.

   1. Arrastre y suelte la **comparación: Propiedad: componente de valor** al editor.
   1. Haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo **Comparación de una propiedad con valor** .
   1. Seleccione **googlesheets/value/1/0** en el menú desplegable del nombre **de** propiedad.

   1. Seleccione el **Operador** como **Igual **en el menú desplegable.

   1. Introduzca el **valor** como **2**.
   >[!NOTE]
   Las reglas aplicadas en los pasos anteriores son sólo un ejemplo de cómo se configuran los segmentos para implementar los siguientes casos de uso.

## Paso 3: Configuración de Context Hub en el canal de pantallas de AEM {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

Siga los pasos a continuación para configurar las configuraciones de ContextHub y la ruta de segmentos al canal de AEM Screens.

1. Vaya a uno de los canales de AEM Screens (**DataDrivenRetail**) que haya creado como requisito previo.
1. Seleccione el canal (**DataDrivenRetail**) y haga clic en **Propiedades** en la barra de acciones.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Seleccione la ficha **Personalización** para configurar las configuraciones de ContextHub.

   1. Seleccione la Ruta **de** ContextHub como **bibliotecas** &gt; **configuración** &gt; **configuración** de nube &gt; **predeterminada** **** ****&gt; Configuraciones de ContextHub y haga clic enSeleccionar.

   1. Seleccione la Ruta **de** segmentos como **conf** &gt; **We.Retail **&gt; **configuración** &gt; **wcm** &gt; **segmentos** **** y haga clic enSeleccionar.

   1. Haga clic en **Guardar y cerrar**.
   >[!NOTE]
   Utilice ContextHub y la ruta Segments, donde inicialmente guardó las configuraciones y los segmentos del concentrador de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   Si no selecciona la **marca** en Configuración **de** objetivo en el cuadro de diálogo anterior, tendrá que seleccionar la marca y la actividad al iniciar el proceso de segmentación.

1. Navegue y seleccione **DataDrivenRetail** en **DataDrivenAssets** &gt; **Channels **y haga clic en **Editar** en la barra de acciones.

   >[!NOTE]
   Si ha configurado todo correctamente, verá la opción **Segmentación** en la lista desplegable del editor, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Una vez que haya configurado las configuraciones de ContextHub para su canal, asegúrese de seguir los pasos anteriores del 1 al 4 para los otros tres canales de secuencia también si desea seguir todos los casos de uso que se mencionan a continuación.

## Caso de uso 1: Activación de inventario comercial {#use-case-retail-inventory-activation}

El siguiente caso de uso muestra tres imágenes diferentes basadas en los valores de la hoja de Google.

### Descripción {#description}

Este Caso de uso muestra el stock de inventario minorista para tres jerseys de diferentes colores. En función del número de jerseys disponibles en stock que se haya grabado en Google Sheets, se mostrará en pantalla la imagen (camisa roja, verde o azul) con el número más alto.

Para este caso de uso, el suéter rojo, verde o azul se mostrará en la pantalla en función del valor más alto del número de suéteres disponibles.

### Procedimiento {#procedure}

Siga los pasos a continuación para implementar el caso de uso de activación de inventario comercial:

1. **Rellenar las hojas de Google**

   1. Vaya a la hoja de Google de ContextHubDemo.
   1. Agregue tres columnas (Rojo, Verde y Azul) con los valores correspondientes para tres camisas azules diferentes.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuración de las audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (creados en el paso 5 de la sección ***Paso 2: Configuración de AEM para recuperar el contenido de las hojas*** de Google).
   1. Agregue tres nuevos segmentos **For_Red**, **For_Green** y **For_Blue**.

   1. Seleccione **For_Red** y haga clic en **Editar** en la barra de acciones.

   1. Arrastre y suelte la **comparación: Propiedad: propiedad** del editor y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable en Nombre de la **propiedad**

   1. Seleccione el **Operador** como **mayor que **en el menú desplegable

   1. Seleccione Tipo **** de datos como **número**

   1. Seleccione **googlesheets/value/1/1** en la lista desplegable del nombre de la **segunda propiedad**

   1. Arrastre y suelte **otra comparación: Propiedad: propiedad **al editor y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable en Nombre de la **propiedad**

   1. Seleccione el **Operador** como **mayor que **en el menú desplegable

   1. Seleccionar tipo **de datos** como **número**

   1. Seleccione **googlesheets/value/1/0** en la lista desplegable del nombre de la **segunda propiedad**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación al segmento **For_Blue** como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Del mismo modo, edite y agregue reglas de propiedad de comparación al segmento** For_Green **como se muestra en la figura siguiente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   Observará que para los segmentos **For_Green** y **For_Green**, los datos no se pueden cargar en el editor, ya que sólo la primera comparación es válida a partir de ahora según los valores de la hoja de Google.

1. Desplácese y seleccione su **DataDrivenRetail **canal (un canal secuencial) y haga clic en **Editar** en la barra de acciones.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   Debería haber configurado las **** configuraciones **de ContextHub** mediante la ficha **Propiedades** del canal —&gt; **Personalización** .

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Si no agrega la **marca** en Configuraciones **de** objetivo mientras configura las configuraciones **de** ContextHub para su proyecto, como se muestra en la imagen anterior, debe seleccionar la **marca** y la **actividad** mientras comienza el proceso de segmentación, en el paso siguiente.

1. **Adición de una imagen predeterminada**

   1. Agregue una imagen predeterminada al canal y haga clic en **Objetivo**.
   1. Seleccione **Marca** y la **actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.

   1. Haga clic en **Iniciar Targeting**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Antes de empezar a establecer el objetivo, debe agregar los segmentos (**For_Green**, **For_Red** y **For_Blue**) haciendo clic en **+ Agregar segmentación** de experiencias desde el carril lateral, como se muestra en la figura siguiente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Agregue las imágenes a los tres escenarios diferentes como se muestra a continuación.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Comprobación de la vista previa**

   1. Haga clic en **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor de las tres columnas diferentes y observará las actualizaciones de la imagen de visualización según el valor más alto del inventario.
   ![retail_result](assets/retail_result.gif)

## Caso de uso 2: Activación del tiempo en el centro de viajes {#use-case-travel-center-weather-activation}

El siguiente caso de uso muestra dos imágenes diferentes basadas en los valores de la hoja de Google.

### Descripción {#description-1}

Para este caso de uso, si las hojas de Google tienen un valor inferior a 50, se mostrará una imagen con bebidas calientes y si el valor es mayor o igual a 50, se mostrará la imagen con bebidas frías. En el caso de algún otro valor o ninguno, el reproductor mostrará una imagen predeterminada.

### Procedimiento {#procedure-1}

Siga los pasos a continuación para implementar el caso de uso de activación del tiempo en el centro de viajes para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google**

   1. Vaya a la hoja de Google de ContextHubDemo.
   1. Agregue una columna con **Encabezado1** con el valor correspondiente para la temperatura.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuración de segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (creados en el paso 5 de la sección ***Paso 2: Configuración de AEM para recuperar el contenido de las hojas*** de Google).
   1. Seleccione las **hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **operador** como **mayor que o igual **en el menú desplegable

   1. Introduzca el **valor** como **50**

   1. Del mismo modo, seleccione las hojas** A1 2 ** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/0** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **Operador** como **menor que **en el menú desplegable

   1. Introduzca el **valor** como **50**

1. Navegue y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenWeather**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   El canal ya debe tener una imagen predeterminada y las audiencias deben preconfigurarse como se describe en el paso (3)

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   Debería haber configurado las **** configuraciones **de ContextHub** mediante la ficha **Propiedades** del canal —&gt; **Personalización** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   Si no agrega la **marca** en Configuraciones **de** objetivo mientras configura las configuraciones **de** ContextHub para su proyecto, como se muestra en la imagen anterior, debe seleccionar la **marca** y la **actividad** mientras comienza el proceso de segmentación, en el paso siguiente.

1. Seleccione **Objetivo** en el editor, seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.

   >[!NOTE]
   Si agregó la **marca** en Configuraciones **de** objetivo al configurar las configuraciones **de** ContextHub para su proyecto, no es necesario seleccionar la **marca** y la **actividad** en este paso.

   ![new_activity3](assets/new_activity3.gif)

1. Comprobación de la vista previa

   1. Haga clic en **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor a menos de 50, debería poder ver una imagen de las bebidas de verano. Si el valor de la hoja de Google es 50 o mayor que el que debería poder ver la imagen de una bebida caliente.
   ![result3](assets/result3.gif)

## Caso de uso 3: Activación de reserva de hospitalidad {#use-case-hospitality-reservation-activation}

El siguiente caso de uso muestra dos imágenes diferentes basadas en los valores y la fórmula aplicados en la hoja de Google.

### Descripción {#description-2}

Para este caso de uso, la hoja de Google se llena con el porcentaje de reserva en dos restaurantes **Restaurant1** y **Restaurant2**. Una fórmula se aplica en función de los valores de Restaurant1 y Restaurant2 y, en función de la fórmula, el valor 1 o 2 se asigna a la columna **AdTarget** .

Si el **Restaurante1** &gt; **Restaurante2**, el valor de **AdTarget** es 1; de lo contrario, **AdTarget** tiene asignado el valor 2. El valor 1 genera la opción *Steak food* y el valor 2 muestra la opción de comida ** tailandesa en la pantalla.

### Enfoque de procedimiento {#procedural-approach}

Siga los pasos a continuación para implementar el caso de uso de activación de la reserva de hospitalidad para su proyecto de AEM Screens:

1. Rellenar las hojas de Google y agregar la fórmula.

   Por ejemplo, aplique la fórmula a la tercera columna **AdTarget**, como se muestra en la figura siguiente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuración de segmentos en Audiencias según los requisitos**

   1. Vaya a los segmentos de la audiencia (creados en el paso 5 de la sección ***Paso 2: Configuración de AEM para recuperar el contenido de las hojas*** de Google).
   1. Seleccione las **hojas A1 1** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **operador** como **igual **en el menú desplegable

   1. Introduzca el **valor** como **1**

   1. Del mismo modo, seleccione las hojas** A1 2 ** y haga clic en **Editar**.

   1. Seleccione la propiedad de comparación y haga clic en el icono de configuración para editar las propiedades.
   1. Seleccione **googlesheets/value/1/2** en la lista desplegable del nombre de la **propiedad**

   1. Seleccione el **operador** como **2**

1. Navegue y seleccione el canal () y haga clic en **Editar** en la barra de acciones. En el siguiente ejemplo, **DataDrivenRestaurant**, se utiliza un canal secuencial para mostrar la funcionalidad.

   >[!NOTE]
   El canal ya debe tener una imagen predeterminada y las audiencias deben estar preconfiguradas como se describe en el paso (3).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   Debería haber configurado las **** configuraciones **de ContextHub** mediante la ficha **Propiedades** del canal —&gt; **Personalización** .

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   Si no agrega la **marca** en Configuraciones **de** objetivo mientras configura las configuraciones **de** ContextHub para su proyecto, como se muestra en la imagen anterior, debe seleccionar la **marca** y la **actividad** mientras comienza el proceso de segmentación, en el paso siguiente.

1. Seleccione **Objetivo** en el editor, seleccione **Marca** y **Actividad** en el menú desplegable y haga clic en **Iniciar objetivo**.
1. Comprobación de la vista previa

   1. Haga clic en **Vista previa.** Además, abra la hoja de Google y actualice su valor.
   1. Cambie el valor en Restaurante1 &gt; Restaurante2, debería poder ver la imagen de un filete y Restaurante1 &lt; Restaurante12, debería poder ver la imagen de la comida tailandesa en la pantalla.
   ![result5](assets/result5.gif)

## Caso de uso 4: Superposición de texto de la placa de menú digital {#use-case-digital-menu-board-text-overlay}

El siguiente caso de uso muestra un caso de uso de tablero de menús digital que suele prevalecer en los restaurantes y las juntas de comida rápida.

### Descripción {#description-3}

El siguiente caso de uso describe el uso de la superposición de texto en un canal secuencial y cómo la actualización de valor del precio en las hojas de Google activa una actualización en la actualización del componente de superposición de texto.

### Enfoque de procedimiento {#procedural-approach-1}

Siga los pasos a continuación para implementar el tablero de menús digital con casos de uso de superposición de texto para su proyecto de AEM Screens:

1. **Rellenar las hojas de Google**

   1. Navegue hasta las hojas de Google.
   1. Agregue una columna con valor de precio para el caso de uso, como se muestra en la figura siguiente.
   ![screen_shot_2019-05-05at111344am](assets/screen_shot_2019-05-05at111344am.png)

1. **Adición de una imagen al canal de secuencia**

   1. Navegue y seleccione su canal (**DataDrivenAssets** —&gt; **Canales** —&gt; **DataDrivenTextOverlay**).

   1. Haga clic en **Editar** en la barra de acciones para abrir el editor.
   1. Arrastre y suelte una imagen circular de manzana en el editor.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **Adición de superposición de texto a la imagen**

   1. Seleccione la imagen en el editor y haga clic en Configurar.
   1. Vaya a la ficha **Superposición** de texto y agregue la superposición de texto a la imagen. Para obtener el valor de las hojas de Google, asegúrese de que el valor se incluye en las ramas de curvas. Por ejemplo, el precio se obtiene de las hojas de Google y se menciona como **{price}** al definir la superposición de texto.

   1. Vaya a la ficha **ContextHub** y configure el valor que se va a recuperar de las hojas de Google, como se muestra en la figura siguiente.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **Comprobación de la vista previa**

   <!-- Edit text in steps below. wonky-->

   1. Haga clic en **Vista previa**.  Además, abra la hoja de Google y actualice su valor.
   1. Cambie el **valor debajo de Precio** y notará el valor como se utiliza en las actualizaciones de superposición de texto correspondientes, como se muestra en la figura siguiente.
   ![textoverlay_result-1](assets/textoverlay_re