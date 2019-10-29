---
title: In-App-Nachrichten
seo-title: In-App-Nachrichten
description: Dieser Abschnitt zeigt Ihnen, wie Sie Orte mit In-App-Nachrichten verwenden.
seo-description: Dieser Abschnitt zeigt Ihnen, wie Sie Orte mit In-App-Nachrichten verwenden.
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# In-App-Benachrichtigungen (#place-push-messaging)

Konfigurieren von In-App-Nachrichten zum Auslösen von Places-Ereignissen; die Nachrichten müssen sich bei einem Analytics-Treffer befinden.

## In-App-Nachricht

Mit AMS können Sie Standortdaten, die an Analytics gesendet werden, als Auslösereignis und/oder Bedingung für eine In-App-Nachricht verwenden. In-App-Nachrichten können dem Benutzer in Echtzeit angezeigt werden, sobald der Auslöser aus dem SDK ausgelöst wird und nicht erst abgewartet werden muss, bis die Daten von Analytics verarbeitet werden.

Lokale Benachrichtigungen: In-App-Nachrichten haben drei verschiedene Typen:

* Vollbild
* Warnhinweis
* Lokale Benachrichtigungen.

Diese Typen gelten als In-App-Nachrichten, da sie vom SDK ausgelöst werden. Beachten Sie jedoch, dass lokale Benachrichtigungen wie Push-Benachrichtigungen aussehen und sich anfühlen, während sich die App nicht im Vordergrund befindet. Lokale Benachrichtigungen sind eine großartige Möglichkeit, um Benutzern Echtzeitbenachrichtigungen zu senden, wenn sie Ihre POIs aufrufen oder verlassen, während sich die App im Hintergrund befindet. Informationen zur Standortüberwachung finden Sie in der Dokumentation zur Platzierungsüberwachung (https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension).

### Voraussetzungen

* Verstehen Sie, wie Sie eine In-App-Nachricht in AMS senden und erstellen und wie Trigger funktionieren.

   Weitere Informationen finden Sie unter [In-App-Nachricht erstellen](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html).


## Regel beim Starten der Erlebnisplattform erstellen

Erstellen Sie Startregeln, die die korrekten Daten an Analytics senden, die Sie als Teil Ihrer In-App-Nachrichten-Auslöserregel(n) verwenden möchten. Sie können Daten aus den Platzierungserweiterungen in Ihren Startregeln je nach Anwendungsfall entweder als Ereignisse und/oder Bedingungen verwenden.

* Verwenden von Positionsdaten als Auslösereignis Wenn Sie beispielsweise Daten an Analytics senden möchten, wenn ein Benutzer einen POI eingibt.

* Verwenden von Standortdaten als Bedingung für ein auslösendes Ereignis Wenn Sie beispielsweise im Location Service ein benutzerdefiniertes Metadaten-Tag für das Wetter an verschiedenen POIs erstellt haben, können Sie diese Metadaten wie unten gezeigt als Parameter für Ihre Regelbedingung verwenden. Obwohl Sie diese Bedingung für das zuvor beschriebene POI-Eingabeereignis verwenden können, können Sie sie auch als Kontext für jedes Ereignis verwenden.

Nachdem die Regel mit den richtigen Ereignis- und Bedingungsparametern eingerichtet wurde, beenden Sie die Regelkonfiguration, indem Sie die Aktion zum Senden von Daten an Analytics konfigurieren. Gehen Sie folgendermaßen vor:

* Adobe Analytics als Erweiterung auswählen
* Wählen Sie "Track"als Aktionstyp
* Namen für die Aktion festlegen
* Legen Sie Kontextdaten fest, die mit dem Ereignis gesendet werden sollen. Verwenden Sie die Benutzeroberfläche "Kontextdaten", um Startdatenelemente den Schlüsselnamen zuzuordnen, die Sie an Analytics senden möchten.

Beachten Sie, dass Analytics-Verarbeitungsregeln so eingestellt werden können, dass diese Kontextdaten aufgenommen werden. Siehe Analytics-Verarbeitungsregeln bei Bedarf (https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html) Diese Aktion sendet beispielsweise den Poiname als Kontext, um das POIentry-Ereignis zu beschreiben, das an Analytics gesendet wird.

![Erstellen einer Aktion](/help/assets/configure-action.png)

Hier ist ein Beispiel dafür, wie die fertige Regel aussehen könnte.

![Abgeschlossene Regel](/help/assets/create-a-rule.png)

## Erstellen einer In-App-Nachricht in AMS:

Sie erstellen die Zielgruppe für die Nachricht mit Daten aus dem Location Service als Teil Ihrer Trigger-Parameter.

* Verwenden standortspezifischer Aktionen wie Einstieg oder Ausstieg
* Verwenden von POI-Metadaten, die als Kontextdaten gesendet werden, um das Ziel Ihrer Zielgruppe einzugrenzen. Dies kann mit einer standortspezifischen Aktion wie "entry"verwendet werden oder als Kontext zu einem anderen Ereignis wie "Launch"oder "button click"verwendet werden.

   Im Folgenden finden Sie ein Beispiel dafür, wie Sie eine In-App-Nachricht einrichten können, um Benutzer aufzunehmen, die einen POI mit "Adobe"im Namen eingeben:

   ![Parameter auslösen](/help/assets/trigger-parameters.png)

* Parameter, die in den Überschriften "Orte"in AMS-Auslösern und -Eigenschaften gefunden werden, funktionieren nicht mit Daten aus dem Location Service. Diese Parameter sind für die alte Places-Datenbank bestimmt, die in AMS erstellt wurde.