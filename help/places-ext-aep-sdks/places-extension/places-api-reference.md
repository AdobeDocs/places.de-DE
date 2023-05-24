---
title: Places-API-Referenz
description: Informationen zu den API-Referenzen in Places.
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Places-API-Referenz {#places-api-reference}

Im Folgenden finden Sie Informationen zu den API-Referenzen in der Places-Erweiterung:

## Verarbeiten eines Region-Ereignisses

Wenn ein Gerät eine der vordefinierten Places Service-Regionsgrenzen Ihrer App überschreitet, werden die Region und der Ereignistyp zur Verarbeitung an das SDK übergeben.

### ProcessGeofence (Android)

Verarbeiten einer `Geofence` Region-Ereignis für die bereitgestellte `transitionType`.

Übergeben Sie die `transitionType` von `GeofencingEvent.getGeofenceTransition()`. Aktuell `Geofence.GEOFENCE_TRANSITION_ENTER` und `Geofence.GEOFENCE_TRANSITION_EXIT` werden unterstützt.

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Beispiel**

Rufen Sie diese Methode in Ihrer `IntentService` das für den Empfang von Android-Geofence-Ereignissen registriert ist.

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

Diese Methode sollte im `CLLocationManager` delegate, der angibt, ob der Benutzer eine bestimmte Region erreicht oder verlassen hat.

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

Alle Prozesse verarbeiten `Geofences` im `GeofencingEvent` gleichzeitig.

**Syntax**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Beispiel**

Rufen Sie diese Methode in Ihrer `IntentService` die für den Empfang von Android-Geofence-Ereignissen registriert ist

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

## Abruf nahegelegener Zielpunkte

Gibt eine geordnete Liste nahegelegener Zielpunkte in einem Callback zurück. Eine überladene Version dieser Methode gibt einen Fehlercode zurück, wenn beim resultierenden Netzwerkaufruf etwas schief gelaufen ist.

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

## Abrufen der aktuellen Zielpunkte des Geräts

Fordert eine Liste von POIs an, an denen sich das Gerät derzeit befindet, und gibt sie in einem Callback zurück.

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

Fordert den Speicherort des Geräts an, wie zuvor durch die Places-Erweiterung bekannt.

>[!TIP]
>
>Die Places-Erweiterung kennt nur Orte, die ihr über Aufrufe von zur Verfügung gestellt wurden. `GetNearbyPointsOfInterest`.


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

## Client-seitige Daten löschen


### Löschen (Android)

Löscht die clientseitigen Daten für die Places-Erweiterung im freigegebenen Status, im lokalen Speicher und im Arbeitsspeicher.

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

Löscht die clientseitigen Daten für die Places-Erweiterung im freigegebenen Status, lokalen Speicher und Arbeitsspeicher.

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

## Festlegen des Autorisierungsstatus für Standorte

### setAuthorizationStatus (Android)

*Verfügbar ab Places v1.4.0*

Legt den Autorisierungsstatus in der Places-Erweiterung fest.

Der angegebene Status wird im Status &quot;Places shared&quot;gespeichert und dient nur als Referenz.
Der Aufruf dieser Methode hat keine Auswirkungen auf den tatsächlichen Status der Standortautorisierung für dieses Gerät.

**Syntax**

Hier finden Sie die Syntax für diese Methode:

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*Verfügbar ab ACPPlaces v1.3.0*

Legt den Autorisierungsstatus in der Places-Erweiterung fest.

Der angegebene Status wird im Status &quot;Places shared&quot;gespeichert und dient nur als Referenz.
Der Aufruf dieser Methode hat keine Auswirkungen auf den tatsächlichen Status der Standortautorisierung für dieses Gerät.

Wenn sich der Status der Geräteautorisierung ändert, wird die `locationManager:didChangeAuthorizationStatus:` -Methode `CLLocationManagerDelegate` aufgerufen wird. Von dieser Methode aus sollten Sie die neue `CLAuthorizationStatus` Wert in die ACPPlaces `setAuthorizationStatus:` API.

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
