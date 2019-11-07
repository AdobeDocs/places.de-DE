---
title: Verwenden Ihres eigenen Monitors
seo-title: Verwenden Ihres eigenen Monitors
description: Sie können Ihre Überwachungsdienste auch verwenden und mit den Orten integrieren, indem Sie die APIs für die Platzierungserweiterung verwenden.
seo-description: Sie können Ihre Überwachungsdienste auch verwenden und mit den Orten integrieren, indem Sie die APIs für die Platzierungserweiterung verwenden.
translation-type: tm+mt
source-git-commit: d12dae0e30fab8639260c2c55accb4b79096382d

---


# Verwenden Ihres eigenen Monitors {#using-your-monitor}

Sie können Ihre Überwachungsdienste auch verwenden und mit den Orten integrieren, indem Sie die APIs für die Platzierungserweiterung verwenden.

## Registrieren von Geofencing

Wenn Sie sich für die Verwendung Ihrer Überwachungsdienste entscheiden, registrieren Sie die Geodaten der POIs um Ihren aktuellen Standort, indem Sie die folgenden Schritte ausführen:

### iOS

Führen Sie unter iOS die folgenden Schritte aus:

1. Übergeben Sie die Ortsaktualisierungen, die Sie von den Core-Standortdiensten des iOS erhalten haben, an die Places-Erweiterung.

1. Verwenden Sie die API für die `getNearbyPointsOfInterest` Platzierungserweiterung, um das Array von `ACPPlacesPoi` Objekten um den aktuellen Speicherort abzurufen.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extrahieren Sie die Informationen aus den erhaltenen `ACPPlacesPOI` Objekten und beginnen Sie mit der Überwachung dieser POI.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center                                                                                                                              radius:currentRegion.radius                                                                                                                    identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
   
       }
   }
   ```

### Android

1. Übergeben Sie die Ortsaktualisierungen, die Sie über die Google Play-Dienste oder die Android-Ortsdienste erhalten haben, an die Places-Erweiterung.

1. Verwenden Sie die `getNearbyPointsOfInterest` `PlacesPoi` Places Extension API, um die Liste der n Objekte um den aktuellen Speicherort abzurufen.

   ```java
       LocationCallback callback = new LocationCallback() {
               @Override
               public void onLocationResult(LocationResult locationResult) {
                   super.onLocationResult(locationResult);
   
                   Places.getNearbyPointsOfInterest(currentLocation, 10, new            AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois)
                   starMonitoringGeofence(pois);
               }
           });
   
               }
           };
   ```

1. Extrahieren Sie die Daten aus den erhaltenen `PlacesPOI` Objekten und beginnen Sie mit der Überwachung dieser POI.

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

Der Aufruf der `getNearbyPointsOfInterest` API führt zu einem Netzwerkaufruf, der den Speicherort um den aktuellen Speicherort abruft.

>[!IMPORTANT]
>
>Sie sollten die API nur sparsam oder nur dann aufrufen, wenn der Benutzer eine wesentliche Standortänderung vornimmt.

## Posting von Geofenereignissen

### iOS

Rufen Sie unter iOS die `processGeofenceEvent` Places-API im `CLLocationManager` Delegaten auf. Diese API informiert Sie darüber, ob der Benutzer eine bestimmte Region eingegeben oder verlassen hat.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```
