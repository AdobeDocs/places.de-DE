---
title: Versionshinweise
description: Versionshinweise für den Places-Dienst.
translation-type: tm+mt
source-git-commit: 04644763a40898432c4b821ca24366c19dda0437

---


# Versionshinweise {#release-notes}

## 27. Januar 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Rufen Sie die neue Orte-API auf, um den Status der Standortautorisierung zu erfassen, wenn die App gestartet wird und sich die Autorisierung ändert, während die App ausgeführt wird.
      * setRequestLocationPermission-API und nicht mehr unterstützte setLocationPermission-API hinzugefügt.

## 9. Januar 2020

* **ACPPlaces 1.4.0**

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
      * Es wurde eine Racebedingung behoben, die manchmal dazu führte, dass Einstiegs-/Ausstiegsereignisse verworfen wurden.

## 9. Oktober 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Es wurde eine neue API hinzugefügt, `setRequestAuthorizationLevel`um den Typ der Autorisierungsanfrage für den Speicherort festzulegen, für den der Benutzer aufgefordert wird.
   * **Android**

      * Es wurde eine neue API hinzugefügt, `setLocationPermission`um den Typ der Ortsberechtigungsanforderung festzulegen, für die der Benutzer aufgefordert wird.
      * Der Orts-Monitor unterstützt jetzt Android 10.



## 08.08.2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

### UI-Updates

Im Folgenden finden Sie eine Liste der Aktualisierungen der Benutzeroberfläche &quot;Orte&quot;:

#### Neue Funktionen

* Es wurde eine neue Listenansicht hinzugefügt, in der POIs ohne Zuordnung angezeigt werden.
* Es wurden POI-Filteroptionen für Stadt, Staat, Land und Metadaten hinzugefügt.
* Die erste Bibliothek in einem Unternehmen wird automatisch erstellt.
* Die POI-Sortierung zur Listenansicht wurde hinzugefügt.

#### UI-Updates

* Liste und Detailbedienfeld wurden auf der Benutzeroberfläche nach rechts verschoben.
* Am Anfang der Benutzeroberfläche wurde ein neues Suchfeld hinzugefügt.
* Wenn nur eine Bibliothek vorhanden ist, wird diese beim Erstellen eines POI automatisch ausgewählt.
* Bibliotheksverwaltung in ein Popup-Fenster verschoben.
* Neben den Filtern wurde eine POI-Anzahl hinzugefügt.

## 06.08.2019

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

   Neue API: `public static void stop (final boolean clearData);`

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

* Es wurde eine neue API hinzugefügt, mit der alle Ortsdaten aus dem Freigabestand, dem In-App-Speicher und der freigegebenen Voreinstellung gelöscht werden.
* Es wurde ein Problem behoben, bei dem der Status &quot;Freigegeben&quot;beim Anwendungsstart nicht aktualisiert wurde.
* Es wurde ein Fehler behoben, durch den `getNearbyPointsOfInterest` Rückruf Fehlercode `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` im Internet zurückgab.
* `getNearbyPointsOfInterest` Die API (ohne errorCallback) hat den `successCallback` Aufruf mit leerer POI-Liste, falls Fehler beim Abrufen der nahe gelegenen Zielpunkte auftreten.

## 19. Juli 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places 1.2.0**

Es wurde eine neue API hinzugefügt, mit der alle Daten zum Thema Orte aus dem Freigabestand, dem In-App-Speicher und `NSUserDefaults`dem gelöscht werden.

## 25. Juni 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places Monitor 1.0.2**

* Verbesserung der Lebensqualität, einschließlich besserer Dokumentation und Protokollierung im Code.

## 17. Juni 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places 1.1.0**

* Es wurde eine neue API hinzugefügt, um einen Fehlercode zurückzugeben, wenn das Abrufen nahegelegener Orte fehlschlägt.
* Wenn sich der Datenschutzstatus in &quot;Opt-out&quot;ändert, werden alle mit Orten zusammenhängenden Daten jetzt vom Gerät gelöscht.
* Es wurde ein Problem behoben, das nach einem ersten Start manchmal dazu führte, dass Places-Ereignisse aufgrund falscher Netzwerkbedingungen verloren gingen.
* Es wurde ein Problem behoben, bei dem bei der Verarbeitung von POI-Einstiegsereignissen in kurzer Folge der Token-Austausch über die Regelmaschine manchmal auf den falschen POI verweist.

## 30. Mai 2019 (Orte)

**Android Places Monitor 1.0.1**

* Es wurde ein Fehler behoben, der dazu führte, dass ein Einstiegsereignis für POIs beim Starten der Orts-Überwachung verhindert wurde.

## 28. Mai 2019

Die folgenden Probleme in der Benutzeroberfläche &quot;Orte&quot;wurden behoben:

* Der Lösungsschalter in Orten wurde aktualisiert, um ihn an den Rest der Experience Cloud auszurichten.
* Es wurde ein Problem behoben, bei dem der Rang gespeichert wurde, wenn keine Rangänderungen vorgenommen wurden.
* Der erlaubte Mindestradius in der Benutzeroberfläche wurde auf 10 Meter erhöht.
* Es wurde ein Problem behoben, bei dem beim Löschen aller Zahlen im Feld das Feld Radius auf 20 Meter zurückgesetzt wurde.

## 17. Mai 2019 (Orte)

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**Android Places 1.1.0**

