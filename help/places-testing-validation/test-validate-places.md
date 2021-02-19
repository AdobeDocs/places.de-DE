---
title: Praktikumsdienst testen und validieren
description: Dieser Abschnitt enthält Informationen dazu, wie Sie den Orte-Dienst testen und validieren können.
translation-type: tm+mt
source-git-commit: 954bd9a12ede841d189138dfbe3d65ad4c1bd3c3
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 2%

---


# Recommendations to test Places Service {#test-validate-loc-svc}

Viele Kunden und Organisationen definieren weltweit POIs. Daher ist es wichtig, die Interaktion des Orte-Dienstes mit Ihrer Anwendung zu simulieren und zu testen. Anhand dieser Informationen erfahren Sie, wie Sie die Einträge und Ausstiege des Orts-Dienstes testen und validieren, die basierend auf den definierten POIs und dem aktuellen Standort des Benutzers korrekt ausgelöst werden.

Da Umgebungsvariablen ein Faktor für Standortsignal und Genauigkeit sein können, empfehlen wir Ihnen, zunächst die Ausgangsergebnisse zu ermitteln, indem Sie lokal mit Entwicklerwerkzeugen und simulierten Ortseinträgen arbeiten. Das Ziel besteht darin, zu überprüfen, ob alle Ereignisse am Standort ordnungsgemäß funktionieren. Nach der ordnungsgemäßen Validierung der Ereignis können Lösungsintegrationen (z. B. Analytics, Zielgruppe und Kampagne) getestet werden. Um Ihre Testing-Aktivitäten zu unterstützen, sollten Sie Slack Webhooks mit einem Postback einrichten und GPX-Dateien in Ihrer individuellen Entwicklungs-Umgebung laden.

