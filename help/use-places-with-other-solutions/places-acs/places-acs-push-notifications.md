---
title: Push-Benachrichtigungen mit dem Places-Dienst
description: Dieser Abschnitt enthält Informationen zur Verwendung des Places-Dienstes mit Push-Benachrichtigungen in Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---

# Push-Benachrichtigungen mit dem Places-Dienst {#push-notifications}

In diesem Abschnitt erfahren Sie, wie Sie historische Geostandortinformationen für Push-Benachrichtigungen verwenden, die über Adobe Campaign Standard bereitgestellt werden.

## Voraussetzungen

Führen Sie zunächst die folgenden Aufgaben aus:

* Sie müssen eine Mobile App mit dem Adobe Experience Platform Mobile SDK konfigurieren, einschließlich der Variablen [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrieren Sie die [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App ein.
* Fügen Sie die [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) in Ihre App-Konfiguration.

* [POI erstellen](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche für POI des Places-Dienstes.

* Aktivieren und Installieren der [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Erstellen von Datenelementen in Experience Platform Launch

Nachdem Sie überprüft haben, ob die Places-Erweiterung und eine Region-Monitoring-Lösung ([Dokumentation zu CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Dokumentation zur Android-Position](https://developer.android.com/training/location/geofencing)) in Ihrer Anwendung ordnungsgemäß funktionieren, müssen Sie Datenelemente in Experience Platform Launch erstellen. Datenelemente ermöglichen es Ihnen, die Informationen zu lesen, die von den Erweiterungen bereitgestellt wurden, die über den Mobile SDK-Ereignis-Hub gelangen, und als Alias zum Abrufen von Daten aus der Client-Anwendung zu fungieren. Um Daten aus den Places-Erweiterungen abzurufen und die Places-Dienst-Informationen an Campaign zu senden, müssen Sie einige Datenelemente erstellen.

Erstellen eines Datenelements:

1. Klicken Sie in der Eigenschaft für Ihr Experience Platform Launch-Mobilgerät auf die **[!UICONTROL Datenelemente]** Registerkarte und klicken Sie auf **[!UICONTROL Datenelement hinzufügen]**.
1. Im **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Places Service]**.
1. Aus dem **[!UICONTROL Datenelementtyp]** Dropdown-Liste auswählen **[!UICONTROL Name]**.
1. Im rechten Seitenbereich können Sie **[!UICONTROL Aktueller POI]** , der den Namen des POI abruft, an dem sich der Benutzer derzeit befindet.

   **[!UICONTROL Zuletzt eingegeben]** ruft den Namen des POI ab, den der Benutzer zuletzt eingegeben hat, und **[!UICONTROL Zuletzt beendet]** gibt den Namen des POI an, den der Benutzer zuletzt verlassen hat. In diesem Beispiel haben wir **[!UICONTROL Zuletzt eingegeben]** und gab einen Namen für das Datenelement ein, z. B. **[!UICONTROL Letzter eingegebener POI-Name]** und geklickt **[!UICONTROL Speichern]**.

   ![&quot;Push-Nachrichten in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Wiederholen Sie die Schritte 1 bis 4 und erstellen Sie Datenelemente für *Letzter eingegebener POI-Breitengrad*, *Letzte eingegebene POI-Längengrad* und *Letzter eingegebener POI-Radius*.

Stellen Sie neben den Datenelementen für den Places-Dienst sicher, dass Sie Mobile Core-Datenelemente für *App-ID* und *Experience Cloud-ID*.

## Erstellen einer Regel zum Senden von Standortdaten an Adobe Campaign Standard

Mit Regeln in Experience Platform Launch können Sie komplexe, lösungsübergreifende Workflows erstellen, die auf Ereignis-Triggern basieren. Mit Regeln können Sie neue Regeln erstellen oder vorhandene ändern und die Aktualisierungen dynamisch für Ihre Mobile Apps bereitstellen. Im folgenden Beispiel wird die Regel ausgelöst, wenn ein Benutzer einen geo-fencing-POI betritt. Nachdem die Regel ausgelöst wurde, wird eine Aktualisierung an den Campaign Standard gesendet, um einen Eintrag für einen bestimmten Benutzer basierend auf der Experience Cloud-ID an einen bestimmten POI aufzuzeichnen.

1. In der Eigenschaft für Mobilgeräte Ihres Experience Platform Launchs auf der **[!UICONTROL Regeln]** Registerkarte, klicken Sie auf **[!UICONTROL Regel hinzufügen]**.
1. Unter dem **[!UICONTROL Veranstaltungen]** Abschnitt, klicken Sie auf **[!UICONTROL +]** und wählen Sie **[!UICONTROL Places Service]** als Erweiterung.
1. Für **[!UICONTROL Ereignistyp]** auswählen **[!UICONTROL POI eingeben]**.
1. Benennen Sie die Regel, z. B. **Benutzer hat POI eingegeben**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.
1. Lassen Sie die **[!UICONTROL Bedingungen]** leer sein.

   In diesem Abschnitt können Sie filtern oder Einschränkungen dafür platzieren, wann diese Regel ausgelöst werden soll.

1. Unter dem **[!UICONTROL Aktionen]** Abschnitt, klicken Sie auf **[!UICONTROL +]**.
1. Im **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Mobile Core]** und im **[!UICONTROL Aktionstyp]** Dropdown-Liste auswählen **[!UICONTROL Postback senden]**.
1. In **[!UICONTROL URL]** müssen Sie den Endpunkt Ihrer Campaign Standard-Standorte erstellen.

   Die URL sollte in etwa wie folgt aussehen: `https:///rest/head/mobileAppV5//locations/`.
Stellen Sie sicher, dass Sie die korrekten Datenelemente verwenden, die Sie zuvor für Ihren Campaign-Server und Ihren pKey erstellt haben.

1. Klicken Sie auf das Kästchen, um einen POST-Hauptteil hinzuzufügen und Folgendes zu senden:

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
1. Wählen Sie für den Push-Benachrichtigungstyp die Option **[!UICONTROL Push-Benachrichtigungen an Campaign-Profile senden]**.
1. Klicken **[!UICONTROL Nächste]** und geben Sie die allgemeinen Details ein.
1. Klicken Sie im Bildschirm &quot;Zielgruppe&quot;auf **[!UICONTROL Count]** , um zu bestimmen, wie viele geschätzte Benutzer die Push-Benachrichtigung senden wird.

   >[!TIP]
   >
   >In diesem Beispiel beträgt die Anzahl 3, da es drei installierte Geräte gibt, auf denen die Anwendung getestet wird.

1. Erweitern Sie im linken Bereich den **[!UICONTROL Profil]** und ziehen Sie die **[!UICONTROL POI-Position]** in den Hauptbereich filtern.
1. Geben Sie im Fenster POI-Filter den genauen Namen des POI ein, der als Ziel ausgewählt werden soll.

   >[!TIP]
   >
   >Sie können zusätzliche Auswahlen vornehmen, um den Zeitraum seit dem letzten Besuch des Benutzers an diesem POI zu bestimmen.

   ![&quot;Push messaging 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.
1. Führen Sie die Zählung oben erneut aus, um die Änderung der Zielgruppengröße anzuzeigen.

   Wenn Ihre Anzahl nicht aktualisiert wird, haben Sie möglicherweise einen POI-Namen eingegeben, für den keine Geräte einen Eintrag ausgelöst haben. In dieser Situation wird der Slack-Web-Hook nützlich, da Sie eine Liste mit POI-Einträgen von verschiedenen Testgeräten sehen können.

1. Sie können zusätzliche POI-Standortfilter herausziehen, um mehrere POIs in Ihre Nachricht einzuschließen.
1. Klicken Sie auf **[!UICONTROL Weiter]**, um die Erstellung der Push-Benachrichtigung für die Bereitstellung abzuschließen.

   ![&quot;Push messaging 3 in ACS&quot;](/help/assets/ACS_push3.png)

Die Verwendung von Places Service mit Adobe Campaign Standard bietet Ihnen ein leistungsstarkes Tool, um Ihre Nachrichten basierend auf Geofeneinstiegen und -ausstiegen zu segmentieren und an Benutzer auszurichten. Diese Integration hilft Ihnen bei der Erstellung personalisierterer und kontextbezogener Anwendungsfälle.
