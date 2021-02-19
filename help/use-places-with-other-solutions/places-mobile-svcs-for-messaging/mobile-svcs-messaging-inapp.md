---
title: In-App-Benachrichtigungen
description: Dieser Abschnitt zeigt Ihnen, wie Sie den Places-Dienst mit In-App-Nachrichten verwenden.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 4%

---


# In-App-Benachrichtigungen {#places-push-messaging}

Die folgenden Informationen zeigen Ihnen, wie Sie In-App-Nachrichten für Trigger aus den Ereignissen des Orts-Dienstes konfigurieren.

>[!IMPORTANT]
>
>Die Meldungen müssen sich bei einem Analytics-Treffer befinden.

## In-App-Nachricht

Mit Mobile Services können Sie Standortdaten, die an Analytics gesendet werden, als Trigger-Ereignis bzw. -Bedingung für eine In-App-Nachricht verwenden. Wenn In-App-Nachrichten aus dem SDK ausgelöst werden und nicht warten müssen, bis Daten von Analytics verarbeitet werden, können die Meldungen in Echtzeit angezeigt werden, sobald der Trigger eintritt.

### Lokale Benachrichtigungen

Im Folgenden finden Sie eine Liste der verfügbaren In-App-Nachrichtentypen:

* Vollbild
* Warnhinweis
* Lokale Benachrichtigungen

Bei diesen Typen handelt es sich um In-App-Nachrichten, da sie vom SDK ausgelöst werden. Lokale Benachrichtigungen sehen wie Push-Benachrichtigungen aus, da sie angezeigt werden, wenn sich die App im Hintergrund befindet. Diese Benachrichtigungen stellen auch Benachrichtigungen in Echtzeit bereit, wenn Benutzer Ihre POIs eingeben oder verlassen, während sich die App im Hintergrund befindet. Weitere Informationen finden Sie unter [Platzierungsmonitor-Erweiterung](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

### Voraussetzungen

Bevor Sie beginnen, erfahren Sie, wie Sie eine In-App-Nachricht in Mobile Services senden und erstellen und wie Trigger funktionieren. Weitere Informationen finden Sie unter [In-App-Nachrichten erstellen.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regeln in Experience Platform Launch

Sie können Experience Platform Launch-Regeln erstellen, die die Daten senden, die Sie als Teil Ihrer In-App-Nachrichten-Trigger-Regeln verwenden möchten, an Analytics senden. Sie können Daten aus den Platzierungserweiterungen in Ihren Experience Platform Launch-Regeln entweder als Ereignisse und/oder als Bedingungen je nach Anwendungsfall verwenden.

* Verwenden von Standortdaten als auslösendes Ereignis

   Sie können beispielsweise Daten an Analytics senden, wenn ein Benutzer einen POI eingibt.

* Verwenden von Standortdaten als Bedingung für ein auslösendes Ereignis

   Wenn Sie beispielsweise im Orte-Dienst ein benutzerdefiniertes Metadaten-Tag für das Wetter an verschiedenen POIs erstellt haben, können Sie diese Metadaten als Parameter für Ihre Regelbedingung verwenden. Sie können diese Bedingung mit einem zuvor beschriebenen POI-Einstiegscode-Ereignis verwenden. Sie können die Bedingung aber auch als Kontext für jedes beliebige Ereignis verwenden.

Nachdem die Regel mit den richtigen Ereignis- und Bedingungsparametern eingerichtet wurde, schließen Sie die Regelkonfiguration ab, indem Sie die Aktion zum Senden von Daten an Analytics konfigurieren.

## Erstellen einer Aktion

So erstellen Sie eine Aktion:

1. Wählen Sie die Erweiterung **[!UICONTROL Adobe Analytics]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Aktionstyp]** **[!UICONTROL Track.]**
1. Geben Sie einen Namen für die Aktion ein.
1. Wählen Sie im rechten Bereich unter **[!UICONTROL Kontextdaten]** das Schlüssel-Wert-Paar aus, um die Kontextdaten festzulegen, die an Analytics gesendet werden.

Sie können beispielsweise `poiname` als Schlüssel und `{%%Last Entered POI Name}` als Wert auswählen.

>[!TIP]
>
>Analytics-Verarbeitungsregeln können so eingestellt werden, dass diese Kontextdaten aufgenommen werden. Weitere Informationen finden Sie unter [Regeln](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). In dem Beispiel unter *Aktion erstellen* sendet die Aktion das `poiname` als Kontext, um das POI-Eintrags-Ereignis zu beschreiben, das an Analytics gesendet wird.

![Erstellen einer Aktion](/help/assets/configure-action.png)

Hier ein Beispiel für die vollständige Regel:

![Abgeschlossene Regel](/help/assets/create-a-rule.png)

## Erstellen einer In-App-Nachricht in Mobile Services

Als Teil Ihrer Trigger-Parameter können Sie die Audience für die Nachricht mit Daten aus dem Orte-Dienst auf eine der folgenden Arten erstellen:

* Verwenden von standortspezifischen Aktionen wie einem Einstieg oder einem Ausstieg.
* Verwenden von POI-Metadaten, die als Kontextdaten gesendet werden, um die Zielgruppe Ihrer Audience einzuschränken.

   Diese Option kann mit einer standortspezifischen Aktion wie &quot;Eintrag&quot;verwendet werden oder als Kontext zu einem anderen Ereignis wie einem Start oder einem Schaltflächenklick verwendet werden.

   Im Folgenden finden Sie ein Beispiel für die Konfiguration einer In-App-Nachricht, um Benutzer aufzunehmen, die einen POI eingeben, der **[!UICONTROL Adobe]** enthält:

   ![Trigger-Parameter](/help/assets/trigger-parameters.png)

* Die Parameter in den Überschriften &quot;Orte-Dienst&quot;auf der Seite *Trigger und Eigenschaften* in Mobile Services funktionieren nicht mit Daten aus dem Orte-Dienst.

   Diese Parameter gelten nur für die Legacy-Datenbank für den Places-Dienst, die in Mobile Services erstellt wurde.