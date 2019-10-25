---
title: Rang einer Bibliothek abrufen
seo-title: Rang einer Bibliothek abrufen
description: Rufen Sie den Rang einer Bibliothek mit der Places REST API ab.
seo-description: Rufen Sie den Rang einer Bibliothek mit der Places REST API ab.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Rang einer Bibliothek abrufen

Eine GET-Methode, mit der Sie Bibliotheken nach Rang ordnen können.

## Anfrage

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## Kopfzeilen

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Beispielantwort

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL, Befehl

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Variablen wie `<API KEY>`, `<TOKEN>`und `<ORGID>` durch tatsächliche Werte ersetzen

