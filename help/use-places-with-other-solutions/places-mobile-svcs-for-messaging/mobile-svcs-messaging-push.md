---
title: Push-Benachrichtigungen
description: In diesem Abschnitt erfahren Sie, wie Sie den Places-Dienst mit Push-Benachrichtigungen verwenden.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# Push-Benachrichtigungen 

Mit Mobile Services können Sie Push-Benachrichtigungen an Adobe Analytics-Segmente senden. In Places Service können Sie die Zielgruppe für Ihre Push-Nachricht mithilfe ihrer historischen Interaktionen mit Ihren POIs segmentieren. Sie können beispielsweise eine Nachricht an Benutzer senden, die sich in einem Ihrer Geschäfte in den letzten 30 Tagen befanden.

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Aufgaben abgeschlossen haben:

* Places Service -Daten wurden von Adobe Analytics verarbeitet.

  Das bedeutet, dass Ihre mobile App erfolgreich Places Service-Daten an eine Report Suite gesendet hat und dass die Daten für die Segmentierung verfügbar sind.

* Der Push-Benachrichtigungskanal in Mobile Services wurde eingerichtet.

  Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=de).

* Erfahren Sie, wie Sie eine Push-Benachrichtigung an ein Analytics-Segment in Mobile Services senden.

  Weitere Informationen finden Sie unter [Push-Nachrichten erstellen](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=de).

## Benachrichtigung senden

Auf der Registerkarte **[!UICONTROL Zielgruppe]** des Workflows *Push-Benachrichtigung erstellen* können Sie die Zielgruppe für diese Nachricht auf eine der folgenden Arten erstellen:

* Wählen Sie in der Dropdownliste **[!UICONTROL Analytics-Segmente]** ein zuvor erstelltes Adobe Analytics-Segment aus.

* Erstellen Sie im Abschnitt **[!UICONTROL Benutzerdefiniertes Segment]** eine Zielgruppe mithilfe der verfügbaren benutzerdefinierten Segmentparameter.

![Einrichten einer Push-Nachricht](/help/assets/push-set-up.png)
