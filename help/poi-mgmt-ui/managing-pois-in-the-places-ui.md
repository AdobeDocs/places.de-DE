---
title: Verwalten vorhandener POIs
description: In der Places Service-Benutzeroberfläche können Sie vorhandene POIs bearbeiten, löschen oder filtern.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
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

     a. Wählen Sie in der Dropdown-Liste „Eigenschaft **[!UICONTROL „Land]**, **[!UICONTROL Bundesland]** oder **[!UICONTROL Stadt]**.

     b. Geben Sie in der nächsten Zeile einen Wert ein.

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
