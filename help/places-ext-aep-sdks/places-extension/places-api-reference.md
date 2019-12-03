---
title: Platzierungs-API-Referenz
seo-title: Platzierungs-API-Referenz
description: Informationen zu den API-Referenzen in Places.
seo-description: Informationen zu den API-Referenzen in Places.
translation-type: tm+mt
source-git-commit: 5d4974a341f6d0009ad93a9eea2f940ac9d8e871

---


# Platzierungs-API-Referenz {#places-api-reference}

Im Folgenden finden Sie Informationen zu den API-Referenzen unter Orte:

## Verarbeiten eines Regionenereignisses

Wenn ein Gerät eine vordefinierte Platzierungsregion Ihrer App überschreitet, werden die Region und der Ereignistyp zur Verarbeitung an das SDK übergeben.

### ProcessGeofence (Android)

Verarbeiten Sie ein `Geofence` Regions-Ereignis für die bereitgestellte `transitionType`.

Geben Sie die `transitionType` Daten ab `GeofencingEvent.getGeofenceTransition()`. Zurzeit `Geofence.GEOFENCE_TRANSITION_ENTER` und `Geofence.GEOFENCE_TRANSITION_EXIT` werden unterstützt.

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Beispiel**

Rufen Sie diese Methode in Ihrer Methode auf, `IntentService` die für den Empfang von Android-Geofence-Ereignissen registriert ist.

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Diese Methode sollte im `CLLocationManager` Delegate aufgerufen werden, der angibt, ob der Benutzer eine bestimmte Region aufgerufen oder verlassen hat.

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

Verarbeiten Sie alle `Geofences` gleichzeitig `GeofencingEvent` .

**Syntax**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Beispiel**

Rufen Sie diese Methode in Ihrer `IntentService` auf, die für den Empfang von Android-Geofencing-Ereignissen registriert ist.

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Abrufen nahegelegener Zielpunkte

Gibt eine geordnete Liste der nahe gelegenen POIs in einem Rückruf zurück. Eine überladene Version dieser Methode gibt einen Fehlercode zurück, wenn beim resultierenden Netzwerkaufruf ein Fehler aufgetreten ist.

### GetNeestedPointsOfInterest (Android)

Hier finden Sie die Syntax für diese Methode:

**Syntax**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNeestedPointsOfInterest (iOS)

**Syntax**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Beispiel**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## Abrufen aktueller Gerätepunkte

Fordert eine Liste der POIs an, in denen das Gerät derzeit bekannt ist, und gibt sie in einem Rückruf zurück.

### GetCurrentPointsOfInterest (Android)

Hier finden Sie die Syntax für diese Methode:

**Syntax**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## Speicherort des Geräts abrufen

Fordert den Speicherort des Geräts an, wie zuvor durch die Plateausgabe bekannt.

>[!TIP]
>
>Die Ortserweiterung kennt nur Orte, an denen sie über Anrufe an `GetNearbyPointsOfInterest`gesendet wurde.


### GetLastKnownLocation (Android)

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Clientseitige Daten löschen


### Clear (Android)

Löscht die clientseitigen Daten für "Orte im Freigabezustand", "lokaler Speicher"und "Arbeitsspeicher".

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```java
public static void clear();
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
Places.clear();
```

### clear (iOS)

Löscht die clientseitigen Daten für "Orte im Freigabezustand", "lokaler Speicher"und "Arbeitsspeicher".

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```objectivec
+ (void) clear;
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```objectivec
[ACPPlaces clear];
```

## Status der Standortautorisierung festlegen

### setAuthorizationStatus (Android)

In Vorbereitung

### setAuthorizationStatus (iOS)

*[Verfügbar ab ACPPlaces v1.3.0]*

Legt den Autorisierungsstatus in der Ortserweiterung fest.

Der angegebene Status wird im Status "Orte freigegeben"gespeichert und dient nur als Referenz.
Der Aufruf dieser Methode hat keine Auswirkungen auf den tatsächlichen Status der Standortautorisierung für dieses Gerät.

Wenn sich der Status der Geräteautorisierung ändert, wird die `locationManager:didChangeAuthorizationStatus:` Methode des Geräts aufgerufen `CLLocationManagerDelegate` . Von dieser Methode aus sollten Sie den neuen `CLAuthorizationStatus` Wert an die ACPPlaces- `setAuthorizationStatus:` API übergeben.

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
