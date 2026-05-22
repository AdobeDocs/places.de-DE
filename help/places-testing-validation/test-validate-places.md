---
title: Places Service testen und validieren
description: Dieser Abschnitt enthält Informationen dazu, wie Sie Places Service testen und validieren können.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
TQID: https://experienceleague.adobe.com/nO4tOQW9rp3zjkHT6aJ5IcXHcD9heOaRAJiEchiz1Fk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c93393a4-e558-47e1-992e-c91ed4d480ceid: d5ef99fa-df0c-4153-bf94-105ad0724167id: daec7ead-f475-492a-a3b3-02ae08565d6fid: e08599ea-8888-4294-ba74-3ba0a7762a46id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7id: ed0d8d0e-04b9-4326-be72-a0fbca265377id: f7c7de77-382f-4f48-8b36-61a170f06d3did: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1748
ht-degree: 2%

---

# Empfehlungen zum Testen von Places Service {#test-validate-loc-svc}

Viele Kunden und Organisationen werden POIs auf der ganzen Welt definieren. Daher ist es wichtig, eine Möglichkeit zu haben, zu simulieren und zu testen, wie der Places Service mit Ihrer Anwendung interagiert. Diese Informationen helfen Ihnen zu verstehen, wie Sie die Ein- und Ausstiege des Places-Service testen und validieren können, die auf der Grundlage der definierten POIs und des aktuellen Speicherorts eines Benutzers korrekt ausgelöst werden.

Da Umgebungsvariablen ein Faktor für Standortsignal und -genauigkeit sein können, empfehlen wir, zunächst Grundlagenergebnisse zu ermitteln, indem lokal mit Entwickler-Tools und simulierten Standorteinträgen gearbeitet wird. Das Ziel besteht darin, sicherzustellen, dass alle Standortereignisse ordnungsgemäß funktionieren. Nachdem die Standortereignisse korrekt validiert wurden, können Lösungsintegrationen (z. B. Analytics, Target und Campaign) getestet werden. Um Ihre Testaktivitäten zu unterstützen, sollten Sie Slack Webhooks mit einem Postback einrichten und GPX-Dateien in Ihre individuelle Entwicklungsumgebung laden.

