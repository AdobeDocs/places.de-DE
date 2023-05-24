---
title: Verwenden von Metadaten mit POIs
description: Dieser Abschnitt enthält Informationen und Strategien zur Verwendung von Metadaten mit POIs.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Strategien zur Verwendung von Metadaten mit POIs {#using-metadata-pois}

Wenn Sie im Places-Dienst einen neuen POI erstellen, sind nur Name, Radius, Breitengrad und Längengrad erforderlich. Weitere Informationen zum Erstellen eines POI finden Sie unter [POI erstellen](/help/poi-mgmt-ui/create-a-poi-ui.md). Wenn Sie jedoch nur die Mindestinformationen eingeben, verpassen Sie die Möglichkeit, einen zusätzlichen Wert zu erzeugen.

POI-Metadaten können auf verschiedene Weise verwendet werden. Aus Sicht der POI-Verwaltung kann das Hinzufügen von Metadatenwerten bei der Suche nach oder Filterung einer Liste mit potenziell Tausenden von POIs hilfreich sein. Das Erstellen von Metadaten für Schlüsselattribute, die sich auf einen POI beziehen, kann in nachgelagerten Workflows einen Wert erbringen. Eine Hotelkette, die POIs für jede Immobilie erstellt, kann beispielsweise Metadaten enthalten, z. B. ob das Hotel über einen Pool verfügt oder nicht, oder über ein Restaurant und eine Bar oder über ein Fitnesscenter verfügt. Diese Metadaten können als Kontextdaten in Analysen und auch für zielgerichtete Angebote oder Nachrichten verwendet werden.

## Places Service-Metadaten in Launch

In Experience Platform Launch können Sie Datenelemente für jedes Places Service-Metadatenfeld erstellen, das für Tracking- oder Messaging-Zwecke wichtig ist.

![Datenelement für die Fitnesscenter-Anlage](/help/assets/gymfacility.png)

Anschließend können Sie eine Aktion mit der Analytics-Erweiterung erstellen, um einen neuen Treffer zu erstellen, der alle Metadaten enthält, die Sie als Kontextdaten verwenden möchten.

![Aktion für die Fitnessanlage](/help/assets/Analytics-gym.png)

## In-App-Nachrichten in Adobe Campaign

Metadaten können als Filter für lokale Benachrichtigungen und In-App-Nachrichten verwendet werden, die in Adobe Campaign Standard definiert sind. Die Verwendung von Metadaten als Filter bietet die Möglichkeit, eine relevantere Nachricht zu erstellen, die kontextbezogen zum tatsächlichen Speicherort ist.

![Filtern lokaler Benachrichtigungen und In-App-Nachrichten in ACS](/help/assets/ACS_gym_metadata.png)
