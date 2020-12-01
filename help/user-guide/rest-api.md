---
title: API REST
seo-title: REST API
description: ' AEM Screens fornisce una semplice API RESTful conforme alle specifiche Siren. Seguite questa pagina per apprendere come navigare nella struttura del contenuto e inviare i comandi ai dispositivi nell''ambiente.'
seo-description: ' AEM Screens fornisce una semplice API RESTful conforme alle specifiche Siren. Seguite questa pagina per apprendere come navigare nella struttura del contenuto e inviare i comandi ai dispositivi nell''ambiente.'
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# REST APIs{#rest-apis}

 AEM Screens fornisce una semplice API RESTful conforme alle specifiche [Siren](https://github.com/kevinswiber/siren). Consente di navigare nella struttura del contenuto e inviare comandi ai dispositivi nell&#39;ambiente.

L&#39;API è accessibile in [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Navigazione nella struttura del contenuto {#navigating-content-structure}

Il JSON restituito dalle chiamate API elenca le entità correlate alla risorsa corrente. Dopo il collegamento autonomo elencato, ciascuna di queste entità è nuovamente accessibile come risorsa REST.

Ad esempio, per accedere ai display nella nostra posizione di punta della demo, puoi chiamare:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

O utilizzando l&#39;arricciatura:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

Il risultato sarà:

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

E per accedere al Display a schermo singolo, puoi chiamare:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Esecuzione di azioni sulla risorsa {#executing-actions-on-the-resource}

Il JSON restituito dalle chiamate API può contenere un elenco di azioni disponibili sulla risorsa.

La visualizzazione, ad esempio, elenca un&#39;azione *broadcast-command* che consente di inviare un comando a tutti i dispositivi assegnati a tale visualizzazione.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

O utilizzando l&#39;arricciatura:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***Risultato:***

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

Per attivare questa azione, è necessario chiamare:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

O utilizzando l&#39;arricciatura:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

