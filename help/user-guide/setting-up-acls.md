---
title: Configuración de ACL
seo-title: Configuración de ACL
description: Siga esta página para aprender a segregar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto.
seo-description: Siga esta página para aprender a segregar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# Configuración de ACL {#setting-up-acls}

En la siguiente sección se explica cómo segregar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto.

Como administrador de AEM, debe asegurarse de que los integrantes del equipo de un proyecto no interfieran con otros proyectos y que a cada uno de los usuarios se les asignen funciones específicas según los requisitos del proyecto.

## Configuración de permisos {#setting-up-permissions}

Los siguientes pasos resumen el procedimiento para configurar ACL para un proyecto:

1. Inicie sesión en AEM y vaya a **Tools** > **Security**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Haga clic en **Grupos** e introduzca un ID (por ejemplo, Acme).

   Alternativamente, utilice este enlace, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Posteriormente, haga clic en **Guardar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Seleccione **Contributors** de la lista y haga doble clic en él.

   ![screen_shot_2018-02-18at3938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Agregue el **Acme** (proyecto que ha creado) a **Agregar miembros al grupo**. Haga clic en **Guardar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Si desea que los miembros del equipo del proyecto registren reproductores (lo que implica crear un usuario para cada reproductor), busque los usuarios administradores del grupo y añada el grupo ACME a los administradores de usuarios

1. Agregue todos los usuarios que estén trabajando en el proyecto **Acme** al grupo **Acme**.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configure los permisos para el grupo **Acme** usando esta `(http://localhost:4502/useradmin)`.

   Seleccione el grupo **Acme** y haga clic en **permissions**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permisos    {#permissions}

La siguiente tabla resume la ruta con los permisos en el nivel de proyecto:

| **Ruta** | **Permiso** | **Descripción** |
|---|---|---|
| `/apps/<project>` | LEER | Proporciona acceso a archivos de proyecto (si corresponde) |
| `/content/dam/<project>` | TODO | Proporciona acceso para almacenar recursos de proyectos como imágenes o vídeo en DAM |
| `/content/screens/<project>` | TODO | Elimina el acceso a todos los demás proyectos en /content/screens |
| `/content/screens/svc` | LEER | Proporciona acceso al servicio de registro |
| `/libs/screens` | LEER | Proporciona acceso a DCC |
| `/var/contentsync/content/screens/` | TODO | Permite actualizar el contenido sin conexión del proyecto |

>[!NOTE]
>
>En algunos casos, puede separar las funciones de autor (como administrar recursos y crear canales) de las funciones de administración (como registrar reproductores). En este caso, cree dos grupos y añada el grupo de autores a los colaboradores y el grupo de administradores a los colaboradores y a los administradores de usuarios.

### Creación de grupos {#creating-groups}

La creación de un nuevo proyecto también debe crear grupos de usuarios predeterminados con un conjunto básico de permisos asignados. Debe ampliar los permisos a las funciones típicas que tenemos para AEM Screens.

Por ejemplo, puede crear los siguientes grupos específicos de proyectos:

* Administradores de proyectos de Screens
* Screens Project Operators (registrar reproductores y administrar ubicaciones y dispositivos)
* Screens Usuarios del proyecto (trabajar con canales, programaciones y asignaciones de canal)

La siguiente tabla resume los grupos con descripción y permisos para un proyecto de AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nombre del grupo</strong></td>
   <td><strong>Descripción</strong></td>
   <td><strong>Permisos</strong></td>
  </tr>
  <tr>
   <td>Administradores de Screens<br /> <em>screens-admins</em></td>
   <td>Acceso a nivel de administrador para las funciones de AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Los Colaboradores</li>
     <li>Miembro de los administradores de usuarios</li>
     <li>TODOS /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>TODOS /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Usuarios de Screens<br /> <em>usuarios de pantallas</em></td>
   <td>Crear y actualizar canales y programaciones y asignar a la ubicación en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Los Colaboradores</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores de Screens<br /> <em>screens-operators</em></td>
   <td>Crear y actualizar la estructura de ubicación y registrar reproductores en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Los Colaboradores</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Pantallas Reproductores<br /> <em>pantallas-&lt;project&gt;-dispositivos</em></td>
   <td>Agrupa todos los reproductores y todos los reproductores/dispositivos son miembros de los colaboradores automáticamente.</td>
   <td><p> Miembro de los colaboradores</p> </td>
  </tr>
 </tbody>
</table>

