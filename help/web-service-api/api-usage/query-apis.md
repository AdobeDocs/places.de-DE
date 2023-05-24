---
title: Übersicht
description: Verstehen und Verwenden von Abfrage-APIs.
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 4%

---

# Abfrage-APIs

Eine GET-Methode, mit der Sie die POIs abfragen können, die dem Aufrufer am nächsten sind.

## Anfrage

```text
GET https://query.places.adobe.com/placesedgequery
```

Mit der folgenden Eingabe gibt der Dienst eine Liste der POIs zurück, die dem Aufrufer am nächsten sind:

* Position des Anrufers (Breitengrad, Längengrad).
* Die IDs der POI-Bibliotheken, die in die Suche einbezogen werden sollen.
* Die maximale Anzahl der zurückzugebenden POIs.  Der Standardwert lautet 100.

   Der Abstand zwischen Anrufer und POI ist definiert als der Abstand vom Anrufer zum Rand der POI-Geofence. In der Antwort werden POIs, die den Aufrufer enthalten, als mit dem Aufrufer gekennzeichnet.

Argumente werden als folgende Abfrageparameter bereitgestellt:

* (**Erforderlich**) `latitude`

   Der Breitengrad des Anrufers, der zwischen -85 und 85 liegen muss.
* (**Erforderlich**) `longitude`

   Der Längengrad des Anrufers, der zwischen -180 und 180 liegen muss.

* (**Optional**) `limit`

   Die maximale Anzahl der zurückzugebenden POIs.

* (**Erforderlich**) `library`

   Die ID der Bibliothek, die abgefragt werden soll. Um mehrere Bibliotheken abzufragen, stellen Sie sicher, dass Sie mehrere Kopien des Bibliotheksparameters in die Abfrage einschließen.

Im Folgenden finden Sie ein Beispiel für das erfolgreich zurückgegebene JSON-Format:

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

POIs unter `places.pois` sind nach der Entfernung vom Anrufer zum Rand der POIs sortiert. POIs unter `places.userWithin` enthält den Aufrufer, und diese POIs werden nach Rang geordnet und dann durch Erhöhung des Radius.

## Beispielaufruf

Im Folgenden finden Sie ein Beispiel für den Aufruf:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
