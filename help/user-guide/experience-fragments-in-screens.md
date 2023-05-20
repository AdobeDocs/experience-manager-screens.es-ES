---
title: Uso de fragmentos de experiencias
seo-title: Using Experience Fragments
description: Siga esta página para obtener más información sobre el uso de Fragmentos de experiencias en AEM Screens.
seo-description: Follow this page to learn about using Experience Fragments in AEM Screens.
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 1%

---

# Uso de fragmentos de experiencias {#using-experience-fragments}

Esta página cubre los siguientes temas:

* **Información general**
* **Uso de fragmentos de experiencias en AEM Screens**
* **Propagación de cambios en la página**

## Información general {#overview}

Un ***Fragmento de experiencia*** es un grupo de uno o más componentes, incluido el contenido y el diseño, al que se puede hacer referencia en las páginas. Los fragmentos de experiencia pueden contener cualquier componente, como, uno o varios componentes que pueden contener cualquier cosa dentro de un sistema de párrafos, a los que se hará referencia en la experiencia completa o que solicitará un tercer punto final.


## Uso de fragmentos de experiencias en AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>El siguiente ejemplo utiliza **We.Retail** como proyecto de demostración desde el que se aprovecha el fragmento de experiencia de un **Sites** a un proyecto de AEM Screens.

Por ejemplo, el siguiente flujo de trabajo muestra el uso de fragmentos de experiencia de We.Retail en Sites. Puede elegir una página web y aprovechar ese contenido en su canal de AEM Screens en uno de sus proyectos.

### Requisitos previos {#pre-requisites}

**Creación de un proyecto de demostración con un canal**

***Creación de un proyecto***

1. Clic **Crear proyecto de Screens** para crear un nuevo proyecto.
1. Escriba el título como **DemoProject**.
1. Haga clic en **Guardar**.

A **DemoProject** se añadirán a su AEM Screens.

***Creación de un canal***

1. Vaya a **DemoProject** ha creado y seleccionado el **Canales** carpeta.

1. Clic **Crear** en la barra de acciones para abrir el asistente.
1. Elija la **Canal de secuencia** en el asistente y haga clic en **Siguiente**.

1. Introduzca el **Título** as **TestChannel** y haga clic en **Crear**.

