---
title: Platzierungs-Ereignis
description: 'Eine Liste der Ereignis, die von der Places-Erweiterung verarbeitet werden. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 25%

---


# Platzierungs-Ereignis {#places-event-reference}

Im Folgenden finden Sie eine Liste der Ereignis, die mit der Places-Erweiterung behandelt werden.

## GetCurrentPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| PLÄTZE | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Ereignisbeschreibung**

Dieses Ereignis ist eine Anforderung zum Abrufen der POIs, in denen sich das Gerät derzeit befindet.

**Datennutzlast-Definition**

n/a

## GetNeestedPointsOfInterest

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| PLÄTZE | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Ereignisbeschreibung**

Dieses Ereignis stellt eine Anforderung dar, die nahe gelegenen POIs unter Berücksichtigung der aktuellen Geräteposition und der konfigurierten Orte-Bibliotheken abzurufen.

**Datennutzlast-Definition**

| Schlüssel | Werttyp | Erforderlich | Standardwert | Beschreibung |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | true | n/a | Enthält den Breitenwert für die Mitte der Suche nach nahe gelegenen POIs. |
| longitude | double | true | n/a | Gibt den Längengradwert für die Mitte der Suche nach nahe gelegenen POIs an. |
| radius | Ganzzahl | false | n/a | Radius, in Metern, verwendet durch die Suche nach nahe gelegenen POIs. |
| count | Ganzzahl | false | 10 | Maximale Anzahl der POIs, die in einem resultierenden Ereignis zurückgegeben werden. |

## ProcessRegionEvent

**Ereignisdetails**

| Typ | Quelle | Name | Gekoppelt |
| :--- | :--- | :--- | :--- |
| PLÄTZE | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Ereignisbeschreibung**

Dieses Ereignis führt dazu, dass die Platzierungserweiterung ein Ereignis zum Abrufen oder Beenden von Geometrien verarbeitet.

**Datennutzlast-Definition**

| Schlüssel | Werttyp | Erforderlich | Beschreibung |
| :--- | :--- | :--- | :--- |
| regionid | Zeichenfolge | wahr | ID des Bereichs, der das Ereignis generiert. |
| regionereigntype | int | wahr | Typ des zu generierenden Regions-Ereignisses. 1 für die Einfahrt und 2 für die Ausfahrt. |

## Ereignis, die von der Places-Erweiterung gesendet werden

Diese Informationen werden derzeit bereitgestellt.

