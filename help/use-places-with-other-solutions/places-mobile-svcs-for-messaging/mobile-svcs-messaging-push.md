---
title: Push-Benachrichtigungen
description: In diesem Abschnitt erfahren Sie, wie Sie den Places-Dienst mit Push-Benachrichtigungen verwenden.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 8%

---

# Push-Benachrichtigungen 

Mit Mobile Services können Sie Push-Benachrichtigungen an Adobe Analytics-Segmente senden. In Places Service können Sie die Zielgruppe für Ihre Push-Nachricht mithilfe ihrer historischen Interaktionen mit Ihren POIs segmentieren. Sie können beispielsweise eine Nachricht an Benutzer senden, die sich in einem Ihrer Geschäfte in den letzten 30 Tagen befanden.

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Aufgaben abgeschlossen haben:

* Places Service -Daten wurden von Adobe Analytics verarbeitet.

   Das bedeutet, dass Ihre mobile App erfolgreich Places Service-Daten an eine Report Suite gesendet hat und dass die Daten für die Segmentierung verfügbar sind.

* Der Push-Benachrichtigungskanal in Mobile Services wurde eingerichtet.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Erfahren Sie, wie Sie eine Push-Benachrichtigung an ein Analytics-Segment in Mobile Services senden.

   Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Benachrichtigung senden

Im **[!UICONTROL Zielgruppe]** des *Push-Benachrichtigung erstellen* um die Audience für diese Nachricht auf eine der folgenden Arten zu erstellen:

* Im **[!UICONTROL Analytics-Segmente]** ein zuvor erstelltes Adobe Analytics-Segment aus.

* Im **[!UICONTROL Benutzerdefiniertes Segment]** erstellen Sie eine Zielgruppe mithilfe der verfügbaren benutzerdefinierten Segmentparameter.

![Push-Nachrichten einrichten](/help/assets/push-set-up.png)
