---
title: eine Bibliothek erstellen
description: Erstellen Sie eine Bibliothek mithilfe der Places REST API.
exl-id: 155cc6e6-9254-4389-bb02-e526d15908f4
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 18%

---

# eine Bibliothek erstellen {#create-a-library}

Eine POST -Methode, mit der Sie eine Bibliothek erstellen können.

## Anfrage

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Kopfzeilen

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Textkörper

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
>Ersetzen Sie Variablen wie `<API KEY>`, `<TOKEN>` und `<ORGID>` durch tatsächliche Werte.
