---
title: Push-Benachrichtigungen
description: In diesem Abschnitt erfahren Sie, wie Sie den Places Service mit Push-Benachrichtigungen verwenden.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

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
