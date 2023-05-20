---
title: API de REST
seo-title: REST API
description: AEM Screens proporciona una API RESTful simple que sigue la especificación de Siren. Siga esta página para aprender a desplazarse por la estructura de contenido y enviar comandos a los dispositivos del entorno.
seo-description: AEM Screens provides a simple RESTful API that follows the Siren specification. Follow this page to learn how to navigate the content structure and send commands to devices in the environment.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: ac01935a-c3ff-485a-b60e-227fb94c75b0
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 2%

---

# API de REST{#rest-apis}

AEM Screens proporciona una API RESTful simple que sigue al [Sirena](https://github.com/kevinswiber/siren) especificación. Permite navegar por la estructura de contenido y enviar comandos a dispositivos del entorno.

Se puede acceder a la API en [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Navegación por estructura de contenido {#navigating-content-structure}

El JSON devuelto por las llamadas de API enumera las entidades relacionadas con el recurso actual. Después del autovínculo enumerado, cada una de estas entidades vuelve a ser accesible como recurso REST.

Por ejemplo, para acceder a las pantallas de nuestra ubicación de buque insignia de demostración, puede llamar a:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

O con curl:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

El resultado tendría este aspecto:

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

Y luego, para acceder a la pantalla única, puede llamar a:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Ejecución de acciones en el recurso {#executing-actions-on-the-resource}

El JSON devuelto por las llamadas de API puede contener una lista de acciones disponibles en el recurso.

La visualización, por ejemplo, enumera una *broadcast-command* acción que permite enviar un comando a todos los dispositivos asignados a esa pantalla.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

O con curl:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***Resultado:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

Para almacenar en déclencheur esta acción se llamaría a:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

O con curl:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```
