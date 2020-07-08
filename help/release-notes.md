---
title: Versionshinweise
description: Versionshinweise für den Places-Dienst.
translation-type: tm+mt
source-git-commit: 3f986697179eb9c0af1d9b54daf67793a99b8491
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 4%

---


# Versionshinweise {#release-notes}

## 8. Juli 2020

* **Platzierungs- und Platzierungsüberwachungserweiterungen**

   * Erweiterungen für Orts- und Ortemonitor wurden für native [React-Anwendungen hinzugefügt.](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Erweiterungen für Platzierungs- und Ortemonitor wurden für [Cordova-Anwendungen hinzugefügt.](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Weitere Informationen finden Sie unter: [Platzierungs-Erweiterung](https://docs.adobe.com/content/help/de-DE/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12. Mai 2020

* **Places Service**

   * Massenimport-POIs aus einer CSV-Datei mit der Schaltfläche &quot;POIs importieren&quot;
   * Auswählen mehrerer POIs und Massenbearbeitung oder Hinzufügen von Metadatenwerten

## 6. Mai 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Verbesserte Protokollierung

## 5. Mai 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Verbesserte Protokollierung

## 20. Februar 2020

* **ACPPlaces 1.3.1 (iOS)**

   * Die Platzierungserweiterung meldet jetzt Versionsinformationen an den Ereignis-Hub im Core SDK.
   * Die Standardzeit bis zum Ende der Gültigkeitsdauer von Device POI-Mitgliedseinformationen beträgt nun eine Stunde ab dem Zeitpunkt der Erfassung. Weitere Informationen finden Sie unter Zeit-zu-Live-Mitgliedschaft [ändern](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Orte 1.4.1 (Android)**

   * Die Platzierungserweiterung meldet jetzt Versionsinformationen an den Ereignis-Hub im Core SDK.
   * Die Standardzeit bis zum Ende der Gültigkeitsdauer von Device POI-Mitgliedseinformationen beträgt nun eine Stunde ab dem Zeitpunkt der Erfassung. Weitere Informationen finden Sie unter Zeit-zu-Live-Mitgliedschaft [ändern](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27. Januar 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Rufen Sie die neue Orte-API auf, um den Status der Standortautorisierung zu erfassen, wenn die App gestartet wird und sich die Autorisierung ändert, während die App ausgeführt wird.
      * setRequestLocationPermission-API und nicht mehr unterstützte setLocationPermission-API hinzugefügt.

## 9. Januar 2020

* **Orte 1.4.0**

   * **Android**

      * Es wurde eine neue API hinzugefügt, `setAuthorizationStatus`um den Status der Geräteautorisierung für Places Services festzulegen. Der Wert wird gespeichert und im Status &quot;Orte freigegeben&quot;verwendet.

## 4. Dezember 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Rufen Sie die Places-API auf, um CLAuthorizationStatus vom Gerät zu erfassen, wenn es sich ändert.

## 3. Dezember 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Es wurde eine neue API hinzugefügt, `setAuthorizationStatus`um den Status der Geräteautorisierung für Places Services festzulegen. Der Wert wird gespeichert und im Status &quot;Orte freigegeben&quot;verwendet.

## 25. November 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Es wurden Importanweisungen für Cocoapods-Projekte mit der Option für mehrere Pod-Projekte behoben.

## 22. November 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * Der Monitor erkennt jetzt den Start eines Android-Geräts und registriert bei Bedarf die Geofencing-Daten anhand der aktuellen Position des Geräts erneut beim Betriebssystem.
      * Es wurde eine Racebedingung behoben, die manchmal dazu führte, dass ein-/Ausstiegs-Ereignis verworfen wurden.

## 9. Oktober 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Es wurde eine neue API hinzugefügt, `setRequestAuthorizationLevel`um den Typ der Autorisierungsanfrage für den Speicherort festzulegen, für den der Benutzer aufgefordert wird.
   * **Android**

      * Es wurde eine neue API hinzugefügt, `setLocationPermission`um den Typ der Ortsberechtigungsanforderung festzulegen, für die der Benutzer aufgefordert wird.
      * Der Orts-Monitor unterstützt jetzt Android 10.



## 8. August 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

### UI-Updates

Im Folgenden finden Sie eine Liste der Aktualisierungen der Benutzeroberfläche &quot;Orte&quot;:

#### Neue Funktionen

* Es wurde eine neue Ansicht zur Liste hinzugefügt, die POIs ohne die Karte anzeigt.
* Es wurden POI-Filteroptionen für Stadt, Staat, Land und Metadaten hinzugefügt.
* Die erste Bibliothek in einem Unternehmen wird automatisch erstellt.
* Der Ansicht Liste wurde eine POI-Sortierung hinzugefügt.

#### UI-Updates

* Das Bedienfeld &quot;Liste und Details&quot;wurde rechts von der Benutzeroberfläche verschoben.
* Am Anfang der Benutzeroberfläche wurde ein neues Suchfeld hinzugefügt.
* Wenn nur eine Bibliothek vorhanden ist, wird diese beim Erstellen eines POI automatisch ausgewählt.
* Bibliotheksverwaltung in ein Popup-Fenster verschoben.
* Es wurde ein POI-Zähler neben den Filtern hinzugefügt.

## 6. August 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

### Monitor Launch Extension 2.0.0

* Die Installationsanweisungen für Android und iOS für Places Monitor 2.0 wurden aktualisiert.

## 31. Juli 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

### Orts-Monitor 2.0.0

* Der Überwachungsstatus wird jetzt zwischen den Starts beibehalten.
* Für die Verarbeitung des Rückrufs, der aus einer Ortsberechtigungsanforderung resultierte, müssen Sie PlacesActivity nicht mehr erweitern.
* Eine vorhandene API wurde geändert, sodass Entwickler alle Ortsdaten vom Gerät löschen können:

   Alte API: `public static void stop();`

   Neue -API: `public static void stop (final boolean clearData);`

* Die Verwendung der `getNearbyPointsOfInterest` API wurde aktualisiert, um Fehlerszenarien effektiver zu behandeln.

## 25. Juli 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

### ACPPlacesMonitor 2.0.0

* So löschen Sie alle Ortsdaten vom Gerät

   in ACPPlacesMonitor eine vorhandene API `+ (void) stop;` durch`+ (void) stop: (BOOL) clearData;`ersetzt.

* Die Verwendung der ACPPlaces- `getNearbyPointsOfInterest` API wurde aktualisiert, um Fehlerszenarien effektiver zu behandeln.

## 22. Juli 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

### Android Places 1.3.0

* Es wurde eine neue API hinzugefügt, mit der alle Daten zum Thema Orte aus dem freigegebenen Status, dem In-App-Speicher und der freigegebenen Voreinstellung gelöscht werden.
* Es wurde ein Problem behoben, bei dem der Status &quot;Freigegeben&quot;während des Beginns der Anwendung nicht aktualisiert wurde.
* Es wurde ein Fehler behoben, durch den `getNearbyPointsOfInterest` Rückruf Fehlercode `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` im Internet zurückgab.
* `getNearbyPointsOfInterest` API (ohne errorCallback) wird mit leerer POI-Liste `successCallback` aufgerufen, falls Fehler beim Abrufen der nahe gelegenen Zielpunkte auftreten.

## 19. Juli 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places 1.2.0**

Es wurde eine neue API hinzugefügt, mit der alle Daten zum Thema Orte aus dem Freigabestand, dem In-App-Speicher und `NSUserDefaults`dem gelöscht werden.

## 25. Juni 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places Monitor 1.0.2**

* Verbesserung der Lebensqualität, einschließlich besserer Dokumentation und Protokollierung im Code.

## 17. Juni 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places 1.1.0**

* Es wurde eine neue API hinzugefügt, um einen Fehlercode zurückzugeben, wenn das Abrufen nahegelegener Orte fehlschlägt.
* Wenn sich der Datenschutzstatus in &quot;Opt-out&quot;ändert, werden alle mit Orten zusammenhängenden Daten jetzt vom Gerät gelöscht.
* Es wurde ein Problem behoben, das nach dem ersten Start manchmal dazu führte, dass Places-Ereignis aufgrund schlechter Netzwerkbedingungen verloren gingen.
* Es wurde ein Problem behoben, bei dem bei der Verarbeitung von POI-Einstiegszertifikaten in kurzer Folge die Token-Ersetzung über den Rules Engine manchmal auf den falschen POI-Ereignis verweisen.

## 30. Mai 2019

**Android Places Monitor 1.0.1**

* Es wurde ein Fehler behoben, der dazu führte, dass beim Starten der Orteüberwachung kein Ereignis für die Eingabe von POIs angezeigt wurde.

## 28. Mai 2019

Die folgenden Probleme in der Benutzeroberfläche &quot;Orte&quot;wurden behoben:

* Der Solution Switcher in Places wurde aktualisiert, um ihn an das restliche Experience Cloud anzupassen.
* Es wurde ein Problem behoben, bei dem der Rang gespeichert wurde, wenn keine Rangänderungen vorgenommen wurden.
* Der erlaubte Mindestradius in der Benutzeroberfläche wurde auf 10 Meter erhöht.
* Es wurde ein Problem behoben, bei dem beim Löschen aller Zahlen im Feld das Feld Radius auf 20 Meter zurückgesetzt wurde.

## 17. Mai 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**Android Places 1.2.0**

* Es wurde eine neue API zur Verarbeitung einer einzelnen Geometrie hinzugefügt.
* Fehlerkorrektur, um mehrere aufeinander folgende Ereignis zu verhindern.

**Android Places Monitor 1.0.0**

Ursprüngliche Version des Orts-Monitors für Android.

Der Orts-Monitor verwaltet die Positionierungs-APIs auf Betriebssystemebene und kommuniziert direkt mit der Ortserweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung eine Out-of-the-Box-Regionsüberwachung verwenden.
Weitere Informationen zum Orts-Monitor finden Sie hier.


## 2. Mai 2019

**Android Places 1.1.0**

* Es wurde eine neue API für getNearByPlaces eingeführt, die einen errorCallback enthält und mit einem errorCode aufgerufen wird, der den Grund für den Fehler angibt.
* Die Platzierungserweiterung stellt die Ereignis jetzt in eine Warteschlange, bis eine Konfiguration abgerufen wird.
* Unterstützung für Umgebung-basierte Konfigurationen hinzugefügt.
* Fehlerbehebung: die Tasten für die Ereignis für die Ein-/Ausstiegsregion korrigiert
* Datenspeicherung des letzten bekannten Standorts respektiert jetzt den Datenschutzstatus des Benutzers ordnungsgemäß


## 9. April 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places Monitor 1.0.1**

* Vollständige Testabdeckung hinzugefügt.
* CI-Integration (CircleCI)
* Coverage-Integration (Codecov)

## 25. März 2019

iOS Places Monitor 1.0.0

Erste Veröffentlichung des Orts-Monitors für iOS.

Der Orts-Monitor verwaltet die Positionierungs-APIs auf Betriebssystemebene und kommuniziert direkt mit der Ortserweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung eine Out-of-the-Box-Regionsüberwachung verwenden. Weitere Informationen zum Platzierungsmonitor finden Sie unter [Platzierungsmonitor-Erweiterung](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## 28. Februar 2019

### Beta-Version

Dies ist die erste Version des Places Service, eine Reihe von Tools, mit denen Kunden die Erlebnisse ihrer Benutzer mit echten Standortdaten bereichern können. In der ersten Version besteht unser wichtigster Verwendungsfall darin, mobilen Apps zu ermöglichen, benutzerdefinierte Standortdaten abzurufen und über den Adobe Experience Platform Launch auf diese Daten zu reagieren.

### Wichtigste Funktionen

Die wichtigsten Funktionen in dieser Version:

#### Platzierungsdienst-Benutzeroberfläche

Wir haben eine Verwaltungs-Benutzeroberfläche veröffentlicht, in der Sie Ihre POIs (Points of Interest) Ansicht und Verwaltung vornehmen können. Sie können auch Ihre POIs in Bibliotheken organisieren. Neben den Standardmetadaten wie Stadt, Bundesland und Kategorie unterstützen wir auch die Möglichkeit, Ihren POIs benutzerdefinierte Metadaten hinzuzufügen.

* Die Benutzeroberfläche finden Sie unter [https://places.adobe.com](https://places.adobe.com).
* Die ersten Schritte mit der Benutzeroberfläche finden Sie unter [Erste Schritte](/help/getting-started.md).

#### Platzierungserweiterung

Mit der Platzierungserweiterung können Sie Ihre Orte-Dienst-Bibliotheken zu Ihrer mobilen App hinzufügen und deren POIs bearbeiten. Mit dem Rule Builder in Experience Platform Launch können Sie Aktionen auslösen, die ausgelöst werden, wenn Benutzer POIs eingeben und beenden.

In der Erweiterung Orte:

* Sie können festlegen, welche POI-Bibliotheken in Ihre App aufgenommen werden sollen.
* Regel-Ereignis, die beim Ein- oder Ausstieg des POI ausgelöst werden.
* Erstellen Sie Datenelemente, die auf den aktuellen POI des Benutzers verweisen.

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Orts-APIs

Sie können die Orte-APIs wie folgt verwenden:

* Erlauben Sie Entwicklern, ihre Liste von POIs zu füllen und zu aktualisieren.
* Erstellen Sie eine eigene Benutzeroberfläche oder integrieren Sie sie in eine bestehende POI-Datenbank.
* Verwenden Sie die Stapelendpunkte der Places API, um POIs stapelweise zu importieren.

   Sie können das angegebene Python-Dienstprogramm verwenden, um den Massenimport abzuschließen.

Weitere Informationen zu den Places-APIs finden Sie unter [Webdienst-API](/help/web-service-api/places-web-services.md).

### Bald

#### Analytics  Integration

Die Analytics-Erweiterung wird aktualisiert, um allen ausgehenden Analytics-Aufrufen automatisch Kontextdaten zum Speicherort aus Ihrer Ortsdienst-Datenbank hinzuzufügen, wenn sich ein Benutzer in einem POI befindet (Passiv-Aufrufe). Diese Aktualisierung ermöglicht auch die Regelerstellung, um Analytics-Verfolgungsaufrufe direkt beim POI-Einstieg oder -Ausstieg auszulösen (Aktive Aufrufe).
