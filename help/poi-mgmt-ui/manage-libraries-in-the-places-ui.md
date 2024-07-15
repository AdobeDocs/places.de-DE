---
title: Verwalten von Bibliotheken in der Benutzeroberfläche des Places Service
description: Verwalten Sie Ihre Bibliotheken mithilfe der Benutzeroberfläche von Places Service .
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 14%

---

# Bibliotheken verwalten {#manage-libraries-places-ui}

Eine Bibliothek ist eine Sammlung von Zielpunkten. Sie können bis zu 150.000 POIs in einer Bibliothek haben und es können bis zu 100 Bibliotheken pro Experience Cloud-Organisation geben.

Es gibt verschiedene Möglichkeiten, Ihre POIs in Bibliotheken zu organisieren, je nachdem, was für Ihr Unternehmen am nützlichsten ist. Einige Kunden bevorzugen möglicherweise die Erstellung einer separaten Bibliothek für jede mobile App, während andere Kunden Bibliotheken verwenden könnten, um bestimmte Arten von Zielpunkten wie Cafés, Parks, Hotels usw. zu gruppieren. Ein großes Entertainment-Unternehmen könnte beispielsweise über eine Bibliothek verfügen, die seine Außenstandorte in einer Bibliothek und ihre Einzelhandelsgeschäfte in einer anderen Bibliothek umfasst. Eine Stadtverwaltung könnte über eine Bibliothek verfügen, die alle Gebäude der Stadt umfasst, und eine andere Bibliothek, die alle Parks der Stadt umfasst.

Bibliotheken werden durch Folgendes definiert:

| Schlüssel: | Beschreibung: |
| :--- | :--- |
| ID | eine eindeutige Kennung, die der Bibliothek bei der Erstellung zugewiesen wird |
| Name | einen Anzeigenamen, der einer Bibliothek gegeben wird |
| Rang | Diese Ranglisten können ignoriert werden, wenn Ihre Organisation keine überlappenden Geofences enthält. Wenn es sich überschneidende POIs gibt, empfehlen wir, dass Sie jeden Geofence in separate Bibliotheken platzieren, damit sie in Relation zueinander gewichtet werden können. Ein Benutzer kann sich immer nur in einem Geofence befinden. <br><br>Der höchste Rang der Geofences, in denen sich ein Benutzer befindet, bestimmt die aktuelle Geofence-Mitgliedschaft. Wenn es Geofences mit demselben Bibliotheksrang gibt, ist der kleinste Geofence der aktuelle Geofence des Benutzers. <br><br>Das SDK erkennt auch die POIs *Letzte Eingaben* und *Letzte Ausstiege*, sodass Sie vollständig steuern können, wie Ihre Regeln basierend auf der Benutzerinteraktion mit Ihren POIs ausgelöst werden sollen. |

## eine Bibliothek erstellen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]** > **[!UICONTROL Bibliotheken verwalten]**.
1. Klicken Sie auf **[!UICONTROL Neu]**.
1. Geben Sie den Namen ein.
1. Klicken Sie auf **[!UICONTROL Bestätigen]**.

## Ändern des Rangs einer Bibliothek in der Places-Benutzeroberfläche

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]** > **[!UICONTROL Bibliotheken verwalten]**.
1. Klicken Sie auf das Symbol links neben dem Bibliotheksnamen und ziehen Sie die Bibliothek in den neuen Rang.

## Bibliothek umbenennen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]** > **[!UICONTROL Bibliotheken verwalten]**.
1. Suchen Sie die Bibliothek, die Sie löschen möchten.
1. Klicken Sie auf &quot;**[!UICONTROL ..]**&quot;und wählen Sie &quot;**[!UICONTROL Umbenennen]**&quot;.
1. Aktualisieren Sie den Namen und klicken Sie auf **[!UICONTROL Speichern]**.

## Bibliothek löschen

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Klicken Sie oben rechts auf **[!UICONTROL ...]** > **[!UICONTROL Bibliotheken verwalten]**.
1. Suchen Sie die Bibliothek, die Sie löschen möchten.
1. Klicken Sie auf &quot;**[!UICONTROL ..]**&quot;und wählen Sie &quot;**[!UICONTROL Löschen]**&quot;.
