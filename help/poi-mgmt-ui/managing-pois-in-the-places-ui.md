---
title: Verwalten vorhandener POIs
description: In der Places Service-Benutzeroberfläche können Sie vorhandene POIs bearbeiten, löschen oder filtern.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 408
ht-degree: 6%

---

# Verwalten vorhandener POIs {#managing-existing-pois}

POIs und Bibliotheken werden in der Places-Datenbank mithilfe der Places-Benutzeroberfläche erstellt und verwaltet.

## POI bearbeiten

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Melden Sie sich mit Ihrer Adobe ID beim Places Service an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Aufzählungsliste aussieht.
1. Suchen Sie den POI, den Sie bearbeiten möchten.
1. Klicken Sie auf **[!UICONTROL …]** und wählen Sie **[!UICONTROL Details anzeigen]**.
1. Aktualisieren Sie die Informationen und klicken Sie auf **[!UICONTROL Speichern]**.

## Löschen eines POI

1. Melden Sie sich mit Ihrer Adobe ID bei Places an.
1. Melden Sie sich mit Ihrer Adobe ID beim Places Service an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Aufzählungsliste aussieht.
1. Suchen Sie den POI, den Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL …]** und wählen Sie **[!UICONTROL Löschen]**.

## POIs nach Stadt, Bundesland, Land oder Metadaten filtern

![Filtern eines POI](/help/assets/filter_poi.png)

1. Melden Sie sich mit Ihrer Adobe ID bei der Places Service-Benutzeroberfläche an.
1. Klicken Sie oben rechts auf das Filtersymbol.
1. Sie können POIs auf eine der folgenden Arten filtern:

   * Nach Bibliothek:

     a. Bibliothek auswählen.

   * Nach Eigenschaft:

     a. Wählen Sie in der Dropdown-Liste „Eigenschaft **[!UICONTROL „Land]**, **[!UICONTROL Bundesland]** oder **[!UICONTROL Stadt]** aus.

     B. Geben Sie in der nächsten Zeile einen Wert ein.

     Sie können beispielsweise „Bundesland **[!UICONTROL auswählen]** &quot;**[!UICONTROL &quot;]**.

   * Mit Metadaten:

     a. Geben Sie einen Schlüssel und einen Wert ein.

## Definieren eines Geofence-POI

Geofences sind ein POI-Typ und werden in der Datenbank anhand der folgenden Schlüssel definiert:

| Schlüssel | Beschreibung | Erforderlich? |
| :--- | :--- | :--- |
| ID | Jedem POI zugewiesene eindeutige Kennung | Ja |
| Name | Der POI erhält einen Anzeigenamen. | Ja |
| Bibliothek | Jedem POI muss eine Bibliothek für die Organisation zugewiesen werden. | Ja |
| Radius | Der Radius für Ihren POI in Metern. | Ja |
| Symbol | Unterstützung bei Visualisierungen der POIs. | Ja (Standardeinstellung zugewiesen) |
| Farbe | Unterstützung bei Visualisierungen der POIs. | Ja (Standardeinstellung zugewiesen) |
| Kategorie | Weisen Sie ein gemeinsames Framework mit Kategorien zu, die für alle POIs in allen Bibliotheken gleich sind. | Nein |
| Adresse | Straße. | Nein |
| Stadt | Stadt des POI. | Nein |
| Land/Region | Bundesland oder Region des POI. | Nein |
| Land | Land des POI. | Nein |
| Breitengrad | Breitenkoordinate für die Mitte des POI. | Ja |
| Längengrad | Längenkoordinate für die Mitte des POI. | Ja |
| Metadaten | Benutzerdefinierte Schlüssel- und Wertpaare, die POIs zugewiesen werden können. Diese Metadaten optimieren zukünftige Workflows, indem Sie POIs bibliotheksübergreifend gruppieren können, um in nachgelagerten Workflows Regeln und Filter zu verwenden. So können Sie beispielsweise eine Push-Benachrichtigung senden, wenn jemand einen POI mit dem Typ Konkurrent betritt. | Nein |
