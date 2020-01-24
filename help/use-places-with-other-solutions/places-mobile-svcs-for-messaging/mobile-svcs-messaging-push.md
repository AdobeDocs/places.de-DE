---
title: Push-Benachrichtigungen
description: Dieser Abschnitt zeigt Ihnen, wie Sie den Places-Dienst mit Push-Benachrichtigungen verwenden.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Push-Benachrichtigungen

Mit Mobile Services können Sie Push-Benachrichtigungen an Adobe Analytics-Segmente senden. Im Orte-Dienst können Sie die Zielgruppe für Ihre Push-Nachricht mithilfe ihrer historischen Interaktionen mit Ihren POIs segmentieren. Beispielsweise können Sie eine Nachricht an Benutzer senden, die sich in den letzten 30 Tagen in einem Ihrer Läden befanden.

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Aufgaben abgeschlossen haben:

* Die Daten des Orts-Service wurden von Adobe Analytics verarbeitet.

   Das bedeutet, dass Ihre mobile App erfolgreich Places Service-Daten an eine Report Suite gesendet hat und die Daten für die Segmentierung verfügbar sind.

* Der Push-Benachrichtigungskanal in Mobile Services wurde eingerichtet.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Hier erfahren Sie, wie Sie eine Push-Benachrichtigung an ein Analytics-Segment in Mobile Services senden.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Benachrichtigung senden

Auf der **[!UICONTROL Audience]**Registerkarte des Arbeitsablaufs *Push-Benachrichtigung*erstellen können Sie die Zielgruppe für diese Nachricht auf eine der folgenden Arten erstellen:

* Wählen Sie in der **[!UICONTROL Analytics Segments]**Dropdownliste ein zuvor erstelltes Adobe Analytics-Segment aus.

* Erstellen Sie im **[!UICONTROL Custom Segment]**Abschnitt eine Zielgruppe mithilfe der verfügbaren benutzerdefinierten Segmentparameter.

![Einrichten einer Push-Nachricht](/help/assets/push-set-up.png)
