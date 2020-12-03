---
title: Verwenden von Metadaten mit POIs
description: Dieser Abschnitt enthält Informationen und Strategien zur Verwendung von Metadaten mit POIs.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Strategien zur Verwendung von Metadaten mit POIs {#using-metadata-pois}

Wenn Sie im Orte-Dienst einen neuen POI erstellen, sind nur Name, Radius, Breitengrad und Längengrad erforderlich. Weitere Informationen zum Erstellen eines POI finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Wenn Sie jedoch nur die Mindestangaben eingeben, verpassen Sie die Möglichkeit, einen zusätzlichen Wert zu erstellen.

POI-Metadaten können auf verschiedene Weise verwendet werden. Unter dem Gesichtspunkt der POI-Verwaltung kann das Hinzufügen von Metadatenwerten bei der Suche nach oder beim Filtern einer Liste von potenziell Tausenden von POIs helfen. Das Erstellen von Metadaten für Schlüsselattribute im Zusammenhang mit einem POI kann Werte in nachgelagerten Workflows erbringen. Eine Hotelkette, die POIs für jede Immobilie erstellt, kann z. B. Metadaten wie einen Pool oder eine Bar oder ein Fitnesscenter enthalten. Diese Metadaten können als Kontextdaten in Analytics eingeschlossen und auch für zielgerichtete Angebot oder Nachrichten verwendet werden.

## Platziert Dienstmetadaten beim Start

In Experience Platform Launch können Sie Datenelemente für jedes Metadatenfeld des Orts-Dienstes erstellen, das für Tracking- und Nachrichtenzwecke wichtig ist.

![Datenelement für die Fitnesseinrichtung](/help/assets/gymfacility.png)

Sie können dann eine Aktion mit der Analytics-Erweiterung erstellen, um einen neuen Treffer zu erstellen, der alle Metadaten enthält, die Sie als Kontextdaten verwenden möchten.

![Aktion für die Einrichtung des Fitnessstudios](/help/assets/Analytics-gym.png)

## In-App-Nachrichten im Adobe Campaign

Metadaten können als Filter für lokale Benachrichtigungen und In-App-Nachrichten verwendet werden, die in Adobe Campaign Standard definiert wurden. Die Verwendung von Metadaten als Filter bietet die Möglichkeit, eine relevantere Meldung zu erstellen, die kontextuell zum tatsächlichen Speicherort ist.

![Filtern lokaler Benachrichtigungen und In-App-Nachrichten in ACS](/help/assets/ACS_gym_metadata.png)