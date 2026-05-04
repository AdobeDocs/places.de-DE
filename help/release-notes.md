---
title: Versionshinweise
description: Versionshinweise für Places Service.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
TQID: https://experienceleague.adobe.com/yo1eXPl9cKbp-EVWQT8gZHcAbSDoIFJVD6xKbdoysMc
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: bef6f891-2e8a-425e-8f99-7ddf22070daa
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1612
ht-degree: 5%

---

# Versionshinweise {#release-notes}

## &#x200B;8. Juli 2020

* **Places and Places Monitor-Erweiterungen**

   * Die Erweiterungen Places und Places Monitor wurden für [React Native-Programme hinzugefügt](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Die Erweiterungen Places und Places Monitor wurden für [Cordova-Anwendungen“ &#x200B;](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Weitere Informationen finden Sie unter [Verwenden der Places-Erweiterung](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html?lang=de)


## &#x200B;12. Mai 2020

* **Places Service**

   * POIs mithilfe der Schaltfläche „POIs importieren“ aus einer CSV-Datei stapelweise importieren
   * Auswählen mehrerer POIs und Massenbearbeitung oder Hinzufügen von Metadatenwerten

## &#x200B;6. Mai 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Verbesserte Protokollierung

## &#x200B;5. Mai 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Verbesserte Protokollierung

## &#x200B;20. Februar 2020

* **ACPPlaces 1.3.1 (iOS)**

   * Die Places-Erweiterung meldet jetzt Versionsinformationen an den Event Hub in der Core SDK.
   * Informationen zur Geräte-POI-Mitgliedschaft haben jetzt standardmäßig eine Lebensdauer von einer Stunde ab dem Zeitpunkt, zu dem sie erfasst werden. Weitere Informationen finden Sie unter [Ändern der Time-to-Live für Mitgliedschaften in Orten](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * Die Places-Erweiterung meldet jetzt Versionsinformationen an den Event Hub in der Core SDK.
   * Informationen zur Geräte-POI-Mitgliedschaft haben jetzt standardmäßig eine Lebensdauer von einer Stunde ab dem Zeitpunkt, zu dem sie erfasst werden. Weitere Informationen finden Sie unter [Ändern der Time-to-Live für Mitgliedschaften in Orten](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## Dienstag, 27. Januar 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Rufen Sie die New Places-API auf, um den Autorisierungsstatus des Standorts beim Start der App und bei Änderungen der Autorisierung während der Ausführung der App zu erfassen.
      * Die setRequestLocationPermission-API und die veraltete setLocationPermission-API wurden hinzugefügt.

## &#x200B;9. Januar 2020

* **Orte 1.4.0**

   * **Android**

      * Eine neue API `setAuthorizationStatus` wurde hinzugefügt, um den Geräteautorisierungsstatus für Places Services festzulegen. Der Wert wird gespeichert und im Status Freigegebene Orte verwendet.

## Donnerstag, 4. Dezember 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Rufen Sie die Places-API auf, um den CLAuthorizationStatus von einem Gerät zu erfassen, wenn es sich ändert.

## Mittwoch, 3. Dezember 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Eine neue API `setAuthorizationStatus` wurde hinzugefügt, um den Geräteautorisierungsstatus für Places Services festzulegen. Der Wert wird gespeichert und im Status Freigegebene Orte verwendet.

## Dienstag, 25. November 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Importanweisungen für CocoaPods-Projekte mit der Option Mehrere Pod-Projekte wurden korrigiert.

## Samstag, 22. November 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * Der Monitor erkennt jetzt den Start eines Android-Geräts und registriert bei Bedarf die Geofences basierend auf dem aktuellen Speicherort des Geräts erneut beim Betriebssystem.
      * Es wurde eine Racebedingung behoben, die manchmal dazu führte, dass Eintritts-/Austrittsereignisse verworfen wurden.

## Donnerstag, 9. Oktober 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Es wurde eine neue API `setRequestAuthorizationLevel` hinzugefügt, um den Typ der Standortautorisierungsanfrage festzulegen, für die der Benutzer aufgefordert wird.


   * **Android**

      * Es wurde eine neue API `setLocationPermission` hinzugefügt, um den Typ der Standortberechtigungsanfrage festzulegen, für die der Benutzer aufgefordert wird.
      * Der Orte-Monitor unterstützt jetzt Android 10.

## &#x200B;8. August 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Aktualisierungen der Benutzeroberfläche

Hier finden Sie eine Liste der Aktualisierungen der Places-Benutzeroberfläche:

#### Neue Funktionen

* Es wurde eine neue Listenansicht hinzugefügt, in der POIs ohne Zuordnung angezeigt werden.
* POI-Filteroptionen für Stadt, Bundesland, Land und Metadaten wurden hinzugefügt.
* Die erste Bibliothek in einer Organisation wird automatisch erstellt.
* POI-Sortierung zur Listenansicht hinzugefügt.

#### Aktualisierungen der Benutzeroberfläche

* Liste und Bedienfeld „Details“ auf die rechte Seite der Benutzeroberfläche verschoben.
* Oben in der Benutzeroberfläche wurde ein neues Suchfeld hinzugefügt.
* Wenn nur eine Bibliothek vorhanden ist, wird diese Bibliothek beim Erstellen eines POI automatisch ausgewählt.
* Die Bibliotheksverwaltung wurde in ein Popup-Fenster verschoben.
* POI-Anzahl neben den Filtern hinzugefügt.

## &#x200B;6. August 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Monitor Launch-Erweiterung 2.0.0

* Die Installationsanweisungen für Android und iOS für Places Monitor 2.0 wurden aktualisiert.

## &#x200B;31. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Places Monitor 2.0.0

* Der Überwachungsstatus wird jetzt zwischen den Launches beibehalten.
* Für die Verarbeitung des Callbacks, die aus einer Ortsberechtigungsanfrage resultierte, müssen Sie PlacesActivity nicht mehr erweitern.
* Eine vorhandene API wurde geändert, sodass Entwicklerinnen und Entwickler alle Places-Daten vom Gerät löschen können:

  Alte API: `public static void stop();`

  Neue API: `public static void stop (final boolean clearData);`

* Die Verwendung der `getNearbyPointsOfInterest`-API zur effektiveren Handhabung von Fehlerszenarien wurde aktualisiert.

## &#x200B;25. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### ACPPlacesMonitor 2.0.0

* So löschen Sie alle Ortsdaten aus dem Gerät:

  hat in ACPPlacesMonitor ein vorhandenes API-`+ (void) stop;` durch ersetzt`+ (void) stop: (BOOL) clearData;`.

* Die Verwendung der ACPPlaces-`getNearbyPointsOfInterest`-API wurde aktualisiert, um Fehlerszenarien effektiver zu handhaben.

## Dienstag, 22. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Android Places 1.3.0

* Es wurde eine neue API hinzugefügt, die alle mit Places verknüpften Daten aus dem freigegebenen Status, dem In-App-Speicher und den freigegebenen Voreinstellungen löscht.
* Es wurde ein Problem behoben, bei dem der freigegebene Status beim Anwendungsstart nicht aktualisiert wurde.
* Es wurde ein Fehler behoben, durch den `getNearbyPointsOfInterest` Callback in keinem Internet Fehlercode `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` zurückgab.
* `getNearbyPointsOfInterest` API (ohne errorCallback) wird die `successCallback` mit leerer POI-Liste aufgerufen, falls ein Fehler beim Abrufen der nahegelegenen Points of Interest auftritt.

## Samstag, 19. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places 1.2.0**

Es wurde eine neue API hinzugefügt, die alle mit Places zusammenhängenden Daten aus dem freigegebenen Status, dem In-App-Speicher und `NSUserDefaults` löscht.

## &#x200B;25. Juni 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places Monitor 1.0.2**

* Verbesserungen der Lebensqualität, einschließlich besserer Dokumentation und Protokollierung im Code.

## &#x200B;17. Juni 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places 1.1.0**

* Es wurde eine neue API hinzugefügt, die einen Fehler-Code zurückgibt, wenn beim Abrufen von nahegelegenen Orten ein Fehler auftritt.
* Wenn sich der Datenschutzstatus in „Opt-out“ ändert, werden alle Daten im Zusammenhang mit Orten jetzt vom Gerät gelöscht.
* Fehlerkorrektur - Nach dem ersten Start gehen jetzt nicht mehr Places-Ereignisse aufgrund schlechter Netzwerkbedingungen verloren.
* Es wurde ein Problem behoben, bei dem bei der Verarbeitung von POI-Eintrittsereignissen in schneller Folge die Token-Ersetzung über die Regel-Engine manchmal auf den falschen POI verweist.

## &#x200B;30. Mai 2019

**Android Places Monitor 1.0.1**

* Es wurde ein Problem behoben, das beim Starten der Orte-Überwachung ein Eintrittsereignis für POIs verhinderte.

## &#x200B;28. Mai 2019

Die folgenden Probleme in der Places-Benutzeroberfläche wurden behoben:

* Der Lösungsschalter wurde stellenweise so aktualisiert, dass er mit dem übrigen Experience Cloud übereinstimmt.
* Es wurde ein Problem behoben, bei dem der Rang in Instanzen gespeichert wurde, in denen keine Rang-Änderungen vorgenommen wurden.
* Der minimal zulässige Radius in der Benutzeroberfläche wurde auf 10 Meter erhöht.
* Es wurde ein Problem behoben, bei dem das Feld Radius auf 20 Meter zurückgesetzt wurde, wenn alle Zahlen im Feld gelöscht wurden.

## &#x200B;17. Mai 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**Android Places 1.2.0**

* Es wurde eine neue API zur Verarbeitung eines einzelnen Geofence hinzugefügt.
* Fehlerbehebung, um mehrere aufeinander folgende Eintrittsereignisse zu verhindern.

**Android Places Monitor 1.0.0**

Erste Veröffentlichung des Places Monitor für Android.

Der Places Monitor verwaltet die Location APIs auf Betriebssystemebene und kommuniziert direkt mit der Places-Erweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung eine vorkonfigurierte Regionsüberwachung verwenden.
Weitere Informationen zum Places Monitor finden Sie hier.


## &#x200B;2. Mai 2019

**Android Places 1.1.0**

* Es wurde eine neue API für getNearByPlaces eingeführt, die über einen errorCallback verfügt und mit einem errorCode aufgerufen wird, der den Grund für den Fehler angibt.
* Die Places-Erweiterung stellt die Ereignisse jetzt in die Warteschlange, bis eine Konfiguration abgerufen wird.
* Unterstützung für umgebungsabhängige Konfigurationen wurde hinzugefügt.
* Fehlerbehebung : Die Schlüssel für die Eintritts-/Austrittsereignisse der Region wurden korrigiert.
* Beim Speichern des letzten bekannten Speicherorts wird nun der Datenschutzstatus des Benutzers ordnungsgemäß berücksichtigt.


## &#x200B;9. April 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places Monitor 1.0.1**

* Vollständige Abdeckung von Modultests hinzugefügt.
* CI-Integration (CircleCI)
* Integration der Codeabdeckung (CodeCov)

## Dienstag, 25. März 2019

iOS Places Monitor 1.0.0

Erste Veröffentlichung des Places Monitor für iOS.

Der Places Monitor verwaltet die Location APIs auf Betriebssystemebene und kommuniziert direkt mit der Places-Erweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung eine vorkonfigurierte Regionsüberwachung verwenden.

## &#x200B;28. Februar 2019

### Beta-Version

Dies ist die erste Version von Places Service, einer Reihe von Tools, mit denen Kunden die Erlebnisse ihrer Benutzer mit realen Standortdaten anreichern können. Für die erste Version besteht unser Hauptanwendungsfall darin, mobilen Apps zu ermöglichen, benutzerdefinierte Standortdaten abzurufen und über Adobe Experience Platform Launch auf diese Daten zu reagieren.

### Wichtigste Funktionen

Im Folgenden finden Sie die wichtigsten Funktionen dieser Version:

#### Places Service-Benutzeroberfläche

Wir haben eine Management-Benutzeroberfläche veröffentlicht, in der Sie Ihre POIs (Points of Interest) anzeigen und verwalten können. Sie können Ihre POIs auch in Bibliotheken organisieren. Zusätzlich zu Standard-Metadaten wie Stadt, Bundesland und Kategorie unterstützen wir auch die Möglichkeit, Ihren POIs benutzerdefinierte Metadaten hinzuzufügen.

* Die Benutzeroberfläche finden Sie unter [https://places.adobe.com](https://places.adobe.com).
* Informationen zu den ersten Schritten mit der Benutzeroberfläche finden [&#x200B; unter „Erste Schritte](/help/getting-started.md).

#### Places-Erweiterung

Mit der Places-Erweiterung können Sie Ihre Places Service-Bibliotheken zu Ihrer Mobile App hinzufügen und auf ihre POIs reagieren. Mit dem Regel-Builder in Experience Platform Launch können Sie Benutzeraktionen festlegen, die ausgelöst werden, wenn Trigger POIs eingeben und verlassen.

In der Places -Erweiterung:

* Sie können auswählen, welche POI-Bibliotheken in Ihre App aufgenommen werden sollen.
* Regelereignisse, die beim POI-Eintritt oder -Austritt einen Trigger verursachen.
* Erstellen Sie Datenelemente, die auf den aktuellen POI des Benutzers verweisen.

Weitere Informationen zur Places-Erweiterung finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places-APIs

Sie können die Places-APIs für die folgenden Aufgaben verwenden:

* Entwickelnden ermöglichen, ihre POI-Liste zu füllen und zu aktualisieren.
* Erstellen Sie Ihre eigene Benutzeroberfläche oder integrieren Sie sie in eine vorhandene POI-Datenbank.
* Verwenden Sie die Batch-Endpunkte der Places-API, um einen Massenimport von POIs durchzuführen.

  Sie können das bereitgestellte Python-Dienstprogramm verwenden, um den Massenimport abzuschließen.

Weitere Informationen zu den Places-APIs finden Sie unter [Webservice-API](/help/web-service-api/places-web-services.md).

### Bald verfügbar

#### Analytics-Integration

Die Analytics-Erweiterung wird aktualisiert, um automatisch Standortkontextdaten aus Ihrer Places-Service-Datenbank zu allen ausgehenden Analytics-Aufrufen hinzuzufügen, wenn sich ein Benutzer in einem POI befindet (passive Aufrufe). Diese Aktualisierung ermöglicht auch die Erstellung von Regeln, die Analytics-Tracking-Aufrufe direkt am POI-Eintritt oder -Ausstieg auslösen (aktive Aufrufe).
