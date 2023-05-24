---
title: Kopfzeilen und Parameter
description: Kopfzeilen und Parameter, die in den Places Service-REST-APIs verfügbar sind.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 17%

---

# Kopfzeilen und Parameter {#headers-and-parameters}

Im Folgenden finden Sie Details zu den Kopfzeilen und Parametern, die in der Places Service REST-API verfügbar sind:

## Unterstützte Kopfzeilen

| Header | Beschreibung | Methode | Beispiel |
| :--- | :--- | :--- | :--- |
| `Authorization` | Ihr Trägertoken | Alle |  |
| `x-api-key` | Ihr API-Schlüssel | Alle | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Ihre Organisations-ID | Alle | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format des gesendeten oder empfangenen Inhalts | PUT, POST | `application/json` |
| `Accept-Language` | Sprache, die für Fehlermeldungen verwendet wird | Optional | `en-US` |

## Bibliotheksparameter

| Parameter | Beschreibung | Typ | Limit | Anforderung oder Antwort | Beispiel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID der Bibliothek | assigned | Nicht zutreffend | Antwort | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Name der Bibliothek | Zeichenfolge | 256 Zeichen | beide in Anfrage erforderlich | `"name": "Amazing Places"` |
| `orgID` | Experience Cloud-Organisations-ID der Organisation | assigned | Nicht zutreffend | Antwort | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Anzahl der POIs in der Bibliothek | integer | 150.000 max. | Antwort | `"poiCount": 25149` |
| `metadataDescriptors` | Zählung für jedes eindeutige Schlüsselwertpaar für POI-Metadaten | gemischt | Nicht zutreffend | Antwort |  |
| `poiCountInCities` | Zählung für jeden einzelnen POI-Stadtwert | gemischt | Nicht zutreffend | Antwort |  |

## POI-Parameter

| Parameter | Beschreibung | Typ | Limit | Anforderung oder Antwort | Beispiel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | POI-Daten | Array von POI-Details | Nicht zutreffend | both |  |
| `id` | Kennung des POI | assigned | Nicht zutreffend | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Name des POI | Zeichenfolge | 512 Zeichen | beides, optional\* | `"name": "My Favorite Place"` |
| `description` | Beschreibung des POI | Zeichenfolge | 512 Zeichen | beides, optional\* | `"description": "This is a very good place."` |
| `location` | Array von Typ und Koordinaten des POI | Array (gemischt) | Nicht zutreffend | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI-Typ | Zeichenfolge | Derzeit nur &quot;Point&quot;unterstützt | beide in Anfrage erforderlich | `"type": "Point"` |
| `coordinates` | Längen- und Breitengrad des POI | array (float) | longitude: -180 bis 180, Breitengrad -85 bis 85 | beide in Anfrage erforderlich | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Größe der kreisförmigen Geofenz um POI | float | 10 - 2000 Meter | beide in Anfrage erforderlich | `"radius": 100` |
| `country` | Land für den POI | Zeichenfolge | 32 Zeichen | beides, optional* | `"country": "United States"` |
| `state` | Bundesstaat für POI | Zeichenfolge | 32 Zeichen | beides, optional* | `"state": "California"` |
| `city` | Ort für den POI | Zeichenfolge | 32 Zeichen | beides, optional* | `"city": "San Jose"` |
| `street` | Straße für den POI | Zeichenfolge | 256 Zeichen | beides, optional* | `"street": "122 Woz Way"` |
| `category` | Kategorie für POI | Zeichenfolge | 100 Zeichen | beides, optional* | `"category": "cafe"` |
| `icon` | Symbol für den POI | Zeichenfolge | 50 Zeichen | beides, optional* | `"icon": "star"` |
| `color` | Farbe für den POI | Zeichenfolge | 8 Zeichen | beides, optional* | `"color": "blue"` |
| `metadata` | Array von Schlüssel/Wert-Paaren für den POI | array(string) | key: 256 Zeichen, Wert: 256 Zeichen, max. 10 Paare | beides, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID der Bibliothek, in der sich der POI befindet | Nicht zutreffend | Nicht zutreffend | beide, erforderlich | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Wenn der Parameterwert nicht enthalten ist, wird der Wert auf `empty` in der Datenbank. Wenn das vorhandene Schlüssel/Wert-Paar nicht enthalten ist, wird das Schlüssel/Wert-Paar für diesen POI in der Datenbank entfernt.
