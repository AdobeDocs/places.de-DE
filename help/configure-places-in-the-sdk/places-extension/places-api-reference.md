---
title: Platzierungs-API-Referenz
seo-title: Platzierungs-API-Referenz
description: Informationen zu den API-Referenzen in Places.
seo-description: Informationen zu den API-Referenzen in Places.
translation-type: tm+mt
source-git-commit: 1fb87285d2ccd581ee59ab1b1efbec4af04a0fab

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

Hier ein Codebeispiel für diese Methode:

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call Adobe Places API to process information
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
        // Call Adobe Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Abrufen nahegelegener Zielpunkte

Gibt eine geordnete Liste der nahe gelegenen POIs in einem Rückruf zurück.

### GetNeestedPointsOfInterest (Android)

Hier finden Sie die Syntax für diese Methode:

**Syntax**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**Beispiel**

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNeestedPointsOfInterest (iOS)

**Syntax**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**Beispiel**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
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
