---
product: Places Service
audience: end-user
user-guide-title: Places Service-Anleitung
user-guide-description: Places-Service ist ein Geolokations-Service, mit dem Mobile Apps mit Standorterkennung den Standortkontext verstehen können.
translation-type: tm+mt
source-git-commit: f9215fa3871d91166ad109a0708105f79536213c
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 19%

---


# Places Service {#using}

+ [Übersicht über den Places Service](home.md)
+ [Versionshinweise](release-notes.md)
+ [Erste Schritte](getting-started.md)
+ [Zugriff auf den Places Service](places-gain-access.md)
+ Platzierungsdienst-Benutzeroberfläche {#poi-mgmt-ui}
   + [Übersicht über die Benutzeroberfläche des Platzierungsdienstes](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [Erstellen eines POI](poi-mgmt-ui/create-a-poi-ui.md)
   + [Zuvor erstellte POIs verwalten](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Strategien zur Verwendung von Metadaten mit POIs](poi-mgmt-ui/metadata-with-pois.md)
   + [Massenupload von POIs](poi-mgmt-ui/bulk-upload-pois.md)
   + [Verwalten mehrerer Bibliotheken](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ Webdienst-API {#web-service-api}
   + [Übersicht über die Webdienst-API](web-service-api/places-web-services.md)
   + [Integrationsvoraussetzungen](web-service-api/adobe-i-o-integration.md)
   + API-Nutzung {#api-usage}
      + [API-Nutzungsübersicht](web-service-api/api-usage/api-usage-overview.md)
      + [Kopfzeilen und Parameter](web-service-api/api-usage/headers-and-parameters.md)
      + Bibliotheken verwalten {#manage-libraries}
         + [Übersicht über die Verwaltung von Bibliotheken](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [eine Bibliothek erstellen](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Bibliothek lesen](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Bibliothek aktualisieren](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Bibliothek löschen](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Alle Bibliotheken in Ihrer Organisation lesen](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Rang auf Ihre Bibliotheken festlegen](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Rang einer Bibliothek abrufen](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Zielpunkte verwalten {#manage-pois}
         + [Überblick über die Verwaltung von POI](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [Erstellen eines POI](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [POI lesen](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [POI aktualisieren](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Einen POI löschen](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Alle POIs in einer Bibliothek lesen](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Alle POIs in Ihrer Organisation lesen](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + Stapel-APIs {#batch-apis}
            + [Übersicht über Stapel-APIs](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Erstellen mehrerer POIs](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Mehrere POIs aktualisieren](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Löschen mehrerer POIs](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [Abfrage-APIs](web-service-api/api-usage/query-apis.md)
+ Erweiterungen für mobile SDKs {#places-ext-aep-sdks}
   + Places-Erweiterung {#places-extension}
      + [Places-Erweiterung](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Platzierungs-API-Referenz](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [Platzierungs-Ereignis](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [Objekte für benutzerdefinierte Orte](places-ext-aep-sdks/places-extension/cust-places-objects.md)
   + Platzierungsmonitor-Erweiterung {#places-monitor-extension}
      + [Platzierungsmonitor-Erweiterung](places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)
      + [Verwenden der Erweiterung &quot;Orts Monitor&quot;](places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)
      + [Platzierungs-Monitor-API-Referenz](places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.md)
+ [Verwenden Sie den Orte-Dienst mit Ihrer eigenen Überwachungslösung](using-your-own-monitor.md)
+ [Orte-Dienst ohne aktive Regionsüberwachung verwenden](use-places-without-active-monitoring.md)
+ Verwenden des Orte-Dienstes als Teil des Experience Platform Launch-Workflows {#use-places-launch-workflow}
   + [Verwenden des Orte-Dienstes als Teil des Experience Platform Launch-Workflows](use-places-launch-workflow/places-launch-workflow.md)
   + [Definieren von Datenelementen](use-places-launch-workflow/define-data-elements.md)
   + [Einstiegs- und Ausstiegsregeln erstellen](use-places-launch-workflow/create-rule-places-property.md)
+ Orte-Dienst mit anderen Adoben-Lösungen verwenden {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Orte-Dienst mit Adobe Analytics verwenden](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [POI-Einstiegs- und -Ausstiegsdaten an Analytics senden](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [hinzufügen Standortkontext für Analytics-Anforderungen](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Bericht zu Standortdaten in Analytics Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Push-Benachrichtigungen ](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [In-App-Benachrichtigungen](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Orte-Dienst mit Adobe Campaign Standard verwenden](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Push-Benachrichtigungen ](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [In-App-Nachrichten](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Orte-Dienst mit Adobe Target verwenden](use-places-with-other-solutions/places-target/places-target.md)
+ Test und Validierung {#places-testing-validation}
   + [Praktikumsdienst testen und validieren](places-testing-validation/test-validate-places.md)
+ [Häufig gestellte Fragen](places-faqs.md)
