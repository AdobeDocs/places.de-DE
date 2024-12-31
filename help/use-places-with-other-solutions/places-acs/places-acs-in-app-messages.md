---
title: In-App-Nachrichten mit Places Service
description: In diesem Abschnitt finden Sie Informationen zur Verwendung von Push-Nachrichten im Campaign Standard mit In-App-Nachrichten im Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# In-App-Messaging mit Places Service {#in-app-messages-loc-service}

Diese Informationen helfen Ihnen zu verstehen, wie Sie Places Service-Informationen zum Senden von In-App-Nachrichten oder lokalen Benachrichtigungen verwenden können.

## Voraussetzungen

Bevor Sie beginnen, führen Sie die folgenden Aufgaben aus:

* Lassen Sie eine Mobile App mit Adobe Experience Platform Mobile SDK konfigurieren, einschließlich der Erweiterung [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrieren Sie die [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* Fügen Sie die [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) zu Ihrer Mobile-App-Konfiguration hinzu.

* [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche des Places Service-POI.

* Installieren und konfigurieren Sie die [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md)-Erweiterung sowie eine Lösung zur Regionsüberwachung ([CoreLocation-](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Dokumentation zu Android-](https://developer.android.com/training/location/geofencing)) in Ihrer Mobile App.

## Senden einer In-App-Nachricht basierend auf einem Geofencing-Ein- oder Ausstieg

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz **[!UICONTROL In-App-Nachricht erstellen]**.
1. Wählen Sie als Nachrichtentyp die Option **[!UICONTROL Alle Benutzer einer Mobile App ansprechen]**.
1. Klicken Sie **[!UICONTROL Weiter]** und geben Sie die allgemeinen Details ein.
1. Stellen Sie im linken Bereich sicher, dass Sie verschiedene Trigger verwenden können, die sich auf Places Services beziehen.

   * Sie können festlegen, dass die In-App-Nachricht angezeigt wird, wenn der Benutzer einen POI-Geo-Fence eingegeben hat.
   * Sie können auch Metadaten verwenden, die in der Places Services-Benutzeroberfläche definiert sind, um die Zielgruppe zu filtern.

   Im folgenden Beispiel können Sie eine In-App-Nachricht erstellen, die nur Benutzenden angezeigt wird, die an einem Ferienresort teilnehmen, das an einem kostenlosen Getränkeprogramm teilnimmt, und Sie möchten diesen Benutzenden bei ihrer Ankunft einen Trigger senden.

   ![„In-App-Nachricht platziert Metadaten“](/help/assets/last-entered-vacation.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, um die Erstellung der In-App-Nachricht für den Versand abzuschließen.

   ![„Ereignis erstellen“](/help/assets/prepare-ACS.png)

   Um den In-App-Nachrichtenversand zu testen, starten Sie die Anwendung in Xcode oder Android Studio und wählen Sie mit dem Standortsimulator einen POI aus, der den Messaging-Kriterien entspricht.

   ![„Getränkecoupon“](/help/assets/drink-coupon-on-app.png)

Die Verwendung von Places Services mit Adobe Campaign Standard bietet Ihnen ein leistungsstarkes Tool, mit dem Sie Ihre Nachrichten segmentieren und basierend auf geografischen Ein- und Ausstiegen zielgerichtet an Benutzende senden können. Durch diese Integration können Sie personalisiertere und kontextuellere Anwendungsfälle erstellen.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service mit Campaign Messaging](https://www.youtube.com/watch?v=ikiTTQw9c-o)
