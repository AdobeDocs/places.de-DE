---
title: Verwenden von Metadaten mit POIs
description: In diesem Abschnitt finden Sie Informationen und Strategien zur Verwendung von Metadaten mit POIs.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Strategien für die Verwendung von Metadaten mit POIs {#using-metadata-pois}

Wenn Sie im Places Service einen neuen POI erstellen, sind nur die Elemente Name, Radius, Breitengrad und Längengrad erforderlich. Weitere Informationen zum Erstellen eines POI finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Wenn Sie jedoch nur die Mindestinformationen eingeben, verpassen Sie eine Gelegenheit, zusätzlichen Wert zu schaffen.

POI-Metadaten können auf verschiedene Weise verwendet werden. Aus Sicht der POI-Verwaltung kann das Hinzufügen von Metadatenwerten bei der Suche oder Filterung nach einer Liste mit potenziell Tausenden von POIs helfen. Das Erstellen von Metadaten für Schlüsselattribute im Zusammenhang mit einem POI kann in nachgelagerten Workflows einen Wert liefern. Beispielsweise kann eine Hotelkette, die POIs für jede Eigenschaft erstellt, Metadaten einbeziehen, z. B. ob die Hoteleigenschaft über einen Pool verfügt oder nicht, ein Restaurant und eine Bar oder ob sie über eine Fitnesseinrichtung verfügen. Diese Metadaten können als Kontextdaten in Analytics eingeschlossen und auch für zielgerichtete Angebote oder Messaging verwendet werden.

## Platziert Service-Metadaten in Launch

Beim Experience Platform Launch können Sie Datenelemente für jedes Metadatenfeld des Places-Services erstellen, das für Tracking- oder Messaging-Zwecke wichtig ist.

![Datenelement für die Turnhalle](/help/assets/gymfacility.png)

Anschließend können Sie mit der Analytics-Erweiterung eine Aktion erstellen, um einen neuen Treffer zu erstellen, der alle gewünschten Metadaten als Kontextdaten enthält.

![Aktion für die Turnhalle](/help/assets/Analytics-gym.png)

## In-App-Nachrichten in Adobe Campaign

Metadaten können als Filter für lokale Benachrichtigungen und In-App-Nachrichten verwendet werden, die in Adobe Campaign Standard definiert sind. Durch die Verwendung von Metadaten als Filter erhalten Sie die Möglichkeit, eine relevantere Nachricht zu erstellen, die kontextuell zum tatsächlichen Speicherort ist.

![Filtern von lokalen Benachrichtigungen und In-App-Nachrichten in ACS](/help/assets/ACS_gym_metadata.png)
