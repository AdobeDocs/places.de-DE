---
title: Bibliothek löschen
seo-title: Bibliothek löschen
description: Löschen Sie eine Bibliothek mithilfe der REST-APIs für Orte.
seo-description: Löschen Sie eine Bibliothek mithilfe der REST-APIs für Orte.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Bibliothek löschen

Eine DELETE-Methode, mit der Sie eine Bibliothek löschen können.

## Anfrage

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

Verwenden Sie den folgenden CURL-Befehl, um diese API zu testen:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Variablen wie `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`und `<ORGID>`durch tatsächliche Werte ersetzen

