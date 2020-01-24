---
title: Verwenden des Orte-Dienstes mit Mobile Services für Messaging
description: Dieser Abschnitt zeigt Ihnen, wie Sie den Places-Dienst mit Mobile Services für Nachrichten verwenden.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

Bevor Sie die Mobile Services-Erweiterung für Nachrichten verwenden können, überprüfen Sie die folgenden Voraussetzungen:

* Interessensgebiete wurden im Ortsdienst erstellt. For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Der Places Service umfasst eine neue und verbesserte POI-Datenbank für Ihr Unternehmen, die außerhalb der alten Mobile Services-Benutzeroberfläche vorhanden ist. POIs, die sich auf der Navigation der Seite &quot;Orte *verwalten* &quot;des Mobile Service befinden, funktionieren nur für Version 4 des SDK.

* Im Folgenden finden Sie die Verwaltungsseite &quot;POI-Verwaltung *für Orte* verwalten&quot;in der alten Mobile Services-Benutzeroberfläche für ältere Versionen des SDK:

   ![Alte Benutzeroberfläche](/help/assets/legacy-location-v4-ui.png)

* Die Benutzeroberfläche des Orte-Dienstes lautet:

   ![Places Service POI Management-Benutzeroberfläche](/help/assets/places-ui.png)

* Das ACP SDK ist ordnungsgemäß mit den Erweiterungen &quot;Places Service&quot;und/oder &quot;Places Monitor&quot;konfiguriert.

   Das bedeutet, dass Daten als Ereignisse und/oder Bedingungen in der Erlebnisplattformstartregeln-Engine für Ihre mobile App verfügbar sind. Weitere Informationen finden Sie unter [Platzierungserweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md) oder [Platzierungsmonitor-Erweiterung](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md).

* Machen Sie sich mit dem Erstellen und Veröffentlichen von Experience Platform Launch-Regeln für das ACP SDK in Ihrer mobilen App vertraut.

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Die Datenelemente zum Starten der Erlebnisplattform werden aus den Platzierungserweiterungsdaten erstellt, die in der Regel-Engine verwendet werden.

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Berichterstellung 

Bevor Sie die Berichterstellung verwenden können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Senden Sie erfolgreich Daten zum Platzierungsdienst an die Adobe Analytics Report Suite.

   Weitere Informationen finden Sie unter [Verwenden des Orte-Dienstes mit Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Machen Sie sich mit der Berichterstellung zu Mobile Services vertraut.

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Berichtsvisualisierung

Sie können Mobile Service-Berichte mit den an Adobe Analytics gesendeten Daten des Places Service ausführen. Im folgenden Beispiel werden Ereignisse gesendet, wenn Benutzer Einträge in einem der POIs haben. In diesem Bericht wurde ein Filter für das POI-Einstiegsereignis über den vordefinierten Benutzerbericht hinzugefügt:

![Berichtsvisualisierung](/help/assets/report-visualize.png)

Zusätzliche Flexibilität bei der Visualisierung der Daten des Orte-Dienstes ist in den Adobe Analytics-Schnittstellen verfügbar.

