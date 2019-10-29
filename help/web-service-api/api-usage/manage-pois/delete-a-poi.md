---
title: Einen POI löschen
seo-title: Einen POI löschen
description: Löschen Sie einen POI mithilfe der Places REST APIs.
seo-description: Löschen Sie einen POI mithilfe der Places REST APIs.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Einen POI löschen

Eine DELETE-Methode, mit der Sie einen POI löschen können.

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

## CURL, Befehl

Verwenden Sie den folgenden CURL-Befehl, um die API zu testen:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Ersetzen `<POIID>`, `<API KEY>`, `<TOKEN>`und `<ORGID>` durch tatsächliche Werte.
