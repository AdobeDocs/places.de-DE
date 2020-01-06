---
title: Bibliotheken in der Benutzeroberfläche "Orte"verwalten
description: Verwalten Sie Ihre Bibliotheken mithilfe der Benutzeroberfläche "Orte".
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Manage libraries {#manage-libraries-places-ui}

Eine Bibliothek ist eine Sammlung von POIs. In einer Bibliothek können bis zu 150.000 POI gespeichert werden. Pro Experience Cloud-Organisation können bis zu 100 Bibliotheken vorhanden sein.

Es gibt verschiedene Möglichkeiten, POIs in Bibliotheken zu organisieren, je nachdem, was für Ihr Unternehmen am nützlichsten ist. Einige Kunden möchten möglicherweise eine separate Bibliothek für jede mobile App erstellen, andere Kunden verwenden Bibliotheken, um bestimmte Arten von POIs wie Cafés, Parks, Hotels usw. zu gruppieren. So könnte eine große Unterhaltungsfirma über eine Bibliothek verfügen, die ihre Außen-Veranstaltungsorte in einer Bibliothek und ihre Einzelhandelsgeschäfte in einer anderen Bibliothek umfasst. Eine Stadtregierung könnte eine Bibliothek haben, die alle Gebäude der Stadt umfasst, und eine andere Bibliothek, die alle Parks der Stadt umfasst.

Bibliotheken werden wie folgt definiert:

| Schlüssel: | Beschreibung: |
| :--- | :--- |
| ID | eine eindeutige ID, die der Bibliothek bei der Erstellung zugewiesen wird |
| Name | einem benutzerfreundlichen Namen, der einer Bibliothek gegeben wird |
| Rang | Diese Ranglisten können ignoriert werden, wenn sich die Geodäten in Ihrem Unternehmen nicht überschneiden. Wenn es sich überschneidende POIs gibt, empfehlen wir, dass Sie jeden Geofence in separate Bibliotheken platzieren, damit sie in Relation zueinander gewichtet werden können. Ein Benutzer kann sich immer nur in einem Geofence befinden. <br><br>Der höchste Rang der Geofences, in denen sich ein Benutzer befindet, bestimmt die aktuelle Geofence-Mitgliedschaft. Wenn Geofences mit dem gleichen Bibliotheksrang vorhanden sind, wird der kleinste aktuelle Geofence des Benutzers verwendet. <br><br>Das SDK erkennt auch die *zuletzt betretenen* und *zuletzt verlassenen* POIs. So haben Sie vollständige Kontrolle darüber, wie Ihre Regeln basierend auf Interaktionen mit Ihren POIs ausgelöst werden sollen. |

## Erstellen einer Bibliothek

1. Melden Sie sich mit Ihrer Adobe ID bei Orten an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Klicken Sie auf **[!UICONTROL New]**.
1. Geben Sie den Namen ein.
1. Klicken Sie auf **[!UICONTROL Confirm]**.

## Ändern des Rangs einer Bibliothek in der Benutzeroberfläche &quot;Orte&quot;

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Klicken Sie auf das Symbol links neben dem Bibliotheksnamen und ziehen Sie die Bibliothek in den neuen Rang.

## Bibliothek umbenennen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Suchen Sie die Bibliothek, die Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL ...]**und wählen Sie**[!UICONTROL Rename]**.
1. Aktualisieren Sie den Namen und klicken Sie auf **[!UICONTROL Save]**.

## Bibliothek löschen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Suchen Sie die Bibliothek, die Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL ...]**und wählen Sie**[!UICONTROL Delete]**.

