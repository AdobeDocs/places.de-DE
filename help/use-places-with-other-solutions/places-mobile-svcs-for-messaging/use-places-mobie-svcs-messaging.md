---
title: Verwenden des Places-Dienstes mit Mobile Services für Messaging
description: In diesem Abschnitt erfahren Sie, wie Sie den Places-Dienst mit Mobile Services für Messaging verwenden.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Bevor Sie die Mobile Services-Erweiterung für Messaging verwenden können, überprüfen Sie die folgenden Voraussetzungen:

* In Places Service wurden Zielpunkte erstellt. Weitere Informationen finden Sie unter [POI erstellen](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Der Places Service enthält eine neue und verbesserte POI-Datenbank für Ihre Organisation, die außerhalb der veralteten Mobile Services-Benutzeroberfläche existiert. POIs, die sich im Mobile Service befinden *Verwalten von Orten* Die Seitennavigation funktioniert nur für Version 4 des SDK.

* Hier finden Sie die *Orte verwalten* Seite zur POI-Verwaltung in der alten Mobile Services-Benutzeroberfläche für ältere Versionen des SDK:

   ![Alte Benutzeroberfläche](/help/assets/legacy-location-v4-ui.png)

* Hier finden Sie die Benutzeroberfläche des Places-Dienstes:

   ![Places Service-POI-Management-Benutzeroberfläche](/help/assets/places-ui.png)

* Das AKP-SDK ist ordnungsgemäß mit der Places-Erweiterung konfiguriert.

   Das bedeutet, dass Daten als Ereignisse und/oder Bedingungen in der Experience Platform Launch-Regel-Engine für Ihre mobile App verfügbar sind. Weitere Informationen finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Machen Sie sich mit dem Erstellen und Veröffentlichen von Experience Platform Launch-Regeln für das AKP-SDK in Ihrer mobilen App vertraut.

   Weitere Informationen finden Sie unter [Regel-Engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch-Datenelemente werden aus den Places-Erweiterungsdaten erstellt, die in der Regel-Engine verwendet werden.

   Weitere Informationen finden Sie unter [Datenelemente](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Reporting

Bevor Sie die Berichterstellung verwenden können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Places Service-Daten erfolgreich an die Adobe Analytics Report Suite senden.

   Weitere Informationen finden Sie unter [Verwenden des Places-Dienstes mit Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Machen Sie sich mit der Berichterstellung für Mobile Services vertraut.

   Weitere Informationen finden Sie unter [Berichte](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Berichtsvisualisierung

Sie können Mobile Service-Berichte mit Places Service-Daten ausführen, die an Adobe Analytics gesendet werden. Im folgenden Beispiel werden Ereignisse gesendet, wenn Benutzer Einträge in einem der POIs haben. In diesem Bericht wurde ein Filter für das POI-Eintrittsereignis zum vordefinierten Benutzerbericht hinzugefügt:

![Berichtsvisualisierung](/help/assets/report-visualize.png)

Zusätzliche Flexibilität bei der Visualisierung von Places Service-Daten ist über die Adobe Analytics-Schnittstellen verfügbar.
