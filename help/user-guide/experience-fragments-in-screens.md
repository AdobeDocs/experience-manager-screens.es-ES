---
title: Uso de fragmentos de experiencias
seo-title: Uso de fragmentos de experiencias
description: 'Siga esta página para obtener información sobre el uso de fragmentos de experiencia en AEM Screens. '
seo-description: 'Siga esta página para obtener información sobre el uso de fragmentos de experiencia en AEM Screens. '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 8%

---


# Uso de fragmentos de experiencias {#using-experience-fragments}

Esta página cubre los siguientes temas:

* **Información general**
* **Uso de fragmentos de experiencias en AEM Screens**
* **Propagación de cambios en la página**

## Información general {#overview}

Un ***fragmento de experiencias*** es un grupo de uno o varios componentes que incluye contenido y diseño que se puede consultar dentro de las páginas. Los fragmentos de experiencias pueden contener cualquier componente, como por ejemplo uno o varios componentes que pueden contener cualquier cosa dentro de un sistema de párrafos, al que se hará referencia en toda la experiencia o que solicitará un punto final tercero.


## Uso de fragmentos de experiencias en AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>El ejemplo siguiente utiliza **We.Retail** como proyecto de demostración desde el que se aprovecha el fragmento de experiencias desde una página **Sites** a un proyecto de AEM Screens.

Por ejemplo, el siguiente flujo de trabajo muestra el uso de fragmentos de experiencia de We.Retail en Sitios. Puede elegir una página web y aprovechar ese contenido en su canal de AEM Screens en uno de sus proyectos.

### Requisitos previos {#pre-requisites}

**Creación de un proyecto de demostración con un Canal**

***Creación de un proyecto***

1. Haga clic en **Crear proyecto de pantallas** para crear un nuevo proyecto.
1. Introduzca **DemoProject** como título.
1. Haga clic en **Guardar**.

Se agregará un **DemoProject** a su AEM Screens.

***Crear un canal*** 

1. Vaya a la carpeta **DemoProject** que ha creado y seleccione la carpeta **Canales**.

1. Haga clic en **Crear** desde la barra de acciones para abrir el asistente.
1. Elija la plantilla **Canal de secuencia** del asistente y haga clic en **Siguiente**.

1. Escriba el **Título** como **TestChannel** y haga clic en **Crear**.