>[!IMPORTANT]
>
>Bei diesem Plan wird davon ausgegangen, dass POIs in der Benutzeroberfläche des Platzierungsdienstes [erstellt wurden und die neuesten Versionen der Erweiterungen &quot;Orte&quot;und &quot;Orte-Monitor&quot;installiert und korrekt konfiguriert sind. ](https://places.adobe.com) Weitere Informationen finden Sie unter [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md) und [Platzierungsmonitor-Erweiterungen](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

| Schritt | Beschreibung | Erwartetes Ergebnis |
|--- |--- |--- |
| 1 | Vergewissern Sie sich, dass die richtigen Manifestschlüssel für Android eingegeben wurden, um Zugriff auf den Verfolgungsort zu gewähren. Weitere Informationen finden Sie unter [Hinzufügen Berechtigungen für das Manifest](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Bestätigt |
| 1a | Bestätigen Sie, dass Ortsaktualisierungen in iOS konfiguriert sind. Vergewissern Sie sich auch, dass in iOS die entsprechenden Plist-Schlüssel eingerichtet sind, um die Berechtigung zum Verfolgen des Speicherorts anzufordern. Weitere Informationen finden Sie unter [Aktivieren von Standortaktualisierungen im Hintergrund.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Bestätigt |
| 2 | Überprüfen Sie, welcher Überwachungsmodus für iOS eingestellt ist. Der kontinuierliche Modus ermöglicht eine höhere Genauigkeit und Persistenz, aber auch eine höhere Akkulaufzeit. Weitere Informationen finden Sie unter [Überwachungsmodus (nur iOS).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Erhebliche Änderungen oder fortlaufend |
| 3 | Wenn Sie mehr als eine POIs-Bibliothek verwenden, bestätigen Sie, dass die entsprechenden Bibliotheken in der Ortserweiterung für den Experience Platform Launch ausgewählt wurden. | Bestätigt |
| 4 | Vergewissern Sie sich, dass die neuesten Versionen der Erweiterungen für den Mobile Core und den Places/Places Monitor mit der App über Gradle- oder CocoaPods gebündelt wurden. | Bestätigt - Weitere Informationen zu aktuellen Updates finden Sie in den [Versionshinweisen.](/help/release-notes.md) |
| 5 | Vergewissern Sie sich, dass die richtigen Umgebung für den Test konfiguriert sind. Die Umgebung-ID für den Start sollte mit Ihrer Umgebung für die Startentwicklung übereinstimmen. | Bestätigt |
| 6 | Erstellen Sie GPX-Dateien für jeden POI, den Sie testen möchten. GPX-Dateien können in der lokalen Entwicklungs-Umgebung verwendet werden, um einen Ortseintrag zu simulieren. Informationen zum Erstellen und Verwenden von GPX-Dateien finden Sie in den folgenden Abschnitten: <br>[GPX-Dateien für den iOS-Simulator [geschlossen]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[LOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX-Dateien werden im App-Projekt erstellt und geladen. |
| 7 | Ohne weitere Schritte sollten Sie die Anwendung von Android Studio oder XCode starten und die entsprechende Warnung zum Anfordern des Zugriffs für den Verfolgungsort sehen können. Klicken Sie auf die Berechtigung *Immer zulassen*.<br><br>Es wird empfohlen, ein richtiges Gerät zu verwenden, das mit Ihrem Computer verbunden ist, anstatt den Gerätesimulator zu verwenden. | Die Eingabeaufforderung für Standortanfragen sollte in der Anwendung angezeigt werden, die über IDE geladen wird |
| 8 | Sobald die Berechtigung Standort akzeptiert wurde. Das Places SDK ruft die aktuelle Position des Geräts ab und die Platzierungsmonitor-Erweiterung Beginn die Überwachung der 20 nächstgelegenen POIs von der aktuellen Position aus | Siehe Protokollbeispiel unter der Tabelle. |
| 9 | Beim Wechseln zwischen verschiedenen Standorten im XCode- oder Android-Studio sollten für bestimmte POIs Einstiegs-Ereignis erstellt werden. Die folgenden Protokolle werden beim Einstieg in einen POI erwartet. | Siehe Protokollbeispiel unter der Tabelle. |
| 10 | Nachdem Sie die Orts-Monitor-Anzeige in der Nähe gefunden haben, sollten Sie einen Test durchführen, indem Sie Ortsdaten senden. Erstellen Sie unter &quot;Start&quot;eine neue Regel, die die Platzierungserweiterung für den Trigger basierend auf einem Geo-Zaun-Eintrag verwendet. Erstellen Sie dann eine neue Aktion, indem Sie mit Mobile Core einen Postback senden. Wenn Sie eine Slack-WebHook-App erstellen, können Sie Standorteinträge und Ausstiege anzeigen. Weitere Informationen zum Erstellen einer Slack-WebHaken-App finden Sie unter [Senden von Nachrichten mit eingehenden Webhooks.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Stellen Sie sicher, dass Sie unter &quot;Start&quot;Datenelemente für die Platzierungserweiterung hinzugefügt haben, darunter Folgendes: <br>Aktueller POI-Name<br>Aktueller POI-Eintrag<br>Aktuelle POI-Länge<br>Letzte Eingabe<br>Letzte Eingabe<br>Letzte Eingabe<br>Letzter ausstiegter Name<br>Letzte Ausstiegszeit<br>Letzte ausgehende Zeit<br>Zeitstempel |  |
| 10 b | Neue Regel mit einem Ereignis erstellen = Orte → POI eingeben |  |
| 10c | Aktion erstellen = Mobile Core → Postback |  |
| 10 T | Verwenden Sie die WebHook-URL für Ihre Slack-App, z. B. https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | Die Stelle würde Folgendem ähneln: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Stellen Sie sicher, dass Sie die spezifischen Datenelemente verwenden, die Sie hier erstellt haben. |  |
| 10f | Vergewissern Sie sich, dass Sie alle neuen Datenelement- und Regeländerungen beim Start veröffentlichen. (Sie sollten eine funktionierende Dev-Bibliothek oben rechts auf der Benutzeroberfläche &quot;Starten&quot;auswählen.) |  |
| 11 | Starten und testen Sie Ihre Anwendung erneut, indem Sie zwischen den GPX-Speicherorten in der Entwickler-IDE wechseln. | Sie sollten nun Slack-Benachrichtigungen mit Einträgen für jeden POI anzeigen, wenn Sie verschiedene Orte in Ihrer Umgebung auswählen. |
|  | **SCHNELLE ZUSAMMENFASSUNG**<br> POINTAall diese Tests können lokal durchgeführt werden, ohne einen bestimmten POI-Standort aufsuchen zu müssen. Mit dem Validierungstest wird sichergestellt, dass Ihre Anwendung korrekt konfiguriert ist und die richtigen Berechtigungen für den Speicherort erhalten hat. <br><br>Diese Überprüfung gibt Ihnen auch die Gewissheit, dass die definierten POIs mit der Plates Monitor Extension korrekt funktionieren.  Nach diesem Schritt beginnen wir mit dem Testen von Nachrichten in der Kampagne, um zu sehen, ob die richtigen Meldungen basierend auf POI-Einstiegen und -Ausstiegen angezeigt werden. |  |
|  | **Testen von Adobe Campaign Standard-In-App-Nachrichten mit dem Places-Dienst.** |  |
| 12 | Konfigurieren Sie im Hauptfenster der Kampagne eine neue In-App-Nachricht (Typ = Broadcast) |  |
| 12a | Wählen Sie in den Triggern **Platzierungs-Ereignistyp - Eintrag als Trigger**. |  |
| 12 b | Wählen Sie **[!UICONTROL Platziert benutzerspezifische Metadaten]** als zusätzlichen Filter - POI-Typ = Letzter eingegebener POI verwenden.<br>Wir verwenden  **[!UICONTROL Last]** Enteredas den POI-Typ, da in den meisten Fällen  **[!UICONTROL Last]** Entered mit  **[!UICONTROL Current POI]** identisch sein wird. <br><br>**[!UICONTROL Aktuelle ]**POIs sollten nur in Fällen verwendet werden, in denen es überlappende POI-Geozäune gibt. In diesem Fall müssen diese POIs RANKED sein, und dann zeigt der**[!UICONTROL  Aktuelle POI ]**den POI mit der höchsten Rangfolge der 2 oder 3 Geozäune an, in denen sich ein Benutzer derzeit befindet. |  |
| 12c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, der Ihnen dabei hilft, einzugrenzen, welche POIs eine Nachricht erhalten. |  |
| 12 T | Halten Sie für Häufigkeit und Dauer nur ein oder zwei Tage ein, damit Sie den Trigger in kürzerer Zeit ablaufen können, wenn Sie das Kriterium nicht mögen. |  |
| 12e | Wählen Sie unter &quot;Immer/Einmal&quot;oder &quot;Bis zum Clickthrough&quot;die Option *IMMER* aus, damit Sie mehrere Orte testen können. | Eine In-App-Nachricht wird IMMER angezeigt, wenn Sie eine Ortsänderung simulieren, die die entsprechenden Metadatenkriterien erfüllt. |
| 12f | Wählen Sie für die Anzeige eine andere Option als &quot;Lokale Benachrichtigung&quot;. Dies erleichtert das Testen mit der App im Vordergrund.) |  |
| 12g | Bereiten Sie die In-App-Nachricht vor/bestätigen und stellen Sie sie bereit. |  |
| 13 | Um sicherzustellen, dass neue Kampagne-Umgebung heruntergeladen werden, beenden Sie die Anwendung und starten Sie sie erneut. | Vergessen Sie nicht, dass die Kampagne erneut vollständig gestartet werden muss, damit die neue Regeldatei auf das Gerät heruntergeladen werden kann. |
| 14 | Wechseln Sie in Ihrer Entwicklungsanwendung die Speicherorte mithilfe der zuvor erstellten GPX-Dateien. | Die In-App-Nachricht sollte auf der Grundlage der zuvor festgelegten Kriterien angezeigt werden. |
| 15 | Für den nächsten Test kopieren wir im Wesentlichen die gleichen Schritte wie zuvor, aber diesmal werden wir die LOKALE BENACHRICHTIGUNG testen. | Das erwartete Ergebnis ist, dass die lokalen Benachrichtigungen bei jeder Erfüllung der Kriterien angezeigt werden. |
| 16 | Konfigurieren Sie eine neue In-App-Nachricht (type = Broadcast). |  |
| 16a | Wählen Sie in den Triggern **[!UICONTROL Platzierte Ereignistyp]** - **[!UICONTROL Eintrag als Trigger]**. |  |
| 16 b | Wählen Sie die Metadaten &quot;Orte benutzerdefiniert&quot;als zusätzlichen Filter - verwenden Sie **[!UICONTROL POI-Typ]** = **[!UICONTROL Letzte eingegebene POI]**. |  |
| 16c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, der Ihnen dabei hilft, einzugrenzen, welche POIs eine Nachricht erhalten. |  |
| 16 T | Behalten Sie für Häufigkeit und Dauer nur ein oder zwei Tage bei, damit Sie den Trigger in kürzeren Zeiträumen ablaufen können, wenn Sie das Kriterium nicht mögen. |  |
| 16e | Für immer/Einmal oder Bis zum Clickthrough **[!UICONTROL IMMER]**. |  |
| 16f | Wählen Sie für den Anzeigetyp **[!UICONTROL Lokale Benachrichtigung]**. |  |
| 16g | Bereiten Sie die In-App-Nachricht vor/bestätigen und stellen Sie sie bereit. |  |
| 17 | Schließen Sie in der Developer-Umgebung das Gerät an und drücken Sie auf **[!UICONTROL Play]**. Nachdem Sie festgestellt haben, dass dieser Speicherort funktioniert, erstellen Sie einen Hintergrund für die Anwendung und fahren Sie mit dem Umschalten der Speicherorte in Xcode oder Android Studio fort. Es sollten weiterhin Konsolenauswertungen angezeigt werden, die auf die Standortänderung hinweisen, und je nach den in Ihrem Trigger festgelegten Kriterien sollten auch lokale Benachrichtigungen angezeigt werden. (Es kann eine Verzögerung von 1-2 Sekunden geben.) | Das erwartete Ergebnis ist, dass lokale Benachrichtigungen jedes Mal angezeigt werden, wenn die entsprechenden Kriterien erfüllt sind. |
|  | **ZUSAMMENFASSUNG** <br>POINTAt in dieser Phase sollten wir POI-Einträge in unserer örtlichen Umgebung sehen. Wir sollten auch Nachrichten aus der Kampagne sehen, die auf der Arbeit des POI basieren. Wenn Fehler auftreten, überprüfen Sie, ob eine Slack-Benachrichtigung nicht gesendet wurde. Wenn keine Slack-Meldung vorhanden ist, überprüfen Sie die Anwendungskonsole, da ein neuer Ortseintrag möglicherweise nicht aufgezeichnet wurde. Wenn die Ergebnisse erfolgreich sind, können wir ziemlich sicher sein, dass die Anwendung korrekt ausgeführt wird und dass der Orteservice und der Kampagne-Nachrichtendienst ebenfalls korrekt funktionieren. |  |
|  | **ON-SITE** <br>TESTINGNetliche Änderungen sollten beim Testen am Standort vorgenommen werden. Die Aktivierung des Flackerns sollte dabei helfen, zu verstehen, ob das Gerät einen Ein- und Ausstieg für den Ort erhält. |  |
| 18 | Führen Sie Tests mit Geräten aus, die mit WLAN und Mobilgerät deaktiviert beginnen, und aktivieren Sie dann einmal in der POI-Region. | Wenn ein Fehler auftritt, beachten Sie, ob Sie einen Geo-Zaun-Eintrag und eine Benachrichtigung in Slack erhalten. Was ist der Zeitstempel in der Benachrichtigung des Slacks? |
| 19 | Führen Sie den Test mit nur zellulärer Aktivierung und mit deaktivierter WLAN-Funktion durch. |  |
| 20 | Führen Sie einen Test mit eingeschaltetem Handy und WLAN durch. |  |
|  | **Die** <br>Tests der ZUSAMMENFASSUNG POINTOn-Site sollten eng mit den Entwicklungstests übereinstimmen. Denken Sie daran, dass bei der Ermittlung des Standorts der Benutzer einige Umweltfaktoren zum Tragen kommen können, wie z. B. die Dauer der Besuchszeit in einem POI-Geozaun, die Verfügbarkeit von Zellensignalen und die Stärke von nahegelegenen WiFi-Zugangspunkten. |  |

## Protokollbeispiele

**Schritt 8:** Erwartete iOS- und Android-Protokolle während einer Ortsaktualisierung

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**Schritt 9:** Erwartete iOS- und Android-Protokolle während eines Ereignisses

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
