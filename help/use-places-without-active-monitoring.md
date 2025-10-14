---
title: Places Service ohne Überwachung der aktiven Region verwenden
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Places-Service ohne Überwachung der aktiven Region.
exl-id: 0ba7949a-447e-4754-9b45-945e58e29541
source-git-commit: 33cbef9b3226be3f013fe82d619b82e093a9752a
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Places Service ohne Überwachung der aktiven Region verwenden {#use-places-without-active-monitoring}

Anwendungsfälle für Ihre Anwendung erfordern möglicherweise keine Überwachung der aktiven Region. Places Service kann weiterhin verwendet werden, um die Standortdaten Ihrer Benutzer in andere Experience Platform-Produkte zu integrieren.

## Voraussetzung

Der Entwickler erfasst den Speicherort des Geräts mithilfe der APIs, die vom Betriebssystem der Zielplattform bereitgestellt werden.

>[!TIP]
>
>Wenn für die Anwendungsfälle Ihrer App eine aktive Regionsüberwachung erforderlich ist, finden Sie weitere Informationen unter [Verwenden des Places Service mit Ihrer eigenen Überwachungslösung](/help/using-your-own-monitor.md).

So verwenden Sie den Places Service ohne Überwachung der aktiven Region:

## 1. Erfassen Sie den Standort des Benutzers

Der App-Entwickler muss den aktuellen Speicherort des Geräts mithilfe der `CoreLocation.framework` (iOS) oder der von Google Play Services (Android) bereitgestellten `Location`-APIs erfassen.

Weitere Informationen finden Sie in der folgenden Dokumentation:

- [CoreLocation](https://developer.apple.com/documentation/corelocation) (Apple)
- [Standort-APIs in Google Play Services](https://developer.android.com/training/location) (Google)

## 2. Abrufen von nahegelegenen Sehenswürdigkeiten aus der SDK

Nachdem Sie den Standort des Benutzers abgerufen haben, können Sie ihn an die SDK übergeben, um eine Liste der nahe gelegenen POIs zu erhalten.

### Android

Im Folgenden finden Sie eine Beispielimplementierung in Android, die einen [`BroadcastReceiver`](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F..index#5) verwendet:

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }
}
```

### Objective-C

Im Folgenden finden Sie eine Beispielimplementierung für iOS. Der Code zeigt die Implementierung der [`locationManager:didUpdateLocations:`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc) in der [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc):

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}
```

### schnell

Im Folgenden finden Sie eine Beispielimplementierung für iOS. Der Code zeigt die Implementierung der [`locationManager(_:didUpdateLocations:)`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager) in der [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager):

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}
```

## 3. Fügen Sie Ihren Analytics-Anfragen Places-Daten hinzu

Durch den Aufruf der `getNearbyPointsOfInterest`-API stellt die Places SDK alle für das Gerät relevanten POI-Daten über Datenelemente in Launch zur Verfügung. Durch Verwendung einer [Daten anhängen](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data)-Regel können Platzierungsdaten automatisch zu zukünftigen Anfragen an Analytics hinzugefügt werden. Dadurch entfällt die Notwendigkeit eines einmaligen Aufrufs an Analytics zum Zeitpunkt der Erfassung des Standorts des Geräts.

Weitere Informationen [&#x200B; diesem Thema finden Sie unter „Hinzufügen &#x200B;](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md) Standortkontext zu Analytics-Anfragen“.

## Optional - Benutzereintrittsereignisse, wenn sich der Trigger in einem POI befindet

>[!TIP]
>
>Die empfohlene Methode zur Erfassung von Daten zu Orten besteht darin[&#x200B; „Places-Daten an Ihre Analytics-Anfragen anzuhängen](#attach-places-data-to-your-analytics-requests).
>
>Wenn der Anwendungsfall erfordert, dass [&#x200B; SDK ein &quot;](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#processregionevent)&quot; auslöst, muss dies manuell geschehen, wie unten beschrieben.

Die von der `getNearbyPointsOfInterest`-API zurückgegebene Liste enthält [benutzerdefinierte Objekte](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#additional-classes-and-enums) die angeben, ob sich der Benutzer derzeit in einem POI befindet. Wenn sich der Benutzer in einem POI befindet, kann der SDK-Trigger ein Eintrittsereignis für diese Region erhalten.

>[!IMPORTANT]
>
>Um zu verhindern, dass Ihre App bei einem Besuch mehrere Eintrittsereignisse auslöst, führen Sie eine Liste der Regionen, von denen Sie wissen, dass sie der Benutzer eingegeben hat. Bei der Verarbeitung der Antwort von POIs in der Nähe aus der SDK wird ein Eintrittsereignis nur dann als Trigger interpretiert, wenn die Region nicht in Ihrer Liste enthalten ist.
>
>Im folgenden Codebeispiel werden `NSUserDefaults` (iOS) und `SharedPreferences` (Android) verwendet, um die Liste der Regionen zu verwalten:

### Android

Das folgende Codebeispiel zeigt die Verarbeitung des Ergebnisses, das im Callback von `getNearbyPointsOfInterest`, einem `List<PlacesPOI>`, bereitgestellt wurde:

```java
void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
    // get the list of regions we know the user is already within from SharedPreferences
    SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
    Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

    // loop through new placesPOIS and post entry events for pois that aren't already in our list
    // also create the new list of regions that the user is in
    Set<String> updatedRegionsUserIsIn = new HashSet<String>();
    for (PlacesPOI poi : nearbyPois) {
        // check if the user is in this poi
        if (poi.containsUser()) {
            // the user is in the poi, now we need to make sure we haven't already recorded this entry event
            if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                Geofence poiGeofence = new Geofence.Builder()
                    .setRequestId(poi.getIdentifier())
                    .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                    .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                    .setExpirationDuration(Geofence.NEVER_EXPIRE)
                    .build();
                Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
            }

            // add the region to our new list of regions
            updatedRegionsUserIsIn.add(poi.getIdentifier());
        }
    }

    // update SharedPreferences with our new list of regions
    SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
    editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
}
```

### Objective-C

Das folgende Codebeispiel zeigt die Verarbeitung des Ergebnisses, das im Callback von `getNearbyPointsOfInterest:limit:callback:errorCallback:` bereitgestellt wurde, einem `NSArray<ACPPlacesPoi *> *`:

```objectivec
- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### schnell

