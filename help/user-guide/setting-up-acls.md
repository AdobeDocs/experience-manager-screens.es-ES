---
title: Configuración de ACL
seo-title: Configuración de ACL
description: Siga esta página para aprender a segregar proyectos mediante ACL, de modo que cada individuo o equipo gestione su propio proyecto.
seo-description: Siga esta página para aprender a segregar proyectos mediante ACL, de modo que cada individuo o equipo gestione su propio proyecto.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuración de ACL {#setting-up-acls}

En la siguiente sección se explica cómo separar proyectos mediante ACL para que cada individuo o equipo gestione su propio proyecto.

Como administrador de AEM, debe asegurarse de que los miembros del equipo de un proyecto no interfieren con otros proyectos y de que a cada uno de los usuarios se les asignan funciones específicas según los requisitos del proyecto.

## Configuración de permisos {#setting-up-permissions}

Los siguientes pasos resumen el procedimiento para configurar las ACL de un proyecto:

1. Inicie sesión en AEM y vaya a **Herramientas** &gt; **Seguridad**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Haga clic en **Grupos** e introduzca un ID (por ejemplo, Acme).

   Como alternativa, utilice este vínculo, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   A continuación, haga clic en **Guardar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Seleccione **Colaboradores** en la lista y haga doble clic en él.

   ![screen_shot_2018-02-18at3938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Agregue el **Acme** (proyecto que ha creado) para **Agregar miembros al grupo**. Haga clic en **Guardar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Si desea que los miembros del equipo del proyecto registren reproductores (lo que implica crear un usuario para cada reproductor), busque el grupo usuarios administradores y agregue el grupo ACME a los administradores de usuarios

1. Agregue todos los usuarios que estarán trabajando en el proyecto **Acme** al grupo **Acme** .

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configure los permisos para el grupo **Acme** con esto `(http://localhost:4502/useradmin)`.

   Seleccione el grupo **Acme** y haga clic en los **permisos**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permisos {#permissions}

La siguiente tabla resume la ruta con los permisos a nivel de proyecto:

| **Ruta** | **Permiso** | **Descripción** |
|---|---|---|
| `/apps/<project>` | LEER | Proporciona acceso a los archivos de proyecto (si corresponde) |
| `/content/dam/<project>` | TODO | Proporciona acceso para almacenar recursos de proyectos como imágenes o vídeo en DAM |
| `/content/screens/<project>` | TODO | Elimina el acceso a todos los demás proyectos en /content/screen |
| `/content/screens/svc` | LEER | Proporciona acceso al servicio de registro |
| `/libs/screens` | LEER | Proporciona acceso a DCC |
| `/var/contentsync/content/screens/` | TODO | Permite actualizar el contenido sin conexión para el proyecto |

>[!NOTE]
>
>En algunos casos, puede separar las funciones de autor (como administrar recursos y crear canales) de las funciones de administración (como registrar reproductores). En este escenario, cree dos grupos y agregue el grupo de autores a colaboradores y el grupo de administradores a colaboradores y administradores de usuarios.

### Creación de grupos {#creating-groups}

La creación de un nuevo proyecto también debe crear grupos de usuarios predeterminados con un conjunto básico de permisos asignados. Debe ampliar los permisos a las funciones típicas que tenemos para AEM Screens.

Por ejemplo, puede crear los siguientes grupos específicos de proyectos:

* Pantallas para administradores de proyectos
* Pantallas Operadores de proyecto (registrar reproductores y administrar ubicaciones y dispositivos)
* Pantallas para usuarios de proyectos (trabajar con canales, programaciones y asignaciones de canal)

En la tabla siguiente se resumen los grupos con descripción y permisos para un proyecto de AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nombre del grupo</strong></td>
   <td><strong>Descripción</strong></td>
   <td><strong>Permisos</strong></td>
  </tr>
  <tr>
   <td>Administradores<br /> de pantallas <em>administradores de pantallas</em></td>
   <td>Acceso a nivel de administrador para funciones de AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Los Colaboradores</li>
     <li>Miembro DE los administradores de usuario</li>
     <li>ALL /content/screen</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screen</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Pantallas Usuarios<br /> <em>pantallas Usuarios</em></td>
   <td>Crear y actualizar canales y programas y asignarlos a la ubicación en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Los Colaboradores</li>
     <li>&lt;project&gt; /content/screen</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;proyecto&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores<br /> de pantallas, <em>operadores de pantallas</em></td>
   <td>Crear y actualizar la estructura de ubicación y registrar reproductores en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Los Colaboradores</li>
     <li>jcr:all /home/users/screen</li>
     <li>jcr:all /home/groups/screen</li>
     <li>&lt;project&gt; /content/screen</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Pantallas Reproductores<br /> <em>pantallas-nosotros-dispositivos minoristas</em></td>
   <td>Agrupa todos los reproductores y todos los reproductores/dispositivos son miembros de los colaboradores automáticamente.</td>
   <td><p> Miembro de los contribuyentes</p> </td>
  </tr>
 </tbody>
</table>
