---
title: Verwalten vorhandener POIs
description: In der Benutzeroberfläche des Location Service können Sie vorhandene POIs bearbeiten, löschen oder filtern.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Verwalten vorhandener POIs {#managing-existing-pois}

POIs und Bibliotheken werden in der Datenbank &quot;Orte&quot;mithilfe der Benutzeroberfläche &quot;Orte&quot;erstellt und verwaltet.

## POI bearbeiten

1. Melden Sie sich mit Ihrer Adobe ID bei Orten an.
1. Melden Sie sich mit Ihrer Adobe ID beim Orts-Dienst an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie bearbeiten möchten.
1. Klicken Sie auf **[!UICONTROL ...]**und wählen Sie**[!UICONTROL View Details]**.
1. Aktualisieren Sie die Informationen und klicken Sie auf **[!UICONTROL Save]**.

## Einen POI löschen

1. Melden Sie sich mit Ihrer Adobe ID bei Orten an.
1. Melden Sie sich mit Ihrer Adobe ID beim Orts-Dienst an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL ...]**und wählen Sie**[!UICONTROL Delete]**.

## Filtern von POIs nach Stadt, Bundesland, Land oder Metadaten

![POI filtern](/help/assets/filter_poi.png)

1. Melden Sie sich mit Ihrer Adobe ID bei der Benutzeroberfläche des Location Service an.
1. Klicken Sie oben rechts auf das Filtersymbol.
1. Sie können POIs auf eine der folgenden Arten filtern:

   * Nach Bibliothek:

      a. Wählen Sie eine Bibliothek aus.

   * Nach Eigenschaft:

      a. Wählen Sie in der Dropdownliste Eigenschaft die Option **[!UICONTROL Country]**,**[!UICONTROL State]** oder **[!UICONTROL City]**.

      b. Geben Sie in der nächsten Zeile einen Wert ein.

      Sie können beispielsweise auswählen **[!UICONTROL State]**und eingeben**[!UICONTROL California]**.

   * Mit Metadaten:

      a. Geben Sie einen Schlüssel und einen Wert ein.

## Definieren eines Geofence POI

Geofences sind ein Typ von POI und werden in der Datenbank anhand der folgenden Schlüssel definiert:

| Schlüssel | Beschreibung | Erforderlich? |
| :--- | :--- | :--- |
| ID | Jedem POI zugewiesene eindeutige Kennung | Ja |
| Name | Freundlicher Name des POI. | Ja |
| Bibliothek | Jeder POI muss eine Bibliothek für die Organisation zugewiesen werden. | Ja |
| Symbol | Hilfe bei Visualisierungen der POIs. | Ja (Standard zugewiesen) |
| Kanalfarbe | Hilfe bei Visualisierungen der POIs. | Ja (Standard zugewiesen) |
| Kategorie | Weisen Sie einen gemeinsamen Rahmen von Kategorien zu, die in allen POIs in allen Bibliotheken verwendet werden. | Nein |
| Adresse | Straße. | Nein |
| Stadt | Stadt der Einrichtung. | Nein |
| Bundesland/Region | Bundesland oder -region des POI. | Nein |
| Land | Land der Einrichtung. | Nein |
| Breitengrad | Breitengrad für die Mitte des POI. | Ja |
| Längengrad | Längengradkoordinate für die Mitte des POI. | Ja |
| Metadaten | Benutzerdefinierte Schlüssel- und Wertpaare, die POIs zugewiesen werden können. Diese Metadaten optimieren zukünftige Arbeitsabläufe, indem Sie POIs für jede Bibliothek gruppieren können, um Regeln und Filter in nachgelagerten Arbeitsabläufen zu verwenden, z. B. eine Push-Benachrichtigung zu senden, wenn jemand einen POI mit dem Typ = Konkurrent eingibt. | Nein |
