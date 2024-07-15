---
title: Push-Benachrichtigungen mit Places Service
description: Dieser Abschnitt enthält Informationen zur Verwendung des Places-Dienstes mit Push-Benachrichtigungen in Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 2%

---

# Push-Benachrichtigungen mit dem Places-Dienst {#push-notifications}

In diesem Abschnitt erfahren Sie, wie Sie historische Geostandortinformationen für Push-Benachrichtigungen verwenden, die über Adobe Campaign Standard bereitgestellt werden.

## Voraussetzungen

Führen Sie zunächst die folgenden Aufgaben aus:

* Lassen Sie eine Mobile App mit dem Adobe Experience Platform Mobile SDK, einschließlich der [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard), konfiguriert.

* Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* Fügen Sie die [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) zu Ihrer App-Konfiguration hinzu.

* [Erstellen Sie einen POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche für POI des Places-Dienstes.

* Aktivieren und installieren Sie die Erweiterung [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Erstellen von Datenelementen in Experience Platform Launch

Nachdem Sie überprüft haben, ob die Places-Erweiterung und eine Regionsüberwachungslösung ([CoreLocation-Dokumentation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Android-Standortdokumentation](https://developer.android.com/training/location/geofencing)) in Ihrer Anwendung ordnungsgemäß funktionieren, müssen Sie Datenelemente in Experience Platform Launch erstellen. Datenelemente ermöglichen es Ihnen, die Informationen zu lesen, die von den Erweiterungen bereitgestellt wurden, die über den Mobile SDK-Ereignis-Hub gelangen, und als Alias zum Abrufen von Daten aus der Client-Anwendung zu fungieren. Um Daten aus den Places-Erweiterungen abzurufen und die Places-Dienst-Informationen an Campaign zu senden, müssen Sie einige Datenelemente erstellen.

So erstellen Sie ein Datenelement:

1. Klicken Sie in Ihrer mobilen Experience Platform Launch-Eigenschaft auf die Registerkarte **[!UICONTROL Datenelemente]** und klicken Sie auf **[!UICONTROL Datenelement hinzufügen]**.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Places Service]** aus.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Datenelementtyp]** die Option **[!UICONTROL Name]** aus.
1. Im rechten Seitenbereich können Sie **[!UICONTROL Aktueller POI]** auswählen, um den Namen des POI abzurufen, an dem sich der Benutzer derzeit befindet.

   **[!UICONTROL Zuletzt eingegeben]** gibt den Namen des POI aus, den der Benutzer zuletzt eingegeben hat, und **[!UICONTROL Letzter Ausstieg]** gibt den Namen des POI an, den der Benutzer zuletzt verlassen hat. In diesem Beispiel haben wir &quot;**[!UICONTROL Zuletzt eingegeben]**&quot;, einen Namen für das Datenelement eingegeben, z. B. &quot;**[!UICONTROL Letzter eingegebener POI-Name]**&quot;, und auf &quot;**[!UICONTROL Speichern]**&quot;geklickt.

   ![&quot;Push messaging in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Wiederholen Sie die obigen Schritte 1 bis 4 und erstellen Sie Datenelemente für *Letzter eingegebener POI-Breitengrad*, *Letzter eingegebener POI-Längengrad* und *Letzter eingegebener POI-Radius*.

Stellen Sie neben den Datenelementen für den Places-Dienst sicher, dass Sie Mobile-Core-Datenelemente für *App-ID* und *Experience Cloud-ID* erstellen.

## Erstellen einer Regel zum Senden von Standortdaten an Adobe Campaign Standard

Mit Regeln in Experience Platform Launch können Sie komplexe, lösungsübergreifende Workflows erstellen, die auf Ereignis-Triggern basieren. Mit Regeln können Sie neue Regeln erstellen oder vorhandene ändern und die Aktualisierungen dynamisch für Ihre Mobile Apps bereitstellen. Im folgenden Beispiel wird die Regel ausgelöst, wenn ein Benutzer einen geo-fencing-POI betritt. Nachdem die Regel ausgelöst wurde, wird ein Update an den Campaign Standard gesendet, um einen Eintrag für einen bestimmten Benutzer basierend auf der Experience Cloud-ID an einem bestimmten POI aufzuzeichnen.

1. Klicken Sie in Ihrer mobilen Experience Platform Launch-Eigenschaft auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Regel hinzufügen]**.
1. Klicken Sie unter dem Abschnitt **[!UICONTROL Ereignisse]** auf **[!UICONTROL +]** und wählen Sie **[!UICONTROL Places Service]** als Erweiterung aus.
1. Wählen Sie für den **[!UICONTROL Ereignistyp]** **[!UICONTROL POI eingeben]** aus.
1. Nennen Sie die Regel, z. B. **Benutzer eingegeben POI**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.
1. Lassen Sie den Abschnitt **[!UICONTROL Bedingungen]** leer.

   In diesem Abschnitt können Sie filtern oder Einschränkungen dafür platzieren, wann diese Regel ausgelöst werden soll.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL +]**.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Mobile Core]** und in der Dropdownliste **[!UICONTROL Aktionstyp]** die Option **[!UICONTROL Postback senden]** aus.
