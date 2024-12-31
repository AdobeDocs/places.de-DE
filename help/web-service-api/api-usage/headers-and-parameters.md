---
title: Kopfzeilen und Parameter
description: Kopfzeilen und Parameter, die in den Places Service-REST-APIs verfügbar sind.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%

---

# Kopfzeilen und Parameter {#headers-and-parameters}

Im Folgenden finden Sie die Details zu den Kopfzeilen und Parametern, die in der Places Service-REST-API verfügbar sind:

## Unterstützte Header

| Header | Beschreibung | Methode | Beispiel |
| :--- | :--- | :--- | :--- |
| `Authorization` | Ihr Bearer-Token | Alle |  |
| `x-api-key` | Ihr API-Schlüssel | Alle | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Ihre Organisations-ID | Alle | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format des gesendeten oder empfangenen Inhalts | PUT, POST | `application/json` |
| `Accept-Language` | Sprache für Fehlermeldungen | Optional | `en-US` |

## Bibliotheksparameter

| Parameter | Beschreibung | Typ | Limit | Anfrage oder Antwort | Beispiel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID der Bibliothek | Zugewiesen | n. z. | Antwort | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Name der Bibliothek | Zeichenfolge | 256 Zeichen | Beide, in der Anfrage erforderlich | `"name": "Amazing Places"` |
| `orgID` | Experience Cloud-Organisations-ID | Zugewiesen | n. z. | Antwort | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Anzahl der POIs in der Bibliothek | integer | max. 150.000 | Antwort | `"poiCount": 25149` |
| `metadataDescriptors` | Anzahl für jedes eindeutige POI-Metadaten-Schlüsselwertpaar | gemischt | n. z. | Antwort |  |
| `poiCountInCities` | Anzahl für jeden eindeutigen POI-Stadtwert | gemischt | n. z. | Antwort |  |

## POI-Parameter

| Parameter | Beschreibung | Typ | Limit | Anfrage oder Antwort | Beispiel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | POI-Daten | Array von POI-Details | n. z. | Beide |  |
| `id` | ID des POI | Zugewiesen | n. z. | Antwort | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Name des POI | Zeichenfolge | 512 Zeichen | Beide, optional\* | `"name": "My Favorite Place"` |
| `description` | Beschreibung des POI | Zeichenfolge | 512 Zeichen | Beide, optional\* | `"description": "This is a very good place."` |
| `location` | Array von Typ und Koordinaten des POI | Array (gemischt) | n. z. | Beide | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI-Typ | Zeichenfolge | nur „Punkt“ derzeit unterstützt | Beide, in der Anfrage erforderlich | `"type": "Point"` |
| `coordinates` | Array von Längen- und Breitengrad des POI | Array (float) | Längengrad: -180 bis 180, Breite -85 bis 85 | Beide, in der Anfrage erforderlich | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Größe des kreisförmigen Geofence um POI | float | 10 - 2000 Meter | Beide, in der Anfrage erforderlich | `"radius": 100` |
| `country` | Land für den POI | Zeichenfolge | 32 Zeichen | Beide, optional* | `"country": "United States"` |
| `state` | Status des POI | Zeichenfolge | 32 Zeichen | Beide, optional* | `"state": "California"` |
| `city` | Stadt für den POI | Zeichenfolge | 32 Zeichen | Beide, optional* | `"city": "San Jose"` |
| `street` | Straße des POI | Zeichenfolge | 256 Zeichen | Beide, optional* | `"street": "122 Woz Way"` |
| `category` | Kategorie für den POI | Zeichenfolge | 100 Zeichen | Beide, optional* | `"category": "cafe"` |
| `icon` | Symbol für den POI | Zeichenfolge | 50 Zeichen | Beide, optional* | `"icon": "star"` |
| `color` | Farbe für den POI | Zeichenfolge | 8 Zeichen | Beide, optional* | `"color": "blue"` |
| `metadata` | Array von Schlüssel/Wert-Paaren für den POI | ARRAY(Zeichenfolge) | Schlüssel: 256 Zeichen, Wert: 256 Zeichen, maximal 10 Paare | Beide, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID der Bibliothek, in der sich der POI befindet | n. z. | n. z. | Beide, erforderlich | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Wenn der Parameterwert nicht enthalten ist, wird der Wert in der Datenbank auf `empty` gesetzt. Wenn das vorhandene Schlüssel/Wert-Paar nicht enthalten ist, wird das Schlüssel/Wert-Paar für diesen POI in der Datenbank entfernt.
