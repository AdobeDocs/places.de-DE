---
title: Vorhandene Zielpunkte verwalten
description: In der Benutzeroberfläche von Places Service können Sie vorhandene POIs bearbeiten, löschen oder filtern.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---

# Vorhandene Zielpunkte verwalten {#managing-existing-pois}

POIs und Bibliotheken werden mithilfe der Places-Benutzeroberfläche in der Places-Datenbank erstellt und verwaltet.

## POI bearbeiten

1. Melden Sie sich mit Ihrer Adobe ID an Orten an.
1. Melden Sie sich mit Ihrer Adobe ID beim Places-Dienst an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie bearbeiten möchten.
1. Klicken **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Details anzeigen]**.
1. Aktualisieren Sie die Informationen und klicken Sie auf **[!UICONTROL Speichern]**.

## Einen POI löschen

1. Melden Sie sich mit Ihrer Adobe ID an Orten an.
1. Melden Sie sich mit Ihrer Adobe ID beim Places-Dienst an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie löschen möchten.
1. Klicken **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Löschen]**.

## POIs nach Stadt, Bundesland, Land oder Metadaten filtern

![POI filtern](/help/assets/filter_poi.png)

1. Melden Sie sich mit Ihrer Adobe ID bei der Places Service-Benutzeroberfläche an.
1. Klicken Sie oben rechts auf das Filtersymbol.
1. Sie können POIs auf eine der folgenden Arten filtern:

   * Nach Bibliothek:

      a. Wählen Sie eine Bibliothek aus.

   * Nach Eigenschaft:

      a. Wählen Sie in der Dropdownliste Eigenschaft die Option **[!UICONTROL Land]**, **[!UICONTROL state]** oder **[!UICONTROL Ort]**.

      b. Geben Sie in der nächsten Zeile einen Wert ein.

      Sie können beispielsweise **[!UICONTROL state]** und Typ **[!UICONTROL Kalifornien]**.

   * Mit Metadaten:

      a. Geben Sie einen Schlüssel und einen Wert ein.

## Definieren eines Geofence-POI

Geofences sind ein POI-Typ und werden in der Datenbank anhand der folgenden Schlüssel definiert:

| Schlüssel | Beschreibung | Erforderlich? |
| :--- | :--- | :--- |
| ID | Jedem POI zugewiesene eindeutige Kennung | Ja |
| Name | Der Anzeigename des POI. | Ja |
| Bibliothek | Jedem POI muss eine Bibliothek für die Organisation zugewiesen werden. | Ja |
| Radius | Der Radius für Ihren POI in Metern. | Ja |
| Symbol | Hilfe bei Visualisierungen der POIs. | Ja (zugewiesene Standardeinstellung) |
| Farbe | Hilfe bei Visualisierungen der POIs. | Ja (zugewiesene Standardeinstellung) |
| Kategorie | Weisen Sie einen gemeinsamen Rahmen von Kategorien zu, die für alle Zielpunkte in allen Bibliotheken gelten. | Nein |
| Adresse | Straße. | Nein |
| Stadt | Stadt des POI. | Nein |
| Bundesland/Region | Bundesland oder Region des POI. | Nein |
| Country | Land des POI. | Nein |
| Breitengrad | Breitengrad der Koordinate für die Mitte des POI. | Ja |
| Längengrad | Längenkoordinate für die Mitte des POI. | Ja |
| Metadaten | Benutzerdefinierte Schlüssel-Wert-Paare, die POIs zugewiesen werden können. Diese Metadaten optimieren zukünftige Workflows, indem sie es Ihnen ermöglichen, POIs über Bibliotheken hinweg zu gruppieren, damit Sie Regeln und Filter in nachgelagerten Workflows verwenden können, z. B. eine Push-Benachrichtigung senden, wenn ein Benutzer einen POI mit dem Typ = Konkurrent eingibt. | Nein |
