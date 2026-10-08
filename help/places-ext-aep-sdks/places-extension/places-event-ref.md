---
title: Places-Ereignisreferenz
description: Eine Liste der Ereignisse, die von der Places-Erweiterung verarbeitet werden.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
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

k. A.

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
| Breitengrad | double | wahr | k. A. | Enthält den Breitengrad für die Mitte der Suche nach nahegelegenen POIs. |
| Längengrad | double | wahr | k. A. | Enthält den Längengrad für die Mitte der Suche nach nahegelegenen POIs. |
| Radius | integer | false | k. A. | Radius (in Metern), der von der Suche nach nahegelegenen POIs verwendet wird. |
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
| regionId | string | wahr | ID der Region, die das Ereignis generiert. |
| regionEventType | int | wahr | Typ des zu erzeugenden Regionsereignisses. 1 für die Einfahrt und 2 für die Ausfahrt. |

## Von der Places-Erweiterung gesendete Ereignisse

Diese Informationen sind derzeit in Bearbeitung.
