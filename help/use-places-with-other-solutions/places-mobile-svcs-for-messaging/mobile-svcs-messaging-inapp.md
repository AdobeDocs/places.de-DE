---
title: In-App-Benachrichtigungen
description: In diesem Abschnitt erfahren Sie, wie Sie den Places Service mit In-App-Nachrichten verwenden.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
TQID: https://experienceleague.adobe.com/Z39ybIytDRlCbkMthWjvk5F-oexy0C9gtqgK1mmyMxM
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 689
ht-degree: 2%

---

# In-App-Benachrichtigungen {#places-push-messaging}

Die folgenden Informationen zeigen Ihnen, wie Sie In-App-Nachrichten von Places Service-Ereignissen aus für den Trigger konfigurieren.

>[!IMPORTANT]
>
>Die Nachrichten müssen sich in einem Analytics-Treffer befinden.

## In-App-Nachricht

Mit Mobile Services können Sie Standortdaten, die an Analytics gesendet werden, als Trigger-Ereignis(e) und/oder Bedingung für eine In-App-Nachricht verwenden. Wenn In-App-Nachrichten vom SDK ausgelöst werden und nicht auf die Verarbeitung von Daten durch Analytics warten müssen, können die Nachrichten in Echtzeit angezeigt werden, sobald der Trigger auftritt.

### Lokale Benachrichtigungen

Im Folgenden finden Sie eine Liste der verfügbaren In-App-Nachrichtentypen:

* Vollbild
* Warnhinweis
* Lokale Benachrichtigungen

Bei diesen Typen handelt es sich um In-App-Nachrichten, da sie von der SDK ausgelöst werden. Lokale Benachrichtigungen wirken wie Push-Benachrichtigungen, da sie angezeigt werden, wenn die App im Hintergrund angezeigt wird. Diese Benachrichtigungen liefern auch Echtzeitbenachrichtigungen, wenn Benutzende Ihre POIs betreten oder verlassen, während die App im Hintergrund läuft.

### Voraussetzungen

Bevor Sie beginnen, erfahren Sie, wie Sie eine In-App-Nachricht in Mobile Services senden und erstellen und wie Trigger funktionieren. Weitere Informationen finden Sie unter [Erstellen einer In-App-Nachricht.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=de)

## Regeln in Experience Platform Launch

Sie können Experience Platform Launch-Regeln erstellen, die die Daten, die Sie als Teil Ihrer In-App-Regeln für den Nachrichten-Trigger verwenden möchten, an Analytics senden. Sie können Daten aus den Places-Erweiterungen in Ihren Experience Platform Launch-Regeln je nach Anwendungsfall entweder als Ereignisse und/oder als Bedingungen verwenden.

* Verwenden von Standortdaten als auslösendes Ereignis.

  Sie können beispielsweise Daten an Analytics senden, wenn ein Benutzer einen POI eingibt.

* Verwenden von Standortdaten als Bedingung zum Auslösen eines Ereignisses.

  Wenn Sie beispielsweise im Places-Service ein benutzerdefiniertes Metadaten-Tag für das Wetter an verschiedenen POIs erstellt haben, können Sie diese Metadaten als Parameter für Ihre Regelbedingung verwenden. Sie können diese Bedingung zwar mit einem zuvor beschriebenen POI-Eintrittsereignis verwenden, aber auch als Kontext für ein beliebiges Ereignis verwenden.

Nachdem die Regel mit den richtigen Ereignis- und Bedingungsparametern eingerichtet wurde, schließen Sie die Regelkonfiguration ab, indem Sie die Aktion zum Senden von Daten an Analytics konfigurieren.

## Erstellen einer Aktion

So erstellen Sie eine Aktion:

1. Wählen Sie die Erweiterung **[!UICONTROL Adobe Analytics]** aus.
1. Wählen **[!UICONTROL in der Dropdown]** Liste „Aktionstyp“ die Option **[!UICONTROL Verfolgen.]**
1. Geben Sie einen Namen für Ihre Aktion ein.
1. Wählen Sie im rechten Bereich unter **[!UICONTROL Kontextdaten]** das Schlüssel-Wert-Paar aus, um die Kontextdaten festzulegen, die an Analytics gesendet werden.

Sie können beispielsweise `poiname` als Schlüssel und `{%%Last Entered POI Name}` als Wert auswählen.

>[!TIP]
>
>Es können Analytics-Verarbeitungsregeln festgelegt werden, um diese Kontextdaten aufzunehmen. Weitere Informationen finden Sie unter [Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html). Im Beispiel in *Aktion erstellen* sendet die Aktion die `poiname` als Kontext, um das POI-Eintrittsereignis zu beschreiben, das an Analytics gesendet wird.

![Erstellen einer Aktion](/help/assets/configure-action.png)

Im Folgenden finden Sie ein Beispiel für die vollständige Regel:

![Abgeschlossene Regel](/help/assets/create-a-rule.png)

## Erstellen einer In-App-Nachricht in Mobile Services

Als Teil Ihrer Trigger-Parameter können Sie die Zielgruppe für die Nachricht mit Daten aus dem Places-Service auf eine der folgenden Arten erstellen:

* Verwenden von standortspezifischen Aktionen wie einem Ein- oder Ausstieg.
* Verwenden von POI-Metadaten, die als Kontextdaten gesendet werden, um die Zielgruppe einzugrenzen.

  Diese Option kann mit einer ortsspezifischen Aktion wie einem Eintrag verwendet werden oder als Kontext zu einem anderen Ereignis wie einem Launch oder einem Schaltflächen-Klick.

  Im Folgenden finden Sie ein Beispiel für die Konfiguration einer In-App-Nachricht, um Benutzer willkommen zu heißen, die einen POI eingeben, dessen Name {]**}Adobe&quot; enthält:**[!UICONTROL 

  ![Trigger-Parameter](/help/assets/trigger-parameters.png)

* Die Parameter in den Überschriften des Orte-Services auf der Seite *Trigger und Eigenschaften* in Mobile Services funktionieren nicht mit Daten aus dem Orte-Service.

  Diese Parameter gelten nur für die alte Places Service-Datenbank, die in Mobile Services erstellt wurde.
