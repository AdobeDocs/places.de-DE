---
title: Orte testen und validieren
seo-title: Orte testen und validieren
description: Dieser Abschnitt enthält Informationen zum Testen und Validieren von Orten.
seo-description: Dieser Abschnitt enthält Informationen zum Testen und Validieren von Orten.
translation-type: tm+mt
source-git-commit: 39374c1457d33f4cd4014c78fb8daaaa59e5d62d

---


# Empfehlungen zum Testen des Location Service {#test-validate-loc-svc}

Viele Kunden und Organisationen definieren weltweit POIs. Daher ist es wichtig, die Interaktion des Location Service mit Ihrer Anwendung zu simulieren und zu testen.

Anhand dieser Informationen erfahren Sie, wie Sie die Ortsdiensteinträge und -ausstiege testen und validieren, die basierend auf den definierten POIs und dem aktuellen Standort des Benutzers korrekt ausgelöst werden.

Da Umgebungsvariablen ein Faktor für Standortsignal und Genauigkeit sein können, empfehlen wir Ihnen, zunächst die Ausgangsergebnisse zu ermitteln, indem Sie lokal mit Entwicklerwerkzeugen und simulierten Ortseinträgen arbeiten. Das Ziel ist hier zu überprüfen, ob alle Positionsereignisse korrekt funktionieren.

Nach der ordnungsgemäßen Validierung der Positionsereignisse können Lösungsintegrationen (z. B. Analytics, Target und Campaign) getestet werden. Um Ihre Testaktivitäten zu unterstützen, sollten Sie Slack Webhooks mit einem Postback einrichten und GPX-Dateien in Ihrer individuellen Entwicklungsumgebung laden.

