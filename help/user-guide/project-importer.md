---
title: Nuevo importador de proyectos desde archivo
seo-title: New Project Importer from File
description: Esta funcionalidad le permite importar de forma masiva un conjunto de ubicaciones de una hoja de cálculo CSV/XLS a su proyecto de AEM Screens.
seo-description: This functionality allows you to bulk-import a set of locations from a CSV/XLS spreadsheet to your AEM Screens project.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 2%

---

# Nuevo importador de proyectos desde archivo {#new-project-importer-from-file}

En esta sección se describe una funcionalidad para importar de forma masiva un conjunto de ubicaciones de una hoja de cálculo CSV/XLS a su proyecto de AEM Screens.

## Introducción {#introduction}

Cuando configure un proyecto de AEM Screens, por primera vez en su organización, también debe crear todas las ubicaciones. Si el proyecto incluye un gran número de ubicaciones, se convierte en una tarea tediosa que implica hacer mucho clic y esperar en la interfaz de usuario.

El objetivo de esta función es reducir el tiempo necesario para configurar el proyecto y resolver así los problemas presupuestarios.

Al permitir que el autor proporcione una hoja de cálculo como archivo de entrada y permitir que el sistema cree automáticamente el árbol de ubicaciones en el back-end, esta función:

* *logra un rendimiento mucho mejor que hacer clic manualmente en la IU*
* *AEM permite que los clientes exporten las ubicaciones que tienen de su propio sistema e importen fácilmente directamente en los archivos de la interfaz de usuario de los clientes de*

Esto ahorra tiempo y dinero durante la configuración inicial del proyecto o al ampliar el AEM Screens existente a nuevas ubicaciones.

## Información general de la arquitectura {#architectural-overview}

En el diagrama siguiente se muestra la descripción general de la arquitectura de la característica Importador de proyectos:

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modelo de datos {#data-model}

A continuación se describe el modelo de datos del importador de proyectos:

>[!NOTE]
>
>La versión actual solo admite la importación de ubicaciones.

| **Propiedad** | **Descripción** |
|---|---|
| ***ruta {string}*}** | Ruta de recurso de la ubicación |
| ***[./jcr:título] {string}*}** | El nombre de la plantilla que se va a utilizar (es decir, la ubicación para *screens/core/templates/location*) |
| ***plantilla {string}*** | Título opcional que se usará para la página |
| ***[./jcr:descripción] {string}*** | Descripción opcional que se utilizará para la página |

El archivo de hoja de cálculo (CSV/XLS), por lo tanto, requiere las siguientes columnas:

* **ruta {string}** Ruta de acceso de la ubicación que se va a importar, donde la raíz de la ruta es la carpeta de ubicación del proyecto (es decir, */foo* se importará a */content/screens/&lt;project>/locations/foo*)

* **plantilla {string}** La plantilla que se utilizará para la nueva ubicación, por ahora el único valor permitido es &quot;ubicación&quot;, pero esto se ampliará a todas las plantillas de Screens en el futuro (&quot;visualización&quot;, &quot;canal de secuencia&quot;, etc.)
* **[./*] {string}** Cualquier propiedad opcional que se establezca en la ubicación (es decir, ./jcr:title, ./jcr:descripción, ./foo, ./barra). La versión actual no permite ningún filtrado en este momento

>[!NOTE]
>
>Se ignorará cualquier columna que no cumpla las condiciones anteriores. Por ejemplo, si tiene cualquier otra columna definida en el archivo de hoja (CSV/XLS) que no sea **ruta**,**plantilla**,**title**, y **description** en el archivo, esos campos se ignorarán y **Importador de proyectos** no validará esos campos adicionales para importar el proyecto a su proyecto de AEM Screens.

## Usar el importador de proyectos {#using-project-importer}

En la siguiente sección se describe cómo se utiliza el importador de proyectos en un proyecto de AEM Screens.

>[!CAUTION]
>
>Restricciones:
>
>* La versión actual no admite archivos que no sean extensiones CSV/XLS/XLSX.
>* No existe ningún filtrado de las propiedades para los archivos importados y nada que comience por &quot;./&quot; se importará.
>


### Requisitos previos {#prerequisites}

* Cree un nuevo proyecto con el título **DemoProjectImport**

* Utilice un archivo CSV o de Excel de ejemplo que necesite importar.

Para fines de demostración, puede descargar un archivo de Excel desde la sección siguiente.

[Obtener archivo](assets/minimal-file.xls)

### Importación del archivo con el mínimo de campos obligatorios {#importing-the-file-with-minimum-required-fields}

Siga los pasos a continuación para importar un archivo a la carpeta de ubicaciones con los campos mínimos requeridos:

>[!NOTE]
>
>El siguiente ejemplo muestra el mínimo de cuatro campos necesarios para importar el proyecto:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Vaya al proyecto de AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Seleccione el proyecto,** DemoProjectImporter **—>** Crear **—>** Importar ubicaciones** desde la barra lateral.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. El **Importar** asistente abierto. Seleccione el archivo que tiene para su proyecto con ubicaciones o seleccione el archivo (***minimal-file.xls***) que descargó del *Requisitos previos* sección.

   Una vez seleccionado el archivo, haga clic en **Siguiente**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Compruebe el contenido del archivo (ubicaciones) desde el Asistente de importación y haga clic en **Importar**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Como resultado, ahora podrá ver todas las ubicaciones importadas en el proyecto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
