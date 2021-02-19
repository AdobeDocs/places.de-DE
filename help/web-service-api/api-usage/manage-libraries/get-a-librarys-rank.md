---
title: Rang einer Bibliothek abrufen
description: Rufen Sie den Rang einer Bibliothek mit der Places REST API ab.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 9%

---


# Rang einer Bibliothek abrufen {#get-library-rank}

Eine GET, mit der Sie Bibliotheken nach Rang ordnen können.

## Anfrage

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## Header

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
>Ersetzen Sie Variablen wie `<API KEY>`, `<TOKEN>` und `<ORGID>` durch tatsächliche Werte.

