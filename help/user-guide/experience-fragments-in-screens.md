---
title: Uso de fragmentos de experiencias
seo-title: Uso de fragmentos de experiencias
description: 'Siga esta página para obtener más información sobre el uso de fragmentos de experiencias en AEM Screens. '
seo-description: 'Siga esta página para obtener más información sobre el uso de fragmentos de experiencias en AEM Screens. '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
translation-type: tm+mt
source-git-commit: ca5c43534bca0e7832a5c9f73388b8e535ce057e
workflow-type: tm+mt
source-wordcount: '1127'
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
>El siguiente ejemplo utiliza **We.Retail** como proyecto de demostración desde el que se aprovecha el fragmento de experiencia de una página **Sites** en un proyecto de AEM Screens.

Por ejemplo, el siguiente flujo de trabajo muestra el uso de fragmentos de experiencia de We.Retail en Sites. Puede elegir una página web y aprovechar ese contenido en el canal de AEM Screens de uno de sus proyectos.

### Requisitos previos {#pre-requisites}

**Creación de un proyecto de demostración con un canal**

***Creación de un proyecto***

1. Haga clic en **Crear proyecto de Screens** para crear un nuevo proyecto.
1. Introduzca **DemoProject** como título.
1. Haga clic en **Guardar**.

Se agregará un **DemoProject** a su AEM Screens.

***Crear un canal*** 

1. Vaya a **DemoProject** que ha creado y seleccione la carpeta **Channels** .

1. Haga clic en **Crear** en la barra de acciones para abrir el asistente.
1. Elija la plantilla **Canal de secuencia** del asistente y haga clic en **Siguiente**.

1. Introduzca **Title** como **TestChannel** y haga clic en **Create**.

