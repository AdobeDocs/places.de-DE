---
title: In-App-Nachrichten mit dem Places-Dienst
description: Dieser Abschnitt enthält Informationen zur Verwendung von Push-Nachrichten im Campaign Standard mit In-App-Nachrichten in Campaign Standard.
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---


# In-App-Nachrichten mit dem Places-Dienst {#in-app-messages-loc-service}

Anhand dieser Informationen können Sie erkennen, wie Sie mit den Informationen des Orts-Dienstes In-App-Nachrichten oder lokale Benachrichtigungen senden können.

## Voraussetzungen 

Führen Sie zuerst die folgenden Aufgaben durch:

* Verwenden Sie eine Mobilanwendung, die mit dem Adobe Experience Platform Mobile SDK einschließlich der [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)konfiguriert ist.

* Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* hinzufügen Sie die [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) auf Ihre App-Konfiguration.

* [Erstellen Sie einen POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche für den POI-Dienst für Orte.

* Installieren und konfigurieren Sie die [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md) und [Orts-Monitorerweiterungen](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) in Ihrer mobilen Anwendung.

## Senden einer In-App-Nachricht basierend auf einem Geo-Zaun-Eintrag oder -Ausstieg

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Create In-App message]**.
1. Wählen Sie für den Nachrichtentyp **[!UICONTROL Target all users of a Mobile application]**.
1. Klicken Sie auf **[!UICONTROL Next]** und geben Sie die allgemeinen Details ein.
1. Überprüfen Sie im linken Bereich, ob Sie eine Vielzahl von Auslösern verwenden können, die mit Places Services zusammenhängen.

   * Sie können festlegen, dass die In-App-Nachricht angezeigt wird, wenn der Benutzer einen POI-Geo-Zaun eingegeben hat.
   * Sie können zum Filtern der Audience auch Metadaten verwenden, die in der Benutzeroberfläche der Places-Dienste definiert sind.

   Im folgenden Beispiel können Sie eine In-App-Nachricht auslösen, die nur Benutzern angezeigt wird, die in einem der Urlaubsresorts einsteigen, die an einem kostenlosen Drink-Programm teilnehmen, und diesen Benutzern bei ihrer Ankunft einen Coupon senden.

   ![&quot;In-App-Nachrichten-Orte-Metadaten&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

   ![&quot;Ereignis erstellen&quot;](/help/assets/prepare-ACS.png)

   Um den In-App-Nachrichten-Versand zu testen, starten Sie die Anwendung im Xcode- oder Android-Studio und wählen Sie mit dem Standortsimulator einen POI aus, der den Messaging-Kriterien entspricht.

   ![&quot;trinken Coupon&quot;](/help/assets/drink-coupon-on-app.png)

Die Verwendung von Places Services mit Adobe Campaign Standard bietet Ihnen ein leistungsfähiges Tool zur Segmentierung und Zielgruppe Ihrer Nachrichten an Benutzer, basierend auf Geo-Zaun-Einstiegen und -Ausstiegen. Mit dieser Integration können Sie personalisierte und kontextbezogene Anwendungsfälle erstellen.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service mit Kampagne Messaging](https://www.youtube.com/watch?v=ikiTTQw9c-o)
