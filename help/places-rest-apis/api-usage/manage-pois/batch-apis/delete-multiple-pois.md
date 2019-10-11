---
title: Löschen mehrerer POIs
seo-title: Löschen mehrerer POIs
description: Verwenden Sie die Batch-APIs, um mehrere POIs zu löschen.
seo-description: Verwenden Sie die Batch-APIs, um mehrere POIs zu löschen.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---



# Löschen mehrerer POIs {#delete-multiple-pois}

Eine POST-Methode, mit der Sie mehrere POIs löschen können.

## Anfrage

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## Kopfzeilen

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Text

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Beispielantwort

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, Befehl

Verwenden Sie den folgenden CURL-Befehl, um diese API zu testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Ersetzen Sie `<API KEY>`, `<TOKEN>`, `<ORGID>`und `<PATHTOBATCHDELETEJSONFILE>` durch echte Werte.

## JSON-Beispieldatei

Im Folgenden finden Sie die JSON-Beispieldatei für die `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
