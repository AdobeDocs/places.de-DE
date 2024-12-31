---
title: Verwalten von Bibliotheken in der Places Service-Benutzeroberfläche
description: Verwalten Sie Ihre Bibliotheken mithilfe der Places-Service-Benutzeroberfläche.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 14%

---

# Bibliotheken verwalten {#manage-libraries-places-ui}

Eine Bibliothek ist eine Sammlung von POIs. Sie können bis zu 150.000 POIs in einer Bibliothek haben, und es können bis zu 100 Bibliotheken pro Experience Cloud-Organisation sein.

Es gibt verschiedene Möglichkeiten, Ihre POIs in Bibliotheken zu organisieren, je nachdem, was für Ihr Unternehmen am nützlichsten ist. Einige Kunden möchten möglicherweise für jede Mobile App eine separate Bibliothek erstellen, während andere Kunden möglicherweise Bibliotheken verwenden, um bestimmte Arten von POIs wie Cafés, Parks, Hotels usw. zu gruppieren. So könnte beispielsweise ein großes Unterhaltungsunternehmen über eine Bibliothek verfügen, die seine Außenanlagen in einer Bibliothek und seine Einzelhandelsgeschäfte in einer anderen Bibliothek umfasst. Eine Stadtverwaltung könnte eine Bibliothek haben, die alle Gebäude der Stadt umfasst, und eine andere Bibliothek, die alle Parks der Stadt umfasst.

Bibliotheken werden wie folgt definiert:

| Schlüssel: | Beschreibung: |
| :--- | :--- |
| ID | Eine eindeutige Kennung, die der Bibliothek bei der Erstellung zugewiesen wurde |
| Name | Ein benutzerfreundlicher Name, der einer Bibliothek zugewiesen wird |
| Rang | Diese Rankings können ignoriert werden, wenn es in Ihrer Organisation keine überlappenden Geofences gibt. Wenn es sich überschneidende POIs gibt, empfehlen wir, dass Sie jeden Geofence in separate Bibliotheken platzieren, damit sie in Relation zueinander gewichtet werden können. Ein Benutzer kann sich immer nur in einem Geofence befinden. <br><br>Der höchste Rang der Geofences, in denen sich ein Benutzer befindet, bestimmt die aktuelle Geofence-Mitgliedschaft. Wenn es Geofences gibt, die denselben Bibliotheks-Rang haben, ist der kleinste Geofence der aktuelle Geofence des Benutzers. <br><br>Die SDK kennt auch die POIs *Zuletzt eingegeben* und *Zuletzt beendet*, sodass Sie die vollständige Kontrolle darüber haben, wie Ihre Regeln basierend auf der Benutzerinteraktion mit Ihren POIs ausgelöst werden sollen. |

## eine Bibliothek erstellen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL …]** > &quot;**[!UICONTROL verwalten]**.
1. Klicken Sie auf **[!UICONTROL Neu]**.
1. Geben Sie den Namen ein.
1. Klicken Sie auf **[!UICONTROL Bestätigen]**.

## Ändern des Rankings einer Bibliothek in der Places-Benutzeroberfläche

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL …]** > &quot;**[!UICONTROL verwalten]**.
1. Klicken Sie auf das Symbol links neben dem Bibliotheksnamen und ziehen Sie die Bibliothek auf den neuen Rang.

## Umbenennen einer Bibliothek

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL …]** > &quot;**[!UICONTROL verwalten]**.
1. Suchen Sie die Bibliothek, die Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL …]** und wählen Sie **[!UICONTROL Umbenennen]** aus.
1. Aktualisieren Sie den Namen und klicken Sie auf **[!UICONTROL Speichern]**.

## Löschen einer Bibliothek

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL …]** > &quot;**[!UICONTROL verwalten]**.
1. Suchen Sie die Bibliothek, die Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL …]** und wählen Sie **[!UICONTROL Löschen]**.
