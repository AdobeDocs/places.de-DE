---
title: 'Push-Benachrichtigungen '
description: Dieser Abschnitt zeigt Ihnen, wie Sie den Places-Dienst mit Push-Benachrichtigungen verwenden.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 8%

---


# Push-Benachrichtigungen 

Mit Mobile Services können Sie Push-Benachrichtigungen an Adobe Analytics-Segmente senden. Im Orte-Dienst können Sie die Audience für Ihre Push-Nachricht mithilfe ihrer historischen Interaktionen mit Ihren POIs segmentieren. Beispielsweise können Sie eine Nachricht an Benutzer senden, die sich in den letzten 30 Tagen in einem Ihrer Läden befanden.

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Aufgaben abgeschlossen haben:

* Die Daten des Orte-Service wurden von Adobe Analytics verarbeitet.

   Das bedeutet, dass Ihre mobile App erfolgreich Places Service-Daten an eine Report Suite gesendet hat und dass die Daten für die Segmentierung verfügbar sind.

* Der Kanal für Push-Benachrichtigungen in Mobile Services wurde eingerichtet.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Hier erfahren Sie, wie Sie eine Push-Benachrichtigung an ein Analytics-Segment in Mobile Services senden.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Benachrichtigung senden

Auf der **[!UICONTROL Audience]** Registerkarte des Arbeitsablaufs *Push-Benachrichtigung* erstellen können Sie die Audience für diese Nachricht auf eine der folgenden Arten erstellen:

* Wählen Sie in der **[!UICONTROL Analytics Segments]** Dropdown-Liste ein zuvor erstelltes Adobe Analytics-Segment aus.

* Erstellen Sie im **[!UICONTROL Custom Segment]** Abschnitt eine Audience mit den verfügbaren Segmentparametern.

![Einrichten einer Push-Nachricht](/help/assets/push-set-up.png)