Das folgende Codebeispiel zeigt die Verarbeitung des Ergebnisses, das im Callback von `getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)` bereitgestellt wurde, einem `[ACPPlacesPoi]`:

```swift
func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

## Vollständige Beispielimplementierung

Die folgenden Codebeispiele zeigen Ihnen, wie Sie den aktuellen Speicherort des Geräts abrufen, die erforderlichen Eintrittsereignisse für den Trigger festlegen und sicherstellen können, dass Sie nicht bei einem Besuch mehrere Einträge für denselben Speicherort erhalten.

Dieses Code-Beispiel enthält den optionalen Schritt [Auslösen eines Eintrittsereignisses, wenn sich der Benutzer in einem POI befindet](#trigger-entry-events-when-the-user-is-in-a-poi).

>[!IMPORTANT]
>
>Diese Snippets sind **only** Beispiele. Entwickler müssen festlegen, wie die Funktion implementiert werden soll. Bei der Entscheidung sollten die Best Practices berücksichtigt werden, die vom Zielbetriebssystem empfohlen werden.

### Android

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                    handleUpdatedPOIs(pois);
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }

    void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
        // get the list of regions we know the user is already within from SharedPreferences
        SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
        Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

        // loop through new placesPOIS and post entry events for pois that aren't already in our list
        // also create the new list of regions that the user is in
        Set<String> updatedRegionsUserIsIn = new HashSet<String>();
        for (PlacesPOI poi : nearbyPois) {
            // check if the user is in this poi
            if (poi.containsUser()) {
                // the user is in the poi, now we need to make sure we haven't already recorded this entry event
                if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                    Geofence poiGeofence = new Geofence.Builder()
                        .setRequestId(poi.getIdentifier())
                        .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                        .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                        .setExpirationDuration(Geofence.NEVER_EXPIRE)
                        .build();
                    Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
                }

                // add the region to our new list of regions
                updatedRegionsUserIsIn.add(poi.getIdentifier());
            }
        }

        // update SharedPreferences with our new list of regions
        SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
        editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
    }
}
```


### Objective-C

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
        [self handleUpdatedPOIs:nearbyPoi];
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}

- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### schnell

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
        self.handleUpdatedPOIs(nearbyPoi!)
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}

func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

Aufgrund der auslösenden Eintrittsereignisse können nicht nur Eintrittsereignisse des Places Service in der SDK ausgelöst werden, sondern auch alle Daten, die Ihre POIs definieren, vom Rest der SDK über `data elements` in Experience Platform Launch verwendet werden. Mit Experience Platform Launch `rules` können Sie die Daten des Places Service dynamisch an eingehende Ereignisse anhängen, die von der SDK verarbeitet werden. Sie können beispielsweise die Metadaten eines POI anhängen, in dem sich der Benutzer befindet, und die Daten als Kontextdaten an Analytics senden.

Weitere Informationen finden Sie unter [Verwenden des Places Service mit anderen Adobe-Lösungen](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md).