>[!IMPORTANT]
>
>In diesem Plan wird davon ausgegangen, dass POIs in der [Places Service-Benutzeroberfläche](https://places.adobe.com) erstellt wurden und die neuesten Versionen der Places-Erweiterung installiert und korrekt konfiguriert sind. Bei der aktiven Regionsüberwachung wird auch von einer Lösung zur Regionsüberwachung ausgegangen. Weitere Informationen finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md), [CoreLocation-Dokumentation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Dokumentation zum Android-Standort](https://developer.android.com/training/location/geofencing).

| Schritt | Beschreibung | Erwartetes Ergebnis |
|--- |--- |--- |
| 1 | Vergewissern Sie sich, dass die richtigen Manifestschlüssel eingegeben wurden, damit Android Zugriff auf den Tracking-Speicherort gewährt. | Bestätigt |
| 1a | Bestätigen Sie, dass Standortaktualisierungen in iOS konfiguriert sind. Stellen Sie außerdem sicher, dass Sie über die entsprechenden PLIST-Schlüssel in iOS verfügen, um die Benutzerberechtigung zum Nachverfolgen des Speicherorts anzufordern. | Bestätigt |
| 2 | Überprüfen Sie, welcher Überwachungsmodus für iOS festgelegt ist. Der kontinuierliche Modus ermöglicht eine höhere Genauigkeit und Persistenz, führt aber auch zu einer höheren Akkulaufzeit. | Wesentliche Änderungen oder kontinuierliche Änderungen |
| 3 | Wenn Sie mehr als eine POIs-Bibliothek verwenden, überprüfen Sie, ob die entsprechenden Bibliotheken in der Places -Erweiterung für Experience Platform Launch ausgewählt wurden. | Bestätigt |
| 4 | Vergewissern Sie sich, dass die neuesten Versionen von Mobile Core und Places Erweiterungen über Gradle oder CocoaPods mit der App gebündelt wurden. | Bestätigt - Weitere Informationen zu aktuellen Updates finden Sie unter [Versionshinweise.](/help/release-notes.md) |
| 5 | Vergewissern Sie sich, dass die richtigen Umgebungen für Tests konfiguriert sind. Die ID der Launch-Umgebung sollte mit Ihrer Launch-Entwicklungsumgebung übereinstimmen. | Bestätigt |
| 6 | Erstellen Sie GPX-Dateien für jeden POI, den Sie testen möchten. GPX-Dateien können in einer lokalen Entwicklungsumgebung verwendet werden, um einen Standorteintrag zu simulieren. Informationen zum Erstellen und Verwenden von GPX-Dateien finden Sie unter: <br>[GPX-Dateien für iOS Simulator [geschlossen]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[LOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX-Dateien werden im App-Projekt erstellt und geladen. |
| 7 | Ohne weitere Maßnahmen sollten Sie in der Lage sein, die Anwendung von Android Studio oder XCode aus zu starten und den entsprechenden Warnhinweis anzuzeigen, um Zugriff auf den Tracking-Speicherort anzufordern. Klicken Sie auf *Immer zulassen* Berechtigung.<br><br>Es wird empfohlen, ein echtes Gerät zu verwenden, das mit Ihrem Computer verbunden ist, anstatt den Gerätesimulator zu verwenden. | Die Eingabeaufforderung für die Standortanfrage sollte bei der Anwendung angezeigt werden, die über die IDE geladen wurde |
| 8 | Sobald die Standortberechtigung akzeptiert wurde. Die Places SDK ruft den aktuellen Speicherort des Geräts ab, und der Überwachungscode der Region sollte mit der Überwachung der 20 nächstgelegenen POIs vom aktuellen Speicherort beginnen | Siehe das Protokollbeispiel unter der Tabelle. |
| 9 | Das Wechseln zwischen verschiedenen Speicherorten in XCode oder Android Studio sollte Eintrittsereignisse für bestimmte POIs erzeugen. Die folgenden Protokolle werden bei Eintritt in einen POI erwartet. | Siehe das Protokollbeispiel unter der Tabelle. |
| 10 | Nachdem der Regionsmonitor in der Nähe POIs gefunden hat, sollten Sie testen, indem Sie Pings an den Standort senden. Erstellen Sie in Launch eine neue Regel, die die Places-Erweiterung zum Trigger auf der Grundlage eines Geofencing-Eintrags verwendet. Erstellen Sie dann eine neue Aktion, indem Sie Mobile Core verwenden, um ein Postback zu senden. Wenn Sie eine Slack Webhook-App erstellen, können Sie Standorteinträge und -austritte anzeigen. Informationen zum Erstellen einer Slack Webhook-App finden Sie unter [Senden von Nachrichten mit eingehenden Webhooks.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Stellen Sie in Launch sicher, dass Sie Datenelemente für die Places-Erweiterung hinzugefügt haben, darunter: <br>Aktueller POI-Name<br>Aktueller POI lat<br>Current POI long<br>Last Entered name<br>Last<br>Last Entered long<br>Last Exited name<br>Last Exited lat<br>Last Exited long<br>Timestamp |  |
| 10b | Erstellen Sie eine neue Regel mit einem Ereignis = Orte → Eingabe des POI |  |
| 10c | Erstellen einer Aktion = Mobile Core → Postback |  |
| 10 T | Verwenden Sie die Webhook-URL für Ihre Slack-App, z. B. https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD… |  |
| 10e | Der Hauptteil des Posts sieht in etwa so aus: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Stellen Sie sicher, dass Sie die spezifischen Datenelemente verwenden, die Sie hier erstellt haben. |  |
| 10f | Stellen Sie sicher, dass Sie alle neuen Datenelement- und Regeländerungen in Launch veröffentlichen. (Sie sollten oben rechts in der Launch-Benutzeroberfläche eine funktionierende Entwicklungsbibliothek auswählen.) |  |
| 11 | Starten und testen Sie Ihre Anwendung erneut, indem Sie zwischen den GPX-Speicherorten in der Entwicklungs-IDE wechseln. | Sie sollten jetzt Slack-Benachrichtigungen mit Einträgen für jeden POI sehen, wenn Sie verschiedene Standorte in Ihrer Entwicklungsumgebung auswählen. |
|  | **QUICK SUMMARY POINT**<br> Alle diese Tests können lokal durchgeführt werden, ohne einen bestimmten POI-Speicherort aufrufen zu müssen. Validierungstests helfen sicherzustellen, dass Ihre Anwendung korrekt konfiguriert ist und die richtigen Berechtigungen für den Speicherort erhalten hat. <br><br>Diese Validierung gibt Ihnen auch die Gewissheit, dass die definierten POIs korrekt mit Ihrer Implementierung zur regionalen Überwachung funktionieren.  Nach diesem Schritt beginnen wir mit dem Testen von Nachrichten in Campaign, um zu sehen, ob die richtigen Nachrichten basierend auf POI-Ein- und Ausstiegen angezeigt werden. |  |
|  | **Testen von In-App-Nachrichten in Adobe Campaign Standard mit dem Places-Service.** |  |
| 12 | Konfigurieren Sie im Hauptdashboard der Kampagne eine neue In-App-Nachricht (Typ = Broadcast) |  |
| 12a | Wählen Sie in Trigger **Ereignistyp Orte - Eintrag als Trigger**. |  |
| 12b | Wählen Sie **[!UICONTROL Orte benutzerdefinierte Metadaten]** als zusätzlichen Filter aus - verwenden Sie den POI-Typ = Zuletzt eingegebener POI.<br>Wir verwenden **[!UICONTROL Zuletzt eingegeben]** als POI-Typ, da in den meisten Fällen **[!UICONTROL Zuletzt eingegeben]** mit **[!UICONTROL Aktueller POI]** übereinstimmt. <br><br>**[!UICONTROL Aktueller POI ]**sollte nur in Fällen verwendet werden, in denen sich POI-Geofences überschneiden. In diesem Fall müssen diese POIs EINEN RANG erhalten. Anschließend zeigt der**[!UICONTROL  Aktuelle POI ]**den POI an, der aus den 2 oder 3 Geofences, in denen sich ein Benutzer derzeit befindet, den höchsten Rang einnimmt. |  |
| 12c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, mit dem Sie einschränken können, welche POIs eine Nachricht erhalten sollen. |  |
| 12 T | Behalten Sie für Häufigkeit und Dauer nur ein oder zwei Tage bei, damit Sie den Trigger in einem kürzeren Zeitraum ablaufen lassen können, wenn Sie die Kriterien nicht mögen. |  |
| 12e | Wählen Sie für Immer/Einmal oder Bis zum Durchklicken die Option *IMMER* aus, damit Sie über mehrere Standorte hinweg testen können. | Eine In-App-Nachricht wird IMMER angezeigt, wenn Sie eine Ortsänderung simulieren, die den entsprechenden Metadatenkriterien entspricht. |
| 12f | Wählen Sie für die Anzeige eine andere Option als Lokale Benachrichtigung aus. Dadurch wird es einfacher, beim Testen mit der App im Vordergrund zu sehen.) |  |
| 12g | In-App-Nachricht vorbereiten/bestätigen und bereitstellen |  |
| 13 | Beenden Sie in Ihrer Entwicklungsumgebung die Anwendung, um sicherzustellen, dass neue Kampagnenregeln heruntergeladen werden, und starten Sie sie erneut. | Vergessen Sie nicht, dass die Anwendungen vollständig neu gestartet werden müssen, damit die neue Campaign-Regeldatei auf das Gerät heruntergeladen werden kann. |
| 14 | Wechseln Sie in Ihrer Entwicklungsanwendung mithilfe der zuvor erstellten GPX-Dateien zwischen Speicherorten. | Die In-App-Nachricht sollte nun basierend auf den zuvor festgelegten Kriterien angezeigt werden. |
| 15 | Beim nächsten Test werden wir im Wesentlichen die gleichen Schritte wie zuvor kopieren, aber dieses Mal werden wir die LOKALE BENACHRICHTIGUNG testen. | Als Ergebnis wird erwartet, dass die lokalen Benachrichtigungen jedes Mal angezeigt werden, wenn übereinstimmende Kriterien erfüllt sind. |
| 16 | Konfigurieren Sie eine neue In-App-Nachricht (Typ = Broadcast). |  |
| 16a | Wählen Sie in Trigger **[!UICONTROL Ereignistyp Orte]** - **[!UICONTROL Eintrag als Trigger]** aus. |  |
| 16b | Wählen Sie die benutzerdefinierten Platzierungen von Metadaten als zusätzlichen Filter aus - verwenden Sie **[!UICONTROL POI-Typ]** = **[!UICONTROL Zuletzt eingegebener POI]**. |  |
| 16c | Wählen Sie einen benutzerdefinierten Metadatenschlüssel aus, mit dem Sie einschränken können, welche POIs eine Nachricht erhalten sollen. |  |
| 16d | Behalten Sie für Häufigkeit und Dauer nur ein oder zwei Tage bei, damit Sie den Trigger in einem kürzeren Zeitraum ablaufen lassen können, wenn Sie die Kriterien nicht mögen. |  |
| 16e | Für „Immer/Einmal“ oder „Bis zum Clickthrough“, **[!UICONTROL IMMER]**. |  |
| 16f | Wählen Sie für den Anzeigetyp die Option **[!UICONTROL Lokale Benachrichtigung]**. |  |
| 16g | In-App-Nachricht vorbereiten/bestätigen und bereitstellen |  |
| 17 | Verbinden Sie in der Entwicklungsumgebung Ihr Gerät und drücken Sie **[!UICONTROL Play]** auf dem Build. Nachdem Sie festgestellt haben, dass der Speicherort funktioniert, führen Sie die Hintergrundanwendung aus und wechseln Sie weiter zwischen Speicherorten in Xcode oder Android Studio. Sie sollten weiterhin Konsolenlesevorgänge sehen, die den Speicherort-Wechsel anzeigen, und Sie sollten auch lokale Benachrichtigungen je nach den in Ihrem Trigger festgelegten Kriterien sehen. (Es kann eine Verzögerung von 1-2 Sekunden geben.) | Es wird erwartet, dass lokale Benachrichtigungen jedes Mal angezeigt werden, wenn die entsprechenden Kriterien erfüllt sind. |
|  | **ZUSAMMENFASSUNGSPUNKT** <br>In dieser Phase sollten POI-Einträge in unserer lokalen Umgebung angezeigt werden. Wir sollten auch Nachrichten von Campaign sehen, die auf der POI-Arbeit basieren. Wenn Fehler auftreten, überprüfen Sie, ob eine Slack-Benachrichtigung nicht ausgegeben wurde. Wenn keine Slack-Nachricht vorhanden ist, überprüfen Sie die Anwendungskonsole, da möglicherweise kein neuer Standorteintrag aufgezeichnet wurde. Wenn die Ergebnisse erfolgreich sind, können wir ziemlich sicher sein, dass die Anwendung ordnungsgemäß funktioniert und dass der Places-Service und der Campaign-Messaging-Service ebenfalls ordnungsgemäß funktionieren. |  |
|  | **TESTS VOR ORT** <br>Beim Testen vor Ort sollte sich nicht viel ändern. Das Aufrechterhalten des Slack-Postbacks sollte Aufschluss darüber geben, ob das Gerät einen Ein- und Ausstieg für den Speicherort erhält. |  |
| 18 | Führen Sie Tests mit Geräten durch, die mit WiFi und Mobile deaktiviert beginnen, und aktivieren Sie dann einmal in der POI-Region. | Beachten Sie bei einem Fehler, ob Sie einen Geo-Fence-Eintrag und eine Benachrichtigung in Slack erhalten. Welcher Zeitstempel ist in der Slack-Benachrichtigung enthalten? |
| 19 | Führen Sie den Test nur mit aktiviertem Mobiltelefon und ausgeschaltetem WLAN durch. |  |
| 20 | Führen Sie einen Test mit eingeschaltetem Handy und WiFi durch. |  |
|  | **SUMMARY POINT** <br>Tests vor Ort sollten eng mit den Entwicklungstests übereinstimmen. Denken Sie daran, dass bei der Bestimmung eines Benutzerstandorts einige Umgebungsfaktoren eine Rolle spielen können, z. B. die Dauer der in einem POI-Geozaun verbrachten Zeit, die Verfügbarkeit des Zellsignals und die Stärke der nahegelegenen WiFi-Zugriffspunkte. |  |

## Protokollbeispiele

**Schritt 8 :** Während einer Standortaktualisierung wurden iOS- und Android-Protokolle erwartet.

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Schritt 9 :** Bei einem Ereignis werden iOS- und Android-Protokolle erwartet.

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
