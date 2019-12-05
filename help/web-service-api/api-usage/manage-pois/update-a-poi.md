---
title: POI aktualisieren
description: Aktualisieren Sie einen POI mit den Places REST APIs.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# POI aktualisieren

Eine PUT-Methode, mit der Sie einen POI aktualisieren können.

## Anfrage

```text
PUT https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Kopfzeilen

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Text

```text
{  "id": "string",  "name": "string",  "description": "string",  "location": {    "type": Point",    "coordinates": [<LONGITUDE>, <LATITUDE>]  },  "radius": 0,  "country": "string",  "state": "string",  "city": "string",  "street": "string",  "category": "string",  "icon": "string",  "color": "string",  "metadata": {          "brand": "string",          "owndership": "string"          },  "lib_id": "{libraryID}"}
```

## Beispielantwort

```text
{    "id": "66e3c0fb-12fe-4af2-863e-16e0e777d777",    "name": "New Name",    "description": "18827",    "location": {        "type": "Point",        "coordinates": [            -123.000507,            37.698029        ]    },    "radius": 66,    "country": "US",    "state": "CA",    "city": "Small City",    "street": "1 Island Road",    "category": "",    "icon": "",    "color": "",    "metadata": {        "ownership": "LS",        "brand": "Island station"    },    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"}
```

## CURL, Befehl

Verwenden Sie den folgenden CURL-Befehl, um diese API zu testen:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '<SINGLEPOIDATA>' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Ersetzen `<POIID>`, `<API KEY>`, `<TOKEN>`, `<ORGID>`und `<SINGLEPOIDATA>` durch tatsächliche Werte.