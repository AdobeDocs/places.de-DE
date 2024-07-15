---
title: Testen und Validieren des Places-Dienstes
description: In diesem Abschnitt finden Sie Informationen dazu, wie Sie den Places-Dienst testen und überprüfen können.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 1%

---

# Recommendations zum Testen des Places-Dienstes {#test-validate-loc-svc}

Viele Kunden und Organisationen definieren Zielpunkte auf der ganzen Welt. Daher ist es wichtig, die Interaktion des Places-Dienstes mit Ihrer Anwendung zu simulieren und zu testen. Diese Informationen helfen Ihnen dabei, zu verstehen, wie Sie die Einstiege und Ausstiege des Places-Dienstes testen und überprüfen können, die basierend auf den definierten Zielpunkten und dem aktuellen Standort eines Benutzers korrekt ausgelöst werden.

Da Umgebungsvariablen ein Faktor für Standortsignal und Genauigkeit sein können, empfehlen wir, dass Sie zunächst Ausgangsergebnisse erstellen, indem Sie lokal mit Entwicklertools und simulierten Standorteinträgen arbeiten. Das Ziel besteht darin zu überprüfen, ob alle Standortereignisse ordnungsgemäß funktionieren. Nachdem die Standortereignisse korrekt validiert wurden, können Lösungsintegrationen (z. B. Analytics, Target und Campaign) getestet werden. Um Ihre Testaktivitäten zu unterstützen, sollten Sie Slack Webhooks mit einem Postback einrichten und GPX-Dateien in Ihre individuelle Entwicklungsumgebung laden.

