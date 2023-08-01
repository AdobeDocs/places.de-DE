---
title: Places-Ereignisreferenz
description: Eine Liste der Ereignisse, die von der Places-Erweiterung verarbeitet werden.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 29%

---

# Places-Ereignisreferenz {#places-event-reference}

Im Folgenden finden Sie eine Liste der Ereignisse, die von der Places-Erweiterung verarbeitet werden.

## GetCurrentPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| ORTE | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Ereignisbeschreibung**

Dieses Ereignis ist eine Anfrage zum Abrufen der POIs, an denen sich das Gerät derzeit befindet.

**Datennutzlast-Definition**

Nicht zutreffend

## GetNeestedPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| ORTE | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Ereignisbeschreibung**

Bei diesem Ereignis handelt es sich um eine Anfrage zum Abrufen der nahegelegenen POIs unter Berücksichtigung des aktuellen Gerätestandorts und der konfigurierten Places-Bibliotheken.

**Datennutzlast-Definition**

| Schlüssel | Werttyp | Erforderlich | Standardwert | Beschreibung |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | wahr | Nicht zutreffend | Enthält den Breitenwert für die Mitte der Suche nach nahe gelegenen Zielpunkten. |
| longitude | double | wahr | Nicht zutreffend | Enthält den Längenwert für die Mitte der Suche nach nahe gelegenen POIs. |
| radius | integer | false | Nicht zutreffend | Radius, in Metern, der für die Suche nach nahe gelegenen POIs verwendet wird. |
| count | integer | false | 10 | Maximale Anzahl an POIs, die in dem resultierenden Antwortereignis zurückgegeben werden. |

## ProcessRegionEvent

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| ORTE | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Ereignisbeschreibung**

Dieses Ereignis bewirkt, dass die Places-Erweiterung ein Geofence-Einstiegs- oder Ausstiegsereignis verarbeitet.

**Datennutzlast-Definition**

| Schlüssel | Werttyp | Erforderlich | Beschreibung |
| :--- | :--- | :--- | :--- |
| regionid | Zeichenfolge | wahr | ID der Region, die das Ereignis generiert. |
| regioneventtype | int | wahr | Typ des zu generierenden Regions-Ereignisses. 1 für die Einreise und 2 für die Ausfahrt. |

## Von der Places-Erweiterung gesendete Ereignisse

Diese Informationen werden derzeit bereitgestellt.
