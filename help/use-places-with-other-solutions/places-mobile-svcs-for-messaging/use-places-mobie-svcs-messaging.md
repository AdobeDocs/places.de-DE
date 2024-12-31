---
title: Verwenden des Places Service mit Mobile Services für das Messaging
description: In diesem Abschnitt erfahren Sie, wie Sie Places Service mit Mobile Services für das Messaging verwenden.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

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
