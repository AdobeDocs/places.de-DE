---
title: Places-Ereignisreferenz
description: Eine Liste der Ereignisse, die von der Places-Erweiterung verarbeitet werden.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%

---

# Places-Ereignisreferenz {#places-event-reference}

Im Folgenden finden Sie eine Liste der Ereignisse, die von der Places-Erweiterung verarbeitet werden.

## GetCurrentPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gepaart |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Ereignisbeschreibung**

Dieses Ereignis ist eine Anfrage zum Abrufen der POIs, in denen sich das Gerät derzeit befindet.

**Daten-Payload-Definition**

n. z.

## GetNearPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gepaart |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Ereignisbeschreibung**

Dieses Ereignis ist eine Anfrage zum Abrufen der nahegelegenen POIs unter Berücksichtigung des aktuellen Gerätestandorts und der konfigurierten Places-Bibliotheken.

**Daten-Payload-Definition**

| Schlüssel | Werttyp | Erforderlich | Standardwert | Beschreibung |
| :--- | :--- | :--- | :--- | :--- |
| Breitengrad | double | wahr | n. z. | Enthält den Breitengrad für die Mitte der Suche nach nahegelegenen POIs. |
| Längengrad | double | wahr | n. z. | Enthält den Längengrad für die Mitte der Suche nach nahegelegenen POIs. |
| Radius | integer | false | n. z. | Radius (in Metern), der von der Suche nach nahegelegenen POIs verwendet wird. |
| count | integer | false | 10 | Maximale Anzahl an POIs, die im resultierenden Antwortereignis zurückgegeben werden sollen. |

## ProcessRegionEvent

**Ereignisdetails**

| Typ | Quelle | Name | Gepaart |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Ereignisbeschreibung**

Dieses Ereignis veranlasst die Places -Erweiterung, ein Geofence-Eintritts- oder -Austrittsereignis zu verarbeiten.

**Daten-Payload-Definition**

| Schlüssel | Werttyp | Erforderlich | Beschreibung |
| :--- | :--- | :--- | :--- |
| regionId | Zeichenfolge | wahr | ID der Region, die das Ereignis generiert. |
| regionEventType | int | wahr | Typ des zu erzeugenden Regionsereignisses. 1 für die Einfahrt und 2 für die Ausfahrt. |

## Von der Places-Erweiterung gesendete Ereignisse

Diese Informationen sind derzeit in Bearbeitung.
