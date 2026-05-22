---
title: Verwalten von Bibliotheken in der Places Service-Benutzeroberfläche
description: Verwalten Sie Ihre Bibliotheken mithilfe der Places-Service-Benutzeroberfläche.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 14%

---

# Bibliotheken verwalten {#manage-libraries-places-ui}

Eine Bibliothek ist eine Sammlung von POIs. Eine Bibliothek kann bis zu 150.000 POIs enthalten, und pro Experience Cloud-Organisation können bis zu 100 Bibliotheken vorhanden sein.

Es gibt verschiedene Möglichkeiten, Ihre POIs in Bibliotheken zu organisieren, je nachdem, was für Ihr Unternehmen am nützlichsten ist. Einige Kunden möchten möglicherweise für jede Mobile App eine separate Bibliothek erstellen, während andere Kunden möglicherweise Bibliotheken verwenden, um bestimmte Arten von POIs wie Cafés, Parks, Hotels usw. zu gruppieren. So könnte beispielsweise ein großes Unterhaltungsunternehmen über eine Bibliothek verfügen, die seine Außenanlagen in einer Bibliothek und seine Einzelhandelsgeschäfte in einer anderen Bibliothek umfasst. Eine Stadtverwaltung könnte eine Bibliothek haben, die alle Gebäude der Stadt umfasst, und eine andere Bibliothek, die alle Parks der Stadt umfasst.

Bibliotheken werden wie folgt definiert:

| Schlüssel: | Beschreibung: |
| :--- | :--- |
| ID | Eine eindeutige Kennung, die der Bibliothek bei der Erstellung zugewiesen wurde |
| Name | Ein benutzerfreundlicher Name, der einer Bibliothek zugewiesen wird |
| Rang | Diese Rankings können ignoriert werden, wenn es in Ihrer Organisation keine überlappenden Geofences gibt. Wenn es sich überschneidende POIs gibt, empfehlen wir, dass Sie jeden Geofence in separate Bibliotheken platzieren, damit sie in Relation zueinander gewichtet werden können. Ein Benutzer kann sich immer nur in einem Geofence befinden. <br><br>Der höchste Rang der Geofences, in denen sich ein Benutzer befindet, bestimmt die aktuelle Geofence-Zugehörigkeit. Wenn es Geofences gibt, die denselben Bibliotheks-Rang haben, ist der kleinste Geofence der aktuelle Geofence des Benutzers. <br><br>Die SDK kennt auch die POIs *Zuletzt eingegeben* und *Zuletzt beendet*, sodass Sie die vollständige Kontrolle darüber haben, wie Ihre Regeln basierend auf der Benutzerinteraktion mit Ihren POIs ausgelöst werden sollen. |

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
