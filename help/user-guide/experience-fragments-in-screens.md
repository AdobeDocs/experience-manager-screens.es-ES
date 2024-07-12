---
title: Uso de fragmentos de experiencias
description: Obtenga información sobre el uso de fragmentos de experiencias en AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 1%

---

# Uso de fragmentos de experiencias {#using-experience-fragments}

Esta página cubre los siguientes temas:

* **Información general**
* **Uso de fragmentos de experiencias en AEM Screens**
* **Propagando cambios a la página**

## Información general {#overview}

Un ***fragmento de experiencia*** es un grupo de uno o más componentes, incluido el contenido y el diseño, a los que se puede hacer referencia en las páginas. Los fragmentos de experiencias pueden contener cualquier componente. Por ejemplo, puede contener uno o varios componentes que pueden contener cualquier cosa dentro de un sistema de párrafos al que se hace referencia en la experiencia completa o que solicita un tercer punto final.


## Uso de fragmentos de experiencias en AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>El siguiente ejemplo usa **`We.Retail`** como proyecto de demostración desde el que se aplica el fragmento de experiencia de una página de **Sites** a un proyecto de AEM Screens.

Como ejemplo, el siguiente flujo de trabajo muestra el uso de fragmentos de experiencias de `We.Retail` en Sites. Puede elegir una página web y utilizar ese contenido en su canal de AEM Screens en uno de sus proyectos.

### Requisitos previos {#pre-requisites}

**Creación de un proyecto de demostración con un canal**

***Creando un proyecto***

1. Para crear un proyecto, haga clic en **Crear proyecto de Screens**.
1. Escriba el título como **DemoProject**.
1. Haga clic en **Guardar**.

Se ha agregado un **DemoProject** a su AEM Screens.

***Creando un canal***

1. Vaya al **DemoProject** que creó y haga clic en la carpeta **Canales**.

1. Haga clic en **Crear** en la barra de acciones para abrir el asistente.
1. Elija la plantilla **Canal de secuencia** del asistente y haga clic en **Siguiente**.

1. Escriba **Title** como **TestChannel** y haga clic en **Crear**.

