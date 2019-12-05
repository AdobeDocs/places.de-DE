---
title: Verwenden von Orten mit Mobile Services für Messaging
description: In diesem Abschnitt wird die Verwendung von Orten mit Mobile Services für Nachrichten erläutert.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Adobe Mobile Services {#places-mobile-services}

Bevor Sie die Mobile Services-Erweiterung für Nachrichten verwenden können, überprüfen Sie die folgenden Voraussetzungen:

* Im Location Service wurden Zielpunkte erstellt. Siehe Dokumentation bei Bedarf. (Link zum Erstellen eines POI)Hinweis: Der Location Service umfasst eine neue und verbesserte Point-of-Interest-Datenbank für Ihr Unternehmen, die außerhalb der alten AMS-Schnittstelle existiert. Alle POIs, die in der AMS-Navigation "Orte verwalten"gefunden werden, funktionieren nur für Version 4 des SDK.
   * Die veraltete Places POI-Verwaltungsoberfläche in AMS für ältere SDK-Versionen:

      ![Alte Benutzeroberfläche](/help/assets/legacy-location-v4-ui.png)

   * Die Verwaltungsoberfläche des Location Service-POI lautet:

      ![POI-Verwaltungsoberfläche des Location Service](/help/assets/places-ui.png)

* ACP SDK ist ordnungsgemäß mit Plates and/or Places Monitor Extensions konfiguriert. Das bedeutet, dass Daten als Ereignisse und/oder Bedingungen in der Startregel-Engine für Ihre mobile App verfügbar sind. Weitere Informationen finden Sie in der Dokumentation. (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* Machen Sie sich mit dem Erstellen und Veröffentlichen von Startregeln für das ACP SDK in Ihrer mobilen App vertraut. Weitere Informationen finden Sie in der Dokumentation. (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* Datenelemente zum Starten werden aus den Speicherorte SDK-Erweiterungsdaten erstellt, die in den Regeln verwendet werden. Siehe Dokumentation (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)

## Berichterstellung 

Bevor Sie die Berichterstellung verwenden können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Senden von Ortsdienstdaten erfolgreich an Adobe Analytics Report Suite. Falls erforderlich, besuchen Sie die Dokumentation zu Adobe Analytics (Link zu Steves Dokumenten).
* Mit AMS-Berichten vertraut. Falls erforderlich, besuchen Sie die Dokumentation (https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## Berichtsvisualisierung

Sie können AMS-Berichte mit den Daten des Location Service ausführen, die an Adobe Analytics gesendet werden. Beispielsweise habe ich Ereignisse gesendet, wenn Benutzer Einträge in einem meiner POIs haben. In diesem Bericht habe ich einen Filter für das POI-Einstiegsereignis zu meinem vordefinierten Benutzerbericht hinzugefügt:

![Berichtsvisualisierung](/help/assets/report-visualize.png)

Zusätzliche Flexibilität bei der Visualisierung von Standortdienstdaten ist in den Adobe Analytics-Schnittstellen verfügbar.

