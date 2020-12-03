---
title: Rang auf Ihre Bibliotheken festlegen
description: Legen Sie mithilfe der Places REST API einen Rang in Ihren Bibliotheken fest.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 5%

---


# Rang auf Ihre Bibliotheken festlegen {#set-rank-on-libraries}

Eine PUT-Methode, mit der Sie eine Rangreihenfolge für alle Bibliotheken festlegen können.

## Anfrage

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## Kopfzeilen

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## PUT von Daten

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## Beispielantwort

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## CURL, Befehl

```
curl -X PUT `'https://api-places.adobe.io/places/placesapi/v1/libraries/rank'` -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Ersetzen Sie Variablen wie `<API KEY>`, `<TOKEN>`und `<ORGID>` durch tatsächliche Werte.

