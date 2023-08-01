---
audience: end-user
user-guide-title: Places Service-Anleitung
user-guide-description: Places-Service ist ein Geolokations-Service, mit dem Mobile Apps mit Standorterkennung den Standortkontext verstehen können.
feature: Places
source-git-commit: 30f083087936f54c692ff5aca245a7ee6b970b3a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 21%

---


# Places Service {#using}

+ [Places Service - Übersicht](home.md)
+ [Versionshinweise](release-notes.md)
+ [Erste Schritte](getting-started.md)
+ [Zugriff auf Places Service erhalten](places-gain-access.md)
+ Places Service-Benutzeroberfläche {#poi-mgmt-ui}
   + [Übersicht über die Places Service-Benutzeroberfläche](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [POI erstellen](poi-mgmt-ui/create-a-poi-ui.md)
   + [Zuvor erstellte Zielpunkte verwalten](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Strategien zur Verwendung von Metadaten mit POIs](poi-mgmt-ui/metadata-with-pois.md)
   + [Massen-Upload von POIs](poi-mgmt-ui/bulk-upload-pois.md)
   + [Verwalten mehrerer Bibliotheken](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ Webservice-API {#web-service-api}
   + [Übersicht über die Webdienst-API](web-service-api/places-web-services.md)
   + [Voraussetzungen für die Integration](web-service-api/adobe-i-o-integration.md)
   + API-Nutzung {#api-usage}
      + [API-Nutzungsübersicht](web-service-api/api-usage/api-usage-overview.md)
      + [Kopfzeilen und Parameter](web-service-api/api-usage/headers-and-parameters.md)
      + Bibliotheken verwalten {#manage-libraries}
         + [Bibliotheken verwalten - Übersicht](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [eine Bibliothek erstellen](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Bibliothek lesen](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Bibliothek aktualisieren](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Bibliothek löschen](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Alle Bibliotheken in Ihrer Organisation lesen](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Rang in Ihren Bibliotheken festlegen](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Bibliotheksrang](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Zielpunkte verwalten {#manage-pois}
         + [Übersicht über POIs verwalten](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [POI erstellen](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [POI lesen](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [POI aktualisieren](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Einen POI löschen](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Alle Zielpunkte in einer Bibliothek lesen](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Alle Zielpunkte in Ihrer Organisation lesen](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + Batch-APIs {#batch-apis}
            + [Batch-APIs - Übersicht](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Mehrere Zielpunkte erstellen](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Mehrere Zielpunkte aktualisieren](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Mehrere Zielpunkte löschen](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [Abfrage-APIs](web-service-api/api-usage/query-apis.md)
+ Erweiterungen für die Mobile SDKs {#places-ext-aep-sdks}
   + Places-Erweiterung {#places-extension}
      + [Places-Erweiterung](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Places-API-Referenz](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [Places-Ereignisreferenz](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [Benutzerdefinierte Places-Objekte](places-ext-aep-sdks/places-extension/cust-places-objects.md)
+ [Verwenden Sie den Places-Dienst mit Ihrer eigenen Überwachungslösung](using-your-own-monitor.md)
+ [Verwenden des Places-Dienstes ohne aktive Regionsüberwachung](use-places-without-active-monitoring.md)
+ Verwenden des Places-Dienstes als Teil des Experience Platform Launch-Workflows {#use-places-launch-workflow}
   + [Verwenden des Places-Dienstes als Teil des Experience Platform Launch-Workflows](use-places-launch-workflow/places-launch-workflow.md)
   + [Definieren von Datenelementen](use-places-launch-workflow/define-data-elements.md)
   + [Einstiegs- und Ausstiegsregeln erstellen](use-places-launch-workflow/create-rule-places-property.md)
+ Places Service mit anderen Adobe-Lösungen verwenden {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Verwenden des Places-Dienstes mit Adobe Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [POI-Einstiegs- und -Ausstiegsdaten an Analytics senden](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Hinzufügen von Standortkontext zu Analytics-Anforderungen](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Bericht zu Standortdaten in Analytics Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Push-Benachrichtigungen ](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [In-App-Benachrichtigungen](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Verwenden des Places-Dienstes mit Adobe Campaign Standard](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Push-Benachrichtigungen ](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [In-App-Nachrichten](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Verwenden des Places-Dienstes mit Adobe Target](use-places-with-other-solutions/places-target/places-target.md)
+ Test und Validierung {#places-testing-validation}
   + [Testen und Validieren des Places-Dienstes](places-testing-validation/test-validate-places.md)
+ [Häufig gestellte Fragen](places-faqs.md)