Se ha agregado un **TestChannel** a su **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Creación de un fragmento de experiencia {#creating-an-experience-fragment}

Siga los pasos a continuación para aplicar el contenido de **`We.Retail`** a su **TestChannel** en **DemoProject**.

1. **Navegar a una página de Sites en We.Retail**

   1. Vaya a Sitios y haga clic en **`We.Retail`** > **Estados Unidos** > **Inglés** > **Equipo** y haga clic en esta página para poder utilizarla como un fragmento de experiencia para su canal de Screens.

   1. Haga clic en **Editar** en la barra de acciones para poder abrir la página que quiera usar como fragmento de experiencia para su canal de Screens.

1. **Reutilizando el contenido**

   1. Haga clic en el fragmento que desee incluir en el canal.
   1. Haga clic en el último icono de la derecha para abrir el cuadro de diálogo **Convertir en fragmento de experiencia**.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Creando un fragmento de experiencia**

   1. Elija **Acción** como **Crear un nuevo Fragmento de experiencia**.

   1. Haga clic en **Ruta principal**.
   1. Haga clic en **Plantilla**. Elija la plantilla **Fragmento de experiencia - Variación de Screens** aquí (valor del campo `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Escriba el **Título del fragmento** como **ScreensFragment**.

   1. Para completar la creación de un nuevo fragmento de experiencia, haga clic en la marca de verificación.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Para seleccionar una opción más sencilla, haga clic en la marca de verificación situada a la derecha del campo para abrir el cuadro de diálogo de selección.

1. **Creando Live Copy del fragmento de experiencia**

   1. AEM Vaya a la página de inicio de la.
   1. Haga clic en **Fragmentos de experiencias**, resalte **ScreensFragment** y haga clic en **Variación como Live Copy**, como se muestra en la figura siguiente:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Haga clic en **ScreensFragment** del asistente de **Crear Live Copy** y haga clic en **Siguiente**.

   d. Escriba **Title** y **Name** como **Screens**.

   e. Haz clic en **Crear** para crear Live Copy.

   f. Haz clic en **Listo** para poder volver a la página **ScreensFragment**.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Después de crear un fragmento de AEM Screens, puede editar las propiedades del fragmento. Haga clic en el fragmento y luego en **Propiedades** en la barra de acciones.

   **Edición de propiedades de un fragmento de Screens**

   1. Vaya a **ScreensFragment** (que creó en los pasos anteriores) y haga clic en **Propiedades** en la barra de acciones.

   1. Haga clic en la ficha **Configuración sin conexión**, como se muestra en la figura siguiente.

   Puede agregar **Bibliotecas del lado del cliente** (Java™ y CSS) y **Archivos estáticos** a su Fragmento de experiencia.

   El siguiente ejemplo muestra la adición de bibliotecas del lado del cliente y las fuentes como parte de archivos estáticos al Fragmento de experiencia.  ![fragmento](assets/fragment.gif)

1. **Uso del fragmento de experiencia como componente en el canal de Screens**

   1. Vaya al canal de Screens donde desee usar el fragmento **Screens**.
   1. Haga clic en **TestChannel** y luego en **Editar** en la barra de acciones.

   1. Haga clic en el icono de componentes de la pestaña lateral.
   1. Arrastre y suelte el **Fragmento de experiencia** en su canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Haga clic en el componente **Fragmento de experiencia** y haga clic en el icono superior izquierdo (llave inglesa) para abrir el cuadro de diálogo **Fragmento de experiencia**.

   f. Haga clic en la Live Copy **Screens** del fragmento que creó en el *Paso 3* en **Ruta**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Haga clic en la Live Copy **Screens** del fragmento que creó en el *paso 3* del **fragmento de experiencia**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Escriba los milisegundos en **Duración**.

   i. Haga clic en **Configuración sin conexión** en el cuadro de diálogo **Fragmentos de experiencias** para que pueda definir las bibliotecas del lado del cliente y los archivos estáticos.

   >[!NOTE]
   >
   >Para agregar bibliotecas del lado del cliente o archivos estáticos además de lo que configuró en el paso (4), puede agregar desde la pestaña **Configuración sin conexión** en el cuadro de diálogo **Fragmento de experiencia**.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Haga clic en la marca de verificación para completar el proceso.

### Validación del resultado {#validating-the-result}

Una vez completados los pasos anteriores, puede validar el fragmento de experiencia en **ChannelOne**:

1. Navegando a **TestChannel**.
1. Seleccionando **Vista previa** de la barra de acciones.

Vea el contenido de la página **Sites** (Live Copy del fragmento de experiencia) en su canal, como se muestra en la figura siguiente:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagación de cambios en la página {#propagating-changes-from-the-master-page}

***Live Copy*** hace referencia a la copia (del origen), mantenida mediante acciones de sincronización definidas según las configuraciones de despliegue.

Dado que el fragmento de experiencia que ha creado es una Live Copy de las páginas de **Sites** y cambia ese fragmento en particular desde la página principal, verá los cambios en su canal. O bien, vea el destino en el que ha utilizado el fragmento de experiencia.

>[!NOTE]
>
>Para obtener más información sobre Live Copy, consulte Reutilización del contenido: administrador de varios sitios y Live Copy.

Siga los pasos a continuación para propagar los cambios del canal principal al canal de destino:

1. Haga clic en el fragmento de experiencia de la página **Sites** (principal) y haga clic en el icono de lápiz para poder editar los elementos del fragmento de experiencia.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Haga clic en el Fragmento de experiencia y haga clic en el icono de la llave inglesa para abrir el cuadro de diálogo y editar las imágenes.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. Se abre el cuadro de diálogo **Cuadrícula de producto**.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Puede editar cualquiera de las imágenes. Por ejemplo, aquí la primera imagen se reemplaza en este fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Haga clic en el Fragmento de experiencia y haga clic en el icono Despliegue para poder propagar los cambios al fragmento que se utiliza en el canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Haga clic en Despliegue.

   Observe que los cambios se despliegan.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validación de los cambios {#validating-the-changes}

Siga los pasos a continuación para confirmar los cambios en el canal:

1. Vaya a **Screens** > **Canales** > **TestChannel**.

1. Haga clic en **Vista previa** en la barra de acciones.

La siguiente imagen ilustra los cambios en su **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
