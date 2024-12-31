---
title: Erhalte den Rang einer Bibliothek
description: Erhalten Sie den Rang einer Bibliothek mithilfe der Places REST-API.
exl-id: c0abedd0-5ff4-4a01-9f8d-e3d17ea53a97
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 9%

---

# Erhalte den Rang einer Bibliothek {#get-library-rank}

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

## CURL-Befehl

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Ersetzen Sie Variablen wie `<API KEY>`, `<TOKEN>` und `<ORGID>` durch tatsächliche Werte.
