---
title: API de REST
seo-title: API de REST
description: AEM Screens proporciona una API RESTful simple que sigue la especificación Siren. Siga esta página para aprender a desplazarse por la estructura de contenido y enviar comandos a los dispositivos del entorno.
seo-description: AEM Screens proporciona una API RESTful simple que sigue la especificación Siren. Siga esta página para aprender a desplazarse por la estructura de contenido y enviar comandos a los dispositivos del entorno.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
feature: Desarrollo de pantallas
role: Desarrollador
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# API de REST{#rest-apis}

AEM Screens proporciona una API RESTful simple que sigue la especificación [Siren](https://github.com/kevinswiber/siren). Permite desplazarse por la estructura de contenido y enviar comandos a dispositivos en el entorno.

Se puede acceder a la API en [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Navegación por la estructura de contenido {#navigating-content-structure}

El JSON devuelto por las llamadas a la API enumera las entidades relacionadas con el recurso actual. Después del autovínculo enumerado, se vuelve a acceder a cada una de estas entidades como recurso REST.

Por ejemplo, para acceder a las pantallas de nuestra ubicación de señalización de demostración, puede llamar a:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

O utilizando curl:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

El resultado sería el siguiente:

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

A continuación, para acceder a la visualización de una sola pantalla, puede llamar a:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Ejecución de acciones en el recurso {#executing-actions-on-the-resource}

El JSON devuelto por las llamadas a la API puede contener una lista de acciones disponibles en el recurso.

La pantalla, por ejemplo, enumera una acción *broadcast-command* que permite enviar un comando a todos los dispositivos asignados a esa pantalla.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

O utilizando curl:

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

Para almacenar en déclencheur esta acción, se llamaría a:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

O utilizando curl:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