A **TestChannel** se añadirá a su **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Creación de un fragmento de experiencia {#creating-an-experience-fragment}

Siga los pasos a continuación para aprovechar el contenido de **We.Retail** a su **TestChannel** in **DemoProject**.

1. **Vaya a una página de Sites en We.Retail**

   1. Vaya a Sitios y seleccione **We.Retail** -> **Estados Unidos** -> **Inglés** -> **Equipamiento** y seleccione esta página para utilizarla como un fragmento de experiencia para su canal de Screens.

   1. Clic **Editar** en la barra de acciones para abrir la página que desea utilizar como fragmento de experiencia para el canal de Screens.

1. **Reutilización del contenido**

   1. Seleccione el fragmento que desea incluir en el canal.
   1. Haga clic en el último icono de la derecha para abrir **Convertir en fragmento de experiencia** Cuadro de diálogo.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Creación del fragmento de experiencia**

   1. Elija la **Acción** as **Crear un nuevo fragmento de experiencia**.

   1. Seleccione el **Ruta principal**.
   1. Seleccione el **Plantilla**. Elija la **Fragmento de experiencias: variación de pantallas** plantilla aquí (valor del campo ) `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Introduzca el **Título del fragmento** as **ScreensFragment**.

   1. Haga clic en la marca de verificación para completar la creación de un nuevo fragmento de experiencia.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Nota: Para seleccionar una opción más fácil, haga clic en la marca de verificación a la derecha de los campos para abrir el cuadro de diálogo de selección.

1. **Creación de la Live Copy del fragmento de experiencia**

   1. AEM Vaya a la página de inicio de la.
   1. Seleccionar **Fragmentos de experiencias** y resalte el **ScreensFragment** y haga clic en **Variación como Live Copy**, como se muestra en la figura siguiente:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Seleccione la **ScreensFragment** de **Crear Live Copy** y haga clic en **Siguiente**.

   d. Introduzca la **Título** y **Nombre** as **Screens**.

   e. Haga clic **Crear** para crear la Live Copy.

   f. Haga clic **Listo** para volver a mover a **ScreensFragment** página.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Una vez creado el fragmento de Screens, puede editar las propiedades del fragmento. Seleccione el fragmento y haga clic en **Propiedades** de la barra de acciones.

   **Edición de propiedades de un fragmento de Screens**

   1. Vaya a **ScreensFragment** (creada en los pasos anteriores) y haga clic en **Propiedades** de la barra de acciones.

   1. Seleccione el **Configuración sin conexión** , como se muestra en la figura siguiente.

   Puede añadir la variable **Bibliotecas del lado del cliente** (java y css) y **Archivos estáticos** a su fragmento de experiencia.

   El siguiente ejemplo muestra la adición de bibliotecas del lado del cliente y las fuentes como parte de archivos estáticos al fragmento de experiencia.  ![fragmento](assets/fragment.gif)

1. **Uso del fragmento de experiencia como componente en el canal de Pantallas**

   1. Vaya al canal de Pantallas donde desee utilizar la variable **Screens** fragmento.
   1. Seleccione el **TestChannel** y haga clic en **Editar** de la barra de acciones.

   1. Haga clic en el icono de componentes de la pestaña lateral.
   1. Arrastre y suelte el **Fragmento de experiencia** a su canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Seleccione la **Fragmento de experiencia** y seleccione el icono superior izquierdo (llave inglesa) para abrir el **Fragmento de experiencia** Cuadro de diálogo.

   f. Seleccione la **Screens** Live Copy del fragmento creado en *Paso 3* in **Ruta**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Seleccione la **Screens** Live Copy del fragmento creado en *Paso 3* en el **Fragmento de experiencia**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Introduzca los milisegundos en **Duración**.

   i. Seleccione la opción **Configuración sin conexión** desde el **Fragmentos de experiencias** para definir las bibliotecas del lado del cliente y los archivos estáticos.

   >[!NOTE]
   >
   >Si desea agregar bibliotecas del lado del cliente o archivos estáticos además de lo que configuró en el paso (4), puede agregar desde el **Configuración sin conexión** en la pestaña **Fragmento de experiencia** Cuadro de diálogo.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Haga clic en la marca de verificación para completar el proceso.

### Validación del resultado {#validating-the-result}

Después de completar los pasos anteriores, puede validar el fragmento de experiencia en **ChannelOne** por:

1. Navegación al **TestChannel**.
1. Selección de la **Previsualizar** de la barra de acciones.

Verá el contenido desde el **Sites** (live-copy del fragmento de experiencia) en su canal, como se muestra en la figura siguiente:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagación de cambios en la página {#propagating-changes-from-the-master-page}

***Live Copy*** hace referencia a la copia (del origen), mantenida mediante acciones de sincronización definidas según las configuraciones de despliegue.

Dado que el fragmento de experiencia, que hemos creado es una Live Copy del **Sites** , de modo que si realiza cambios en ese fragmento en particular desde la página maestra, verá los cambios en su canal o en el destino en el que ha utilizado el fragmento de experiencia.

>[!NOTE]
>
>Para obtener más información sobre Live Copy, consulte Reutilización del contenido: administrador de varios sitios y Live Copy.

Siga los pasos a continuación para propagar los cambios del canal principal al canal de destino:

1. Seleccione el fragmento de experiencia de la lista **Sites** (principal) y haga clic en el icono de lápiz para editar los elementos del fragmento de experiencia.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Seleccione el fragmento de experiencia y haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo y editar las imágenes.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. El **Cuadrícula de producto** se abre el cuadro de diálogo.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Puede editar cualquiera de las imágenes. Por ejemplo, aquí la primera imagen se reemplaza en este fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Seleccione el Fragmento de experiencia y haga clic en el icono Despliegue para propagar los cambios al fragmento que se utiliza en el canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Haga clic en Despliegue para confirmar los cambios.

   Verá que los cambios se implementan.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validación de los cambios {#validating-the-changes}

Siga los pasos a continuación para confirmar los cambios en el canal:

1. Vaya a **Screens** -> **Canales** -> **TestChannel**.

1. Clic **Previsualizar** en la barra de acciones para confirmar los cambios.

La siguiente imagen ilustra los cambios en su **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
