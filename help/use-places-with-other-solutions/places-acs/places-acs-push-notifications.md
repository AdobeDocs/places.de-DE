---
title: Push-Benachrichtigungen mit dem Places-Dienst
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Orte-Dienstes mit Push-Benachrichtigungen in Campaign Standard.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Push-Benachrichtigungen mit dem Ortsdienst {#push-notifications}

In diesem Abschnitt erfahren Sie, wie Sie historische Geo-Positionsinformationen verwenden, um Push-Benachrichtigungen, die über Adobe Campaign Standard bereitgestellt werden, gezielt anzusprechen.

## Voraussetzungen 

Führen Sie zuerst die folgenden Aufgaben aus:

* Verwenden Sie eine mobile Anwendung, die mit dem Adobe Experience Platform Mobile SDK, einschließlich der [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard), konfiguriert wurde.

* Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* Fügen Sie Ihrer App-Konfiguration die [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) hinzu.

* [Erstellen Sie einen POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche für den POI-Dienst für Orte.

* Aktivieren und installieren Sie die [Ortserweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Datenelemente in Experience Platform Launch erstellen

Nachdem Sie überprüft haben, ob die Erweiterungen &quot;Orte&quot;und &quot;Orte-Monitor&quot;in Ihrer Anwendung ordnungsgemäß funktionieren, müssen Sie Datenelemente in Experience Platform Launch erstellen. Datenelemente ermöglichen es Ihnen, die Informationen zu lesen, die von den Erweiterungen bereitgestellt wurden, die über den Mobile SDK-Ereignis-Hub gesendet werden, und als Alias zum Abrufen von Daten aus der Clientanwendung zu fungieren. Um Daten aus den Platzierungserweiterungen abzurufen und die Informationen zum Orte-Dienst an Campaign zu senden, müssen Sie einige Datenelemente erstellen.

So erstellen Sie ein Datenelement:

1. Klicken Sie in der Eigenschaft &quot;Experience Platform Launch mobile&quot;auf die **[!UICONTROL Data Elements]**Registerkarte und klicken Sie auf**[!UICONTROLA Datenelement]**hinzufügen.
1. Wählen Sie in der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Places Service]**.
1. Wählen Sie aus der **[!UICONTROL Data Element Type]**Dropdownliste**[!UICONTROL Name]**.
1. Im rechten Fensterbereich können Sie auswählen, **[!UICONTROL Current POI]**welcher den Namen des POI abruft, in dem sich der Benutzer derzeit befindet.

   **[!UICONTROL Last Entered]**ruft den Namen des POI ab, das der Benutzer zuletzt eingegeben hat, und**[!UICONTROL Last Exited]** gibt den Namen des POI an, das der Benutzer zuletzt verlassen hat. In diesem Beispiel haben wir einen Namen für das Datenelement ausgewählt **[!UICONTROL Last Entered]**und eingegeben, z. B.**[!UICONTROL Last Entered POI Name]** und darauf geklickt **[!UICONTROL Save]**.

   ![&quot;Push-Nachrichten in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Achten Sie neben den Datenelementen für den Places-Dienst darauf, Mobile-Core-Datenelemente für *App-ID* und *Experience Cloud-ID* zu erstellen.

## Regel zum Senden von Ortsdaten an Adobe Campaign Standard erstellen

Mit Regeln im Experience Platform Launch können Sie komplexe, lösungsübergreifende Arbeitsabläufe erstellen, die auf Ereignisauslösern basieren. Mit Regeln können Sie neue Regeln erstellen oder vorhandene ändern und die Updates dynamisch für Ihre mobilen Anwendungen bereitstellen. Im folgenden Beispiel wird die Regel ausgelöst, wenn ein Benutzer einen Geofencing-POI aufruft. Nachdem die Regel ausgelöst wurde, wird ein Update an Campaign Standard gesendet, um einen Eintrag für einen bestimmten POI für einen bestimmten Benutzer basierend auf der Experience Cloud ID aufzuzeichnen.

1. Klicken Sie in der Eigenschaft Experience Platform Launch mobile auf der **[!UICONTROL Rules]**Registerkarte auf**[!UICONTROL Add Rule]**.
1. Klicken Sie unter dem **[!UICONTROL Events]**Abschnitt auf**[!UICONTROL +]** und wählen Sie **[!UICONTROL Places Service]**als Erweiterung aus.
1. For the **[!UICONTROL Event Type]**, select**[!UICONTROL Enter POI]**.
1. Benennen Sie die Regel, z. B. **Benutzer eingegeben POI**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.
1. Lassen Sie den **[!UICONTROL Conditions]**Abschnitt leer.

   In diesem Abschnitt können Sie filtern oder Einschränkungen festlegen, wann diese Regel ausgelöst werden soll.

1. Klicken Sie unter dem **[!UICONTROL Actions]**Abschnitt auf**[!UICONTROL +]**.
1. Wählen Sie in der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Mobile Core]** und in der **[!UICONTROL Action Type]**Dropdownliste die Option**[!UICONTROL Send Postback]**.
1. In **[!UICONTROL URL]**diesem Fall müssen Sie den Endpunkt &quot;Campaign Standard-Standorte&quot;erstellen.

   Die URL sollte ähnlich aussehen wie `https:///rest/head/mobileAppV5//locations/`.
Stellen Sie sicher, dass Sie die korrekten Datenelemente verwenden, die Sie zuvor für Ihren Campaign-Server und Ihren pKey erstellt haben.

1. Klicken Sie auf das Feld, um einen Beitragstext hinzuzufügen und senden Sie Folgendes:

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

1. Stellen Sie sicher, dass Sie die Datenelemente verwenden, die Sie im vorherigen Abschnitt erstellt haben.
1. Geben Sie in **[!UICONTROL Content Type]**ein**[!UICONTROL application/json]**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Es kann hilfreich sein, einen Slack-Web-Haken als zusätzliche Aktion einzurichten, um zu überprüfen, ob Einträge ausgelöst werden und ob die richtigen Daten erfasst werden.
>* Denken Sie daran, die letzten Änderungen an Ihrer App zu veröffentlichen, um sicherzustellen, dass die Regel und alle Datenelemente im Rahmen Ihrer Konfiguration bereitgestellt werden. Starten Sie nach der Veröffentlichung die mobile Anwendung erneut, um die neuesten Konfigurationsaktualisierungen zu erhalten.


## Standortdaten zum Targeting von Kampagnenmeldungen verwenden

Nachdem wir nun Ortsdaten in Campaign ausgefüllt haben, können wir POIs als Tool für Zielgruppensegmente verwenden.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Create Push Notification]**.
1. Wählen Sie für den Push-Benachrichtigungstyp **[!UICONTROL Send push to Campaign profiles]**.
1. Klicken Sie auf **[!UICONTROL Next]**und geben Sie die allgemeinen Details ein.
1. Klicken Sie im Anzeigebereich &quot;Zielgruppe&quot;auf **[!UICONTROL Count]**, um zu ermitteln, wie viele Benutzer die Push-Benachrichtigung gesendet werden soll.

   >[!TIP]
   >
   >In diesem Beispiel ist der Zähler 3, da es drei installierte Geräte gibt, auf denen die Anwendung getestet wird.

1. Erweitern Sie im linken Bereich die **[!UICONTROL Profile]**Registerkarte und ziehen Sie den**[!UICONTROL POI location]** Filter in den Hauptbereich.
1. Geben Sie im Fenster &quot;POI-Filter&quot;den genauen Namen des POI ein, für das Sie ein Targeting vornehmen möchten.

   >[!TIP]
   >
   >Sie können zusätzliche Auswahlen vornehmen, um den Zeitraum seit dem vorherigen Besuch des Benutzers an diesem POI zu bestimmen.

   ![&quot;Push Messaging 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Klicken Sie auf **[!UICONTROL Confirm]**.
1. Führen Sie die Zählung erneut oben aus, um eine Änderung der Zielgruppengröße zu sehen.

   Wenn Ihre Zähleraktualisierung nicht angezeigt wird, haben Sie möglicherweise einen POI-Namen eingegeben, für den keine Geräte einen Eintrag ausgelöst haben. In dieser Situation wird es nützlich, den Slack-Web-Haken zu haben, weil Sie eine Liste der POI-Einträge von verschiedenen Testgeräten sehen können.

1. Sie können weitere POI-Ortsfilter ziehen, um mehrere POIs in Ihre Nachricht einzuschließen.
1. Click **[!UICONTROL Next]**to finish creating the push notification for delivery.

   ![&quot;Push Messaging 3 in ACS&quot;](/help/assets/ACS_push3.png)

Die Verwendung des Orte-Dienstes mit Adobe Campaign Standard bietet Ihnen ein leistungsfähiges Tool, um Ihre Nachrichten basierend auf Geo-Zaun-Einstiegen und -Ausstiegen zu segmentieren und gezielt an Benutzer auszurichten. Diese Integration hilft Ihnen bei der Erstellung personalisierter und kontextbezogener Anwendungsfälle.