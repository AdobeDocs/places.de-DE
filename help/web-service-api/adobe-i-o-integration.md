---
title: Überblick über die Adobe-E/A-Integration
description: Informationen zum Erstellen einer Adobe I/O-Integration.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# Übersicht über die Integration und Voraussetzungen {#integration-prereqs}

Diese Informationen zeigen Ihnen, wie Sie eine Adobe-E/A- und eine Orte-Service-Integration erstellen.

## Voraussetzungen für den Benutzerzugriff

Vergewissern Sie sich beim Systemadministrator Ihres Unternehmens, dass die folgenden Aufgaben abgeschlossen wurden:

* Der Orte-Core-Service wird in der Admin-Konsole Ihres Unternehmens angezeigt.
* Sie wurden der Organisation hinzugefügt.
* Sie wurden als Benutzer zum Platzierungs-Core-Service in Ihrem Unternehmen hinzugefügt.

   Weitere Informationen finden Sie unter Benutzer oder Entwickler *zu den Profilen* &quot;Orte-Dienst&quot;und &quot;Erlebnisplattform&quot;hinzufügen unter Zugriff [auf den Places-Dienst](/help/places-gain-access.md).

* Sie wurden als Entwickler zum Platzierungs-Core-Service in Ihrem Unternehmen hinzugefügt.

   Weitere Informationen zum Hinzufügen von Entwicklern finden Sie unter Benutzer oder Entwickler zu den Profilen *&quot;Orte-Dienst&quot;und &quot;Erlebnisplattform&quot;* hinzufügen unter Zugriff [auf den Orte-Dienst](/help/places-gain-access.md).

   Weitere Informationen zur Rolle &quot;Entwickler&quot;finden Sie unter Entwickler [verwalten](https://helpx.adobe.com/enterprise/using/manage-developers.html).

### REST-API-Anfragen

Für jede Anforderung an die REST-API des Places-Dienstes sind die folgenden Elemente erforderlich:

* Eine Organisations-ID
* Ein API-Schlüssel
* Ein InhaberToken

Eine Integration mit Adobe I/O bietet diese Elemente und eine Möglichkeit, das Inhabertoken mithilfe eines JSON-WebTokens (JWT) anzufordern.

* Weitere Informationen zu JWTs finden Sie unter [Einführung in JSON-WebToken](https://jwt.io/introduction/).
* Informationen zum Erstellen einer Integration für den Places-Dienst finden Sie im Abschnitt zur Integration *des* Platzierungsdienstes.
* Informationen zur Integration von API-Schlüsseln, zum Generieren von JWT-Zertifikaten und Zertifikaten öffentlicher Schlüssel finden Sie unter Übersicht über die [Adobe-E/A-Authentifizierung](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei der Adobe I/O-Konsole anmelden können oder wenn der Platzierungsdienst keine Option auf der Seite &quot;Integrationen *erstellen&quot;ist*, finden Sie Informationen zu den Anforderungen *der* Organisation in der Übersicht über die [Web-Services-APIs](/help/web-service-api/places-web-services.md).

## Integration des Orte-Dienstes erstellen

Führen Sie die folgenden Aufgaben aus, um eine Integration des Places-Dienstes zu erstellen:

### Generieren eines öffentlichen und privaten Schlüsselpaars

Um eine Integration des Platzierungsdienstes zu erstellen, benötigen Sie ein öffentliches und ein privates Schlüsselpaar. Diese Paare können gekauft werden oder Sie können eigene, selbstsignierte Schlüssel erstellen.

So generieren Sie eigene, selbstsignierte Schlüssel:

1. Kopieren Sie die folgenden Zeilen in ein Terminalfenster und fügen Sie sie ein und drücken Sie **[!UICONTROL Enter]**nach dem Einfügen der einzelnen Zeilen die Eingabetaste:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Es wird empfohlen, die Schlüssel zur einfachen Referenz zu benennen und in einem Ordner zu speichern. Wenn Sie mehrere Integrationen erstellen, können Sie einfach identifizieren und verwalten, welche Schlüssel zu welcher Integration gehören.

1. Geben Sie die von OpenSSL angeforderten Informationen ein:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Weitere Informationen zu OpenSSL finden Sie unter [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >Die von Ihnen bereitgestellten Informationen sind in die Schlüssel eingebunden.

1. Navigieren Sie zu dem Ordner, in dem sich die Dateien `.key` und `.crt` Dateien befinden.

   Gehen Sie in MacOS beispielsweise zu **[!UICONTROL Macintosh HD]**>**[!UICONTROL users]** > **[!UICONTROL (your user name)]**>**[!UICONTROL Keys]**.

Das folgende Video führt Sie durch den Prozess der Generierung des Schlüsselpaars:

![Integrationsvideo](/help/assets/places_integration_video.gif)

### Erstellen einer Integration des Places Service in der Adobe I/O-Konsole

So erstellen Sie eine Integration des Places-Dienstes:

1. Wechseln Sie zu [https://console.adobe.io](https://console.adobe.io) und melden Sie sich mit Ihrer Adobe ID an.
1. Klicken Sie im Abschnitt **Kurzanleitung** auf Integration **erstellen**.
1. Wählen Sie **[!UICONTROL Access an API]**und klicken Sie auf**[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]**ist der Standardspeicherort.

1. Wenn Sie Zugriff auf mehr als eine Experience Cloud-Organisation haben, wählen Sie die Organisation in der Dropdownliste oben rechts aus.
1. Under **[!UICONTROL Experience Cloud]**, select**[!UICONTROL Places Service]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. Wählen Sie **[!UICONTROL New integration]**und klicken Sie auf**[!UICONTROL Continue]**.
1. Geben Sie im Bildschirm &quot;Neue Integration erstellen&quot;einen Namen und eine Beschreibung ein.
1. Ziehen Sie die oben erstellte `xxxx_public.crt` Datei in den **[!UICONTROL Public keys certificates]**Ablagebereich.
1. Wählen Sie ein Produktprofil aus.

   Wenn Sie sich nicht sicher sind, welches Profil Sie auswählen möchten, wenden Sie sich an Ihren Systemadministrator.
1. At the bottom of the page, click **[!UICONTROL Create integration]**.
1. Überprüfen Sie nach einigen Sekunden im Bildschirm *Integration erstellt* , ob folgende Meldung angezeigt wird:

   `Your integration has been created.`

1. Die Seite mit den Integrationsdetails wird oben mit dem Namen der Integration angezeigt.

   Die **[!UICONTROL Overview]**Registerkarte wird standardmäßig angezeigt und enthält den API-Schlüssel, Ihre Organisations-ID, die technische Konto-ID und weitere Details zu Ihren Integrationen.

### Unternehmen-ID und API-Schlüssel aufzeichnen

1. Klicken Sie auf der Seite mit den Integrationsdetails auf die **[!UICONTROL Services]**Registerkarte und bestätigen Sie, dass diese angezeigt**[!UICONTROL Places Service]** wird **[!UICONTROL Configured Services]**.
1. Suchen Sie auf der **[!UICONTROL Overview]**Registerkarte den API-Schlüssel (Client-ID) und die Organisations-ID und zeichnen Sie ihn auf.

   Diese IDs werden für jede REST-API-Anforderung des Places-Dienstes benötigt.

![](/help/assets/places_orgid_api-key.png)

### JWT-Token erstellen

Klicken Sie auf der Seite mit den Integrationsdetails auf die **[!UICONTROL JWT]**Registerkarte, damit Sie Ihre Integration testen können, indem Sie eine JWT generieren und die Austausch-URL angeben.

So generieren Sie ein JWT-Token:

1. Öffnen Sie die oben erstellte `private.key` Datei in einem Texteditor.
1. On the **[!UICONTROL JWT]**tab, copy the contents of the key and paste it in the**[!UICONTROL Paste private key]** field.
1. Klicken Sie auf **[!UICONTROL Generate JWT]**.
1. In the **[!UICONTROL Sample CURL command]**section, click**[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. Führen Sie den Befehl aus, indem Sie **[!UICONTROL Enter]**auf die Tastatur drücken.
1. Suchen Sie den Wert `"token_type": "bearer"` und den `"access_token"` Wert.

   Der Wert des Inhaberzugriffszeichens ist der Wert, den Sie in Ihren Places Service API-Anforderungen verwenden werden.

>[!IMPORTANT]
>
>Adobe-Zugriffstoken sind **nur** 24 Stunden gültig. Speichern Sie daher den CURL-Beispielbefehl (Schritt 5). Wenn das Zugriffstoken nicht mehr gültig ist, müssen Sie das Token neu generieren.