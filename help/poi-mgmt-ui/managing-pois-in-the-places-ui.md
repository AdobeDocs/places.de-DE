---
title: POIs in der Benutzeroberfläche "Orte"verwalten
seo-title: POIs in der Benutzeroberfläche "Orte"verwalten
description: Verwenden Sie die Benutzeroberfläche "Orte", um Ihre POIs zu verwalten.
seo-description: Verwenden Sie die Benutzeroberfläche "Orte", um Ihre POIs zu verwalten.
translation-type: tm+mt
source-git-commit: fdfeb8c17820c4eb0eae249da39be4eebece22d3

---


# Verwalten vorhandener POIs in der Benutzeroberfläche "Orte"

POIs und Bibliotheken werden in der Datenbank "Orte"mithilfe der Benutzeroberfläche "Orte"erstellt und verwaltet.

## Definieren eines Geofence POI

Geofences sind ein Typ von POI und werden in der Datenbank anhand der folgenden Schlüssel definiert:

| Schlüssel | Beschreibung | Erforderlich? |
| :--- | :--- | :--- |
| ID | Jedem POI zugewiesene eindeutige Kennung | Ja |
| Name | Freundlicher Name des POI | Ja |
| Bibliothek | Jedem POI muss eine Bibliothek für die Einrichtung zugewiesen werden | Ja |
| Symbol | Unterstützung bei Visualisierungen der POIs | Ja (Standard zugewiesen) |
| Kanalfarbe | Unterstützung bei Visualisierungen der POIs | Ja (Standard zugewiesen) |
| Kategorie | Zuweisen eines gemeinsamen Rahmens von Kategorien, die in allen POIs in allen Bibliotheken verwendet werden | Nein |
| Adresse | Straße | Nein |
| Stadt | Ort POI | Nein |
| Bundesland/Region | Bundesland oder -region POI | Nein |
| Land | POI-Land | Nein |
| Breitengrad | Breitenkoordinate für die Mitte des POI | Ja |
| Längengrad | Längengradkoordinate für das Zentrum von POI | Ja |
| Metadaten | benutzerdefinierte Schlüssel- und Wertpaare, die POIs zugewiesen werden können. Diese Metadaten optimieren zukünftige Arbeitsabläufe, indem Sie POIs für jede Bibliothek gruppieren können, um Regeln und Filter in nachgelagerten Arbeitsabläufen zu verwenden, z. B. wenn jemand einen POI mit Typ = Konkurrent eingibt. | Nein |


## POI bearbeiten

1. Melden Sie sich mit Ihrer Adobe ID bei Orten an.
1. Melden Sie sich mit Ihrer Adobe ID beim Adobe Places Service an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie bearbeiten möchten.
1. Klicken Sie auf **[!UICONTROL ...]** und wählen Sie **[!UICONTROL View Details]**.
1. Aktualisieren Sie die Informationen und klicken Sie auf **[!UICONTROL Save]**.

## Einen POI löschen

1. Melden Sie sich mit Ihrer Adobe ID bei Orten an.
1. Melden Sie sich mit Ihrer Adobe ID beim Adobe Places Service an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Delete]**.

## Filtern von POIs nach Stadt, Bundesland, Land oder Metadaten

1. Melden Sie sich mit Ihrer Adobe ID beim Adobe Places Service an.
1. Klicken Sie oben rechts auf das Filtersymbol.
1. Sie können POIs auf eine der folgenden Arten filtern:

   * Nach Bibliothek:

      a. Wählen Sie eine Bibliothek aus.

   * Nach Eigenschaft:

      a. Wählen Sie in der Dropdownliste Eigenschaft die Option **[!UICONTROL Country]**, **[!UICONTROL State]** oder **[!UICONTROL City]**.

      b. Geben Sie in der nächsten Zeile einen Wert ein.

      Sie können beispielsweise auswählen **[!UICONTROL State]** und eingeben **[!UICONTROL California]**.

   * Mit Metadaten:

      a. Geben Sie einen Schlüssel und einen Wert ein.
