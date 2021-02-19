---
title: Kopfzeilen und Parameter
description: Kopfzeilen und Parameter, die in den REST-APIs des Places-Dienstes verfügbar sind.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 12%

---


# Überschriften und Parameter {#headers-and-parameters}

Im Folgenden finden Sie die Details zu den Headern und Parametern, die in der REST-API des Places Service verfügbar sind:

## Unterstützte Header

| Header | Beschreibung | Methode | Beispiel |
| :--- | :--- | :--- | :--- |
| `Authorization` | Ihr InhaberToken | Alle |  |
| `x-api-key` | Ihr API-Schlüssel | Alle | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Ihre Organisations-ID | Alle | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format der gesendeten oder empfangenen Inhalte | PUT, POST | `application/json` |
| `Accept-Language` | Sprache für Fehlermeldungen | Optional | `en-US` |

## Bibliotheksparameter

| Parameter | Beschreibung | Typ | Maximal | Anforderung oder Antwort | Beispiel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID der Bibliothek | zugewiesen | n/a | Antwort | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Name der Bibliothek | Zeichenfolge | 256 Zeichen | beide in Anforderung erforderlich | `"name": "Amazing Places"` |
| `orgID` | Experience Cloud-Organisations-ID des Unternehmens | zugewiesen | n/a | Antwort | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Anzahl der POI in der Bibliothek | Ganzzahl | 150.000 max. | Antwort | `"poiCount": 25149` |
| `metadataDescriptors` | Anzahl der einzelnen eindeutigen POI-Metadaten-Schlüsselwertpaare | gemischt | n/a | Antwort |  |
| `poiCountInCities` | Anzahl für jeden eindeutigen POI-Stadtwert | gemischt | n/a | Antwort |  |

## POI-Parameter

| Parameter | Beschreibung | Typ | Maximal | Anforderung oder Antwort | Beispiel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poddaten | Array von POI-Details | n/a | both |  |
| `id` | ID der POI | zugewiesen | n/a | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Name der Einrichtung | Zeichenfolge | 512 Zeichen | beide, optional\* | `"name": "My Favorite Place"` |
| `description` | Beschreibung des POI | Zeichenfolge | 512 Zeichen | beide, optional\* | `"description": "This is a very good place."` |
| `location` | Array von Typ und Koordinaten des POI | array (gemischt) | n/a | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Art der POI | Zeichenfolge | Nur &quot;Point&quot;wird derzeit unterstützt | beide in Anforderung erforderlich | `"type": "Point"` |
| `coordinates` | Längen- und Breitengrad von POI | array (float) | Längengrad: -180 bis 180, Breitengrad -85 bis 85 | beide in Anforderung erforderlich | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Größe der kreisförmigen Gewichte um POI | float | 10 - 2000 Meter | beide in Anforderung erforderlich | `"radius": 100` |
| `country` | Land für den POI | Zeichenfolge | 32 Zeichen | beide, optional* | `"country": "United States"` |
| `state` | Bundesland für Berufsbildung | Zeichenfolge | 32 Zeichen | beide, optional* | `"state": "California"` |
| `city` | Ort für den POI | Zeichenfolge | 32 Zeichen | beide, optional* | `"city": "San Jose"` |
| `street` | Straße für das POI | Zeichenfolge | 256 Zeichen | beide, optional* | `"street": "122 Woz Way"` |
| `category` | Kategorie für den POI | Zeichenfolge | 100 Zeichen | beide, optional* | `"category": "cafe"` |
| `icon` | Symbol für die POI | Zeichenfolge | 50 Zeichen | beide, optional* | `"icon": "star"` |
| `color` | Farbe für die POI | Zeichenfolge | 8 Zeichen | beide, optional* | `"color": "blue"` |
| `metadata` | Array von Schlüssel/Wert-Paaren für den POI | array(string) | key: 256 Zeichen, Wert: 256 Zeichen, max. 10 Paare | beide, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID der Bibliothek, in der sich der POI befindet | n/a | n/a | beide, erforderlich | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Wenn der Parameterwert nicht enthalten ist, wird der Wert in der Datenbank auf `empty` gesetzt. Wenn das vorhandene Schlüssel/Wert-Paar nicht enthalten ist, wird das Schlüssel/Wert-Paar für diesen POI in der Datenbank entfernt.

