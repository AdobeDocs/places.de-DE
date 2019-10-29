---
title: Push-Benachrichtigung
seo-title: Push-Benachrichtigung
description: Dieser Abschnitt zeigt Ihnen, wie Sie Orte mit Push-Nachrichten verwenden.
seo-description: Dieser Abschnitt zeigt Ihnen, wie Sie Orte mit Push-Nachrichten verwenden.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Push-Benachrichtigungen (#place-push-messaging)

Push-Benachrichtigung: Mit AMS können Sie Push-Benachrichtigungen an Adobe Analytics-Segmente senden. Mit dem Location Service können Sie die Zielgruppe Ihrer Push-Nachricht anhand ihrer historischen Interaktionen mit Ihren POIs segmentieren. Sie können beispielsweise eine Nachricht an Benutzer senden, die sich in den letzten 30 Tagen in einem Ihrer Läden befanden.

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Aufgaben abgeschlossen haben:

* Die Daten des Location Service wurden von Adobe Analytics verarbeitet.

   Das bedeutet, dass Ihre mobile App erfolgreich Standortdienstdaten an eine Report Suite gesendet hat und die Daten für die Segmentierung verfügbar sind.

* Der Push-Benachrichtigungskanal in Mobile Services wurde eingerichtet.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Machen Sie sich mit dem Senden einer Push-Benachrichtigung an ein Analytics-Segment in Mobile Services vertraut.

   * Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Senden einer Benachrichtigung

Auf der **[!UICONTROL Audience]** Registerkarte des Arbeitsablaufs für Push-Benachrichtigungen *erstellen* können Sie die Zielgruppe für diese Nachricht auf eine der folgenden Arten erstellen:

* Wählen Sie ein zuvor erstelltes Adobe Analytics-Segment aus.

* Erstellen Sie eine Zielgruppe mithilfe der verfügbaren benutzerdefinierten Segmentparameter.

![Einrichten einer Push-Nachricht](/help/assets/push-set-up.png)

