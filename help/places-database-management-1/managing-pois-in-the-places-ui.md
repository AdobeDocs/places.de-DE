---
title: POIs in der Benutzeroberfläche "Orte"verwalten
seo-title: POIs in der Benutzeroberfläche "Orte"verwalten
description: Verwenden Sie die Benutzeroberfläche "Orte", um Ihre POIs zu verwalten.
seo-description: Verwenden Sie die Benutzeroberfläche "Orte", um Ihre POIs zu verwalten.
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# POIs in der Benutzeroberfläche "Orte"verwalten

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

## POI erstellen {#create-a-poi}

Ein POI (Point of Interest) ist ein Ort oder ein Punkt auf einer Karte, der für Sie von Interesse ist. Es kann Orte wie Cafés, Restaurants usw. umfassen.

1. Melden Sie sich mit Ihrer Adobe ID bei Adobe Places an.
2. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht, und klicken Sie dann auf **[!UICONTROL New]**.
3. Geben Sie einen Namen für Ihren POI ein.
4. Wählen Sie eine Bibliothek aus oder fügen Sie sie hinzu.
5. Geben Sie einen Radius ein oder wählen Sie ihn aus.

   a. Wählen Sie ein Symbol für Ihren POI.
b.b. Wählen Sie eine Farbe für das Symbol aus.

6. Erweitern Sie den **[!UICONTROL Location]** Abschnitt.

   a. Geben Sie eine Adresse ein.

   b. Geben Sie die Stadt ein.

   c. Geben Sie den Namen des Status ein.

   d. Geben Sie den Namen des Landes ein.

   e. Wählen Sie einen Breiten- oder Längengrad aus oder geben Sie ihn ein.

   f. Klicken Sie auf **[!UICONTROL Drop Pin on Map]**.

7. Erweitern Sie den **[!UICONTROL Metadata]** Abschnitt und klicken Sie auf **[!UICONTROL Add Metadata]**.

   a. Geben Sie den Schlüsselnamen ein.

   b. Geben Sie den Schlüsselwert ein.

8. Klicken Sie auf **[!UICONTROL Confirm]** und dann **[!UICONTROL  Save]**.

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

