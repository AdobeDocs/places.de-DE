---
title: Push-Benachrichtigungen mit Places Service
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Places Service mit Push-Benachrichtigungen im Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 2%

---

# Push-Benachrichtigungen mit Places Service {#push-notifications}

In diesem Abschnitt erfahren Sie, wie Sie historische Informationen zur geografischen Lage verwenden können, um Push-Benachrichtigungen auszuwählen, die über Adobe Campaign Standard bereitgestellt werden.

## Voraussetzungen

Bevor Sie beginnen, führen Sie die folgenden Aufgaben aus:

* Lassen Sie eine Mobile App mit Adobe Experience Platform Mobile SDK konfigurieren, einschließlich der Erweiterung [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrieren Sie die [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
* Fügen Sie die [Adobe Campaign Standard-Erweiterung](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) zu Ihrer Mobile-App-Konfiguration hinzu.

* [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in der Verwaltungsoberfläche des Places Service-POI.

* Aktivieren und installieren Sie die [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Erstellen von Datenelementen im Experience Platform Launch

Nachdem Sie überprüft haben, ob die Places-Erweiterung und eine Lösung zur Regionsüberwachung ([CoreLocation-](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) für iOS oder [Android-Standortdokumentation](https://developer.android.com/training/location/geofencing)) in Ihrer Anwendung ordnungsgemäß funktionieren, müssen Sie Datenelemente im Experience Platform Launch erstellen. Datenelemente ermöglichen es Ihnen, die Informationen zu lesen, die von den Erweiterungen bereitgestellt wurden, die über den mobilen SDK Event Hub eingehen, und dienen als Alias zum Abrufen von Daten aus der Client-Anwendung. Um Daten aus den Places-Erweiterungen abzurufen und die Places Service-Informationen an Campaign zu senden, müssen Sie einige Datenelemente erstellen.

So erstellen Sie ein Datenelement:

1. Klicken Sie in der Eigenschaft für mobiles Experience Platform Launch auf die Registerkarte **[!UICONTROL Datenelemente]** und dann auf **[!UICONTROL Datenelement hinzufügen]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Places Service]** aus.
1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Datenelementtyp“ **[!UICONTROL Name]** aus.
1. Im rechten Bereich können Sie „Aktueller POI“ auswählen **[!UICONTROL wodurch der Name des POI abgerufen]**, in dem sich der Benutzer derzeit befindet.

   **[!UICONTROL Zuletzt eingegeben]** ruft den Namen des POI ab, den der Benutzer zuletzt eingegeben hat, und **[!UICONTROL Zuletzt beendet]** gibt den Namen des POI an, den der Benutzer zuletzt verlassen hat. In diesem Beispiel haben wir **[!UICONTROL Zuletzt eingegeben]** einen Namen für das Datenelement eingegeben, z. B. **[!UICONTROL Zuletzt eingegebener POI-Name]** und auf **[!UICONTROL Speichern]** geklickt.

   ![„Push-Messaging im Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Wiederholen Sie die Schritte 1-4 oben und erstellen Sie Datenelemente für *Zuletzt eingegeben POI-Breitengrad*, *Zuletzt eingegeben POI-* und *Zuletzt eingegeben POI-Radius*.

Stellen Sie sicher, dass Sie zusätzlich zu den Datenelementen für den Places-Service die mobilen Core-Datenelemente für *App-ID* und *Experience Cloud-ID* erstellen.

## Erstellen einer Regel zum Senden von Standortdaten an Adobe Campaign Standard

Regeln in Experience Platform Launch ermöglichen es Ihnen, komplexe Workflows mit mehreren Lösungen basierend auf Ereignis-Triggern zu erstellen. Mit Regeln können Sie neue Regeln erstellen oder vorhandene ändern und die Aktualisierungen dynamisch für Ihre Mobile Apps bereitstellen lassen. Im folgenden Beispiel wird die Regel ausgelöst, wenn ein Benutzer einen Geofencing-POI eingibt. Nachdem die Regel ausgelöst wurde, wird eine Aktualisierung an den Campaign Standard gesendet, um einen Eintrag für einen bestimmten Benutzer basierend auf der Experience Cloud-ID in einem bestimmten POI aufzuzeichnen.

1. Klicken Sie in der Eigenschaft für mobiles Experience Platform Launch auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Regel hinzufügen]**.
1. Klicken Sie **[!UICONTROL Abschnitt]** Ereignisse“ auf **[!UICONTROL +]** und wählen Sie **[!UICONTROL Places Service]** als Erweiterung aus.
1. Wählen Sie für **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL POI eingeben]** aus.
1. Benennen Sie die Regel, z. B. **Benutzer hat POI eingegeben**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.
1. Lassen Sie den **[!UICONTROL Bedingungen]** leer.

   In diesem Abschnitt können Sie filtern oder Einschränkungen festlegen, wann diese Regel ausgelöst werden soll.

1. Klicken Sie **[!UICONTROL Abschnitt]** Aktionen“ auf **[!UICONTROL +]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Mobile Core]** und in der Dropdown-Liste **[!UICONTROL Aktionstyp]** die Option **[!UICONTROL Postback senden]**.
1. In **[!UICONTROL URL]** müssen Sie Ihren Campaign Standard Locations-Endpunkt erstellen.

   Die URL sollte in etwa wie `https:///rest/head/mobileAppV5//locations/` aussehen.
Stellen Sie sicher, dass Sie die richtigen Datenelemente verwenden, die Sie zuvor für Ihren Campaign-Server und Ihren pKey erstellt haben.

1. Klicken Sie auf das Kästchen, um einen POST-Textkörper hinzuzufügen und Folgendes zu senden:

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

1. Stellen Sie sicher, dass Sie Datenelemente verwenden, die Sie im vorherigen Abschnitt erstellt haben.
1. Geben Sie unter **[!UICONTROL Content-Typ]** den Wert **[!UICONTROL application/json]** ein.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

>[!IMPORTANT]
>
>* Es kann hilfreich sein, einen Slack-Webhook als zusätzliche Aktion einzurichten, um zu überprüfen, ob Einträge ausgelöst werden und ob die richtigen Daten erfasst werden.
>* Denken Sie daran, die letzten Änderungen an Ihrer App zu veröffentlichen, um sicherzustellen, dass die Regel und alle Ihre Datenelemente als Teil Ihrer Konfiguration bereitgestellt werden. Starten Sie die Mobile App nach der Veröffentlichung erneut, um die neuesten Konfigurationsaktualisierungen zu erhalten.

## Standortdaten für das Targeting von Campaign-Nachrichten verwenden

Nachdem wir nun Standortdaten in Campaign ausgefüllt haben, können wir POIs als Zielgruppensegment-Tool verwenden.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Push-Benachrichtigung erstellen]**.
1. Wählen Sie als Typ der Push-Benachrichtigung die Option **[!UICONTROL Push an Campaign-Profile senden]**.
1. Klicken Sie **[!UICONTROL Weiter]** und geben Sie die allgemeinen Details ein.
1. Klicken Sie auf dem Bildschirm Zielgruppe auf **[!UICONTROL Anzahl]**, um zu bestimmen, wie viele geschätzte Benutzer die Push-Benachrichtigung gesendet werden soll.

   >[!TIP]
   >
   >In diesem Beispiel beträgt die Anzahl 3, da drei Geräte installiert sind, auf denen die Anwendung getestet wird.

1. Erweitern Sie im linken Bereich die Registerkarte **[!UICONTROL Profil]** und ziehen Sie den **[!UICONTROL POI-Standort]**-Filter in den Hauptbereich.
1. Geben Sie im Fenster POI-Filter den genauen Namen des POI ein, den Sie ansprechen möchten.

   >[!TIP]
   >
   >Sie können zusätzliche Auswahlen treffen, um den Zeitraum seit dem vorherigen Besuch des Benutzers bei diesem POI zu bestimmen.

   ![„Push-Messaging 2 in ACS“](/help/assets/ACS_push2.png)

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.
1. Führen Sie die Anzahl oben erneut aus, um die Änderung der Zielgruppengröße zu sehen.

   Wenn die Aktualisierung der Zählung nicht angezeigt wird, haben Sie möglicherweise einen POI-Namen eingegeben, für den kein Gerät einen Eintrag ausgelöst hat. Der Slack-Webhook wird in dieser Situation nützlich, da Sie eine Liste von POI-Einträgen von verschiedenen Testgeräten sehen können.

1. Sie können zusätzliche POI-Standortfilter ziehen, um mehrere POIs in Ihre Nachricht aufzunehmen.
1. Klicken Sie auf **[!UICONTROL Weiter]**, um die Erstellung der Push-Benachrichtigung für die Bereitstellung abzuschließen.

   ![„Push-Messaging 3 in ACS“](/help/assets/ACS_push3.png)

Die Verwendung des Places Service mit Adobe Campaign Standard bietet Ihnen ein leistungsstarkes Tool, mit dem Sie Ihre Nachrichten segmentieren und basierend auf geografischen Ein- und Ausstiegen zielgerichtet an Benutzende senden können. Mit dieser Integration können Sie personalisiertere und kontextuellere Anwendungsfälle erstellen.
