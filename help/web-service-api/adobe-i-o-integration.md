---
title: Übersicht über die Adobe I/O-Integration
description: Informationen zum Erstellen einer Adobe I/O-Integration.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---


# Übersicht über die Integration und Voraussetzungen {#integration-prereqs}

Diese Informationen zeigen Ihnen, wie Sie eine Integration von Adobe I/O und Places Service erstellen.

## Voraussetzungen für den Benutzerzugriff

Vergewissern Sie sich beim Systemadministrator Ihres Unternehmens, dass die folgenden Aufgaben abgeschlossen wurden:

* Der Orte-Core-Service wird in der Admin-Konsole Ihres Unternehmens angezeigt.
* Sie wurden der Organisation hinzugefügt.
* Sie wurden als Benutzer zum Platzierungs-Core-Service in Ihrem Unternehmen hinzugefügt.

   Weitere Informationen finden Sie unter *Hinzufügen Sie einen Benutzer oder Entwickler auf die Profil für den Orte-Dienst und den Experience Platform Launch* in [Zugriff auf den Orte-Dienst](/help/places-gain-access.md) erhalten.

* Sie wurden als Entwickler zum Platzierungs-Core-Service in Ihrem Unternehmen hinzugefügt.

   Weitere Informationen zum Hinzufügen von Entwicklern finden Sie unter *Hinzufügen einem Benutzer oder Entwickler zu Ihren Places Service- und Experience Platform Launch-Profilen* in [Zugriff auf Places Service](/help/places-gain-access.md) erhalten.

   Weitere Informationen zur Rolle &quot;Entwickler&quot;finden Sie unter [Entwickler verwalten](https://helpx.adobe.com/de/enterprise/using/manage-developers.html).

### REST-API-Anfragen

Für jede Anforderung an die REST-API des Places-Dienstes sind die folgenden Elemente erforderlich:

* Eine Organisations-ID
* Ein API-Schlüssel
* Ein InhaberToken

Eine Integration mit Adobe I/O bietet diese Elemente und eine Möglichkeit, das Inhabertoken mithilfe eines JSON-WebTokens (JWT) anzufordern.

* Weitere Informationen zu JWTs finden Sie unter [Einführung in JSON Web Tokens](https://jwt.io/introduction/).
* Informationen zum Erstellen einer Integration für den Places-Dienst finden Sie im Abschnitt *Erstellen einer Platzierungsdienstintegration* unten.
* Informationen zur Integration von API-Schlüsseln, zum Generieren von JWT-Zertifikaten und Zertifikaten öffentlicher Schlüssel finden Sie unter [Übersicht über die Adobe I/O-Authentifizierung](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei der Adobe I/O-Konsole anmelden können oder wenn auf der Seite *Integrationen erstellen* der Ortsdienst keine Option ist, finden Sie weitere Informationen unter *Organisationsanforderungen* in [Übersicht über die Web-Services-API](/help/web-service-api/places-web-services.md).

## Eine Integration des Orte-Dienstes erstellen

Führen Sie die folgenden Aufgaben aus, um eine Integration des Places-Dienstes zu erstellen:

### Generieren eines öffentlichen und privaten Schlüsselpaars

Um eine Integration des Platzierungsdienstes zu erstellen, benötigen Sie ein öffentliches und ein privates Schlüsselpaar. Diese Paare können gekauft werden oder Sie können eigene, selbstsignierte Schlüssel erstellen.

So generieren Sie eigene, selbstsignierte Schlüssel:

1. Kopieren Sie in ein Terminalfenster die folgenden Zeilen und fügen Sie sie ein und drücken Sie nach dem Einfügen der einzelnen Zeilen die Eingabetaste:****

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

1. Navigieren Sie zu dem Ordner, in dem sich die Dateien `.key` und `.crt` befinden.

   Gehen Sie in MacOS beispielsweise zu **[!UICONTROL Macintosh HD]** > **[!UICONTROL Benutzer]** > **[!UICONTROL (Ihr Benutzername)]** > **[!UICONTROL Schlüssel]**.

Das folgende Video führt Sie durch den Prozess der Generierung des Schlüsselpaars:

![Integrationsvideo](/help/assets/places_integration_video.gif)

### Erstellen einer Integration des Places-Dienstes in der Adobe I/O-Konsole

So erstellen Sie eine Integration des Places-Dienstes:

1. Wechseln Sie zu [https://console.adobe.io](https://console.adobe.io) und melden Sie sich mit Ihrem Adobe ID an.
1. Klicken Sie im Abschnitt **Quick Beginn** auf **Integration erstellen**.
1. Wählen Sie **[!UICONTROL Access an API]** (Auf API zugreifen) aus und klicken Sie auf **[!UICONTROL Continue]** (Weiter).

   **[!UICONTROL Der Zugriff auf eine]** API ist der Standardspeicherort.

1. Wenn Sie Zugriff auf mehr als ein Experience Cloud-Unternehmen haben, wählen Sie das Unternehmen in der Dropdown-Liste oben rechts aus.
1. Wählen Sie unter **[!UICONTROL Experience Cloud]** **[!UICONTROL Ortsdienst]** als Adobe-Dienst, in den Sie integrieren möchten, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie **[!UICONTROL Neue Integration]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie im Bildschirm &quot;Neue Integration erstellen&quot;einen Namen und eine Beschreibung ein.
1. Ziehen Sie die oben erstellte `xxxx_public.crt`-Datei in den Ablagebereich **[!UICONTROL Public keys certificates]**.
1. Wählen Sie ein Profil aus.

   Wenden Sie sich an Ihren Systemadministrator, wenn Sie sich nicht sicher sind, welches Profil Sie auswählen möchten.
1. Klicken Sie unten auf der Seite auf **[!UICONTROL Integration erstellen]**.
1. Überprüfen Sie nach einigen Sekunden, ob im Bildschirm *Integration, die erstellt wurde*, die folgende Meldung angezeigt wird:

   `Your integration has been created.`

1. Die Seite mit den Integrationsdetails wird oben mit dem Namen der Integration angezeigt.

   Das Register **[!UICONTROL Übersicht]** wird standardmäßig angezeigt und zeigt den API-Schlüssel, Ihre Organisations-ID, die technische Konto-ID und andere Details zu Ihren Integrationen an.

### Unternehmen-ID und API-Schlüssel aufzeichnen

1. Klicken Sie auf der Seite mit den Integrationsdetails auf die Registerkarte **[!UICONTROL Dienste]** und bestätigen Sie, dass **[!UICONTROL Ortsdienst]** unter **[!UICONTROL Konfigurierte Dienste]** angezeigt wird.
1. Suchen Sie auf der Registerkarte **[!UICONTROL Übersicht]** den API-Schlüssel (Client-ID) und die Organisations-ID und zeichnen Sie ihn auf.

   Diese IDs werden für jede REST-API-Anforderung des Places-Dienstes benötigt.

![](/help/assets/places_orgid_api-key.png)

### JWT-Token erstellen

Klicken Sie auf der Seite mit den Integrationsdetails auf die Registerkarte **[!UICONTROL JWT]**, damit Sie Ihre Integration testen können, indem Sie eine JWT generieren und die Austausch-URL angeben.

So generieren Sie ein JWT-Token:

1. Öffnen Sie in einem Texteditor die Datei `private.key`, die Sie oben erstellt haben.
1. Kopieren Sie auf dem Tab **[!UICONTROL JWT]** den Inhalt des Schlüssels und fügen Sie ihn in das Feld **[!UICONTROL Privaten Schlüssel einfügen]** ein.
1. Klicken Sie auf **[!UICONTROL Generate JWT]**.
1. Klicken Sie im Bereich **[!UICONTROL Beispiel-CURL-Befehl]** auf **[!UICONTROL Kopieren]** und fügen Sie den Inhalt in die Eingabeaufforderung oder im Terminal-Fenster ein.
1. Führen Sie den Befehl aus, indem Sie auf der Tastatur die Eingabetaste **[!UICONTROL drücken.]**
1. Suchen Sie den Wert `"token_type": "bearer"` und den Wert `"access_token"`.

   Der Wert des Zugriffstokens des Inhabers ist der Wert, den Sie in Ihren Anforderungen der Orte-Dienst-API verwenden werden.

>[!IMPORTANT]
>
>Zugriffstoken der Adobe sind 24 Stunden lang gültig. Speichern Sie daher den CURL-Beispielbefehl (Schritt 5). **** Wenn das Zugriffstoken nicht mehr gültig ist, müssen Sie das Token neu generieren.