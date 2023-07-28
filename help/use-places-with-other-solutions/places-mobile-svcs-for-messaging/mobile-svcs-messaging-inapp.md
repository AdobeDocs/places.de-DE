---
title: In-App-Benachrichtigungen
description: In diesem Abschnitt erfahren Sie, wie Sie den Places-Dienst mit In-App-Nachrichten verwenden.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 4%

---

# In-App-Benachrichtigungen {#places-push-messaging}

Die folgenden Informationen zeigen Ihnen, wie Sie In-App-Nachrichten für Trigger über Places Service-Ereignisse konfigurieren.

>[!IMPORTANT]
>
>Die Nachrichten müssen sich auf einen Analytics-Treffer beziehen.

## In-App-Nachricht

Mit Mobile Services können Sie Standortdaten verwenden, die an Analytics als Trigger-Ereignis(e) und/oder Bedingung für eine In-App-Nachricht gesendet werden. Wenn In-App-Nachrichten aus dem SDK ausgelöst werden und nicht warten müssen, bis Daten von Analytics verarbeitet werden, können die Nachrichten in Echtzeit angezeigt werden, sobald der Trigger auftritt.

### Lokale Benachrichtigungen

Im Folgenden finden Sie eine Liste der verfügbaren In-App-Nachrichtentypen:

* Vollbild
* Warnhinweis
* Lokale Benachrichtigungen

Diese Typen sind In-App-Nachrichten, da sie vom SDK ausgelöst werden. Lokale Benachrichtigungen wirken wie Push-Benachrichtigungen, da sie im Hintergrund angezeigt werden. Diese Benachrichtigungen senden auch Echtzeitbenachrichtigungen, wenn Benutzer Ihre POIs aufrufen oder beenden, während sich die App im Hintergrund befindet.

### Voraussetzungen

Bevor Sie beginnen, wissen Sie, wie Sie eine In-App-Nachricht in Mobile Services senden und erstellen und wie Trigger funktionieren. Weitere Informationen finden Sie unter [In-App-Nachrichten erstellen.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html)

## Regeln in Experience Platform Launch

Sie können Experience Platform Launch-Regeln erstellen, die die Daten senden, die Sie als Teil Ihrer Regeln für den Trigger von In-App-Nachrichten verwenden möchten, an Analytics senden. Je nach Anwendungsfall können Sie Daten aus den Places-Erweiterungen in Ihren Experience Platform Launch-Regeln entweder als Ereignisse und/oder als Bedingungen verwenden.

* Verwendung von Standortdaten als Auslöserereignis.

  Beispielsweise können Sie Daten an Analytics senden, wenn ein Benutzer einen POI aufruft.

* Verwendung von Standortdaten als Bedingung für ein auslösendes Ereignis.

  Wenn Sie beispielsweise im Places-Dienst ein benutzerdefiniertes Metadaten-Tag für das Wetter an verschiedenen POIs erstellt haben, können Sie diese Metadaten als Parameter für Ihre Regelbedingung verwenden. Sie können diese Bedingung zwar mit einem zuvor beschriebenen POI-Eintrittsereignis verwenden, Sie können die Bedingung aber auch als Kontext für jedes Ereignis verwenden.

Nachdem die Regel mit den richtigen Ereignis- und Bedingungsparametern eingerichtet wurde, schließen Sie die Regelkonfiguration ab, indem Sie die Aktion konfigurieren, um Daten an Analytics zu senden.

## Erstellen einer Aktion

So erstellen Sie eine Aktion:

1. Wählen Sie die **[!UICONTROL Adobe Analytics]** -Erweiterung.
1. Im **[!UICONTROL Aktionstyp]** Dropdown-Liste auswählen **[!UICONTROL Verfolgen Sie.]**
1. Geben Sie einen Namen für Ihre Aktion ein.
1. Im rechten Bereich, in **[!UICONTROL Kontextdaten]** wählen Sie das Schlüssel-Wert-Paar aus, um die Kontextdaten festzulegen, die an Analytics gesendet werden.

Sie können beispielsweise `poiname` als Schlüssel und `{%%Last Entered POI Name}` als Wert.

>[!TIP]
>
>Analytics-Verarbeitungsregeln können so eingestellt werden, dass sie diese Kontextdaten abrufen. Weitere Informationen finden Sie unter [Regeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html). Im Beispiel in *Erstellen einer Aktion*, sendet die Aktion `poiname` als Kontext zur Beschreibung des POI-Eintrittsereignisses, das an Analytics gesendet wird.

![Erstellen einer Aktion](/help/assets/configure-action.png)

Im Folgenden finden Sie ein Beispiel für die vollständige Regel:

![abgeschlossene Regel](/help/assets/create-a-rule.png)

## In-App-Nachricht in Mobile Services erstellen

Im Rahmen Ihrer Trigger-Parameter können Sie die Zielgruppe für die Nachricht mit Daten aus dem Places-Dienst auf eine der folgenden Arten erstellen:

* Verwendung standortspezifischer Aktionen wie Einstiege oder Ausstiege
* Verwendung von POI-Metadaten, die als Kontextdaten gesendet werden, um das Ziel Ihrer Zielgruppe einzuschränken.

  Diese Option kann mit einer standortspezifischen Aktion wie &quot;Eintrag&quot;verwendet werden oder als Kontext zu einem anderen Ereignis wie einem Launch oder einem Schaltflächenklick.

  Im Folgenden finden Sie ein Beispiel für die Konfiguration einer In-App-Nachricht, um Benutzer willkommen zu heißen, die einen POI mit **[!UICONTROL Adobe]** im Namen:

  ![Trigger-Parameter](/help/assets/trigger-parameters.png)

* Parameter in den Überschriften der Places Service im *Trigger und Eigenschaften* -Seite in Mobile Services funktionieren nicht mit Daten aus dem Places-Dienst.

  Diese Parameter gelten nur für die alte Places Service-Datenbank, die in Mobile Services erstellt wurde.