Se agregará un **TestChannel** a su **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Creación de un fragmento de experiencia {#creating-an-experience-fragment}

Siga los pasos a continuación para aprovechar el contenido de **We.Retail** a su **TestChannel** en **DemoProject**.

1. **Vaya a la página Sitios de We.Retail**

   1. Vaya a Sitios y seleccione **We.Retail** -> **Estados Unidos** -> **Inglés** -> **Equipo** y seleccione esta página para utilizarla como fragmento de experiencia para el canal Screens.

   1. Haga clic en **Editar** en la barra de acciones para abrir la página que desee utilizar como fragmento de experiencia para el canal de Screens.

1. **Reutilización del contenido**

   1. Seleccione el fragmento que desee incluir en el canal.
   1. Haga clic en el último icono de la derecha para abrir el cuadro de diálogo **Convertir en fragmento de experiencia**.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Creación de un fragmento de experiencia**

   1. Elija la **Acción** como **Crear un nuevo fragmento de experiencia**.

   1. Seleccione la **Ruta principal**.
   1. Seleccione la **Plantilla**. Elija la plantilla **Fragmento de experiencia - Variación de Screens** aquí (valor en el campo `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Introduzca el **Título del fragmento** como **Fragmento de pantalla**.

   1. Haga clic en la marca de verificación para completar la creación de un nuevo fragmento de experiencia.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Nota: Para seleccionar una opción más sencilla, haga clic en la marca de verificación a la derecha de los campos para abrir el cuadro de diálogo de selección.

1. **Creación de una Live Copy del fragmento de experiencia**

   1. Vaya a la página principal de AEM.
   1. Seleccione **Fragmentos de experiencias**, resalte **ScreensFragment** y haga clic en **Variación como Live Copy**, como se muestra en la figura siguiente:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Seleccione el asistente **ScreensFragment** en **Crear Live Copy** y haga clic en **Siguiente**.

   d. Introduzca **Title** y **Name** como **Screens**.

   e. Haga clic en **Create** para crear la Live Copy.

   f. Haga clic en **Listo** para volver a la página **Fragmento de pantalla**.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Una vez creado el fragmento Screens, puede editar las propiedades del fragmento. Seleccione el fragmento y haga clic en **Properties** en la barra de acciones.

   **Edición de propiedades de un fragmento de Screens**

   1. Vaya al **ScreensFragment** (creado en los pasos anteriores) y haga clic en **Properties** en la barra de acciones.

   1. Seleccione la pestaña **Offline Config** , como se muestra en la figura siguiente.

   Puede agregar **Bibliotecas del lado del cliente** (java y css) y **Archivos estáticos** al fragmento de experiencia.

   El siguiente ejemplo muestra la adición de bibliotecas del lado del cliente y las fuentes como parte de archivos estáticos al fragmento de experiencia.  ![fragmento](assets/fragment.gif)

1. **Uso del fragmento de experiencia como componente en el canal de Screens**

   1. Vaya al canal Screens en el que desea utilizar el fragmento **Screens**.
   1. Seleccione **TestChannel** y haga clic en **Editar** en la barra de acciones.

   1. Haga clic en el icono de componentes de la pestaña lateral.
   1. Arrastre y suelte el **fragmento de experiencia** en el canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Seleccione el componente **Fragmento de experiencia** y seleccione el icono de la parte superior izquierda (llave inglesa) para abrir el cuadro de diálogo **Fragmento de experiencia**.

   f. Seleccione la Live Copy **Screens** del fragmento que ha creado en *Paso 3* en **Path**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Seleccione la Live Copy **Screens** del fragmento que ha creado en el *paso 3* del **fragmento de experiencia**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Introduzca los milisegundos en **Duration**.

   i. Seleccione la **Configuración sin conexión** del cuadro de diálogo **Fragmentos de experiencias** para definir las bibliotecas del lado del cliente y los archivos estáticos.

   >[!NOTE]
   >
   >Si desea agregar bibliotecas del lado del cliente o archivos estáticos además de lo que configuró en el paso (4), puede agregar desde la pestaña **Configuración sin conexión** en el cuadro de diálogo **Fragmento de experiencia**.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Haga clic en la marca de verificación para completar el proceso.

### Validación del resultado {#validating-the-result}

Después de completar los pasos anteriores, puede validar el fragmento de experiencia en **ChannelOne** mediante:

1. Vaya a **TestChannel**.
1. Seleccionar **Preview** en la barra de acciones.

Verá el contenido desde la página **Sitios** (Live Copy del fragmento de experiencia) del canal, como se muestra en la figura siguiente:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagación de cambios en la página {#propagating-changes-from-the-master-page}

***Live*** Copy hace referencia a la copia (del origen), que se mantiene mediante acciones de sincronización definidas por las configuraciones de lanzamiento.

Desde el fragmento de experiencia, hemos creado una Live Copy desde las páginas **Sitios**, por lo que si realiza cambios en ese fragmento concreto desde la página de formato, verá los cambios en su canal o en el destino donde haya utilizado el fragmento de experiencia.

>[!NOTE]
>
>Para obtener más información sobre Live Copy, consulte Reutilización de contenido: Multi Site Manager y Live Copy.

Siga los pasos a continuación para propagar los cambios del canal maestro al canal de destino:

1. Seleccione el fragmento de experiencia en la página **Sitios** (maestra) y haga clic en el icono de lápiz para editar los elementos del fragmento de experiencia.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Seleccione el fragmento de experiencia y haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo y editar las imágenes.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. Se abre el cuadro de diálogo **Cuadrícula de producto**.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Puede editar cualquiera de las imágenes. Por ejemplo, aquí la primera imagen se reemplaza en este fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Seleccione el fragmento de experiencia y haga clic en el icono Despliegue para propagar los cambios al fragmento que se utiliza en el canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Haga clic en Despliegue para confirmar los cambios.

   Verá que los cambios se implementan.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validación de los cambios {#validating-the-changes}

Siga los pasos a continuación para confirmar los cambios en el canal:

1. Vaya a **Screens** -> **Channels** -> **TestChannel**.

1. Haga clic en **Preview** en la barra de acciones para confirmar los cambios.

La siguiente imagen ilustra los cambios en su **TestChannel**:\
![screen_shot_2018-06-08at3351pm](assets/screen_shot_2018-06-08at33351pm.png)

