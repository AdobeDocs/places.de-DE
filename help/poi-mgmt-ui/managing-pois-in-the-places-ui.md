---
title: Verwalten vorhandener POIs
description: In der Benutzeroberfläche des Orts-Dienstes können Sie vorhandene POIs bearbeiten, löschen oder filtern.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---


# Verwalten vorhandener POIs {#managing-existing-pois}

POIs und Bibliotheken werden in der Datenbank &quot;Orte&quot;mithilfe der Benutzeroberfläche &quot;Orte&quot;erstellt und verwaltet.

## POI bearbeiten

1. Melden Sie sich mit Ihrem Adobe ID an Orten an.
1. Melden Sie sich mit Ihrem Adobe ID beim Places Service an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie bearbeiten möchten.
1. Klicken Sie auf **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Ansicht Details]**.
1. Aktualisieren Sie die Informationen und klicken Sie auf **[!UICONTROL Speichern]**.

## Einen POI löschen

1. Melden Sie sich mit Ihrem Adobe ID an Orten an.
1. Melden Sie sich mit Ihrem Adobe ID beim Places Service an.
1. Klicken Sie oben rechts auf das Symbol, das wie eine Liste mit Aufzählungszeichen aussieht.
1. Suchen Sie den POI, den Sie löschen möchten.
1. Klicken Sie auf **[!UICONTROL ...]** und wählen Sie **[!UICONTROL Löschen]**.

## Filtern von POIs nach Stadt, Bundesland, Land oder Metadaten

![POI filtern](/help/assets/filter_poi.png)

1. Melden Sie sich mit Ihrem Adobe ID bei der Benutzeroberfläche des Places-Dienstes an.
1. Klicken Sie oben rechts auf das Filtersymbol.
1. Sie können POIs auf eine der folgenden Arten filtern:

   * Nach Bibliothek:

      a. Wählen Sie eine Bibliothek aus.

   * Nach Eigenschaft:

      a. Wählen Sie in der Dropdown-Liste Eigenschaft die Optionen **[!UICONTROL Land]**, **[!UICONTROL Bundesland]** oder **[!UICONTROL Ort]**.

      b. Geben Sie in der nächsten Zeile einen Wert ein.

      Sie können beispielsweise **[!UICONTROL Bundesland]** auswählen und **[!UICONTROL Kalifornien]** eingeben.

   * Mit Metadaten:

      a. Geben Sie einen Schlüssel und einen Wert ein.

## Definieren eines Geofence POI

Geofences sind ein Typ von POI und werden in der Datenbank anhand der folgenden Schlüssel definiert:

| Schlüssel | Beschreibung | Erforderlich? |
| :--- | :--- | :--- |
| ID | Jedem POI zugewiesene eindeutige Kennung | Ja |
| Name | Freundlicher Name des POI. | Ja |
| Bibliothek | Jedem POI muss eine Bibliothek für die Organisation zugewiesen werden. | Ja |
| Radius | Der Radius für Ihren POI in Metern. | Ja |
| Symbol | Hilfe bei Visualisierungen der POIs. | Ja (Standard zugewiesen) |
| Farbe | Hilfe bei Visualisierungen der POIs. | Ja (Standard zugewiesen) |
| Kategorie | Weisen Sie einen gemeinsamen Rahmen von Kategorien zu, die in allen POIs in allen Bibliotheken verwendet werden. | Nein |
| Adresse | Straße. | Nein |
| Stadt | Stadt der Einrichtung. | Nein |
| Bundesland/-region | Bundesland oder -region des POI. | Nein |
| Country | Land der Einrichtung. | Nein |
| Breitengrad | Breitengrad für die Mitte des POI. | Ja |
| Längengrad | Längengradkoordinate für die Mitte des POI. | Ja |
| Metadaten | Benutzerdefinierte Schlüssel- und Wertpaare, die POIs zugewiesen werden können. Diese Metadaten optimieren zukünftige Workflows, indem Sie POIs über Bibliotheken hinweg gruppieren können, um Regeln und Filter in nachgeschalteten Workflows zu verwenden, wie z. B. eine Push-Benachrichtigung zu senden, wenn jemand einen POI mit dem Konkurrent &quot;Typ =&quot;eingibt. | Nein |
