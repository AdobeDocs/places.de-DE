---
title: Verwenden des Places Service mit Mobile Services für das Messaging
description: In diesem Abschnitt erfahren Sie, wie Sie Places Service mit Mobile Services für das Messaging verwenden.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
TQID: https://experienceleague.adobe.com/-axuli6p-QHthMkucGLCcgyHCqrwudXmif-dZwpGli4
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 359
ht-degree: 3%

---

# Adobe Mobile Services {#places-mobile-services}

Bevor Sie die Mobile Services-Erweiterung für das Messaging verwenden können, überprüfen Sie die folgenden Voraussetzungen:

* In Places Service wurden interessante Punkte erstellt. Weitere Informationen finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >Der Places-Service enthält eine neue und verbesserte POI-Datenbank für Ihre Organisation, die außerhalb der veralteten Mobile Services-Benutzeroberfläche existiert. POIs, die sich auf der Seitennavigation des Mobile Service *Orte verwalten* befinden, funktionieren nur für Version 4 der SDK.

* Die folgende Seite *Orte verwalten* POI-Verwaltung in der veralteten Mobile Services-Benutzeroberfläche für ältere Versionen von SDK:

  ![Alte Benutzeroberfläche](/help/assets/legacy-location-v4-ui.png)

* Hier finden Sie die Benutzeroberfläche des Places-Service:

  ![Places Service-POI-Verwaltungsoberfläche](/help/assets/places-ui.png)

* ACP SDK ist mit der Places-Erweiterung ordnungsgemäß konfiguriert.

  Das bedeutet, dass die Daten als Ereignisse und/oder Bedingungen in der Experience Platform Launch-Regel-Engine für Ihre Mobile App verfügbar sind. Weitere Informationen finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Machen Sie sich mit dem Erstellen und Veröffentlichen von Experience Platform Launch-Regeln in der Mobile App in der ACP SDK vertraut.

  Weitere Informationen finden Sie unter [Regel-](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch-Datenelemente werden aus den Places-Erweiterungsdaten erstellt, die in der Regel-Engine verwendet werden.

  Weitere Informationen finden Sie unter [Datenelemente](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Reporting

Bevor Sie Berichte verwenden können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Places Service-Daten erfolgreich an Adobe Analytics Report Suite senden.

  Weitere Informationen finden Sie unter [Verwenden des Places Service mit Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Machen Sie sich mit dem Reporting für Mobile Services vertraut.

  Weitere Informationen finden Sie unter [Berichte](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=de).

## Visualisierung für Berichte

Sie können Mobile-Service-Berichte ausführen, indem Sie die Daten des Places-Service verwenden, die an Adobe Analytics gesendet werden. Im folgenden Beispiel werden Ereignisse gesendet, wenn Benutzer Einträge in einem der POIs haben. In diesem Bericht wurde ein Filter des POI-Eintrittsereignisses zum vordefinierten Benutzerbericht hinzugefügt:

![Berichtsvisualisierung](/help/assets/report-visualize.png)

Zusätzliche Flexibilität bei der Visualisierung der Places Service-Daten ist in den Adobe Analytics-Benutzeroberflächen verfügbar.
