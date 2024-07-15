---
title: Verwenden eines eigenen Monitors
description: Sie können Ihre Überwachungsdienste auch verwenden und mit Places Service integrieren, indem Sie die APIs der Places Service-Erweiterung verwenden.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# Verwenden eines eigenen Monitors {#using-your-monitor}

Sie können Ihre Überwachungsdienste auch verwenden und mit dem Places-Dienst integrieren, indem Sie die Places-Erweiterungs-APIs verwenden.

## Registrieren von Geofences

Wenn Sie sich für die Verwendung Ihrer Überwachungsdienste entscheiden, registrieren Sie die Geofences der POIs um Ihren aktuellen Standort, indem Sie die folgenden Schritte ausführen:

### iOS

Führen Sie in iOS die folgenden Schritte aus:

1. Übergeben Sie die Standortaktualisierungen, die von den Core-Standortdiensten der iOS erhalten wurden, an die Places-Erweiterung.

1. Verwenden Sie die API für die Erweiterung `getNearbyPointsOfInterest` Places , um das Array von `ACPPlacesPoi` -Objekten um die aktuelle Position zu beziehen.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extrahieren Sie die Informationen aus den erhaltenen `ACPPlacesPOI` -Objekten und beginnen Sie mit der Überwachung dieser POIs.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Übergeben Sie die Standortaktualisierungen, die von den Google Play-Diensten oder den Android-Standortdiensten erhalten wurden, an die Places-Erweiterung.

1. Verwenden Sie die Places Extension-API `getNearbyPointsOfInterest` , um die Liste der `PlacesPoi` -Objekte um den aktuellen Speicherort zu erhalten.

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. Extrahieren Sie die Daten aus den erhaltenen `PlacesPOI` -Objekten und beginnen Sie mit der Überwachung dieser POIs.

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


Der Aufruf der `getNearbyPointsOfInterest` -API führt zu einem Netzwerkaufruf, der den Speicherort um den aktuellen Speicherort abruft.

>[!IMPORTANT]
>
>Sie sollten die API sparsam oder nur dann aufrufen, wenn eine wesentliche Standortänderung des Benutzers erfolgt.

## Posten von Geofence-Ereignissen

### iOS

Rufen Sie in iOS die API `processGeofenceEvent` Places im Delegate `CLLocationManager` auf. Diese API informiert Sie darüber, ob der Benutzer eine bestimmte Region aufgerufen oder beendet hat.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Rufen Sie in Android die Methode `processGeofence` zusammen mit dem entsprechenden Übergangsereignis in Ihrem Geofence Broadcast-Empfänger auf. Sie können die Liste der empfangenen Geofences kuratieren, um doppelte Einstiege/Ausstiege zu verhindern.

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