Se agregará un **TestChannel** a su **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Creación de un fragmento de experiencia {#creating-an-experience-fragment}

Siga los pasos a continuación para aprovechar el contenido de **We.Retail** a su **TestChannel** en **DemoProject**.

1. **Navegue a la página Sitios en We.Retail**

   1. Vaya a Sitios y seleccione **Web.Retail In-Store** -> **Canales** ->**Canal inactivo - Noche** y seleccione esta página para utilizarla como fragmento de experiencia en el canal Pantallas.

   1. Haga clic en **Editar** en la barra de acciones para abrir la página que desee utilizar como fragmento de experiencia para el canal Pantallas.

1. **Reutilización del contenido**

   1. Seleccione el fragmento que desee incluir en el canal.
   1. Haga clic en el último icono de la derecha para abrir el cuadro de diálogo **Convertir en fragmento de experiencia**.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Creación del fragmento de experiencia**

   1. Elija la **Acción** como **Crear un nuevo fragmento de experiencia**.

   1. Seleccione la **ruta principal**.
   1. Seleccione la **Plantilla**. Elija la plantilla **Fragmento de experiencias - Variación de pantallas** aquí.

   1. Introduzca el **Título del fragmento** como **Fragmento de pantalla**.

   1. Haga clic en la marca de verificación para completar la creación de un nuevo fragmento de experiencia.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

1. **Creación de Live Copy del fragmento de experiencias**

   1. Vaya a la página de inicio AEM.
   1. Seleccione **Fragmentos de experiencia** y resalte el **Fragmento de pantalla** y haga clic en **Variación como Live-Copy**, como se muestra en la figura siguiente:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Seleccione el asistente **ScreensFragment** en **Crear Live Copy** y haga clic en **Siguiente**.

   d. Escriba **Título** y **Nombre** como **Pantallas**.

   e. Haga clic en **Crear** para crear la Live Copy.

   f. Haga clic en **Listo** para volver a la **página ScreensFragment**.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Una vez creado el fragmento Pantallas, puede editar las propiedades del fragmento. Seleccione el fragmento y haga clic en **Propiedades** en la barra de acciones.

   **Edición de propiedades de un fragmento de pantallas**

   1. Vaya a **ScreensFragment** (creado en los pasos anteriores) y haga clic en **Propiedades** en la barra de acciones.

   1. Seleccione la ficha **Configuración sin conexión**, como se muestra en la figura siguiente.

   Puede agregar las **bibliotecas del lado del cliente** (java y css) y **Archivos estáticos** al fragmento de experiencia.

   En el siguiente ejemplo se muestra la adición de bibliotecas de cliente y fuentes como parte de archivos estáticos al fragmento de experiencia.  ![fragmento](assets/fragment.gif)

1. **Uso del fragmento de experiencia como componente en el Canal Pantallas**

   1. Vaya al canal Pantallas donde desee utilizar el fragmento **Pantallas**.
   1. Seleccione **TestChannel** y haga clic en **Editar** en la barra de acciones.

   1. Haga clic en el icono de componentes en la ficha lateral.
   1. Arrastre y suelte el **fragmento de experiencias** en el canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Seleccione el componente **Fragmento de experiencias** y seleccione el icono de la parte superior izquierda (llave inglesa) para abrir el cuadro de diálogo **Fragmento de experiencias**.

   f. Seleccione la **Live Copy de Pantallas** del fragmento que creó en *Paso 3* en **Ruta**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Seleccione la **Live Copy de Pantallas** del fragmento creado en *Paso 3* en el **Fragmento de experiencias**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Introduzca los milisegundos en **Duración**.

   i. Seleccione **Configuración sin conexión** en el cuadro de diálogo **Fragmentos de experiencia** para definir las bibliotecas del lado del cliente y los archivos estáticos.

   >[!NOTE]
   >
   >Si desea agregar bibliotecas del lado del cliente o archivos estáticos además de lo que configuró en el paso (4), puede agregar desde la ficha **Configuración sin conexión** del cuadro de diálogo **Fragmento de experiencia**.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Haga clic en la marca de verificación para completar el proceso.

### Validación del resultado {#validating-the-result}

Después de completar los pasos anteriores, puede validar el fragmento de experiencia en **ChannelOne** mediante:

1. Navegar a **TestChannel**.
1. Seleccionar la **Previsualización** de la barra de acciones.

Vista del contenido desde la página **Sitios** (Live-Copy del fragmento de experiencia) en el canal, como se muestra en la figura siguiente:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagación de cambios en la página {#propagating-changes-from-the-master-page}

***Live*** Copy hace referencia a la copia (del origen), mantenida por las acciones de sincronización definidas por las configuraciones de despliegue.

Desde el fragmento de experiencias, hemos creado una Live Copy desde las páginas **Sitios**, por lo que si realiza cambios en ese fragmento concreto desde la página de formato, vista los cambios en el canal o en el destino donde ha utilizado el fragmento de experiencias.

>[!NOTE]
>
>Para obtener más información sobre Live Copy, consulte Reutilización del contenido: Multi Site Manager y Live Copy.

Siga los pasos a continuación para propagar los cambios del canal maestro al canal de destino:

1. Seleccione el fragmento de experiencias en la página **Sitios** (maestra) y haga clic en el icono del lápiz para editar los elementos en el fragmento de experiencias.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Seleccione el fragmento de experiencias y haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo y editar las imágenes.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. Se abre el cuadro de diálogo **Cuadrícula de producto**.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Puede editar cualquiera de las imágenes. Por ejemplo, aquí la primera imagen se sustituye en este fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Seleccione el fragmento de experiencias y haga clic en el icono de despliegue para propagar los cambios en el fragmento que se utiliza en el canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Haga clic en Despliegue para confirmar los cambios.

   Verá que los cambios se implementan.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validación de los cambios {#validating-the-changes}

Siga los pasos a continuación para confirmar los cambios en el canal:

1. Vaya a **Pantallas** -> **Canales** -> **TestChannel**.

1. Haga clic en **Previsualización** en la barra de acciones para confirmar los cambios.

La siguiente imagen ilustra los cambios en su **TestChannel**:\
![screen_shot_2018-06-08at3351pm](assets/screen_shot_2018-06-08at33351pm.png)

