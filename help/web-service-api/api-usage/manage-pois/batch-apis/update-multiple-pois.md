---
title: Mehrere POIs aktualisieren
description: Verwenden Sie die Batch-APIs, um mehrere POIs zu aktualisieren.
exl-id: 194027fb-eafd-4207-9190-47125ebf3bc3
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 5%

---

# Mehrere POIs aktualisieren {#update-multiple-pois}

Eine POST-Methode, mit der Sie mehrere POIs aktualisieren können.

## Anfrage

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchUpdate
```

## Kopfzeilen

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Textkörper

```text
{    "updates": [        {            "id": "<POIID>,            ""lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "id": "<POIID>,            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        .        .        .        {            "id": "<POIID>,            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "id": "<POIID>,            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        }    ]}
```

## Beispielantwort

```text
{    "ids": [        "558360b5-5b4b-4c8a-777f-5e3f4b60e4cb",        "ac01c21c-6274-4922-86d5-7777b59dc9b0",        .        .        .        "acf0fde0-22ee-470a-bfa9-b760777cefdc",        "d3cf8338-520f-49a5-8ee7-3777df69be91"    ],    "_links": {        "pois": {            "href": "https://api-places-dev.adobe.io/places/placesapi/v1/pois/{poi_id}",            "templated": true        }    }}
```

## CURL-Befehl

Verwenden Sie den folgenden CURL-Befehl, um die API zu testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchUpdate' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHUPDATEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Ersetzen Sie `<API KEY>`, `<TOKEN>`, `<ORGID>` und `<PATHTOBATCHUPDATEJSONFILE>` durch reale Werte.

## JSON-Beispieldatei

Hier finden Sie die JSON-Beispieldatei für die `batchUpdate`-API:

```text
updates":[{"id":"31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","name":"Updated POI 1","description":"1","location":{"type":"Point","coordinates":[0.0000000,0.0000000]},"radius":25.0,"country":"Ghana","state":"Ghana","city":"Accra","street":"","category":"cafe","icon":"nice","color":"red","metadata":{"region":"Equator"},"lib_id":"42b4d03c-672c-4deb-83e0-134ef070c2af"},{"id":"6a78a729-7973-4373-9199-36da18cc5b8c","name":"Updated POI 2","description":"2","location":{"type":"Point","coordinates":[0.0250000,0.0250000]},"radius":50.0,"country":"Ghana","state":"Ghana","city":"Accra","street":"","category":"cafe","icon":"nice","color":"red","metadata":{"region":"Equator"},"lib_id":"42b4d03c-672c-4deb-83e0-134ef070c2af"},{"id":"74eaa3da-2464-4298-9b6d-5376fa7ea00f","name":"Updated POI 3","description":"3","location":{"type":"Point","coordinates":[0.0500000,0.0500000]},"radius":100.0,"country":"Ghana","state":"Ghana","city":"Accra","street":"","category":"cafe","icon":"nice","color":"red","metadata":{"region":"Equator"},"lib_id":"42b4d03c-672c-4deb-83e0-134ef070c2af"}]}
```
