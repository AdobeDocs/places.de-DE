---
title: Rang in Ihren Bibliotheken festlegen
description: Legen Sie mithilfe der Places REST-API einen Rang in Ihren Bibliotheken fest.
exl-id: c922bddc-1587-4da8-acb4-c2d69ce11808
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 7%

---

# Rang in Ihren Bibliotheken festlegen {#set-rank-on-libraries}

Eine PUT-Methode, mit der Sie eine Rangfolge für alle Bibliotheken festlegen können.

## Anfrage

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## Kopfzeilen

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## PUT-Daten

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
>Ersetzen Sie Variablen wie `<API KEY>`, `<TOKEN>` und `<ORGID>` durch tatsächliche Werte.
