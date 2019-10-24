---
title: Bibliotheken in der Benutzeroberfläche "Orte"verwalten
seo-title: Bibliotheken in der Benutzeroberfläche "Orte"verwalten
description: Verwalten Sie Ihre Bibliotheken mithilfe der Benutzeroberfläche "Orte".
seo-description: Verwalten Sie Ihre Bibliotheken mithilfe der Benutzeroberfläche "Orte".
translation-type: tm+mt
source-git-commit: fd1b37a0f50d93de1efff4cb38fc23253f02d517

---


# Bibliotheken in der Benutzeroberfläche "Orte"verwalten {#manage-libraries-places-ui}

Eine Bibliothek ist eine Sammlung von POIs. In einer Bibliothek können bis zu 150.000 POI gespeichert werden. Pro Experience Cloud-Organisation können bis zu 100 Bibliotheken vorhanden sein.

Es gibt verschiedene Möglichkeiten, POIs in Bibliotheken zu organisieren, je nachdem, was für Ihr Unternehmen am nützlichsten ist. Einige Kunden möchten möglicherweise eine separate Bibliothek für jede mobile App erstellen, andere Kunden verwenden Bibliotheken, um bestimmte Arten von POIs wie Cafés, Parks, Hotels usw. zu gruppieren. So könnte eine große Unterhaltungsfirma über eine Bibliothek verfügen, die ihre Außen-Veranstaltungsorte in einer Bibliothek und ihre Einzelhandelsgeschäfte in einer anderen Bibliothek umfasst. Eine Stadtregierung könnte eine Bibliothek haben, die alle Gebäude der Stadt umfasst, und eine andere Bibliothek, die alle Parks der Stadt umfasst.

Bibliotheken werden wie folgt definiert:

| Schlüssel: | Beschreibung: |
| :--- | :--- |
| ID | eine eindeutige ID, die der Bibliothek bei der Erstellung zugewiesen wird |
| Name | einem benutzerfreundlichen Namen, der einer Bibliothek gegeben wird |
| Rang | Diese Ranglisten können ignoriert werden, wenn sich die Geodäten in Ihrem Unternehmen nicht überschneiden. Wenn es überlappende POIs gibt, empfehlen wir, dass Sie jede der Geofences in separate Bibliotheken setzen, damit sie relativ zueinander gewichtet werden können. Ein Benutzer kann immer nur in einem Gefecht sein. <br><br>Die höchste Rangfolge der Geofencing-Werte, die ein Benutzer erhält, bestimmt seine aktuelle Geofence-Mitgliedschaft. Wenn es Geofences gibt, die die gleiche Bibliotheksreihenfolge haben, ist die kleinste Häufigkeit die aktuelle Stärke des Benutzers. <br><br>Dem SDK sind auch die *zuletzt eingegebenen* und die *letzten ausgehenden* POIs bekannt, sodass Sie vollständig steuern können, wie Ihre Regeln auf der Grundlage der Benutzerinteraktion mit Ihren POIs ausgelöst werden sollen. |

## Erstellen einer Bibliothek

1. Melden Sie sich mit Ihrer Adobe ID bei Orten an.
2. Klicken Sie oben rechts auf **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Klicken Sie auf **[!UICONTROL New]**.
4. Geben Sie den Namen ein.
5. Klicken Sie auf **[!UICONTROL Confirm]**.

## Ändern des Rangs einer Bibliothek in der Benutzeroberfläche "Orte"

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
2. Klicken Sie oben rechts auf **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Klicken Sie auf das Symbol links neben dem Bibliotheksnamen und ziehen Sie die Bibliothek in den neuen Rang.

## Bibliothek umbenennen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
2. Klicken Sie oben rechts auf **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Suchen Sie die Bibliothek, die Sie löschen möchten.
4. Klicken Sie auf **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Rename]**.
5. Aktualisieren Sie den Namen und klicken Sie auf **[!UICONTROL Save]**.

## Bibliothek löschen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
2. Klicken Sie oben rechts auf **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Suchen Sie die Bibliothek, die Sie löschen möchten.
4. Klicken Sie auf **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Delete]**.

