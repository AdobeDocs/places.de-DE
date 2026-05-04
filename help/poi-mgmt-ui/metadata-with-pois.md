---
title: Verwenden von Metadaten mit POIs
description: In diesem Abschnitt finden Sie Informationen und Strategien zur Verwendung von Metadaten mit POIs.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
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
source-wordcount: 296
ht-degree: 0%

---

# Strategien für die Verwendung von Metadaten mit POIs {#using-metadata-pois}

Wenn Sie im Places Service einen neuen POI erstellen, sind nur die Elemente Name, Radius, Breitengrad und Längengrad erforderlich. Weitere Informationen zum Erstellen eines POI finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Wenn Sie jedoch nur die Mindestinformationen eingeben, verpassen Sie eine Gelegenheit, zusätzlichen Wert zu schaffen.

POI-Metadaten können auf verschiedene Weise verwendet werden. Aus Sicht der POI-Verwaltung kann das Hinzufügen von Metadatenwerten bei der Suche oder Filterung nach einer Liste mit potenziell Tausenden von POIs helfen. Das Erstellen von Metadaten für Schlüsselattribute im Zusammenhang mit einem POI kann in nachgelagerten Workflows einen Wert liefern. Beispielsweise kann eine Hotelkette, die POIs für jede Eigenschaft erstellt, Metadaten einbeziehen, z. B. ob die Hoteleigenschaft über einen Pool verfügt oder nicht, ein Restaurant und eine Bar oder ob sie über eine Fitnesseinrichtung verfügen. Diese Metadaten können als Kontextdaten in Analytics eingeschlossen und auch für zielgerichtete Angebote oder Messaging verwendet werden.

## Platziert Service-Metadaten in Launch

In Experience Platform Launch können Sie Datenelemente für jedes Metadatenfeld des Places-Services erstellen, das für Tracking- oder Messaging-Zwecke wichtig ist.

![Datenelement für die Turnhalle](/help/assets/gymfacility.png)

Anschließend können Sie mit der Analytics-Erweiterung eine Aktion erstellen, um einen neuen Treffer zu erstellen, der alle gewünschten Metadaten als Kontextdaten enthält.

![Aktion für die Turnhalle](/help/assets/Analytics-gym.png)

## In-App-Nachrichten in Adobe Campaign

Metadaten können als Filter für lokale Benachrichtigungen und In-App-Nachrichten verwendet werden, die in Adobe Campaign Standard definiert sind. Durch die Verwendung von Metadaten als Filter erhalten Sie die Möglichkeit, eine relevantere Nachricht zu erstellen, die kontextuell zum tatsächlichen Speicherort ist.

![Filtern von lokalen Benachrichtigungen und In-App-Nachrichten in ACS](/help/assets/ACS_gym_metadata.png)
