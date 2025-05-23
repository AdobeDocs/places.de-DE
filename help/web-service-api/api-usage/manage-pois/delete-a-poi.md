---
title: Löschen eines POI
description: Löschen eines POI mithilfe der Places REST-APIs.
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 4%

---

# Löschen eines POI {#delete-a-poi}

Eine DELETE-Methode zum Löschen eines POI.

## Anfrage

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Kopfzeilen

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Beispielantwort

```text
If successful a Status of "204 No Content" is returned.
```

## CURL-Befehl

Verwenden Sie den folgenden CURL-Befehl, um die API zu testen:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Ersetzen Sie `<POIID>`, `<API KEY>`, `<TOKEN>` und `<ORGID>` durch tatsächliche Werte.
