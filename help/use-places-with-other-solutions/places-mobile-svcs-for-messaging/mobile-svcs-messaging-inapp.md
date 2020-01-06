---
title: In-App-Benachrichtigungen
description: Dieser Abschnitt zeigt Ihnen, wie Sie Orte mit In-App-Nachrichten verwenden.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# In-App-Benachrichtigungen (#place-push-messaging)

Die folgenden Informationen zeigen Ihnen, wie In-App-Nachrichten so konfiguriert werden, dass sie von Places-Ereignissen ausgelöst werden.

>[!IMPORTANT]
>
>Die Meldungen müssen sich bei einem Analytics-Treffer befinden.

## In-App-Nachricht

Mit Mobile Services können Sie Standortdaten, die an Analytics gesendet werden, als Auslösereignis und/oder Bedingung für eine In-App-Nachricht verwenden. Wenn In-App-Nachrichten aus dem SDK ausgelöst werden und nicht warten müssen, bis Daten von Analytics verarbeitet werden, können die Nachrichten in Echtzeit angezeigt werden, sobald der Auslöser eintritt.

### Lokale Benachrichtigungen

Im Folgenden finden Sie eine Liste der verfügbaren In-App-Nachrichtentypen:

* Vollbild
* Warnhinweis
* Lokale Benachrichtigungen

Diese Typen sind In-App-Nachrichten, da sie vom SDK ausgelöst werden. Lokale Benachrichtigungen sehen wie Push-Benachrichtigungen aus, da sie angezeigt werden, wenn sich die App im Hintergrund befindet. Diese Benachrichtigungen stellen auch Benachrichtigungen in Echtzeit bereit, wenn Benutzer Ihre POIs eingeben oder verlassen, während sich die App im Hintergrund befindet. Weitere Informationen finden Sie unter [Platzierungsmonitor-Erweiterung](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

### Voraussetzungen 

Bevor Sie beginnen, erfahren Sie, wie Sie eine In-App-Nachricht in Mobile Services senden und erstellen und wie Auslöser funktionieren. Weitere Informationen finden Sie unter [In-App-Nachricht erstellen.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regeln in Experience Platform Launch

Sie können Startregeln erstellen, die die Daten senden, die Sie als Teil Ihrer In-App-Nachrichten-Auslöserregeln für Analytics verwenden möchten. Sie können Daten aus den Platzierungserweiterungen in Ihren Startregeln je nach Anwendungsfall entweder als Ereignisse und/oder Bedingungen verwenden.

* Verwenden von Positionsdaten als Auslösereignis

   Sie können beispielsweise Daten an Analytics senden, wenn ein Benutzer einen POI eingibt.

* Verwenden von Standortdaten als Bedingung für ein auslösendes Ereignis

   Wenn Sie beispielsweise im Location Service ein benutzerdefiniertes Metadaten-Tag für das Wetter an verschiedenen POIs erstellt haben, können Sie diese Metadaten als Parameter für Ihre Regelbedingung verwenden. Sie können diese Bedingung zwar mit einem zuvor beschriebenen POI-Eingabeereignis verwenden, Sie können die Bedingung aber auch als Kontext für jedes Ereignis verwenden.

Nachdem die Regel mit den richtigen Ereignis- und Bedingungsparametern eingerichtet wurde, schließen Sie Ihre Regelkonfiguration ab, indem Sie die Aktion zum Senden von Daten an Analytics konfigurieren.

## Erstellen einer Aktion

So erstellen Sie eine Aktion:

1. Wählen Sie die **[!UICONTROL Adobe Analytics]**-Erweiterung aus.
1. Wählen Sie in der **[!UICONTROL Action type]**Dropdownliste**[!UICONTROL Track.]**
1. Geben Sie einen Namen für die Aktion ein.
1. Wählen Sie im rechten Bereich **[!UICONTROL Context Data]**das Schlüssel-Wert-Paar aus, um die Kontextdaten festzulegen, die an Analytics gesendet werden.

Sie können beispielsweise `poiname` als Schlüssel und `{%%Last Entered POI Name}` als Wert auswählen.

>[!TIP]
>
>Analytics-Verarbeitungsregeln können so eingestellt werden, dass diese Kontextdaten aufgenommen werden. Weitere Informationen finden Sie unter [Regeln](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). In dem Beispiel unter *Aktion* erstellen sendet die Aktion den `poiname` als Kontext, um das POI-Eingabeereignis zu beschreiben, das an Analytics gesendet wird.

![Erstellen einer Aktion](/help/assets/configure-action.png)

Hier ein Beispiel für die vollständige Regel:

![Abgeschlossene Regel](/help/assets/create-a-rule.png)

## Erstellen einer In-App-Nachricht in Mobile Services

Als Teil Ihrer Auslöserparameter können Sie die Zielgruppe für die Nachricht mit Daten aus dem Location Service auf eine der folgenden Arten erstellen:

* Verwenden von standortspezifischen Aktionen wie einem Einstieg oder einem Ausstieg.
* Verwenden von POI-Metadaten, die als Kontextdaten gesendet werden, um das Ziel Ihrer Zielgruppe einzugrenzen.

   Diese Option kann mit einer standortspezifischen Aktion wie &quot;Eintrag&quot;verwendet werden oder als Kontext zu einem anderen Ereignis wie einem Start- oder Schaltflächenklick verwendet werden.

   Im Folgenden finden Sie ein Beispiel, wie Sie eine In-App-Nachricht konfigurieren, um Benutzer aufzunehmen, die einen POI mit **[!UICONTROL Adobe]**dem Namen eingeben:

   ![Parameter auslösen](/help/assets/trigger-parameters.png)

* Parameter in den Überschriften &quot;Orte&quot;auf der Seite &quot; *Auslöser und Eigenschaften* &quot;in Mobile Services funktionieren nicht mit Daten aus dem Location Service.

   Diese Parameter gelten nur für die alte Places-Datenbank, die in Mobile Services erstellt wurde.