* Es wurde eine neue API zur Verarbeitung einer einzelnen Geometrie hinzugefügt.
* Fehlerbehebung, um mehrere aufeinander folgende Einstiegsereignisse zu verhindern.

**Android Places Monitor 1.0.0**

Ursprüngliche Version des Orts-Monitors für Android.

Der Orts-Monitor verwaltet die Positionierungs-APIs auf Betriebssystemebene und kommuniziert direkt mit der Ortserweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung eine Out-of-the-Box-Regionsüberwachung verwenden.
Weitere Informationen zum Orts-Monitor finden Sie hier.


## 2. Mai 2019

**Android Places 1.1.0**

* Es wurde eine neue API für getNearByPlaces eingeführt, die einen errorCallback enthält und mit einem errorCode aufgerufen wird, der den Grund für den Fehler angibt.
* Die Platzierungserweiterung stellt die Ereignisse jetzt in eine Warteschlange, bis eine Konfiguration abgerufen wird.
* Unterstützung für umweltbewusste Konfigurationen hinzugefügt.
* Fehlerbehebung: Korrektur der Schlüssel für die Ereignisse &quot;Ein-/Ausstieg&quot;der Region
* Die Speicherung des zuletzt bekannten Speicherorts respektiert jetzt den Datenschutzstatus des Benutzers ordnungsgemäß


## 9. April 2019

Die folgenden Aktualisierungen wurden in dieser Version vorgenommen:

**iOS Places Monitor 1.0.1**

* Vollständige Testabdeckung hinzugefügt.
* CI-Integration (CircleCI)
* Coverage-Integration (Codecov)

## 25. März 2019

iOS Places Monitor 1.0.0

Erste Veröffentlichung des Orts-Monitors für iOS.

Der Orts-Monitor verwaltet die Positionierungs-APIs auf Betriebssystemebene und kommuniziert direkt mit der Ortserweiterung. Wenn beide Erweiterungen installiert sind, können Kunden in ihrer Anwendung eine Out-of-the-Box-Regionsüberwachung verwenden. Weitere Informationen zum Platzierungsmonitor finden Sie unter [Platzierungsmonitor-Erweiterung](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## 28. Februar 2019

### Beta-Version

Dies ist die erste Version des Places Service, eine Reihe von Tools, mit denen Kunden die Erlebnisse ihrer Benutzer mit echten Standortdaten bereichern können. In der ersten Version besteht unser wichtigster Verwendungsfall darin, mobilen Apps zu ermöglichen, benutzerdefinierte Standortdaten abzurufen und über den Adobe Experience Platform Launch auf diese Daten zu reagieren.

### Wichtigste Funktionen

Die wichtigsten Funktionen in dieser Version:

#### Platzierungsdienst-Benutzeroberfläche

Wir haben eine Verwaltungs-Benutzeroberfläche veröffentlicht, in der Sie Ihre POIs (Points of Interest) anzeigen und verwalten können. Sie können auch Ihre POIs in Bibliotheken organisieren. Zusätzlich zu Standard-Metadaten wie Stadt, Bundesland und Kategorie unterstützen wir auch die Möglichkeit, Ihren POIs benutzerdefinierte Metadaten hinzuzufügen.

* Die Benutzeroberfläche finden Sie unter [https://places.adobe.com](https://places.adobe.com).
* Die ersten Schritte mit der Benutzeroberfläche finden Sie unter [Erste Schritte](/help/getting-started.md).

#### Platzierungserweiterung

Mit der Platzierungserweiterung können Sie Ihre Orte-Dienst-Bibliotheken zu Ihrer mobilen App hinzufügen und deren POIs bearbeiten. Mit dem Rule Builder in Experience Platform Launch können Sie Aktionen auslösen, die ausgelöst werden, wenn Benutzer POIs eingeben und beenden.

In der Erweiterung Orte:

* Sie können festlegen, welche POI-Bibliotheken in Ihre App aufgenommen werden sollen.
* Regelereignisse, die beim Ein- oder Ausstieg des POI ausgelöst werden.
* Erstellen Sie Datenelemente, die auf den aktuellen POI des Benutzers verweisen.

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Orts-APIs

Sie können die Orte-APIs wie folgt verwenden:

* Erlauben Sie Entwicklern, ihre Liste der POIs zu füllen und zu aktualisieren.
* Erstellen Sie eine eigene Benutzeroberfläche oder integrieren Sie sie in eine bestehende POI-Datenbank.
* Verwenden Sie die Stapelendpunkte der Places API, um POIs stapelweise zu importieren.

   Sie können das angegebene Python-Dienstprogramm verwenden, um den Massenimport abzuschließen.

Weitere Informationen zu den Places-APIs finden Sie unter [Webdienst-API](/help/web-service-api/places-web-services.md).

### In Vorbereitung

#### Analytics  Integration

Die Analytics-Erweiterung wird aktualisiert, um allen ausgehenden Analytics-Aufrufen automatisch Kontextdaten zum Standort aus Ihrer Datenbank für den Places-Dienst hinzuzufügen, wenn sich ein Benutzer in einem POI befindet (Passiv-Aufrufe). Mit diesem Update können auch Regelerstellungen Analytics-Verfolgungsaufrufe direkt beim POI-Einstieg oder -Ausstieg auslösen (Aktive Aufrufe).
