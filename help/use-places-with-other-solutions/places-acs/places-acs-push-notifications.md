---
title: Push-Benachrichtigungen mit dem Places-Dienst
description: Dieser Abschnitt enthält Informationen zur Verwendung des Orts-Dienstes mit Push-Benachrichtigungen in Campaign Standard.
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 4%

---


# Push-Benachrichtigungen mit Places-Dienst {#push-notifications}

In diesem Abschnitt erfahren Sie, wie Sie historische Geo-Positionsinformationen zur Zielgruppe von Push-Benachrichtigungen verwenden, die über Adobe Campaign Standard bereitgestellt werden.

## Voraussetzungen

Führen Sie zuerst die folgenden Aufgaben durch:

* Verwenden Sie eine Mobilanwendung, die mit dem Adobe Experience Platform Mobile SDK konfiguriert ist, einschließlich der Erweiterung [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* hinzufügen Sie die [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) in Ihre Mobile App-Konfiguration ein.

* [Erstellen Sie einen ](/help/poi-mgmt-ui/create-a-poi-ui.md) POI in der Verwaltungsoberfläche des Places-Dienstes.

* Aktivieren und installieren Sie die Erweiterung [Orte](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Datenelemente in Experience Platform Launch erstellen

Nachdem Sie überprüft haben, ob die Erweiterungen &quot;Orte&quot;und &quot;Orte-Monitor&quot;in Ihrer Anwendung ordnungsgemäß funktionieren, müssen Sie Datenelemente in Experience Platform Launch erstellen. Mithilfe von Datenelementen können Sie die Informationen lesen, die von den Erweiterungen bereitgestellt wurden, die über den Mobile SDK-Ereignis-Hub gesendet werden, und als Alias fungieren, um Daten aus der Clientanwendung abzurufen. Um Daten aus den Platzierungs-Erweiterungen abzurufen und die Informationen zum Orte-Dienst an die Kampagne zu senden, müssen Sie einige Datenelemente erstellen.

Erstellen eines Datenelements:

1. Klicken Sie in der Mobileigenschaft Ihres Experience Platform Launchs auf die Registerkarte **[!UICONTROL Datenelemente]** und dann auf **[!UICONTROL Hinzufügen Datenelement]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Places Service]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Datenelementtyp]** **[!UICONTROL Name]**.
1. Im rechten Fensterbereich können Sie **[!UICONTROL Aktuelle POI]** auswählen, um den Namen des POI abzurufen, in dem sich der Benutzer derzeit befindet.

   **[!UICONTROL &quot;Letzte]** Eingabe&quot;ruft den Namen des POI ab, das der Benutzer zuletzt eingegeben hat, und &quot; **[!UICONTROL Letzte]** Ausstiege&quot;gibt den Namen des POI an, das der Benutzer zuletzt verlassen hat. In diesem Beispiel haben wir **[!UICONTROL Letzte Eingabe]** ausgewählt und einen Namen für das Datenelement eingegeben, z. B. **[!UICONTROL Letzte Eingabe POI-Name]** und auf **[!UICONTROL Speichern]** geklickt.

   ![&quot;Push-Nachrichten in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Wiederholen Sie die Schritte 1-4 oben und erstellen Sie Datenelemente für *Zuletzt eingegebene POI-Breitengrad*, *Letzte eingegebene POI-Längengrad* und *Letzter eingegebener POI-Radius*.

Achten Sie neben den Datenelementen für den Orte-Dienst darauf, dass Sie Mobile-Core-Datenelemente für *App-ID* und *Experience Cloud-ID* erstellen.

## Regel zum Senden von Ortsdaten an Adobe Campaign Standard erstellen

Mit Regeln in Experience Platform Launch können Sie komplexe Workflows mit mehreren Lösungen erstellen, die auf Ereignis-Triggern basieren. Mit Regeln können Sie neue Regeln erstellen oder vorhandene ändern und die Updates dynamisch für Ihre mobilen Anwendungen bereitstellen. Im folgenden Beispiel wird die Regel ausgelöst, wenn ein Benutzer einen Geofencing-POI aufruft. Nachdem die Regel ausgelöst wurde, wird ein Update an Campaign Standard gesendet, um einen Eintrag für einen bestimmten POI für einen bestimmten Benutzer basierend auf der Experience Cloud-ID aufzuzeichnen.

1. Klicken Sie in der Eigenschaft mobile Ihres Experience Platform Launchs auf der Registerkarte **[!UICONTROL Rules]** auf **[!UICONTROL Hinzufügen Regel]**.
1. Klicken Sie unter **[!UICONTROL Ereignis]** auf **[!UICONTROL +]** und wählen Sie **[!UICONTROL Ortsdienst]** als Erweiterung.
1. Wählen Sie für den Ereignistyp **** **[!UICONTROL POI]** eingeben.
1. Benennen Sie die Regel, z. B. **Benutzer eingegeben POI**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.
1. Lassen Sie den Abschnitt **[!UICONTROL Bedingungen]** leer.

   In diesem Abschnitt können Sie filtern oder Einschränkungen festlegen, wann diese Regel ausgelöst werden soll.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL +]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Mobile Core]** und in der Dropdown-Liste **[!UICONTROL Aktionstyp]** **[!UICONTROL Postback senden]**.
