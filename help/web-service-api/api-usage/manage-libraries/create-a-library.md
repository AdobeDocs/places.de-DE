---
title: Erstellen einer Bibliothek
description: Erstellen Sie eine Bibliothek mit der Places REST API.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Erstellen einer Bibliothek

Eine POST-Methode, mit der Sie eine Bibliothek erstellen können.

## Anfrage

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Kopfzeilen

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Text

```text
{"name": "<LIBRARY_NAME>"}
```

## Beispielantwort

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, Befehl

Verwenden Sie den folgenden CURL-Befehl, um diese API zu testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Variablen wie `<API KEY>`, `<TOKEN>`und `<ORGID>` durch tatsächliche Werte ersetzen

