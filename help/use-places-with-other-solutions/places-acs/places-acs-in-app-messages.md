---
title: In-App-Nachrichten mit dem Places-Dienst
description: Dieser Abschnitt enthält Informationen zur Verwendung von Push-Nachrichten im Campaign Standard mit In-App-Nachrichten in Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# In-App-Messaging mit Places Service {#in-app-messages-loc-service}

Diese Informationen helfen Ihnen dabei zu verstehen, wie Sie mit Places Service-Informationen In-App-Nachrichten oder lokale Benachrichtigungen senden können.

## Voraussetzungen

Führen Sie zunächst die folgenden Aufgaben aus:

* Sie müssen eine Mobile App mit dem Adobe Experience Platform Mobile SDK konfigurieren, einschließlich der Variablen [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrieren Sie die [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App ein.
* Fügen Sie die [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) in Ihre App-Konfiguration.

* [POI erstellen](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche für POI des Places-Dienstes.

* Installieren und konfigurieren Sie die [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md) und einer regionalen Überwachungslösung ([Dokumentation zu CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Dokumentation zur Android-Position](https://developer.android.com/training/location/geofencing)) in Ihrer Mobile App.

## In-App-Nachricht basierend auf einem Geo-Fence-Ein- oder Ausstieg senden

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL In-App-Nachricht erstellen]**.
1. Wählen Sie für den Nachrichtentyp **[!UICONTROL Alle Nutzer einer Mobile App auswählen]**.
1. Klicken **[!UICONTROL Nächste]** und geben Sie die allgemeinen Details ein.
1. Vergewissern Sie sich im linken Bereich, dass Sie eine Vielzahl von Triggern verwenden können, die mit Places Services in Verbindung stehen.

   * Sie können festlegen, dass die In-App-Nachricht angezeigt wird, wenn der Benutzer einen POI-GeoZaun aufgerufen hat.
   * Sie können auch in der Benutzeroberfläche von Places Services definierte Metadaten verwenden, um die Zielgruppe zu filtern.

   Im folgenden Beispiel können Sie eine In-App-Nachricht Trigger haben, die nur Benutzern angezeigt wird, die in einen der Urlaubsressorts einsteigen, die an einem Programm für kostenlose Getränke teilnehmen, und diesen Benutzern bei ihrer Ankunft einen Gutschein senden.

   ![&quot;In-App Message Places-Metadaten&quot;](/help/assets/last-entered-vacation.png)

1. Klicken Sie auf **[!UICONTROL Nächste]** , um die Erstellung der In-App-Nachricht für die Bereitstellung abzuschließen.

   ![&quot;Ereignis erstellen&quot;](/help/assets/prepare-ACS.png)

   Um den In-App-Nachrichtenversand zu testen, starten Sie die Anwendung in Xcode oder Android Studio und wählen Sie mithilfe des Standortsimulators einen POI aus, der den Messaging-Kriterien entspricht.

   ![&quot;Coupon trinken&quot;](/help/assets/drink-coupon-on-app.png)

Die Verwendung von Places Services mit Adobe Campaign Standard bietet Ihnen ein leistungsstarkes Tool, um Ihre Nachrichten basierend auf Geofeneinstiegen und -ausstiegen zu segmentieren und an Benutzer auszurichten. Mit dieser Integration können Sie personalisiertere und kontextbezogenere Anwendungsfälle erstellen.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service mit Campaign Messaging](https://www.youtube.com/watch?v=ikiTTQw9c-o)