1. Unter **[!UICONTROL URL]** müssen Sie den Endpunkt &quot;Campaign Standard-Speicherorte&quot;erstellen.

   Die URL sollte ähnlich wie `https:///rest/head/mobileAppV5//locations/` aussehen.
Stellen Sie sicher, dass Sie die korrekten Datenelemente verwenden, die Sie zuvor für Ihren Kampagnen-Server und Ihren pKey erstellt haben.

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
1. Geben Sie unter **[!UICONTROL Content-Typ]** den Wert **[!UICONTROL application/json]** ein.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

>[!IMPORTANT]
>
>* Es kann hilfreich sein, einen Slack-Web-Haken als zusätzliche Aktion einzurichten, um zu überprüfen, ob Einsendungen ausgelöst werden und ob die richtigen Daten erfasst werden.
>* Denken Sie daran, die letzten Änderungen an Ihrer App zu veröffentlichen, um sicherzustellen, dass die Regel und alle Ihre Datenelemente im Rahmen Ihrer Konfiguration bereitgestellt werden. Starten Sie nach der Veröffentlichung die mobile Anwendung erneut, um die neuesten Konfigurationsaktualisierungen zu erhalten.


## Standortdaten zur Zielgruppe von Kampagnen-Nachrichten verwenden

Nachdem wir nun Ortsdaten in Kampagne ausgefüllt haben, können wir POIs als Segmentwerkzeug für Audiencen verwenden.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Push-Benachrichtigung erstellen]**.
1. Wählen Sie für den Typ der Push-Benachrichtigung **[!UICONTROL Push-an-Kampagne-Profil]**.
1. Klicken Sie auf **[!UICONTROL Weiter]** und geben Sie die allgemeinen Details ein.
1. Klicken Sie im Bildschirm &quot;Audience&quot;auf **[!UICONTROL Anzahl]**, um festzustellen, wie viele Benutzer die Push-Benachrichtigung gesendet werden soll.

   >[!TIP]
   >
   >In diesem Beispiel ist der Zähler 3, da es drei installierte Geräte gibt, auf denen die Anwendung getestet wird.

1. Erweitern Sie im linken Bereich die Registerkarte **[!UICONTROL Profil]** und ziehen Sie den Filter **[!UICONTROL POI-Position]** in den Hauptbereich.
1. Geben Sie im Fenster &quot;POI-Filter&quot;den exakten Namen des POI ein, der Zielgruppe werden soll.

   >[!TIP]
   >
   >Sie können zusätzliche Auswahlen vornehmen, um den Zeitraum seit dem vorherigen Besuch des Benutzers an diesem POI zu bestimmen.

   ![&quot;Push Messaging 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Wählen Sie **[!UICONTROL Bestätigen]** aus.
1. Führen Sie die Zählung erneut oben aus, um die Größenänderung Ihrer Audience zu sehen.

   Wenn Ihre Zähleraktualisierung nicht angezeigt wird, haben Sie möglicherweise einen POI-Namen eingegeben, für den keine Geräte einen Eintrag ausgelöst haben. Der Slack-Web-Haken wird in dieser Situation wertvoll, da Sie eine Liste der POI-Einträge von verschiedenen Testgeräten sehen können.

1. Sie können weitere POI-Filter herausziehen, um mehrere POIs in Ihre Nachricht einzuschließen.
1. Klicken Sie auf **[!UICONTROL Weiter]**, um die Erstellung der Push-Benachrichtigung für die Bereitstellung abzuschließen.

   ![&quot;Push Messaging 3 in ACS&quot;](/help/assets/ACS_push3.png)

Die Verwendung des Places Service mit Adobe Campaign Standard bietet Ihnen ein leistungsfähiges Tool, um Ihre Nachrichten zu segmentieren und an Benutzer basierend auf Geo-Zaun-Einstiegen und -Ausstiegen Zielgruppe. Diese Integration hilft Ihnen bei der Erstellung personalisierter und kontextueller Anwendungsfälle.