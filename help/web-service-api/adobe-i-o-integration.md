---
title: Übersicht über die Adobe I/O-Integration
description: Informationen zum Erstellen einer Adobe I/O-Integration.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 6%

---

# Integrationsübersicht und Voraussetzungen {#integration-prereqs}

Diese Informationen zeigen Ihnen, wie Sie eine Adobe I/O und eine Places Service-Integration erstellen.

## Voraussetzungen für den Benutzerzugriff

Vergewissern Sie sich beim Systemadministrator Ihres Unternehmens, dass die folgenden Aufgaben abgeschlossen sind:

* Places Core Service wird in der Admin Console Ihres Unternehmens angezeigt.
* Sie wurden zur Organisation hinzugefügt.
* Sie wurden als Benutzer zu Places Core Service in Ihrem Unternehmen hinzugefügt.

   Weitere Informationen finden Sie unter *Benutzer oder Entwickler zu Ihren Places Service- und Experience Platform Launch-Profilen hinzufügen* in [Zugriff auf Places Service erhalten](/help/places-gain-access.md).

* Sie wurden als Entwickler zu Places Core Service in Ihrem Unternehmen hinzugefügt.

   Weitere Informationen zum Hinzufügen von Entwicklern finden Sie unter *Benutzer oder Entwickler zu Ihren Places Service- und Experience Platform Launch-Profilen hinzufügen* in [Zugriff auf Places Service erhalten](/help/places-gain-access.md).

   Weitere Informationen zur Entwicklerrolle finden Sie unter [Entwickler verwalten](https://helpx.adobe.com/de/enterprise/using/manage-developers.html).

### REST-API-Anfragen

Für jede Anfrage an die Places Service-REST-API sind die folgenden Elemente erforderlich:

* Eine Organisations-ID
* Ein API-Schlüssel
* Trägertoken

Eine Integration mit Adobe I/O bietet diese Elemente und eine Möglichkeit, das Trägertoken mithilfe eines JSON Web Token (JWT) anzufordern.

* Weitere Informationen zu JWTs finden Sie unter [Einführung in JSON-Web-Token](https://jwt.io/introduction/).
* Informationen zum Erstellen einer Integration für den Places-Dienst finden Sie unter *Erstellen einer Places Service-Integration* unten.
* Informationen zur Integration von API-Schlüsseln, zum Generieren von JWT- und Zertifikaten mit öffentlichen Schlüsseln finden Sie unter [Übersicht über die Adobe I/O-Authentifizierung](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei der Adobe I/O Console anmelden können oder wenn der Places-Dienst keine Option für die *Seite &quot;Integrationen erstellen&quot;*, siehe *Organisationsanforderungen* in [Übersicht über die Web-Services-API](/help/web-service-api/places-web-services.md).

## Erstellen einer Places Service-Integration

Führen Sie die folgenden Aufgaben aus, um eine Integration des Places-Dienstes zu erstellen:

### Generieren eines öffentlichen und privaten Schlüsselpaars

Um eine Integration mit dem Places-Dienst zu erstellen, benötigen Sie ein Paar aus öffentlichem und privatem Schlüssel. Diese Paare können erworben werden oder Sie können eigene, selbstsignierte Schlüssel generieren.

So generieren Sie eigene selbstsignierte Schlüssel:

1. Kopieren Sie in einem Terminalfenster die folgenden Zeilen, fügen Sie sie ein und drücken Sie die Eingabetaste **[!UICONTROL Eingabe]** nach dem Einfügen der einzelnen Zeilen:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Wir empfehlen Ihnen, Ihre Schlüssel zur einfachen Referenz zu benennen und in einem Ordner zu speichern. Wenn Sie mehrere Integrationen erstellen, können Sie auf einfache Weise ermitteln und verwalten, welche Schlüssel zu welcher Integration gehören.

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
   >Die von Ihnen bereitgestellten Informationen sind in die Schlüssel integriert.

1. Navigieren Sie zu dem Ordner, in dem die `.key` und `.crt` -Dateien befinden.

   Navigieren Sie in MacOS beispielsweise zu **[!UICONTROL Macintosh HD]** > **[!UICONTROL Benutzer]** > **[!UICONTROL (Benutzername)]** > **[!UICONTROL Schlüssel]**.

Das folgende Video führt Sie durch den Prozess der Generierung des Schlüsselpaars:

![Integrationsvideo](/help/assets/places_integration_video.gif)

### Erstellen einer Places Service-Integration in der Adobe I/O Console

So erstellen Sie eine Places Service-Integration:

1. Navigieren Sie zu [https://console.adobe.io](https://console.adobe.io) und melden Sie sich mit Ihrer Adobe ID an.
1. Im **Schnellstart** Abschnitt, klicken Sie auf **Integration erstellen**.
1. Wählen Sie **[!UICONTROL Access an API]** (Auf API zugreifen) aus und klicken Sie auf **[!UICONTROL Continue]** (Weiter).

   **[!UICONTROL Zugriff auf APIs]** ist der Standardspeicherort.

1. Wenn Sie Zugriff auf mehr als ein Experience Cloud-Unternehmen haben, wählen Sie das Unternehmen aus der Dropdownliste oben rechts aus.
1. under **[!UICONTROL Experience Cloud]** auswählen **[!UICONTROL Places Service]** als Adobe-Dienst, in den Sie integrieren möchten, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Auswählen **[!UICONTROL Neue Integration]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie im Bildschirm Neue Integration erstellen einen Namen und eine Beschreibung ein.
1. Ziehen und ablegen `xxxx_public.crt` -Datei, die Sie oben erstellt haben, zum **[!UICONTROL Öffentliche Schlüsselzertifikate]** Dropzone.
1. Produktprofil auswählen.

   Wenden Sie sich an Ihren Systemadministrator, wenn Sie sich nicht sicher sind, welches Profil ausgewählt werden soll.
1. Klicken Sie unten auf der Seite auf **[!UICONTROL Integration erstellen]**.
1. Nach einigen Sekunden wird in der Variablen *Integration erstellt* überprüfen Sie, ob folgende Meldung angezeigt wird:

   `Your integration has been created.`

1. Die Seite mit den Integrationsdetails wird oben mit dem Namen der Integration angezeigt.

   Die **[!UICONTROL Übersicht]** standardmäßig angezeigt und zeigt den API-Schlüssel, Ihre Organisations-ID, die technische Konto-ID und weitere Details zu Ihren Integrationen an.

### Organisations-ID und API-Schlüssel aufzeichnen

1. Klicken Sie auf der Seite mit den Integrationsdetails auf die **[!UICONTROL Dienste]** und bestätigen Sie, dass **[!UICONTROL Places Service]** wird angezeigt unter **[!UICONTROL Konfigurierte Dienste]**.
1. Im **[!UICONTROL Übersicht]** den API-Schlüssel (Client-ID) und die Organisations-ID suchen und aufzeichnen.

   Diese IDs werden für jede Places Service-REST-API-Anfrage benötigt.

![](/help/assets/places_orgid_api-key.png)

### JWT-Token generieren

Klicken Sie auf der Seite mit den Integrationsdetails auf die **[!UICONTROL JWT]** , damit Sie Ihre Integration testen können, indem Sie ein JWT generieren und die Austausch-URL angeben.

So generieren Sie ein JWT-Token:

1. Öffnen Sie in einem Texteditor Ihre `private.key` -Datei, die Sie oben erstellt haben.
1. Kopieren Sie auf dem Tab **[!UICONTROL JWT]** den Inhalt des Schlüssels und fügen Sie ihn in das Feld **[!UICONTROL Privaten Schlüssel einfügen]** ein.
1. Klicken **[!UICONTROL JWT generieren]**.
1. Klicken Sie im Bereich **[!UICONTROL Beispiel-CURL-Befehl]** auf **[!UICONTROL Kopieren]** und fügen Sie den Inhalt in die Eingabeaufforderung oder im Terminal-Fenster ein.
1. Führen Sie den Befehl durch Drücken der **[!UICONTROL Eingabe]** auf Ihrer Tastatur.
1. Suchen Sie die `"token_type": "bearer"` und `"access_token"` -Wert.

   Der Wert des Trägerzugriffs-Tokens ist der Wert, den Sie in Ihren Places Service-API-Anfragen verwenden werden.

>[!IMPORTANT]
>
>Adobe-Zugriffstoken sind gültig **only** 24 Stunden lang, speichern Sie also den CURL-Beispielbefehl (Schritt 5). Wenn das Zugriffstoken nicht mehr gültig ist, müssen Sie das Token neu generieren.