1. In **[!UICONTROL URL]** müssen Sie den Endpunkt &quot;Campaign Standard-Speicherorte&quot;erstellen.

   Die URL sollte ähnlich wie `https:///rest/head/mobileAppV5//locations/` aussehen.
Stellen Sie sicher, dass Sie die korrekten Datenelemente verwenden, die Sie zuvor für Ihren Campaign-Server und Ihren pKey erstellt haben.

1. Klicken Sie auf das Kästchen, um einen POST-Hauptteil hinzuzufügen, und senden Sie Folgendes:

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
>* Es kann hilfreich sein, einen Slack-Web-Hook als zusätzliche Aktion einzurichten, um zu überprüfen, ob Einträge ausgelöst werden und die richtigen Daten erfasst werden.
>* Denken Sie daran, die letzten Änderungen an Ihrer App zu veröffentlichen, um sicherzustellen, dass die Regel und alle Ihre Datenelemente im Rahmen Ihrer Konfiguration bereitgestellt werden. Starten Sie nach der Veröffentlichung die Mobile App erneut, um die neuesten Konfigurationsaktualisierungen zu erhalten.

## Verwenden von Standortdaten für Campaign-Nachrichten

Nachdem wir nun Standortdaten in Campaign ausgefüllt haben, können wir POIs als Tool für Zielgruppensegmente verwenden.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Push-Benachrichtigung erstellen]**.
1. Wählen Sie für den Push-Benachrichtigungstyp **[!UICONTROL Push-Benachrichtigungen an Campaign-Profile senden]** aus.
1. Klicken Sie auf **[!UICONTROL Weiter]** und geben Sie die allgemeinen Details ein.
1. Klicken Sie im Bildschirm &quot;Zielgruppe&quot;auf **[!UICONTROL Zählung]** , um zu bestimmen, wie viele geschätzte Benutzer die Push-Benachrichtigung gesendet wird.

   >[!TIP]
   >
   >In diesem Beispiel beträgt die Anzahl 3, da es drei installierte Geräte gibt, auf denen die Anwendung getestet wird.

1. Erweitern Sie im linken Bereich die Registerkarte **[!UICONTROL Profil]** und ziehen Sie den Filter **[!UICONTROL POI-Position]** in den Hauptbereich.
1. Geben Sie im Fenster POI-Filter den genauen Namen des POI ein, der als Ziel ausgewählt werden soll.

   >[!TIP]
   >
   >Sie können zusätzliche Auswahlen vornehmen, um den Zeitraum seit dem letzten Besuch des Benutzers an diesem POI zu bestimmen.

   ![&quot;Push messaging 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.
1. Führen Sie die Zählung oben erneut aus, um die Änderung der Zielgruppengröße anzuzeigen.

   Wenn Ihre Anzahl nicht aktualisiert wird, haben Sie möglicherweise einen POI-Namen eingegeben, für den keine Geräte einen Eintrag ausgelöst haben. In dieser Situation wird der Slack-Webhook nützlich, da Sie eine Liste mit POI-Einträgen von verschiedenen Testgeräten sehen können.

1. Sie können zusätzliche POI-Standortfilter herausziehen, um mehrere POIs in Ihre Nachricht einzuschließen.
1. Klicken Sie auf **[!UICONTROL Weiter]**, um die Erstellung der Push-Benachrichtigung für die Bereitstellung abzuschließen.

   ![&quot;Push messaging 3 in ACS&quot;](/help/assets/ACS_push3.png)

Die Verwendung von Places Service mit Adobe Campaign Standard bietet Ihnen ein leistungsstarkes Tool, um Ihre Nachrichten basierend auf Geofeneinstiegen und -ausstiegen zu segmentieren und an Benutzer auszurichten. Diese Integration hilft Ihnen bei der Erstellung personalisierterer und kontextbezogener Anwendungsfälle.
