---
title: Überblick über die Adobe-E/A-Integration
seo-title: Überblick über die Adobe-E/A-Integration
description: Informationen zum Erstellen einer Adobe I/O-Integration.
seo-description: Informationen zum Erstellen einer Adobe-E/A-Integration.
translation-type: tm+mt
source-git-commit: 6ff72eb72ce3ae1abf805b7b542721a7e4915824

---


# Überblick über die Adobe-E/A-Integration {#adobeio-integration}

Für jede Anforderung an die Places REST API sind die folgenden Elemente erforderlich:

* Eine Organisations-ID
* Ein API-Schlüssel
* Ein InhaberToken

Eine Integration mit Adobe I/O bietet diese Elemente und eine Möglichkeit, das Inhabertoken mithilfe eines JSON-WebTokens (JWT) anzufordern.

## Weitere Informationen

* Weitere Informationen zu JWTs finden Sie unter [Einführung in JSON-WebToken](https://jwt.io/introduction/).
* Informationen zum Erstellen einer Integration für Orte finden Sie im Abschnitt *Erstellen einer Platzierungsintegration* unten.
* Informationen zur Integration von API-Schlüsseln, zum Generieren von JWT-Zertifikaten und Zertifikaten öffentlicher Schlüssel finden Sie unter Übersicht über die [Adobe-E/A-Authentifizierung](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei der Adobe I/O-Konsole anmelden können oder der Experience Platform Location Service keine Option auf der Seite "Integrationen *erstellen"ist*, finden Sie Informationen zu den *Organisationsanforderungen* in der Übersicht über die [Web-Services-APIs](/help/web-service-api/places-web-services.md).

## Erstellen einer Ortsintegration {#create-places-integration}

Führen Sie die folgenden Aufgaben aus, um eine Ortsintegration zu erstellen:

### Generieren eines öffentlichen und privaten Schlüsselpaars

Um eine Platzierungsintegration zu erstellen, benötigen Sie ein öffentliches und ein privates Schlüsselpaar. Diese Paare können gekauft werden oder Sie können eigene, selbstsignierte Schlüssel erstellen.

So generieren Sie eigene, selbstsignierte Schlüssel:

1. Kopieren Sie die folgenden Zeilen in ein Terminalfenster und fügen Sie sie ein und drücken Sie **[!UICONTROL Enter]** nach dem Einfügen der einzelnen Zeilen die Eingabetaste:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Es wird empfohlen, die Schlüssel zur einfachen Referenz zu benennen und in einem Ordner zu speichern. Wenn Sie mehrere Integrationen erstellen, können Sie einfach identifizieren und verwalten, welche Schlüssel zu welcher Integration gehören.

2. Geben Sie die von OpenSSL angeforderten Informationen ein:

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

3. Navigieren Sie zu dem Ordner, in dem sich die Dateien `.key` und `.crt` Dateien befinden.

   Gehen Sie in iOS beispielsweise zu **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**.

Das folgende Video führt Sie durch den Prozess der Generierung des Schlüsselpaars:

![](/help/assets/places_integration_video.gif)

### Erstellen einer Ortsintegration in der Adobe I/O-Konsole

So erstellen Sie eine Ortsintegration:

1. Wechseln Sie zu [https://console.adobe.io](https://console.adobe.io) und melden Sie sich mit Ihrer Adobe ID an.
2. Wenn Sie Zugriff auf mehr als eine Experience Cloud-Organisation haben, wählen Sie die Organisation aus der Dropdownliste auf der linken Seite aus.
3. Klicken Sie auf **[!UICONTROL New Integration]**.
4. Wählen Sie **[!UICONTROL Access an API]** und klicken Sie auf **[!UICONTROL Continue]**.
5. Wählen Sie unter **[!UICONTROL Experience Cloud]** den Adobe-Dienst **[!UICONTROL Places]** aus, in den Sie integrieren möchten, und klicken Sie auf **[!UICONTROL Continue]**.
6. Wählen Sie **[!UICONTROL New integration]** und klicken Sie auf **[!UICONTROL Continue]**.
7. Geben Sie im Bildschirm "Neue Integration *erstellen* "einen Namen und eine Beschreibung ein.
8. Ziehen Sie die oben erstellte `xxxx_public.crt` Datei in den **[!UICONTROL Public keys certificates]** Ablagebereich.
9. At the bottom of the page, click **[!UICONTROL Create integration]**.
10. Überprüfen Sie nach einigen Sekunden im Bildschirm *Integration erstellt* , ob folgende Meldung angezeigt wird:

   `Your integration has been created.`

11. Klicken Sie auf **[!UICONTROL Continue to integration details]**.

   Es wird ein Überblick über Ihre Integration mit dem API-Schlüssel, Ihrer Organisations-ID, der technischen Konto-ID und anderen Details zu Ihren Integrationen angezeigt.

### Unternehmen-ID und API-Schlüssel aufzeichnen

1. Vergewissern Sie sich, dass auf der **[!UICONTROL Services]** Registerkarte angezeigt **[!UICONTROL Places]** wird.
2. Suchen Sie auf der **[!UICONTROL Overview]** Registerkarte den API-Schlüssel (Client-ID) und die Organisations-ID und zeichnen Sie ihn auf.

   Diese IDs werden für jede Places REST API-Anforderung benötigt.

![](/help/assets/places_orgid_api-key.png)

### JWT-Token erstellen

Auf der **[!UICONTROL JWT]** Registerkarte können Sie mit der Adobe-E/A-Konsole Ihre Integration testen, indem Sie eine JWT generieren und die Austausch-URL angeben.

So generieren Sie ein JWT-Token:

1. Öffnen Sie die oben erstellte `private.key` Datei in einem Texteditor.
2. Kopieren Sie auf der **[!UICONTROL JWT]** Registerkarte den Inhalt des Schlüssels und fügen Sie ihn in das **[!UICONTROL Paste private key]** Feld ein.
3. Klicken Sie auf **[!UICONTROL Generate JWT]**.
4. Klicken Sie im **[!UICONTROL Sample CURL command]** Abschnitt auf den Inhalt **[!UICONTROL Copy]** und fügen Sie ihn an der Eingabeaufforderung oder im Terminalfenster ein.
5. Führen Sie den Befehl aus, indem Sie **[!UICONTROL Enter]** auf die Tastatur drücken.
6. Suchen Sie den Wert `"token_type": "bearer"` und den `"access_token"` Wert.

   Der Wert des Benutzerzugriffszeichens ist der Wert, den Sie in Ihren Places API-Anforderungen verwenden werden.

>[!IMPORTANT]
>
>Adobe-Zugriffstoken sind **nur** 24 Stunden gültig. Speichern Sie daher den CURL-Beispielbefehl (Schritt 5). Wenn das Zugriffstoken nicht mehr gültig ist, müssen Sie das Token erneut generieren.

