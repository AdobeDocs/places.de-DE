---
title: Ereignisreferenz für Orte
description: 'Eine Liste der Ereignisse, die von der Places-Erweiterung verarbeitet werden. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Ereignisreferenz für Orte {#places-event-reference}

Im Folgenden finden Sie eine Liste der Ereignisse, die von der Places-Erweiterung behandelt werden.

## GetCurrentPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| PLÄTZE | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Ereignisbeschreibung**

Dieses Ereignis ist eine Anforderung zum Abrufen der POIs, in denen sich das Gerät derzeit befindet.

**Datennutzlast-Definition**

Keine

## GetNeestedPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| PLÄTZE | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Ereignisbeschreibung**

Bei diesem Ereignis werden die nahe gelegenen POIs unter Berücksichtigung des aktuellen Geräteorts und der konfigurierten Orte-Bibliotheken abgerufen.

**Datennutzlast-Definition**

| Schlüssel | Werttyp | Erforderlich | Standardwert | Beschreibung |
| :--- | :--- | :--- | :--- | :--- |
| Breitengrad | double | wahr | Keine | Enthält den Breitenwert für die Mitte der Suche nach nahe gelegenen POIs. |
| Längengrad | double | wahr | Keine | Gibt den Längengradwert für die Mitte der Suche nach nahe gelegenen POIs an. |
| radius | integer | false | Keine | Radius, in Metern, verwendet durch die Suche nach nahe gelegenen POIs. |
| count | integer | false | 10 | Maximale Anzahl an POIs, die in einem resultierenden Antwortereignis zurückgegeben werden. |

## ProcessRegionEvent

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| PLÄTZE | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Ereignisbeschreibung**

Dieses Ereignis bewirkt, dass die Places-Erweiterung ein Ereignis zum Abrufen oder Beenden von Geofencing verarbeitet.

**Datennutzlast-Definition**

| Schlüssel | Werttyp | Erforderlich | Beschreibung |
| :--- | :--- | :--- | :--- |
| regionid | string | wahr | ID der Region, die das Ereignis generiert. |
| regionereigntype | int | wahr | Typ des zu generierenden Regions-Ereignisses. 1 für Einfahrt und 2 für Ausfahrt. |

## Ereignisse, die von der Places-Erweiterung ausgelöst werden

Diese Informationen werden derzeit bereitgestellt.

