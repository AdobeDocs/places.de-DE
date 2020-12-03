---
title: Übersicht
description: Grundlegendes und Verwenden von Abfrage-APIs.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 4%

---



# Abfrage-APIs

Eine GET, mit der Sie die POIs, die dem Aufrufer am nächsten sind, Abfrage werden können.

## Anfrage

```text
GET https://query.places.adobe.com/placesedgequery
```

Mit der folgenden Eingabe gibt der Dienst eine Liste der POIs zurück, die dem Aufrufer am nächsten sind:

* Die Position des Aufrufers (Breitengrad, Längengrad).
* Die IDs der POI-Bibliotheken, die in die Suche einbezogen werden sollen.
* Die maximale Anzahl der zurückzugebenden POIs.  Der Standardwert lautet 100.

   Der Abstand zwischen Anrufer und POI ist definiert als der Abstand vom Anrufer bis zum Rand der POI-Sequenz. In der Antwort werden POIs, die den Aufrufer enthalten, als mit dem Aufrufer gekennzeichnet.

Argumente werden als folgende Abfragen bereitgestellt:

* (**Erforderlich**) `latitude`

   Der Breitengrad des Anrufers, der zwischen -85 und 85 liegen muss.
* (**Erforderlich**) `longitude`

   Der Längengrad des Anrufers, der zwischen -180 und 180 liegen muss.

* (**Optional**) `limit`

   Die maximale Anzahl der zurückzugebenden POIs.

* (**Erforderlich**) `library`

   Die ID der zu Abfrage Bibliothek. Um mehrere Bibliotheken Abfrage, stellen Sie sicher, dass Sie mehrere Kopien des library-Parameters in die Abfrage einschließen.

Hier ein Beispiel für das erfolgreich zurückgegebene JSON-Format:

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

POIs unter `places.pois` werden nach Entfernung vom Anrufer bis zum Rand der POIs sortiert. POIs unter `places.userWithin` enthalten den Aufrufer, und diese POIs werden nach Rang und dann nach Radius sortiert.

## Beispielaufruf

Hier ein Beispiel für den Aufruf:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
