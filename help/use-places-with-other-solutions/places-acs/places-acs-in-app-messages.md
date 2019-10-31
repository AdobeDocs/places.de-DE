---
title: In-App-Nachrichten mit dem Location Service
seo-title: In-App-Nachrichten mit dem Location Service
description: Dieser Abschnitt enthält Informationen zur Verwendung von Push-Nachrichten in Campaign Standard mit In-App-Nachrichten in Campaign Standard.
seo-description: 'Dieser Abschnitt enthält Informationen zur Verwendung von "Push-Nachrichten in Campaign Standard"mit In-App-Nachrichten in Campaign Standard. '
translation-type: tm+mt
source-git-commit: a76e91775efd92ce56f2dc5cbdcc65786855b5c3

---


# In-App-Nachrichten mit dem Location Service {#in-app-messages-loc-service}

Anhand dieser Informationen erhalten Sie einen Einblick, wie Sie mit den Informationen des Adobe Experience Platform Location Service In-App-Nachrichten oder lokale Benachrichtigungen senden können.

## Voraussetzungen

Führen Sie zuerst die folgenden Aufgaben aus:

* Verwenden Sie eine mobile Anwendung, die mit dem Adobe Experience Platform Mobile SDK, einschließlich der [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard), konfiguriert wurde.

* Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* Fügen Sie Ihrer App-Konfiguration die [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) hinzu.

* [Erstellen Sie einen POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche Orte POI.

* Installieren und konfigurieren Sie die [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md) und [Orts-Monitorerweiterungen](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) in Ihrer mobilen Anwendung.

## Senden einer In-App-Nachricht basierend auf einem Geo-Zaun-Eintrag oder -Ausstieg

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Create In-App message]**.
2. Wählen Sie für den Nachrichtentyp **[!UICONTROL Target all users of a Mobile application]**.
3. Klicken Sie auf **[!UICONTROL Next]** und geben Sie die allgemeinen Details ein.
4. Überprüfen Sie im linken Bereich, ob Sie eine Vielzahl von Auslösern verwenden können, die mit Location Services in Zusammenhang stehen.

   * Sie können festlegen, dass die In-App-Nachricht angezeigt wird, wenn der Benutzer einen POI-Geo-Zaun eingegeben hat.
   * Sie können auch Metadaten verwenden, die in der Benutzeroberfläche von Location Services definiert sind, um die Zielgruppe zu filtern.
   Im folgenden Beispiel können Sie eine In-App-Nachricht auslösen, die nur Benutzern angezeigt wird, die in einen der Ferienresorts einsteigen, die an einem kostenlosen Getränkeprogramm teilnehmen, und diesen Benutzern bei ihrer Ankunft einen Coupon senden.

   !["In-App-Nachrichten-Orte-Metadaten"](/help/assets/last-entered-vacation.png)

5. Klicken Sie auf das Symbol, **[!UICONTROL Next]** um die In-App-Nachricht für die Bereitstellung zu erstellen.

   !["Ereignis erstellen"](/help/assets/prepare-ACS.png)

   Um die Bereitstellung der In-App-Nachricht zu testen, starten Sie die Anwendung im Xcode- oder Android-Studio und wählen Sie mit dem Standortsimulator einen POI aus, der den Messaging-Kriterien entspricht.

   !["trinken Coupon"](/help/assets/drink-coupon-on-app.png)

Die Verwendung von Location Services mit Adobe Campaign Standard bietet Ihnen ein leistungsfähiges Tool, um Ihre Nachrichten basierend auf Geo-Zaun-Einstiegen und -Ausstiegen zu segmentieren und gezielt an Benutzer auszurichten. Mit dieser Integration können Sie personalisierte und kontextbezogene Anwendungsfälle erstellen.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)