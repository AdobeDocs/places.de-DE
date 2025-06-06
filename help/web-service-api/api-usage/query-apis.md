---
title: Übersicht
description: Verstehen und Verwenden von Abfrage-APIs.
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%

---

# Abfrage-APIs

Eine GET-Methode, mit der Sie die POIs abfragen können, die dem Aufrufer am nächsten sind.

## Anfrage

```text
GET https://query.places.adobe.com/placesedgequery
```

Mit der folgenden Eingabe gibt der Service eine Liste der POIs zurück, die den Aufrufern am nächsten sind:

* Die Position des Anrufers (Breitengrad, Längengrad).
* Die IDs der POI-Bibliotheken, die in die Suche einbezogen werden sollen.
* Die maximale Anzahl an zurückzugebenden POIs.  Der Standardwert lautet 100.

  Der Abstand zwischen dem Anrufer und dem POI wird als der Abstand zwischen dem Anrufer und dem Rand des Geofence des POI definiert. In der Antwort werden POIs, die den Aufrufer enthalten, als mit dem Aufrufer gekennzeichnet.

Argumente werden als die folgenden Abfrageparameter bereitgestellt:

* (**Erforderlich**) `latitude`

  Der Breitengrad des Anrufers, der zwischen -85 und 85 liegen muss.
* (**Erforderlich**) `longitude`

  Der Längengrad des Aufrufers, der zwischen -180 und 180 liegen muss.

* (**Optional**) `limit`

  Die maximale Anzahl an zurückzugebenden POIs.

* (**Erforderlich**) `library`

  Die ID der abzufragenden Bibliothek. Um mehrere Bibliotheken abzufragen, stellen Sie sicher, dass Sie mehrere Kopien des Bibliotheksparameters in die Abfrage einbeziehen.

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

POIs unter `places.pois` werden nach Entfernung vom Anrufer zum Rand der POIs sortiert. POIs unter `places.userWithin` enthalten die Aufrufenden. Diese POIs werden nach Rang und dann nach wachsendem Radius sortiert.

## Beispielaufruf

Im Folgenden finden Sie ein Beispiel für den Aufruf:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
