---
title: Push-Benachrichtigungen
seo-title: Push-Benachrichtigungen
description: Dieser Abschnitt enthält Informationen zur Verwendung von Orten mit Push-Benachrichtigungen in Campaign Standard.
seo-description: 'Dieser Abschnitt enthält Informationen zur Verwendung von Orten mit Push-Benachrichtigungen in Campaign Standard. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Push-Benachrichtigungen mit Experience Platform Location Service {#push-notifications}

In diesem Handbuch werden wir zeigen, wie Sie historische Geo-Positionsinformationen verwenden können, um Push-Benachrichtigungen, die über Adobe Campaign Standard gesendet werden, zielgerichtet durchzuführen.

>[!IMPORTANT]
>
>Führen Sie zuerst die folgenden Aufgaben aus:
>
>* Verwenden Sie eine mobile Anwendung, die mit dem Adobe Experience Platform Mobile SDK, einschließlich der [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard), konfiguriert wurde.
   >
   >
* Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
>* Fügen Sie Ihrer App-Konfiguration die [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) hinzu.
   >
   >
* [Erstellen Sie einen POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche Orte POI.
   >
   >
* Aktivieren und installieren Sie die [Ortserweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).



## Datenelemente in Experience Platform Launch erstellen

Nachdem Sie sich vergewissert haben, dass die Positionierungs- und Orteüberwachung für Positionserweiterungen in Ihrer Anwendung ordnungsgemäß funktioniert, erstellen Sie Datenelemente in Experience Platform Launch. Datenelemente ermöglichen es Ihnen, die Informationen zu lesen, die von den Erweiterungen bereitgestellt wurden, die über den Mobile SDK-Ereignis-Hub gesendet werden, und als Alias zum Abrufen von Daten aus der Clientanwendung zu fungieren. Erstellen wir einige Datenelemente, um Daten aus den Platzierungserweiterungen abzurufen, damit wir die Ortsinformationen an Campaign senden können.

1. Klicken Sie in der Eigenschaft "Experience Platform Launch mobile"auf die Registerkarte **Datenelemente** und dann auf Datenelement **hinzufügen**.
2. Wählen Sie in der Dropdownliste **Erweiterung** die Option **Orte**.
3. Wählen Sie aus der Dropdownliste **Datenelementtyp** die Option **Name**.
4. Im rechten Fensterbereich können Sie " **Aktueller POI** "auswählen, der den Namen des POI abruft, in dem sich der Benutzer derzeit befindet.

   **"Zuletzt eingegeben** "ruft den Namen des POI ab, das der Benutzer zuletzt eingegeben hat, und " **Letzter Ausstieg** "gibt den Namen des POI an, das der Benutzer zuletzt verlassen hat. In diesem Beispiel wählen wir " **Zuletzt eingegeben** "und geben einen Namen für das Datenelement ein, z. B. " **Zuletzt eingegebener POI-Name** "und klicken auf " **Speichern**".

   !["Push-Nachrichten in Campaign Standard"](/help/assets/ACS_Push1.png)


5. Wiederholen Sie die obigen Schritte und erstellen Sie Datenelemente für _Letzte Eingabe-POI-Breitengrad_, _Letzte Eingabe-POI-Längengrad_ und _Letzte Eingabe-POI-Radius_.

Achten Sie neben den Datenelementen für den Location Service darauf, dass Sie Mobile-Core-Datenelemente für die _App-ID_ und _Experience Cloud-ID_ erstellen.

## Regel zum Senden von Ortsdaten an Adobe Campaign Standard erstellen

Mit Regeln im Experience Platform Launch können Sie komplexe, lösungsübergreifende Arbeitsabläufe erstellen, die auf Ereignisauslösern basieren. Regeln sind besonders nützlich, da Sie neue Regeln erstellen oder vorhandene ändern können und die Updates dynamisch für Ihre mobilen Anwendungen bereitgestellt werden. In diesem Beispiel erstellen wir eine Regel, die ausgelöst wird, wenn ein Benutzer einen Geo-Fencing-Point aufruft. Nachdem die Regel ausgelöst wurde, wird eine Aktualisierung an Campaign gesendet, um einen Eintrag für einen bestimmten POI für einen bestimmten Benutzer basierend auf der Experience Cloud ID aufzuzeichnen.

1. Klicken Sie in der Eigenschaft Start für Mobilgeräte auf die Registerkarte **Regeln** und dann auf Regel **hinzufügen**.
2. Klicken Sie im Abschnitt **Ereignisse** auf **+** und wählen Sie **Orte** als Erweiterung.
3. Wählen Sie für den **Ereignistyp** "POI **eingeben"**.
4. Benennen Sie die Regel, z. B. **Benutzer eingegeben POI**.
5. Click **Keep Changes**.
6. Im Abschnitt " **Bedingungen** "können Sie filtern oder Beschränkungen dafür festlegen, wann diese Regel ausgelöst werden soll.  Vorerst werden wir das leer lassen.
7. Klicken Sie im Abschnitt **Aktionen** auf **+** , um eine neue Aktion zu erstellen
8. Wählen Sie in der Dropdownliste **Erweiterung** die Option **Mobile Core und in der Dropdownliste** Aktionstyp **die Option Postback** senden **** .
9. Für die **URL** müssen Sie den Endpunkt "Campaign Standard-Standorte"erstellen.  Die URL sollte ähnlich wie die unten stehende aussehen. Stellen Sie sicher, dass Sie die korrekten Datenelemente verwenden, die Sie zuvor für Ihren Campaign-Server und Ihren pKey erstellt haben. `https:///rest/head/mobileAppV5//locations/`
10. Klicken Sie auf das Feld, um einen Beitragstext hinzuzufügen und senden Sie Folgendes:

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

11. Stellen Sie sicher, dass Sie Ihre spezifischen Datenelemente verwenden, die Sie im vorherigen Abschnitt erstellt haben.
12. Geben Sie in **Content Type****application/json** ein.
13. Klicken Sie auf Änderungen **beibehalten** , nachdem Sie diese eingerichtet haben.
14. Es kann hilfreich sein, wenn Sie als zusätzliche Aktion eine Slack-Web-Hook-Einrichtung einrichten, um zu überprüfen, ob Einträge ausgelöst werden und ob die richtigen Daten erfasst werden.


>Vergessen Sie nicht, die neuesten Änderungen an Ihrer App zu veröffentlichen, um sicherzustellen, dass die Regel und alle Datenelemente im Rahmen Ihrer Konfiguration bereitgestellt werden. Nach der Veröffentlichung sollten Sie die Mobilanwendung erneut starten, um die neuesten Konfigurationsaktualisierungen zu erhalten.

## Standortdaten zum Targeting von Kampagnenmeldungen verwenden

Nachdem wir nun Ortsdaten in Campaign ausgefüllt haben, können wir POIs als Tool für Zielgruppensegmente verwenden.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf Push-Benachrichtigung **erstellen**.
2. Wählen Sie für den Typ der Push-Benachrichtigung die Option Push- **an Kampagnenprofile** senden.
3. Klicken Sie auf **Weiter** und geben Sie im nächsten Bildschirm die allgemeinen Details ein.
4. Klicken Sie im Anzeigebereich "Zielgruppe"auf **Zähler** , um zu sehen, wie viele Benutzer die Push-Benachrichtigung gesendet werden soll.

   *In diesem Fall ist meine Anzahl gleich drei, da ich drei Geräte habe, auf denen ich die Anwendung testen kann.*

5. Erweitern Sie auf der linken Seitenleiste die Registerkarte " **Profil** "und ziehen Sie den Filter " **POI-Position** "in den Hauptbereich
6. Geben Sie im Fenster "POI-Filter"den genauen Namen des POI ein, für das Sie ein Targeting vornehmen möchten.

   *Sie können zusätzliche Auswahlen vornehmen, um den Zeitraum seit dem letzten Besuch des Benutzers an diesem POI zu bestimmen.*

   !["Push Messaging 2 in ACS"](/help/assets/ACS_push2.png)


7. Klicken Sie auf **Bestätigen**.
8. Führen Sie die Zählung erneut oben aus, um eine Änderung der Zielgruppengröße zu sehen.  Wenn Ihre Zähleraktualisierung nicht angezeigt wird, haben Sie möglicherweise einen POI-Namen eingegeben, für den keine Geräte einen Eintrag ausgelöst haben. Hier wird der Slack-Web-Haken wertvoll, da Sie eine Liste der POI-Einträge von verschiedenen Testgeräten sehen können.
9. Sie können weitere POI-Ortsfilter ziehen, um mehrere POIs in Ihre Nachricht einzuschließen.
10. Klicken Sie auf **Weiter** , um die Erstellung der Push-Benachrichtigung für die Bereitstellung abzuschließen.

   !["Push Messaging 3 in ACS"](/help/assets/ACS_push3.html)

Die Verwendung des Location Service mit Adobe Campaign Standard bietet Ihnen ein leistungsfähiges Tool, um Ihre Nachrichten basierend auf Geo-Zaun-Einstiegen und Ausstiegen zu segmentieren und gezielt an Benutzer auszurichten. Diese einfache Integration öffnet die Tür zum Aufbau von personalisierteren und kontextbezogenen Anwendungsfällen.