>[!IMPORTANT]
>
>In diesem Plan wird davon ausgegangen, dass POIs in der Benutzeroberfläche von [Places Service](https://places.adobe.com) erstellt wurden und die neuesten Versionen der Places-Erweiterung installiert und korrekt konfiguriert sind. Bei der aktiven Regionsüberwachung wird außerdem davon ausgegangen, dass eine Regionsüberwachungslösung implementiert ist. Weitere Informationen finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md), [CoreLocation-Dokumentation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Dokumentation zum Android-Speicherort](https://developer.android.com/training/location/geofencing).

| Schritt | Beschreibung | Erwartetes Ergebnis |
|--- |--- |--- |
| 1 | Vergewissern Sie sich, dass die richtigen Manifestschlüssel für Android eingegeben wurden, um Zugriff auf den Tracking-Speicherort zu gewähren. | Bestätigt |
| 1a | Bestätigen Sie, dass die Standortaktualisierungen in iOS konfiguriert sind. Stellen Sie außerdem sicher, dass Sie in iOS die entsprechenden plist-Schlüssel eingerichtet haben, um die Benutzerberechtigung zum Tracking des Standorts anzufordern. | Bestätigt |
| 2 | Überprüfen Sie, welcher Überwachungsmodus für iOS festgelegt ist. Der kontinuierliche Modus ermöglicht höhere Genauigkeit und Persistenz, aber auch eine höhere Akkulaufzeit. | Erhebliche Änderungen oder fortlaufend |
| 3 | Wenn Sie mehr als eine POIs-Bibliothek verwenden, überprüfen Sie, ob die entsprechenden Bibliotheken in der Places-Erweiterung für Experience Platform Launch ausgewählt wurden. | Bestätigt |
| 4 | Vergewissern Sie sich, dass die neuesten Versionen der Mobile Core- und Places-Erweiterungen mit der App über Gradle oder CocoaPods gepackt wurden. | Bestätigt - Weitere Informationen zu aktuellen Aktualisierungen finden Sie in den [Versionshinweisen](/help/release-notes.md) . |
| 5 | Vergewissern Sie sich, dass die richtigen Umgebungen für Tests konfiguriert sind. Die Launch-Umgebungs-ID sollte mit Ihrer Launch-Entwicklungsumgebung übereinstimmen. | Bestätigt |
| 6 | Erstellen Sie GPX-Dateien für jeden POI, den Sie testen möchten. GPX-Dateien können in der lokalen Entwicklungsumgebung verwendet werden, um einen Standorteintrag zu simulieren. Informationen zum Erstellen und Verwenden von GPX-Dateien finden Sie unter: <br>[GPX-Dateien für iOS Simulator [geschlossen]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[LOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX-Dateien werden im App-Projekt erstellt und geladen. |
| 7 | Ohne andere Aktionen sollten Sie in der Lage sein, die Anwendung von Android Studio oder XCode aus zu starten und den entsprechenden Warnhinweis anzuzeigen, um den Zugriff für den Tracking-Speicherort anzufordern. Klicken Sie auf die Berechtigung *Immer zulassen* .<br><br>Wir empfehlen, anstelle des Gerätesimulators ein echtes Gerät zu verwenden, das mit Ihrem Computer verbunden ist. | Die Eingabeaufforderung zur Standortanforderung sollte in der Anwendung angezeigt werden, die über IDE geladen wird |
| 8 | Sobald die Berechtigung Standort akzeptiert wurde. Das Places-SDK ruft die aktuelle Position des Geräts ab und der Regions-Überwachungscode sollte mit der Überwachung der 20 nächstgelegenen POIs vom aktuellen Standort beginnen | Siehe Protokollbeispiel unter der Tabelle. |
| 9 | Beim Wechseln zwischen verschiedenen Standorten in XCode oder Android Studio sollten Eintrittsereignisse für bestimmte POIs generiert werden. Die folgenden Logs werden beim Einstieg in einen POI erwartet. | Siehe Protokollbeispiel unter der Tabelle. |
| 10 | Nachdem der Regionsmonitor nahe gelegene POIs gefunden hat, sollten Sie testen, indem Sie Standortpfade senden. Erstellen Sie in Launch eine neue Regel, die die Places-Erweiterung für den Trigger basierend auf einem Geofeneintrag verwendet. Erstellen Sie dann eine neue Aktion, indem Sie mit Mobile Core einen Postback senden. Wenn Sie eine Slack Webhook-App erstellen, können Sie Standorteinstiege und -ausstiege anzeigen. Informationen zum Erstellen einer Slack Webhook-App finden Sie unter [Senden von Nachrichten mit eingehenden Webhooks.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Stellen Sie in Launch sicher, dass Sie Datenelemente für die Places-Erweiterung hinzugefügt haben, einschließlich: <br>Aktueller POI-Name<br>Aktueller POI lat<br>Aktueller POI long<br>Letzter Einstiegsname<br>Letzte Eingabe am letzten Tag<br>Letzter Ausstiegsname<br>Letzter Ausstiegsname<br>Letzter Ausstieg am letzten Tag<br>Lange<br>Zeitstempel |  |
| 10b | Erstellen Sie eine neue Regel mit Ereignis = Places → POI eingeben |  |
| 10c | Erstellen einer Aktion = Mobile Core → Postback |  |
| 10 T | Verwenden Sie die Webhook-URL für Ihre Slack-App, z. B. https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | Der Post-Body wäre ähnlich wie: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Stellen Sie sicher, dass Sie die spezifischen Datenelemente verwenden, die Sie hier erstellt haben. |  |
| 10f | Stellen Sie sicher, dass Sie alle neuen Datenelement- und Regeländerungen in Launch veröffentlichen. (Sie sollten oben rechts auf der Launch-Oberfläche eine funktionierende Entwicklungsbibliothek auswählen.) |  |
| 11 | Starten und testen Sie Ihre Anwendung erneut, indem Sie zwischen den GPX-Speicherorten in der Entwickler-IDE wechseln. | Sie sollten jetzt Slack-Benachrichtigungen sehen, die Einträge für jeden POI anzeigen, wenn Sie verschiedene Orte in Ihrer Entwicklungsumgebung auswählen. |
|  | **QUICK-ZUSAMMENFASSUNGSPUNKT**<br> Alle diese Tests können lokal durchgeführt werden, ohne dass ein bestimmter POI-Standort aufgerufen werden muss. Mithilfe von Validierungstests kann sichergestellt werden, dass Ihre Anwendung korrekt konfiguriert ist und über die richtigen Berechtigungen für den Speicherort verfügt. <br><br>Durch diese Validierung können Sie außerdem sicherstellen, dass die definierten Zielpunkte ordnungsgemäß mit Ihrer Implementierung der regionalen Überwachung funktionieren.  Danach werden wir mit dem Testen von Nachrichten in Campaign beginnen, um zu sehen, ob die richtigen Nachrichten basierend auf POI-Einstiegen und -Ausstiegen angezeigt werden. |  |
|  | **Testen von Adobe Campaign Standard-In-App-Nachrichten mit dem Places-Dienst.** |  |
| 12 | Konfigurieren Sie im Hauptkampagnen-Dashboard eine neue In-App-Nachricht (Typ = broadcast). |  |
| 12a | Wählen Sie in Trigger **Places-Ereignistyp - Eintrag als Trigger** aus. |  |
| 12b | Wählen Sie **[!UICONTROL Places Custom Metadata]** als zusätzlichen Filter - use POI type = Last Entered POI.<br>Wir verwenden **[!UICONTROL Letzte Eingabe]** als POI-Typ, da in den meisten Fällen **[!UICONTROL Letzte Eingabe]** mit dem **[!UICONTROL Aktueller POI]** übereinstimmt. <br><br>**[!UICONTROL Aktueller POI ]**sollte nur in Fällen verwendet werden, in denen sich die POI-Geofense überschneiden. In diesem Fall müssen diese POIs mit Rang versehen werden, und dann zeigt der**[!UICONTROL  aktuelle POI ]**den POI mit der höchsten Rangfolge von den 2 oder 3 Geofencing, in dem sich ein Benutzer derzeit befindet. |  |
| 12c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, mit dem Sie eingrenzen können, welche Zielpunkte eine Nachricht erhalten. |  |
| 12 T | Halten Sie für Häufigkeit und Dauer nur ein oder zwei Tage ein, damit Sie den Trigger in einem kürzeren Zeitraum ablaufen können, wenn Ihnen das Kriterium nicht gefällt. |  |
| 12e | Wählen Sie für Immer/Einmal oder Bis zum Clickthrough *IMMER* aus, damit Sie mehrere Orte testen können. | Eine In-App-Nachricht wird IMMER angezeigt, wenn Sie eine Standortänderung simulieren, die den entsprechenden Metadatenkriterien entspricht. |
| 12f | Wählen Sie für die Anzeige eine andere Option als &quot;Lokale Benachrichtigung&quot;. Dies erleichtert das Testen mit der App im Vordergrund.) |  |
| 12g | Bereiten Sie die In-App-Nachricht vor/bestätigen und stellen Sie sie bereit. |  |
| 13 | Beenden Sie in Ihrer Entwicklungsumgebung die Anwendung, um sicherzustellen, dass neue Kampagnenregeln heruntergeladen werden, und starten Sie sie erneut. | Vergessen Sie nicht, dass die Anwendungen vollständig neu gestartet werden müssen, damit die neue Datei mit den Campaign-Regeln auf das Gerät heruntergeladen werden kann. |
| 14 | Wechseln Sie in Ihrer Entwicklungsanwendung die Speicherorte mithilfe der zuvor erstellten GPX-Dateien. | Sie sollten sehen, dass die In-App-Nachricht basierend auf den zuvor festgelegten Kriterien angezeigt wird. |
| 15 | Für den nächsten Test werden wir im Wesentlichen die gleichen Schritte wie zuvor kopieren, aber diesmal testen wir die LOKALE BENACHRICHTIGUNG. | Das erwartete Ergebnis ist, dass die lokalen Benachrichtigungen bei jeder Erfüllung der Kriterien angezeigt werden. |
| 16 | Konfigurieren Sie eine neue In-App-Nachricht (Typ = broadcast). |  |
| 16a | Wählen Sie in Trigger **[!UICONTROL Places event type]** - **[!UICONTROL Entry als Trigger]** aus. |  |
| 16b | Wählen Sie die Metadaten Places Custom als zusätzlichen Filter aus - verwenden Sie **[!UICONTROL POI-Typ]** = **[!UICONTROL Letzter eingegebener POI]**. |  |
| 16c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, mit dem Sie eingrenzen können, welche Zielpunkte eine Nachricht erhalten. |  |
| 16 T | Bewahren Sie für Häufigkeit und Dauer nur ein oder zwei Tage auf, damit Sie den Trigger in kürzerer Zeit ablaufen können, wenn Ihnen das Kriterium nicht gefällt. |  |
| 16e | Für immer/Einmal oder Bis zum Clickthrough **[!UICONTROL IMMER]**. |  |
| 16f | Wählen Sie für den Anzeigetyp **[!UICONTROL Lokale Benachrichtigung]** aus. |  |
| 16g | Bereiten Sie die In-App-Nachricht vor/bestätigen und stellen Sie sie bereit. |  |
| 17 | Verbinden Sie das Gerät in der Entwicklungsumgebung und drücken Sie auf **[!UICONTROL Abspielen]** im Build. Nachdem Sie festgestellt haben, dass der Speicherort funktioniert, hinterlegen Sie die Anwendung und fahren Sie mit dem Umschalten von Standorten in Xcode oder Android Studio fort. Es sollten weiterhin Konsolenauslesen angezeigt werden, die auf die Standortänderung hinweisen. Abhängig von den in Ihrem Trigger festgelegten Kriterien sollten auch lokale Benachrichtigungen angezeigt werden. (Es kann eine Verzögerung von 1 bis 2 Sekunden geben.) | Das erwartete Ergebnis ist, dass lokale Benachrichtigungen jedes Mal angezeigt werden, wenn die entsprechenden Kriterien erfüllt werden. |
|  | **ZUSAMMENFASSUNGSPUNKT** <br>In diesem Stadium sollten POI-Einträge in unserer lokalen Umgebung angezeigt werden. Wir sollten auch Nachrichten von Campaign sehen, die auf der POI-Arbeit basieren. Wenn Fehler auftreten, überprüfen Sie, ob eine Slack-Benachrichtigung nicht gesendet wurde. Wenn keine Slack-Meldung vorhanden ist, überprüfen Sie die Anwendungskonsole, da ein neuer Standorteintrag möglicherweise nicht aufgezeichnet wurde. Wenn die Ergebnisse erfolgreich sind, können wir ziemlich sicher sein, dass die Anwendung ordnungsgemäß funktioniert und dass der Places-Dienst und der Campaign-Messaging-Dienst ebenfalls ordnungsgemäß funktionieren. |  |
|  | **ON-SITE-TESTING** <br>Beim Testen am Standort sollte sich nicht viel ändern. Die Aktivierung des Slack-Postbacks hilft dabei zu verstehen, ob das Gerät einen Einstieg und einen Ausstieg für den Standort erhält. |  |
| 18 | Führen Sie Tests mit Geräten durch, die mit WLAN und Mobilgeräten mit Behinderung beginnen, und aktivieren Sie dann einmal im POI-Bereich. | Wenn ein Fehler auftritt, notieren Sie sich, ob Sie einen Geo-Fence-Eintrag und eine Benachrichtigung im Slack erhalten. Was ist der Zeitstempel auf der Slack-Benachrichtigung? |
| 19 | Führen Sie den Test mit nur zellulärer Aktivierung und ausgeschaltetem WLAN durch. |  |
| 20 | Führen Sie einen Test mit eingeschaltetem Handy und WLAN durch. |  |
|  | **ZUSAMMENFASSUNGSPUNKT** <br>Vor-Ort-Tests sollten eng mit den Entwicklungstests übereinstimmen. Beachten Sie, dass bei der Bestimmung des Benutzerstandorts einige Umgebungsfaktoren zum Tragen kommen können, z. B. die Dauer der Besuchszeit für einen POI-GeoZaun, die Verfügbarkeit von Zellensignalen und die Stärke nahegelegener WLAN-Zugangspunkte. |  |

## Protokollbeispiele

**Schritt 8:** Erwartete iOS- und Android-Protokolle während einer Standortaktualisierung

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Schritt 9:** Erwartete Protokolle von iOS und Android während eines Ereignisses

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
