---
title: Configuración de ACL
description: Aprenda a separar proyectos mediante Listas de control de acceso (ACL) para que cada individuo o equipo administre su propio proyecto.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: 71b4f55c860d559dceaac9d5bf7ea71ce52210fa
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Configuración de listas de control de acceso (ACL) {#setting-up-acls}

En la siguiente sección se explica cómo separar proyectos mediante Listas de control de acceso (ACL) para que cada individuo o equipo administre su propio proyecto.

AEM Como administrador de un proyecto, desea asegurarse de que los integrantes del equipo de un proyecto no interfieran con otros proyectos. A cada usuario se le asignan funciones específicas según los requisitos del proyecto.

## Configuración de permisos {#setting-up-permissions}

Los siguientes pasos resumen el procedimiento para configurar ACL para un proyecto:

1. AEM Inicie sesión para iniciar sesión y navegue hasta **Herramientas** > **Seguridad**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Haga clic en **Grupos** e introduzca un ID (por ejemplo, Acme).

   También se puede usar este vínculo `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   A continuación, haga clic en **Guardar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Haga clic en **Colaboradores** de la lista y haga doble clic en él.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Agregue **Acme** (proyecto que creó) a **Agregar miembros al grupo**. Haga clic en **Guardar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Si desea que los miembros del equipo del proyecto registren jugadores (lo que implica crear un usuario para cada reproductor), busque los administradores de usuarios del grupo y añada el grupo ACME a los administradores de usuarios

1. Agregue todos los usuarios que estén trabajando en el proyecto **Acme** al grupo **Acme**.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configure los permisos para el grupo **Acme** con este(a) `(http://localhost:4502/useradmin)`.

   Haga clic en el grupo **Acme** y luego en los **permisos**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permisos {#permissions}

La siguiente tabla resume la ruta con los permisos en el nivel de proyecto:

| **Ruta** | **Permiso** | **Descripción** |
|---|---|---|
| `/apps/<project>` | LECTURA | Proporcionar acceso a los archivos de proyecto, si corresponde. |
| `/content/dam/<project>` | TODO | Proporcionar acceso para almacenar los recursos del proyecto, como imágenes o vídeo, en DAM. |
| `/content/screens/<project>` | TODO | Elimina el acceso a todos los demás proyectos en /content/screens. |
| `/content/screens/svc` | LECTURA | Proporcionar acceso al servicio de registro. |
| `/libs/screens` | LECTURA | Proporcionar acceso a DCC. |
| `/var/contentsync/content/screens/` | TODO | Ayudarle a actualizar el contenido sin conexión del proyecto. |

>[!NOTE]
>
>A veces, puede separar las funciones de creación (como la administración de recursos y la creación de canales) de las funciones de administración (como el registro de reproductores). En este caso, cree dos grupos y agregue el grupo Autores a Colaboradores y el grupo Administrador a Colaboradores y a administradores de usuarios.

### Creación de grupos {#creating-groups}

Al crear un proyecto, también se deben crear grupos de usuarios predeterminados con un conjunto básico de permisos asignados. Amplíe los permisos a las funciones típicas definidas en AEM Screens.

Por ejemplo, puede crear los siguientes grupos específicos de proyectos:

* Administradores de proyectos de Screens
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
   <td>Administradores de Screens<br /> <em><code>screens-admins</code></em></td>
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
   <td>Usuarios de Screens<br /> <em><code>screens-users</code></em></td>
   <td>Cree y actualice canales y programaciones, y asígnelos a ubicaciones en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Colaboradores</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores de Screens<br /> <em><code>screens-operators</code></em></td>
   <td>Cree y actualice la estructura de ubicación y registre reproductores en AEM Screens</td>
   <td>
    <ul>
     <li>Miembro De Colaboradores</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Players<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>Todos los reproductores y todos los reproductores/dispositivos son miembros de los colaboradores automáticamente.</td>
   <td><p> Miembro de colaboradores</p> </td>
  </tr>
 </tbody>
</table>
