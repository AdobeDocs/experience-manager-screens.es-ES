---
title: Nuevo importador de proyectos a partir de archivo
seo-title: Nuevo importador de proyectos a partir de archivo
description: Esta funcionalidad le permite importar de forma masiva un conjunto de ubicaciones desde una hoja de cálculo CSV/XLS a su proyecto de AEM Screens.
seo-description: Esta funcionalidad le permite importar de forma masiva un conjunto de ubicaciones desde una hoja de cálculo CSV/XLS a su proyecto de AEM Screens.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Nuevo importador de proyectos a partir de archivo {#new-project-importer-from-file}

En esta sección se describe una funcionalidad para importar de forma masiva un conjunto de ubicaciones desde una hoja de cálculo CSV/XLS a su proyecto de AEM Screens.

## Introducción {#introduction}

Al configurar un proyecto de AEM Screens por primera vez en su organización, también debe crear todas las ubicaciones. Si el proyecto incluye un gran número de ubicaciones, resulta en una tarea tediosa que implica hacer mucho clic y esperar en la interfaz de usuario.

El objetivo de esta función es reducir el tiempo necesario para configurar el proyecto y resolver así los problemas presupuestarios.

Al permitir que el autor proporcione una hoja de cálculo como archivo de entrada y que el sistema cree automáticamente el árbol de ubicación en el back-end, esta función:

* *logra mejores resultados que hacer clic manualmente a través de la interfaz de usuario*
* *permite a los clientes exportar las ubicaciones que tienen desde su propio sistema e importarlas fácilmente directamente en AEM*

Esto ahorra tiempo y dinero durante la configuración inicial del proyecto o al ampliar las pantallas de AEM existentes a nuevas ubicaciones.

## Información general de arquitectura {#architectural-overview}

En el diagrama siguiente se muestra la descripción general de la arquitectura de la función Importador de proyectos:

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modelo de datos {#data-model}

El modelo de datos para el importador de proyectos se describe a continuación:

>[!NOTE]
>
>La versión actual solo admite la importación de ubicaciones.

| **Propiedad** | **Descripción** |
|---|---|
| ***path {string*}** | Ruta de acceso del recurso para la ubicación |
| ***[./jcr:title]{string*}** | El nombre de la plantilla que se va a utilizar (es decir, la ubicación de *pantallas/núcleo/plantillas/ubicación*) |
| ***plantilla {string}*** | Título opcional que se usará para la página |
| ***[./jcr:description]{string}*** | Descripción opcional que se usará para la página |

El archivo de hoja de cálculo (CSV/XLS) requiere, por tanto, las siguientes columnas:

* **path {string}** La ruta de la ubicación que se va a importar, donde la raíz de la ruta es la carpeta de ubicación del proyecto (es decir, */foo* se importará a */content/screen/&lt;project&gt;/locations/foo*)

* **plantilla {string}** La plantilla que se usará para la nueva ubicación, por ahora el único valor permitido es "location", pero se extenderá a todas las plantillas de Pantallas en el futuro ("display", "secuencechannel, etc.)
* [**./*] {string}** Cualquier propiedad opcional que se establezca en la ubicación (es decir, ./jcr:title, ./jcr:description, ./foo, ./barra). La versión actual no permite ningún filtrado en este momento

>[!NOTE]
>
>Cualquier columna que no coincida con las condiciones anteriores se ignorará. Por ejemplo, si tiene cualquier otra columna definida en el archivo de hoja (CSV/XLS) que no sea **ruta**,**plantilla**,**título** y **descripción** en el archivo, esos campos se omitirán y el importador **de** proyectos no validará los campos adicionales para importar el proyecto en el proyecto de AEM Screens.

## Uso del Importador de proyectos {#using-project-importer}

En la sección siguiente se describe cómo se utiliza el importador de proyectos en un proyecto de AEM Screens.

>[!CAUTION]
>
>Restricciones:
>
>* La versión actual no admite archivos que no sean extensiones CSV/XLS/XLSX.
>* No existe ningún filtro de las propiedades para los archivos importados ni para nada que empiece con "./" se importará.
>



### Requisitos previos {#prerequisites}

* Crear un nuevo proyecto denominado **DemoProjectImport**

* Utilice un archivo CSV o Excel de muestra que necesite importar.

Para fines de demostración, puede descargar un archivo de Excel desde la sección siguiente.

[Obtener archivo](assets/minimal-file.xls)

### Importación del archivo con los campos mínimos requeridos {#importing-the-file-with-minimum-required-fields}

Siga los pasos a continuación para importar un archivo a la carpeta de ubicaciones con los campos mínimos requeridos:

>[!NOTE]
>
>En el siguiente ejemplo se muestran los cuatro campos mínimos necesarios para importar el proyecto:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Vaya al proyecto de AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Seleccione el proyecto,** DemoProjectImporter **—&gt;** Crear **—&gt;** Importar ubicaciones** de la barra lateral.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Se abrirá el asistente **Importar** . Seleccione el archivo que tiene para el proyecto con ubicaciones o seleccione el archivo (***Minimum-file.xls***) que descargó de la sección *Requisitos previos* .

   Una vez seleccionado el archivo, haga clic en **Siguiente**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Compruebe el contenido del archivo (ubicaciones) desde el asistente de importación y haga clic en **Importar**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Como resultado, ahora podrá ver todas las ubicaciones importadas al proyecto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
