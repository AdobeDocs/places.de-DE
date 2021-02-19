---
title: Bibliothek aktualisieren
description: Aktualisieren Sie eine Bibliothek mit der Places REST API.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 8%

---


# Aktualisieren einer Bibliothek {#update-a-library}

Eine PUT-Methode, mit der Sie eine Bibliothek aktualisieren können.

## Anfrage

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## Header

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Body

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## Beispielantwort

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, Befehl

Verwenden Sie den folgenden CURL-Befehl, um diese API zu testen:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Ersetzen Sie Variablen wie `<lIBRARYID>`, `<API KEY>`, `<TOKEN>` und `<ORGID>` durch tatsächliche Werte.

