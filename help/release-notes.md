---
title: Versionshinweise
description: Versionshinweise für den Places-Dienst.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 4%

---

# Versionshinweise {#release-notes}

## 8. Juli 2020

* **Places und Places Monitor-Erweiterungen**

   * Erweiterungen für Places und Places Monitor wurden hinzugefügt für [React Native Apps](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Erweiterungen für Places und Places Monitor wurden hinzugefügt für [Cordova-Anwendungen](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Weitere Informationen finden Sie unter: [Verwenden der Places-Erweiterung](https://docs.adobe.com/content/help/de-DE/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12. Mai 2020

* **Places Service**

   * Massenimport von POIs aus einer CSV-Datei mithilfe der Schaltfläche &quot;POIs importieren&quot;
   * Auswählen mehrerer POIs und Massenbearbeitung oder Hinzufügen von Metadatenwerten

## Mittwoch, 6. Mai 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Verbesserte Protokollierung

## 5. Mai 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Verbesserte Protokollierung

## 20. Februar 2020

* **ACPPlaces 1.3.1 (iOS)**

   * Die Places-Erweiterung meldet nun Versionsinformationen an den Ereignis-Hub im Core SDK.
   * Die Informationen zur Geräte-POI-Mitgliedschaft haben jetzt eine standardmäßige Live-Zeit von einer Stunde ab dem Zeitpunkt der Erfassung. Weitere Informationen finden Sie unter [Ändern der Gültigkeitsdauer der Places-Mitgliedschaft](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * Die Places-Erweiterung meldet nun Versionsinformationen an den Ereignis-Hub im Core SDK.
   * Die Informationen zur Geräte-POI-Mitgliedschaft haben jetzt eine standardmäßige Live-Zeit von einer Stunde ab dem Zeitpunkt der Erfassung. Weitere Informationen finden Sie unter [Ändern der Gültigkeitsdauer der Places-Mitgliedschaft](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27. Januar 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Rufen Sie die neue Places-API auf, um den Autorisierungsstatus des Standorts zu erfassen, wenn die App gestartet wird und sich die Autorisierung während der Ausführung der App ändert.
      * Die API setRequestLocationPermission und die nicht mehr unterstützte API setLocationPermission wurden hinzugefügt.

## 9. Januar 2020

* **Places 1.4.0**

   * **Android**

      * Es wurde eine neue API hinzugefügt, `setAuthorizationStatus`, um den Geräteautorisierungsstatus für Places Services festzulegen. Der Wert wird gespeichert und im Status &quot;Places shared&quot;verwendet.

## 4. Dezember 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Rufen Sie die Places-API auf, um den CLAuthorizationStatus von dem Gerät zu erfassen, wenn es sich ändert.

## 3. Dezember 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Es wurde eine neue API hinzugefügt, `setAuthorizationStatus`, um den Geräteautorisierungsstatus für Places Services festzulegen. Der Wert wird gespeichert und im Status &quot;Places shared&quot;verwendet.

## 25. November 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Fehlerkorrektur - Importanweisungen für Cocoapods-Projekte mit der Option für mehrere Pod-Projekte werden nun korrekt eingefügt.

## 22. November 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * Der Monitor erkennt jetzt den Start eines Android-Geräts und registriert bei Bedarf die Geofences anhand des aktuellen Standorts des Geräts erneut beim Betriebssystem.
      * Es wurde eine Race-Bedingung behoben, die manchmal dazu führte, dass Einstiegs-/Ausstiegsereignisse verworfen wurden.

## 9. Oktober 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Es wurde eine neue API hinzugefügt, `setRequestAuthorizationLevel`, um den Typ der Standortautorisierungsanforderung festzulegen, für die der Benutzer aufgefordert wird.
   * **Android**

      * Es wurde eine neue API hinzugefügt, `setLocationPermission`, um den Typ der Anforderung für Standortberechtigungen festzulegen, für die der Benutzer aufgefordert wird.
      * Der Places Monitor unterstützt jetzt Android 10.



## 8. August 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Benutzeroberflächen-Updates

Im Folgenden finden Sie eine Liste der Aktualisierungen der Places-Benutzeroberfläche:

#### Neue Funktionen

* Es wurde eine neue Listenansicht hinzugefügt, die POIs ohne Karte anzeigt.
* Es wurden POI-Filteroptionen für Stadt, Staat, Land und Metadaten hinzugefügt.
* Die erste Bibliothek in einer Organisation wird automatisch erstellt.
* Der Listenansicht wurde eine POI-Sortierung hinzugefügt.

#### Benutzeroberflächen-Updates

* Das Listen- und Detailbedienfeld wurde rechts von der Benutzeroberfläche verschoben.
* Am oberen Rand der Benutzeroberfläche wurde ein neues Suchfeld hinzugefügt.
* Wenn nur eine Bibliothek vorhanden ist, wird diese Bibliothek beim Erstellen eines POI automatisch ausgewählt.
* Die Bibliotheksverwaltung wurde in ein Popup-Fenster verschoben.
* Neben den Filtern wurde eine POI-Anzahl hinzugefügt.

## 6. August 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Überwachen der Launch-Erweiterung 2.0.0

* Die Installationsanweisungen für Android und iOS für Places Monitor 2.0 wurden aktualisiert.

## 31. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Places Monitor 2.0.0

* Der Überwachungsstatus wird jetzt zwischen den Launches beibehalten.
* Für die Verarbeitung des Rückrufs, der aus einer Anfrage zur Erteilung von Standortberechtigungen resultierte, müssen Sie PlacesActivity nicht mehr erweitern.
* Eine vorhandene API wurde geändert, sodass Entwickler alle Places-Daten vom Gerät löschen können:

   Alte API: `public static void stop();`

   Neue -API: `public static void stop (final boolean clearData);`

* Die Verwendung der `getNearbyPointsOfInterest` API zur effektiveren Handhabung von Fehlerszenarien.

## Donnerstag, 25. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### ACPPlacesMonitor 2.0.0

* So löschen Sie alle Places -Daten vom Gerät:

   Ersetzt in ACPPlacesMonitor eine vorhandene API `+ (void) stop;` mit`+ (void) stop: (BOOL) clearData;`.

* Die Verwendung der ACPPlaces wurde aktualisiert. `getNearbyPointsOfInterest` API zur effektiveren Handhabung von Fehlerszenarien.

## 22. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

### Android Places 1.3.0

* Es wurde eine neue API hinzugefügt, mit der alle Places-bezogenen Daten aus dem freigegebenen Status, dem In-App-Speicher und der freigegebenen Voreinstellung gelöscht werden.
* Es wurde ein Problem behoben, bei dem der freigegebene Status während des Anwendungsstarts nicht aktualisiert wurde.
* Es wurde ein Fehler behoben, durch den `getNearbyPointsOfInterest` callback gab Fehlercode zurück `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` nicht im Internet.
* `getNearbyPointsOfInterest` Die API (ohne den errorCallback) verfügt über die `successCallback` mit leerer POI-Liste aufgerufen werden, falls beim Abrufen der nahe gelegenen Zielpunkte ein Fehler auftritt.

## 19. Juli 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places 1.2.0**

Es wurde eine neue API hinzugefügt, die alle Places-bezogenen Daten aus dem freigegebenen Status, dem In-App-Speicher und `NSUserDefaults`.

## 25. Juni 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places Monitor 1.0.2**

* Verbesserungen der Lebensqualität, einschließlich einer besseren Dokumentation und Protokollierung im Code.

## 17. Juni 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places 1.1.0**

* Es wurde eine neue API hinzugefügt, mit der ein Fehlercode zurückgegeben wird, wenn das Abrufen nahegelegener Orte fehlschlägt.
* Wenn der Datenschutzstatus zu &quot;opt-out&quot;geändert wird, werden alle Places-bezogenen Daten jetzt vom Gerät gelöscht.
* Es wurde ein Problem behoben, das nach einem ersten Start manchmal dazu führte, dass Places-Ereignisse aufgrund schlechter Netzwerkbedingungen verloren gingen.
* Es wurde ein Problem behoben, bei dem bei der Verarbeitung von POI-Eintrittsereignissen in kurzer Folge die Token-Ersetzung über die Regel-Engine manchmal auf den falschen POI verweist.

## 30. Mai 2019

**Android Places Monitor 1.0.1**

* Es wurde ein Problem behoben, das ein Eintrittsereignis für POIs verhinderte, wenn die Places-Überwachung gestartet wurde.

## 28. Mai 2019

Die folgenden Probleme in der Places-Benutzeroberfläche wurden behoben:

* Der Lösungsschalter in Places wurde aktualisiert, um mit dem Rest des Experience Cloud in Einklang zu stehen.
* Es wurde ein Problem behoben, bei dem der Rang in Instanzen gespeichert wurde, in denen keine Rangänderungen vorgenommen wurden.
* Der erlaubte Mindestradius in der Benutzeroberfläche wurde auf 10 Meter erhöht.
* Es wurde ein Problem behoben, bei dem das Feld radius bei Löschung aller Zahlen im Feld wieder auf 20 Meter zurückgesetzt wurde.

## 17. Mai 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**Android Places 1.2.0**

* Es wurde eine neue API zur Verarbeitung eines einzelnen Geofence hinzugefügt.
* Fehlerbehebung , um mehrere aufeinander folgende Einstiegsereignisse zu verhindern.

**Android Places Monitor 1.0.0**

Erste Version von Places Monitor for Android.

Der Places Monitor verwaltet die Standort-APIs auf Betriebssystemebene und kommuniziert direkt mit der Places-Erweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung über eine native Regionsüberwachung verfügen.
Weitere Informationen zum Places Monitor finden Sie hier.


## 2. Mai 2019

**Android Places 1.1.0**

* Es wurde eine neue API für getNearByPlaces eingeführt, die über einen errorCallback verfügt und mit einem errorCode aufgerufen wird, der den Grund für den Fehler anzeigt.
* Die Places-Erweiterung stellt die Ereignisse jetzt in die Warteschlange, bis eine Konfiguration abgerufen wird.
* Unterstützung für umgebungsbasierte Konfigurationen hinzugefügt.
* Fehlerbehebung : die Schlüssel für die Ein-/Ausstiegsereignisse der Region korrigiert
* Die Speicherung des letzten bekannten Speicherorts respektiert jetzt den Datenschutzstatus des Benutzers ordnungsgemäß.


## Dienstag, 9. April 2019

In dieser Version wurden die folgenden Aktualisierungen vorgenommen:

**iOS Places Monitor 1.0.1**

* Vollständige Testabdeckung für Einheiten wurde hinzugefügt.
* CI-Integration (CircleCI)
* Codepage-Integration (Codecov)

## 25. März 2019

iOS Places Monitor 1.0.0

Erstmalige Veröffentlichung des Places Monitor for iOS.

Der Places Monitor verwaltet die Standort-APIs auf Betriebssystemebene und kommuniziert direkt mit der Places-Erweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung über eine native Regionsüberwachung verfügen.

## 28. Februar 2019

### Beta-Version

Dies ist die erste Version von Places Service, einem Satz von Tools, mit denen Kunden die Erlebnisse ihrer Benutzer mit echten Standortdaten anreichern können. In der ersten Version besteht unser Hauptanwendungsfall darin, mobile Apps zu aktivieren, um benutzerdefinierte Standortdaten abzurufen und über Adobe Experience Platform Launch auf diese Daten zu reagieren.

### Wichtigste Funktionen

Hier finden Sie die wichtigsten Funktionen dieser Version:

#### Places Service-Benutzeroberfläche

Wir haben eine Verwaltungs-Benutzeroberfläche veröffentlicht, über die Sie Ihre Zielpunkte (POIs) anzeigen und verwalten können. Sie können Ihre POIs auch in Bibliotheken organisieren. Zusätzlich zu Standard-Metadaten wie Stadt, Bundesland und Kategorie unterstützen wir auch die Möglichkeit, Ihren Zielpunkten benutzerdefinierte Metadaten hinzuzufügen.

* Um die Benutzeroberfläche anzuzeigen, navigieren Sie zu [https://places.adobe.com](https://places.adobe.com).
* Informationen zu den ersten Schritten mit der Benutzeroberfläche finden Sie unter [Erste Schritte](/help/getting-started.md).

#### Places-Erweiterung

Mithilfe der Places-Erweiterung können Sie Ihre Places Service-Bibliotheken zu Ihrer mobilen App hinzufügen und deren POIs bearbeiten. Mithilfe des Regel-Builders in Experience Platform Launch können Sie Trigger-Aktionen auslösen, die ausgelöst werden, wenn Benutzer POIs aufrufen und beenden.

In der Places-Erweiterung:

* Sie können auswählen, welche POI-Bibliotheken in Ihre App aufgenommen werden sollen.
* Regelereignisse, die beim Ein- oder Ausstieg eines POI-Triggers auftreten.
* Erstellen Sie Datenelemente, die auf den aktuellen POI des Benutzers verweisen.

Weitere Informationen zur Places-Erweiterung finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places-APIs

Sie können die Places-APIs wie folgt verwenden:

* Ermöglichen es Entwicklern, ihre Liste von POIs zu füllen und zu aktualisieren.
* Erstellen Sie Ihre eigene Benutzeroberfläche oder integrieren Sie sie in eine vorhandene POI-Datenbank.
* Verwenden Sie die Batch-Endpunkte der Places-API, um einen Massenimport von POIs durchzuführen.

   Sie können das bereitgestellte Python-Dienstprogramm verwenden, um den Massenimport abzuschließen.

Weitere Informationen zu den Places-APIs finden Sie unter [Webdienst-API](/help/web-service-api/places-web-services.md).

### Demnächst

#### Analytics  Integration

Die Analytics-Erweiterung wird aktualisiert, um allen ausgehenden Analytics-Aufrufen automatisch Standortkontextdaten aus Ihrer Places Service-Datenbank hinzuzufügen, wenn sich ein Benutzer an einem POI befindet (passive Aufrufe). Durch diese Aktualisierung kann die Regelerstellung auch Analytics-Tracking-Aufrufe direkt beim Ein- oder Ausstieg (aktive Aufrufe) des POI auslösen.
