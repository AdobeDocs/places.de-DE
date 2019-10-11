---
title: Verwenden von Orten mit Adobe Campaign Standard
seo-title: Verwenden von Orten mit Adobe Campaign Standard
description: Ein tiefergehendes Verständnis Ihrer Kundenpräferenzen und -gewohnheiten ist der Schlüssel zu jeder erfolgreichen Marketingkampagne. Wenn Sie wissen, ob ein Benutzer einen physischen Ort besucht hat, können Sie auch einen sehr wertvollen Kontext zur Herstellung einer Beziehung mit dem Verbraucher hinzufügen.
seo-description: Ein tiefergehendes Verständnis Ihrer Kundenpräferenzen und -gewohnheiten ist der Schlüssel zu jeder erfolgreichen Marketingkampagne. Wenn Sie wissen, ob ein Benutzer einen physischen Ort besucht hat, können Sie auch einen sehr wertvollen Kontext zur Herstellung einer Beziehung mit dem Verbraucher hinzufügen.
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Verwenden von Orten mit Adobe Campaign Standard {#places-with-acs}

*Vielen Dank, dass Sie uns letzte Woche besucht haben, wir würden Ihnen gerne eine Überraschung für Ihren nächsten Besuch geben!*

Ein tiefergehendes Verständnis Ihrer Kundenpräferenzen und -gewohnheiten ist der Schlüssel zu jeder erfolgreichen Marketingkampagne. Die Elemente, nach denen ein Benutzer gesucht hat, und der vorherige Kaufverlauf spielen eine große Rolle beim Zielgruppen-Targeting. Wenn Sie wissen, ob ein Benutzer einen physischen Ort besucht hat, können Sie auch einen sehr wertvollen Kontext zur Herstellung einer Beziehung mit dem Verbraucher hinzufügen.

Laut einem aktuellen Bericht von eMarketer halten 85 % der leistungsstarken Einzelhändler den Standort für sehr wichtig für ihre Marketingbemühungen. Darüber hinaus planen über 58 % der Einzelhändler in Nordamerika, in räumliche Nähe/Standort-Technologien zu investieren, um ihre Kundenerfahrung zu verbessern.

![](/help/assets/using-loc-services-acs_0.png)

Denken Sie darüber nach, an welcher kritischen Position Ihr Smartphone genutzt wird. Wie oft bitten Sie Ihr Smartphone, in der Nähe Restaurants, Tankstellen, Lebensmittelgeschäfte oder andere Dienstleistungen zu finden.

Es ist daher sinnvoll, als Marke darüber nachzudenken, wie Sie Standort in Ihre Marketingkampagnen einbinden können. In diesem Leitfaden zeigen wir Ihnen, wie Sie die Leistungsfähigkeit des Experience Platform Experience Platform Platform Location Service nutzen können, um über Adobe Campaign Standard Ortskontext zu Messaging hinzuzufügen. So können Sie personalisierte Push-Benachrichtigungen oder In-App-Nachrichten basierend auf einem POI-Eintrag (historischer Point of Interest) ausblenden.

Bevor wir beginnen, geht dieses Handbuch davon aus, dass Sie über eine mobile Anwendung verfügen, die mit dem Adobe Experience Platform Mobile SDK mit der Adobe Campaign Standard-Erweiterung konfiguriert wurde. Zusätzlich zu Adobe Experience Platform Mobile SDK und Campaign Standard sollten Sie Zugriff auf Experience Platform Location Service haben.

## Voraussetzungen  

1. Integrieren Sie das [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in Ihre App.
1. Fügen Sie Ihrer App-Konfiguration die [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) hinzu.
1. [Erstellen Sie einen oder mehrere POIs](/help/places-database-management-1/managing-pois-in-the-places-ui.md).

>[!TIP]
>
>Wenn Sie Wege zum Massen-Upload oder zur Verwaltung von POIs suchen, sehen Sie sich dieses [Skript an, um POIs aus einer CSV](https://github.com/adobe/places-scripts) -Datei hochzuladen. Darüber hinaus können die [Orte-APIs](/help/places-rest-apis/api-usage/api-usage.md) zum Erstellen oder Verwalten von Zielpunkten verwendet werden.

Wenn Sie keinen Zugriff auf Orte haben, können Sie hier den Zugriff [anfordern](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u).

### Aktivieren und Installieren der Platzierungserweiterungen in Ihrer Anwendung

Nachdem Sie Punkte erstellt haben, die für Sie von Interesse sind, müssen Sie der Anwendung die Funktion Orte hinzufügen.

1. Befolgen Sie die Anweisungen zum Aktivieren der Erweiterungen "Orte und Orte-Monitor"in Ihrer Anwendung.
1. Vergewissern Sie sich, dass Sie in der Plates-Erweiterung die entsprechende Bibliothek der zuvor erstellten POIs ausgewählt haben.

   Zusätzliche Bibliotheken können jederzeit zur Erweiterungskonfiguration hinzugefügt werden.

1. Vergewissern Sie sich, dass Sie diese Konfigurationen zu einer Bibliothek hinzugefügt und die Konfigurationsänderungen in Launch veröffentlicht haben.
1. Klicken Sie auf der Registerkarte " **[UICONTROL-Startumgebungen]** "auf das Symbol "Installationsanweisungen", um Anweisungen zum Herunterladen der entsprechenden CocoaPod- und Gradle-Dateien in Ihr App-Projekt anzuzeigen.
1. Befolgen Sie in Ihrer Anwendung die Anweisungen zum Hinzufügen des Location-Hintergrundmodus zu Ihrer Anwendung und starten Sie den Orts-Standortmonitor.
1. Testen Sie Ihre Anwendung über einen Gerätesimulator, um die Anwendungsanforderung an nahe gelegenen Orten anzuzeigen, die vom Standort des Geräts abhängen.

### Erstellen von Datenelementen in Experience Platform Launch

Nachdem Sie überprüft haben, ob die Erweiterungen "Orte und Orte überwachen"in Ihrer Anwendung ordnungsgemäß funktionieren, erstellen Sie Datenelemente in Experience Platform Launch, um die Informationen zu lesen, die von den Erweiterungen bereitgestellt werden und die über den Mobile SDK-Ereignis-Hub gelangen. Datenelemente dienen im Wesentlichen als Alias zum Abrufen von Daten aus der Clientanwendung. Erstellen wir einige Datenelemente, um Daten aus den Platzierungs-Erweiterungen abzurufen.

1. Klicken Sie in der Eigenschaft Experience Platform Launch mobile auf der **[!UICONTROL Data Elements]** Registerkarte auf **[!UICONTROL Add Data Element]**.
1. Wählen Sie im Erweiterungsmenü **[!UICONTROL Places]**.
1. Wählen Sie aus der **[!UICONTROL Data Element]** Dropdownliste **[!UICONTROL-Name}**.
1. Im Fenster auf der rechten Seite können Sie auswählen, **[!UICONTROL Current POI]** welcher den Namen des POI abruft, in dem sich der Benutzer gerade befindet.

   * **[!UICONTROL Last Entered]** ruft den Namen der POI ab, bei der der Benutzer zuletzt eine
   * **[!UICONTROL Last Exited]** gibt den Namen des POI an, das der Benutzer zuletzt verlassen hat.

1. Select **[!UICONTROL Last Entered]**.
1. Geben Sie einen Namen für das Datenelement ein, z. B. **[!UICONTROL Last Entered POI Name]** und klicken Sie auf **[!UICONTROL Save]**.


   ![](/help/assets/using-loc-services-acs_1.png)

1. Wiederholen Sie die obigen Schritte und erstellen Sie Datenelemente für *Letzter eingegebener POI-Breitengrad*, *Letzte eingegebene POI-Längengrad* und *Letzter eingegebener POI-Radius*.

Zusätzlich zu den Datenelementen für Orte müssen Sie auch Mobile-Core-Datenelemente für *App-ID* und *Experience Cloud-ID* erstellt haben.

### Regel zum Senden von Standortdaten an Adobe Campaign Standard erstellen

Regeln in Experience Platform Launch ermöglichen Ihnen das Erstellen komplexer Arbeitsabläufe mit mehreren Lösungen basierend auf Ereignisauslösern. Sie können neue Regeln erstellen oder Änderungen an bestehenden Regeln vornehmen und die Updates dynamisch für Ihre mobilen Anwendungen bereitstellen. In diesem Beispiel erstellen wir eine Regel, die ausgelöst wird, wenn ein Benutzer einen Geofencing-POI aufruft. Nachdem die Regel ausgelöst wurde, wird ein Update an Campaign Standard gesendet, um einen Eintrag für einen bestimmten POI für den Benutzer aufzuzeichnen. Dieser POI basiert auf der Experience Cloud ID.

1. Klicken Sie in der Eigenschaft Experience Platform Launch mobile auf die **[!UICONTROL Rules]** Registerkarte und dann auf **[!UICONTROL Add Rule]**.
1. Klicken Sie im **[!UICONTROL Events]** Abschnitt auf **[!UICONTROL +]** und wählen Sie **[!UICONTROL Places]**.
1. Wählen Sie **[!UICONTROL Event Type]** in **[!UICONTROL Enter POI]**.
1. Geben Sie beispielsweise einen Namen für die Regel ein **[!UICONTROL User entered POI]**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.
1. Lassen Sie den **[!UICONTROL Conditions]** Abschnitt leer.

   In diesem Abschnitt können Sie filtern oder Einschränkungen festlegen, wann diese Regel ausgelöst werden soll.

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. Wählen Sie **[!UICONTROL Extension]** in **[!UICONTROL Mobile Core]** und **[!UICONTROL Action Type]** wählen Sie **[!UICONTROL Send Postback]**.

1. Für die URL müssen Sie den Endpunkt "Campaign Standard-Standorte"erstellen.

   Die URL sollte ähnlich wie die unten stehende aussehen. Vergewissern Sie sich, dass Sie die korrekten Datenelemente verwenden, die Sie zuvor für Ihren Campaign-Server und Ihren pKey erstellt haben.

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. Klicken Sie auf das Feld, um einen Beitragstext hinzuzufügen und senden Sie Folgendes:

   ```text
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

1. Verwenden Sie die spezifischen Datenelemente, die Sie im vorherigen Abschnitt erstellt haben.
1. Geben Sie in **[!UICONTROL Content Type]** ein **[!UICONTROL application/json]**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]** , nachdem Sie diese Einrichtung eingerichtet haben.

   Es kann hilfreich sein, einen Slack-Web-Haken als zusätzliche Aktion einzurichten, um zu überprüfen, ob meine Aktion ausgelöst wird und ob die richtigen Daten erfasst werden.

   >[!IMPORTANT]
   >
   >Denken Sie daran, die letzten Änderungen an Ihrer App zu veröffentlichen, um sicherzustellen, dass die Regel und alle Datenelemente im Rahmen Ihrer Konfiguration bereitgestellt werden. Nach der Veröffentlichung sollten Sie die Mobilanwendung neu starten, um die neuesten Konfigurationsaktualisierungen zu erhalten.

### Verwenden von Standortdaten zum Targeting von Campaign-Standardmeldungen

Nachdem wir nun Ortsdaten in Campaign ausgefüllt haben, können wir Zielpunkte als Tool für Zielgruppensegmente verwenden.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[UICONTROL Push-Benachrichtigung]** erstellen.
1. Wählen Sie für den Typ "Push-Benachrichtigung"die Option "Push- **[an App-Abonnenten]** senden"aus.

   Dieser Push-Typ richtet sich an alle Benutzer Ihrer Anwendung. Wenn Ihre mobilen Benutzer an ein Kampagnenprofil angehängt sind, können Sie auch " **[UICONTROL Push an Kampagnenprofile]** i senden"auswählen.

1. Klicken Sie auf **[!UICONTROL Next]** und geben Sie im nächsten Bildschirm die allgemeinen Details ein.
1. Klicken Sie im Anzeigebereich "Zielgruppe"auf **[!UICONTROL Count]** , um zu ermitteln, wie viele Benutzer die Push-Benachrichtigung gesendet werden soll.

   In diesem Fall beträgt die Anzahl 3, da in der Testanwendung drei Geräte installiert sind.

1. Erweitern Sie auf der linken Seitenleiste die **[!UICONTROL Profile]** Registerkarte und ziehen Sie den **[!UICONTROL POI location]** Filter auf den Hauptbereich.
1. Geben Sie im Fenster "POI-Filter"den genauen Namen des POI ein, für das Sie ein Targeting vornehmen möchten.

   Sie können zusätzliche Auswahlen vornehmen, um den Zeitraum seit dem letzten Besuch des Benutzers an diesem POI zu bestimmen.

   ![](/help/assets/using-loc-services-acs_2.png)

1. Klicken Sie auf [!**UICONTROL Confirm]**
1. Führen Sie die Zählung erneut oben aus, um eine Änderung der Zielgruppengröße zu sehen.

   Wenn Sie Ihre Zähleraktualisierung nicht sehen, haben Sie möglicherweise einen POI-Namen eingegeben, für den keine Geräte einen Eintrag ausgelöst haben. Hier wird der Slack-Web-Haken wertvoll, da Sie eine Liste der POI-Einträge von verschiedenen Testgeräten sehen können.
1. Sie können weitere POI-Ortsfilter ziehen, um mehrere POIs in Ihre Nachricht einzuschließen.
1. Klicken Sie auf **[!UICONTROL Next]** , um die Erstellung der Push-Benachrichtigung für die Bereitstellung abzuschließen.

   ![](/help/assets/using-loc-services-acs_3.png)

Neben Push-Benachrichtigungen können Sie auch Standortdaten verwenden, um zu segmentieren, welche Benutzer eine In-App-Nachricht erhalten sollen.

1. Klicken Sie in Ihrer Adobe Campaign Standard-Instanz auf **[!UICONTROL Create In-App message]**.
1. Wählen Sie für den Nachrichtentyp **[!UICONTROL Target all users of a Mobile application]**.
1. Klicken Sie auf **[!UICONTROL Next]** und geben Sie im nächsten Bildschirm die allgemeinen Details ein.
1. Überprüfen Sie im linken Bereich, ob Sie jetzt eine Vielzahl von Auslösern für Orte verwenden können.
1. Wenn der Benutzer einen POI-Geo-Zaun eingegeben hat, können Sie festlegen, dass die In-App-Nachricht angezeigt werden soll.

   Sie können auch Metadaten verwenden, die Sie in der Benutzeroberfläche "Orte"definiert haben, um Ihre Zielgruppe zu filtern. In diesem Beispiel möchte ich eine In-App-Nachricht auslösen, die nur Benutzern angezeigt wird, die zuletzt einen POI verlassen haben, der auch eine Gym-Funktion hatte. Vielleicht möchte ich ihnen eine Umfrage schicken, um zu sehen, ob sie die Fitnessstudio verwendet/gefallen haben.

1. Klicken Sie auf , **[!UICONTROL Next]** um die In-App-Nachricht für die Bereitstellung zu erstellen.

   ![](/help/assets/using-loc-services-acs_4.png)

Die Verwendung von Orten mit Adobe Campaign Standard bietet Ihnen ein leistungsfähiges Tool, um Ihre Nachrichten zu segmentieren und gezielt an Benutzer basierend auf dem historischen Standort auszurichten. Diese einfache Integration öffnet die Tür zum Aufbau von personalisierteren und kontextbezogenen Anwendungsfällen.

Wir verbessern ständig die Platzierungen und die integrierten Lösungen, um Standortkontexte in mobile Arbeitsabläufe zu integrieren. Ein Produkt, das Places nutzen wird, ist die bevorstehende Lösung von "Ausgelöste Reise", mit der Kunden Echtzeit-Arbeitsabläufe erstellen können, die auf Ereignisauslösern wie dem Standort basieren.

## Empfohlene Links

Weitere Informationen finden Sie unter:

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard ](https://www.adobe.com/marketing/campaign.html)
* [Anmelden für den Zugriff auf Adobe Places Beta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Integration von Adobe Campaign in Experience Platform SDK](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
