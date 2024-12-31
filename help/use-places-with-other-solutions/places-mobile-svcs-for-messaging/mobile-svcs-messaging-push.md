---
title: 'Push-Benachrichtigungen '
description: In diesem Abschnitt erfahren Sie, wie Sie den Places Service mit Push-Benachrichtigungen verwenden.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# Push-Benachrichtigungen 

Mit Mobile Services können Sie Push-Benachrichtigungen an Adobe Analytics-Segmente senden. Im Places-Service können Sie die Zielgruppe für Ihre Push-Nachricht mithilfe ihrer historischen Interaktionen mit Ihren POIs segmentieren. Sie können beispielsweise eine Nachricht an Benutzer senden, die sich in den letzten 30 Tagen in einem Ihrer Stores befunden haben.

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Aufgaben abgeschlossen haben:

* Die Daten des Places Service wurden von Adobe Analytics verarbeitet.

  Das bedeutet, dass Ihre Mobile App erfolgreich Places Service-Daten an eine Report Suite gesendet hat und dass die Daten für die Segmentierung verfügbar sind.

* Der Push-Benachrichtigungskanal in Mobile Services ist eingerichtet.

  Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=de).

* Informationen zum Senden einer Push-Benachrichtigung an ein Analytics-Segment in Mobile Services.

  Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=de).

## Benachrichtigung senden

Auf der Registerkarte **[!UICONTROL Audience]** des Workflows *Push-Benachrichtigung erstellen* können Sie die Audience für diese Nachricht auf eine der folgenden Arten erstellen:

* Wählen **[!UICONTROL in der Dropdown]** Liste „Analytics-Segmente“ ein zuvor erstelltes Adobe Analytics-Segment aus.

* Erstellen Sie **[!UICONTROL Abschnitt]** Benutzerdefiniertes Segment“ mithilfe der verfügbaren benutzerdefinierten Segmentparameter eine Zielgruppe.

![Einrichten einer Push-Nachricht](/help/assets/push-set-up.png)
