---
title: Configuración de ACL
seo-title: Setting up ACLs
description: Siga esta página para aprender a separar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto.
seo-description: Follow this page to learn how to segregate projects using ACLs so that each individual or team handles their own project.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 2%

---

# Configuración de ACL {#setting-up-acls}

En la siguiente sección se explica cómo separar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto.

AEM Como administrador de un proyecto, desea asegurarse de que los integrantes del equipo de un proyecto no interfieran con otros proyectos y de que a cada uno de los usuarios se les asignen funciones específicas según los requisitos del proyecto.

## Configuración de permisos {#setting-up-permissions}

Los siguientes pasos resumen el procedimiento para configurar ACL para un proyecto:

1. AEM Inicie sesión en el servicio de correo electrónico y navegue hasta **Herramientas** > **Seguridad**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Clic **Grupos** e introduzca un ID (por ejemplo, Acme).

   También puede utilizar este vínculo. `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Posteriormente, haga clic en **Guardar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Seleccionar **Colaboradores** en la lista y haga doble clic en ella.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Añada el **Acme** (proyecto que ha creado) a **Añadir miembros al grupo**. Haga clic en **Guardar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Si desea que los miembros del equipo del proyecto registren jugadores (lo que implica crear un usuario para cada reproductor), busque los administradores de usuarios del grupo y añada el grupo ACME a los administradores de usuarios

1. Agregue todos los usuarios que trabajarán en la **Acme** Proyecto a **Acme** grupo.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configuración de los permisos para el grupo **Acme** usando esto `(http://localhost:4502/useradmin)`.

   Seleccione el grupo **Acme** y haga clic en **permissions**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permisos {#permissions}

La siguiente tabla resume la ruta con los permisos en el nivel de proyecto:

| **Ruta** | **Permiso** | **Descripción** |
|---|---|---|
| `/apps/<project>` | LECTURA | Proporciona acceso a los archivos de proyecto (si corresponde) |
| `/content/dam/<project>` | TODO | Proporciona acceso para almacenar los recursos de los proyectos, como imágenes o vídeo, en DAM |
| `/content/screens/<project>` | TODO | Elimina el acceso a todos los demás proyectos en /content/screens |
| `/content/screens/svc` | LECTURA | Proporciona acceso al servicio de registro |
| `/libs/screens` | LECTURA | Proporciona acceso a DCC |
| `/var/contentsync/content/screens/` | TODO | Permite actualizar el contenido sin conexión del proyecto |

>[!NOTE]
>
>En algunos casos, puede separar las funciones de creación (como la administración de recursos y la creación de canales) de las funciones de administración (como el registro de reproductores). En este caso, cree dos grupos y agregue el grupo Autores a Colaboradores y el grupo Administrador a Colaboradores y a administradores de usuarios.

### Creación de grupos {#creating-groups}

Al crear un nuevo proyecto, también se deben crear grupos de usuarios predeterminados con un conjunto básico de permisos asignados. Debe ampliar los permisos a las funciones habituales que tenemos para AEM Screens.

Por ejemplo, puede crear los siguientes grupos específicos de proyectos:

* Administradores de proyecto de Screens
* Operadores de proyectos de Screens (registrar reproductores y administrar ubicaciones y dispositivos)
* Usuarios de proyectos de Screens (trabajar con canales, programaciones y asignaciones de canales)

La siguiente tabla resume los grupos con descripción y permisos para un proyecto de AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nombre del grupo</strong></td>
   <td><strong>Descripción</strong></td>
   <td><strong>Permisos</strong></td>
  </tr>
  <tr>
   <td>Administradores de Screens<br /> <em>screens-admin</em></td>
   <td>Acceso de nivel de administrador para funciones de AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Colaboradores</li>
     <li>Miembro DE user-administrators</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Usuarios de Screens<br /> <em>screens-users</em></td>
   <td>Cree y actualice canales y programaciones, y asígnelos a una ubicación en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Colaboradores</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores de Screens<br /> <em>screens-operators</em></td>
   <td>Cree y actualice la estructura de ubicación y registre reproductores en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Colaboradores</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Reproductores de Screens<br /> <em>screens-&lt;project&gt;-devices</em></td>
   <td>Agrupa todos los reproductores y todos los reproductores/dispositivos que son miembros de los colaboradores automáticamente.</td>
   <td><p> Miembro de colaboradores</p> </td>
  </tr>
 </tbody>
</table>