>[!IMPORTANT]
>
>Bei diesem Plan wird davon ausgegangen, dass POIs in der Benutzeroberfläche[ für die Verwaltung des ](https://places.adobe.com)Standorts erstellt wurden und die neuesten Versionen der Erweiterungen "Orte"und "Orte-Monitor"installiert und korrekt konfiguriert sind.

| Schritt | Beschreibung | Erwartetes Ergebnis |
|--- |--- |--- |
| 1 | Vergewissern Sie sich, dass die richtigen Manifestschlüssel für Android eingegeben wurden, um Zugriff auf den Verfolgungsort zu gewähren. Weitere Informationen finden Sie unter [Berechtigungen zum Manifest](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest)hinzufügen. | Bestätigt |
| 1a | Bestätigen Sie, dass Ortsaktualisierungen in iOS konfiguriert sind. Vergewissern Sie sich auch, dass in iOS die entsprechenden Plist-Schlüssel eingerichtet sind, um die Berechtigung zum Verfolgen des Speicherorts anzufordern. Weitere Informationen finden Sie unter [Aktivieren von Standortaktualisierungen im Hintergrund.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Bestätigt |
| 2 | Überprüfen Sie, welcher Überwachungsmodus für iOS eingestellt ist. Der kontinuierliche Modus ermöglicht eine höhere Genauigkeit und Persistenz, aber auch eine höhere Akkulaufzeit. Weitere Informationen finden Sie unter [Überwachungsmodus (nur iOS).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Erhebliche Änderungen oder fortlaufend |
| 3 | Wenn Sie mehr als eine POIs-Bibliothek verwenden, bestätigen Sie, dass die entsprechenden Bibliotheken in der Places-Erweiterung für Experience Platform Launch ausgewählt wurden. | Bestätigt |
| 4 | Vergewissern Sie sich, dass die neuesten Versionen der Erweiterungen für den Mobile Core und den Places/Places Monitor mit der App über Gradle- oder CocoaPods gebündelt wurden. | Bestätigt - Weitere Informationen zu aktuellen Updates finden Sie in den [Versionshinweisen.](/help/release-notes.md) |
| 5 | Überprüfen Sie, ob die richtigen Umgebungen für Tests konfiguriert sind. Die ID der Startumgebung sollte mit der Entwicklungsumgebung für Launch übereinstimmen. | Bestätigt |
| 6 | Erstellen Sie GPX-Dateien für jeden POI, den Sie testen möchten. GPX-Dateien können in der lokalen Entwicklungsumgebung zur Simulation eines Ortseintrags verwendet werden. Informationen zum Erstellen und Verwenden von GPX-Dateien finden Sie in den folgenden Abschnitten: <br>[GPX-Dateien für den iOS Simulator [geschlossen]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX-Dateien werden im App-Projekt erstellt und geladen. |
| 7 | Ohne weitere Schritte sollten Sie die Anwendung von Android Studio oder XCode starten und die entsprechende Warnung zum Anfordern des Zugriffs für den Verfolgungsort sehen können. Klicken Sie auf die Berechtigung *Immer zulassen* .<br><br>Es wird empfohlen, ein richtiges Gerät zu verwenden, das mit Ihrem Computer verbunden ist, anstatt den Gerätesimulator zu verwenden. | Die Eingabeaufforderung für Standortanfragen sollte in der Anwendung angezeigt werden, die über IDE geladen wird |
| 8 | Nachdem die Berechtigung "Position"akzeptiert wurde, sollten Sie in der Anwendungskonsole Meldungen anzeigen, die darauf hinweisen, dass `ACPExtensionEventName : requestgetnearbyplaces`aufgerufen wurde. Beim Wechseln zwischen verschiedenen Orten im XCode- oder Android-Studio sollten Einstiegsereignisse für bestimmte POIs entstehen. | `ACPExtensionEventName : requestgetnearbyplaces` angezeigt werden, während Sie verschiedene Orte simulieren. |
| 9 | Wenn sich der ausgewählte Standort in der Nähe der nahe gelegenen POIs befindet, beginnt die Monitorerweiterung, die 20 nächstgelegenen POIs vom aktuellen Standort aus zu überwachen. Die Meldung in der Konsole sieht wie folgt aus: `[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places:`. | Das Wechseln zwischen verschiedenen Orten im XCode- oder Android-Studio sollte zu Einstiegsereignissen für bestimmte POIs führen. |
| 10 | Nachdem Sie die Orts-Monitor-Anzeige in der Nähe gefunden haben, sollten Sie einen Test durchführen, indem Sie Ortsdaten senden. Erstellen Sie unter "Start"eine neue Regel, die die Platzierungserweiterung verwendet, um basierend auf einem Geo-Zaun-Eintrag ausgelöst zu werden. Erstellen Sie dann eine neue Aktion, indem Sie mit Mobile Core einen Postback senden. Durch das Erstellen einer Slack-WebHook-App können Sie Standorteinträge und Ausstiege anzeigen. Weitere Informationen zum Erstellen einer Slack-WebHook-App finden Sie unter [Senden von Nachrichten mit eingehenden Webhooks.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Stellen Sie sicher, dass Sie unter "Start"Datenelemente für die Platzierungserweiterung hinzugefügt haben, darunter Folgendes: <br>Aktueller POI-<br>NameAktueller POI-<br>latAktueller POI-<br>LongLast Entered<br>NameLast Entered<br>latLast Entered<br>longLast Exited<br>nameLast Exited<br>last Exited<br>longTimeStempel |  |
| 10b | Neue Regel mit einem Ereignis erstellen = Orte → POI eingeben |  |
| 10c | Aktion erstellen = Mobile Core → Postback |  |
| 10d | Verwenden Sie die WebHaken-URL für Ihre Slack-App, z. B. https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | Die Stelle wäre ähnlich wie folgt: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Stellen Sie sicher, dass Sie die spezifischen Datenelemente verwenden, die Sie hier erstellt haben. |  |
| 10f | Vergewissern Sie sich, dass Sie alle neuen Datenelement- und Regeländerungen beim Start veröffentlichen. (Sie sollten eine funktionierende Dev-Bibliothek oben rechts auf der Benutzeroberfläche "Starten"auswählen.) |  |
| 11 | Starten und testen Sie Ihre Anwendung erneut, indem Sie zwischen den GPX-Speicherorten in der Entwickler-IDE wechseln. | Sie sollten jetzt Slack-Benachrichtigungen mit Einträgen für jeden POI sehen, wenn Sie verschiedene Orte in Ihrer Entwicklungsumgebung auswählen. |
|  | **SCHNELLE ZUSAMMENFASSUNG**<br>POINTAall diese Tests können lokal durchgeführt werden, ohne einen bestimmten POI-Standort aufsuchen zu müssen. Mit dem Validierungstest wird sichergestellt, dass Ihre Anwendung korrekt konfiguriert ist und die richtigen Berechtigungen für den Speicherort erhalten hat. <br><br>Diese Überprüfung gibt Ihnen auch die Gewissheit, dass die definierten POIs mit der Plates Monitor Extension korrekt funktionieren.  Nach diesem Schritt beginnen wir mit dem Testen von Nachrichten in Campaign, um zu sehen, ob die richtigen Meldungen basierend auf POI-Einstiegen und -Ausstiegen angezeigt werden. |  |
|  | **Testen der In-App-Nachrichten von Adobe Campaign Standard mit dem Location Service.** |  |
| 12 | Konfigurieren Sie im Hauptkampagnen-Dashboard eine neue In-App-Nachricht (type = Broadcast) |  |
| 12a | Wählen Sie in Triggern den Ereignistyp **Orte - Eintrag als Auslöser**. |  |
| 12b | Wählen Sie **[UICONTROL Plates Custom Metadata]** as a additional filter - use POI type = Last Entered POI.<br>Wir verwenden **[!UICONTROL Last Entered]** als POI-Typ, weil in den meisten Fällen, **[!UICONTROL Last Entered]** wird die gleiche wie **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** sollte nur in Fällen verwendet werden, in denen sich die POI-Geozäune überschneiden. In diesem Fall müssen diese POIs RANKED sein, und dann zeigt der POIs mit dem höchsten Rang aus den 2 oder 3 Geozäunen, in denen sich ein Benutzer derzeit befindet, an. **[!UICONTROL Current POI]** |  |
| 12c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, der Ihnen dabei hilft, einzugrenzen, welche POIs eine Nachricht erhalten. |  |
| 12d | Halten Sie für Häufigkeit und Dauer nur ein oder zwei Tage ein, damit Sie den Auslöser in kürzeren Zeiträumen ablaufen können, wenn Sie das Kriterium nicht mögen. |  |
| 12e | Wählen Sie unter "Immer/Einmal"oder "Bis zum Clickthrough" *IMMER* aus, damit Sie mehrere Orte testen können. | Eine In-App-Nachricht wird IMMER angezeigt, wenn Sie eine Ortsänderung simulieren, die die entsprechenden Metadatenkriterien erfüllt. |
| 12f | Wählen Sie für die Anzeige eine andere Option als "Lokale Benachrichtigung". Dies erleichtert das Testen mit der App im Vordergrund.) |  |
| 12g | Bereiten Sie die In-App-Nachricht vor/bestätigen und stellen Sie sie bereit. |  |
| 13 | Um sicherzustellen, dass neue Kampagnenregeln heruntergeladen werden, beenden Sie die Anwendung und starten Sie sie erneut. | Vergessen Sie nicht, dass die Anwendungen erneut vollständig gestartet werden müssen, damit die neue Kampagnen-Regeldatei auf das Gerät heruntergeladen werden kann. |
| 14 | Wechseln Sie in Ihrer Entwicklungsanwendung die Speicherorte mithilfe der zuvor erstellten GPX-Dateien. | Die In-App-Nachricht sollte auf der Grundlage der zuvor festgelegten Kriterien angezeigt werden. |
| 15 | Für den nächsten Test kopieren wir im Wesentlichen die gleichen Schritte wie zuvor, aber diesmal werden wir die LOKALE BENACHRICHTIGUNG testen. | Das erwartete Ergebnis ist, dass die lokalen Benachrichtigungen bei jeder Erfüllung der Kriterien angezeigt werden. |
| 16 | Konfigurieren Sie eine neue In-App-Nachricht (type = Broadcast). |  |
| 16a | Wählen Sie in Auslösern **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**. |  |
| 16b | Wählen Sie die Metadaten "Orte benutzerdefiniert"als zusätzlichen Filter - verwenden **[!UICONTROL POI type]** = **[!UICONTROL Last Entered POI]**. |  |
| 16c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, der Ihnen dabei hilft, einzugrenzen, welche POIs eine Nachricht erhalten. |  |
| 16d | Behalten Sie für Häufigkeit und Dauer nur ein oder zwei Tage bei, damit Sie den Auslöser in kürzeren Zeiträumen ablaufen können, wenn Sie das Kriterium nicht mögen. |  |
| 16e | Für immer/Einmal oder Bis zum Clickthrough, **[!UICONTROL ALWAYS]**. |  |
| 16f | Wählen Sie für den Anzeigetyp **[!UICONTROL Local Notification]**. |  |
| 16g | Bereiten Sie die In-App-Nachricht vor/bestätigen und stellen Sie sie bereit. |  |
| 17 | Schließen Sie das Gerät in der Entwicklungsumgebung an und drücken Sie **[!UICONTROL Play]** die Eingabetaste. Nachdem Sie festgestellt haben, dass dieser Speicherort funktioniert, erstellen Sie einen Hintergrund für die Anwendung und fahren Sie mit dem Umschalten der Speicherorte in Xcode oder Android Studio fort. Es sollten weiterhin Konsolenauswertungen angezeigt werden, die auf die Änderung des Speicherorts hinweisen. Außerdem sollten lokale Benachrichtigungen in Abhängigkeit von den im Auslöser festgelegten Kriterien angezeigt werden. (Es kann eine Verzögerung von 1-2 Sekunden geben.) | Das erwartete Ergebnis ist, dass lokale Benachrichtigungen bei jeder Erfüllung der entsprechenden Kriterien angezeigt werden. |
|  | **ZUSAMMENFASSUNGSPUNKT** In <br>diesem Stadium sollten wir POI-Einträge in unserer Umgebung sehen. Wir sollten auch Nachrichten von Campaign sehen, die auf der POI-Arbeit basieren. Wenn Fehler auftreten, überprüfen Sie, ob eine Meldung über eine fehlende Meldung nicht gesendet wurde. Wenn keine Meldung über den Slot angezeigt wird, überprüfen Sie die Anwendungskonsole, da ein neuer Ortseintrag möglicherweise nicht aufgezeichnet wurde. Wenn die Ergebnisse erfolgreich sind, können wir ziemlich sicher sein, dass die Anwendung korrekt ausgeführt wird und dass der Location Service- und Kampagnen-Nachrichtendienst ebenfalls korrekt funktioniert. |  |
|  | **ON-SITE-TESTS** Beim Testen vor Ort sollte sich <br>nicht viel ändern. Die Aktivierung des Flackerns sollte dabei helfen, zu verstehen, ob das Gerät einen Ein- und Ausstieg für den Ort erhält. |  |
| 18 | Führen Sie Tests mit Geräten aus, die mit WLAN und Mobilgerät deaktiviert beginnen, und aktivieren Sie dann einmal in der POI-Region. | Wenn ein Fehler auftritt, beachten Sie, ob Sie einen Geo-Zaun-Eintrag und eine Benachrichtigung in Slack erhalten. Was ist der Zeitstempel in der Meldung "Slack"? |
| 19 | Führen Sie den Test mit nur zellulärer Aktivierung und mit deaktivierter WLAN-Funktion durch. |  |
| 20 | Führen Sie einen Test mit eingeschaltetem Handy und WLAN durch. |  |
|  | **Der** On-site-Test von ZUSAMMENFASSUNGSPUNKT<br> sollte eng mit dem Entwicklungstest übereinstimmen. Denken Sie daran, dass bei der Ermittlung des Standorts der Benutzer einige Umweltfaktoren zum Tragen kommen können, wie z. B. die Dauer der Besuchszeit in einem POI-Geozaun, die Verfügbarkeit von Zellensignalen und die Stärke von nahegelegenen WLAN-Zugangspunkten. |  |
