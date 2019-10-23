---
title: Platzierungs-Monitor-API-Referenz
seo-title: Platzierungs-Monitor-API-Referenz
description: 'Eine Liste der APIs für den Orts-Monitor. '
seo-description: 'Eine Liste der APIs für den Orts-Monitor.  '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Platzierungs-Monitor-API-Referenz {#places-api-reference}

## Platzierungs-Monitor-Erweiterung registrieren

Registriert die Platzierungsmonitor-Erweiterung mit dem Core Event Hub.

### RegisterExtension (Android)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

Die Syntax in Java lautet wie folgt:

```java
public static void registerExtension();
```

#### Beispiel

Rufen Sie diese Methode in der `onCreate` Methode auf, in der Sie den Rest des Experience Platform SDK initialisieren.

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension (iOS)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

Die Syntax in Objective-C lautet wie folgt:

```objective-c
+ (void) registerExtension;
```

#### Beispiel

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## Erweiterungsversion

Gibt die aktuelle Version der Erweiterung "Orts Monitor"zurück

### ExtensionVersion (Android)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```java
public static String extensionVersion();
```

#### Beispiel

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Beispiel

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Geräteüberwachung starten

Beginnen Sie mit der Verfolgung der Position des Geräts und der Überwachung nahe gelegener Orte.

### Start (Android)

Wenn der Benutzer die Berechtigung zum Verwenden des Geräteorts nicht erteilt hat, wird der Benutzer beim ersten Aufruf der `start` API zur Eingabe der Berechtigung aufgefordert.

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```java
public static void start();
```

#### Beispiel

```java
PlacesMonitor.start();
```

### Start (iOS)

>[!IMPORTANT]
>
>Um mit der Überwachung beginnen zu können, muss der Standortdienst über die erforderliche Genehmigung verfügen:
>
>* Wenn die Autorisierung für den Standortdienst nicht für die Anwendung bereitgestellt wurde, fordert der erste Aufruf der `start` API die Autorisierung zur Verwendung des für die Anwendung konfigurierten Ortsdienstes auf.
>* Wenn die Autorisierung bereitgestellt wurde, verfolgt der Orts-Monitor je nach Gerätefunktionen den Standort des Benutzers anhand des aktuellen Sets `ACPPlacesMonitorMode`. Der Monitor verwendet standardmäßig `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Wenn Ihr Aufruf zum Starten der Überwachung ausgeführt wird, bevor die Initialisierung des SDK abgeschlossen ist, wird er möglicherweise ignoriert.

Sie können sicherstellen, dass das SDK die Initialisierung abgeschlossen hat, indem Sie `start` aus dem Rückruf, der bereitgestellt wird, aufrufen `ACPCore::start:`.

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```objectivec
+ (void) start;
```

#### Beispiel

Starten des Orts-Monitors, wenn das SDK initialisiert wird:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Starten des Orts-Monitors später in der App-Ausführung:

```objective-c
[ACPPlacesMonitor start];
```

## Geräteüberwachung beenden

Stoppt die Verfolgung der Position des Geräts.

### Stopp (Android)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```java
public static void stop();
```

#### Beispiel

```java
PlacesMonitor.stop();
```

### Stopp (iOS)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```objectivec
+ (void) stop;
```

#### Beispiel

```objective-c
[ACPPlacesMonitor stop];
```

## Speicherort aktualisieren

Verwenden Sie diese API für eine sofortige Aktualisierung des Speicherorts des Geräts. Wenn Sie diese API aufrufen, versucht das Gerät, den Ort mit der von Ihnen angegebenen Genauigkeit zu ermitteln. Durch diesen Prozess werden auch die nahe gelegenen POIs aktualisiert, die durch die Erweiterung überwacht werden.

### UpdateLocation (Android)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```java
public static void updateLocation();
```

#### Beispiel

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Syntax

```objective-c
+ (void) updateLocationNow;
```

#### Beispiel

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Berechtigung zum App-Speicherort

Sie können diese API verwenden, um den Typ der Ortsberechtigung festzulegen, für den der Benutzer zur Verwendung für Standortdienste aufgefordert und autorisiert wird.

### SetLocationPermission (Android)

Diese API legt den Typ der Ortsberechtigungsanforderung fest, für die der Benutzer zur Auswahl aufgefordert wird.

>[!TIP]
>
>Diese API ist nur für Geräte mit Android 10 und höher wirksam.
>
>Um die entsprechende Autorisierungsaufforderung festzulegen, die dem Benutzer angezeigt werden soll, rufen Sie diese API vor dem `PlacesMonitor.start()`Aufruf auf. Beim Aufruf dieser Methode wird bei aktiver Überwachung die Ebene der Standortberechtigungen auf den Wert der angeforderten Berechtigung aktualisiert. Wenn die angeforderte Autorisierungsebene vom Anwendungsbenutzer bereits bereitgestellt oder verweigert wurde oder Sie versuchen, die Berechtigung von herabzusetzen `ALWAYS_ALLOW` auf `WHILE_USING_APP`, hat diese Methode keine Auswirkungen.

Die Standortberechtigung kann auf einen der folgenden Werte eingestellt werden:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Dieser Wert fordert den Benutzer auf, nur während der Verwendung der Anwendung auf den Speicherort des Geräts zuzugreifen. Eine App gilt als verwendet, wenn der Benutzer die App auf seinem Gerätebildschirm ansieht, z. B. wenn eine Aktivität im Vordergrund ausgeführt wird.

   >[!TIP]
   >
   >Vergewissern Sie sich, dass die Zugriffsberechtigung für ACCESS_FINE_LOCATION in der Manifestdatei der App festgelegt ist.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Dieser Wert fordert den Benutzer auf, auf die Geräteposition zuzugreifen, selbst wenn die Anwendung im Hintergrund ausgeführt wird.

   >[!TIP]
   >
   >Vergewissern Sie sich, dass die Zugriffsberechtigungen für ACCESS_HINTERGRUND_LOCATION und ACCESS_FINE_LOCATION in der Manifestdatei der App festgelegt sind.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` ist der Standardwert für die Berechtigung für den Speicherort.

>[!IMPORTANT]
>
>Wenn dem App-Benutzer die `WHILE_USING_APP` Berechtigung erteilt wurde, werden Geofencing nicht beim Betriebssystem registriert. Die Erweiterung "Orte überwachen"löst daher keine Ein-/Ausstiegsereignisse in Regionen aus, die im Hintergrund stattfinden.

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Beispiel

So fordern Sie die `WHILE_USING_APP` Berechtigung an:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

So aktualisieren Sie auf `ALWAYS_ALLOW` Berechtigung:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Diese API legt den Typ der Ortsautorisierungsanforderung fest, für die der Benutzer aufgefordert wird.

Um die entsprechende Autorisierungsaufforderung für den Benutzer festzulegen, rufen Sie `SetRequestAuthorizationLevel` vor dem Aufruf an `[ACPPlacesMonitor start]`. Um die entsprechende Autorisierungsaufforderung festzulegen, die dem Benutzer angezeigt werden soll, rufen Sie diese API vor dem `[ACPPlacesMonitor start]`Aufruf auf. Durch Aufruf dieser Methode und gleichzeitiger aktiver Überwachung wird die Standortautorisierungsebene auf den gewünschten Autorisierungswert aktualisiert. Wenn die beantragte Autorisierungsstufe entweder bereits vom Anwendungsbenutzer bereitgestellt oder verweigert wurde oder wenn eine Herabstufung der Berechtigung von `ACPPlacesRequestAuthorizationLevelAlways` zur `ACPPlacesRequestAuthorizationLevelWhenInUse` Autorisierung vorliegt, hat diese Methode keine Auswirkungen.

Die Autorisierungsebene kann auf einen der folgenden Werte eingestellt werden:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Fordert die Berechtigung des Benutzers zur Verwendung von Standortdiensten an, während die App verwendet wird. Die Benutzeraufforderung enthält den Text des `NSLocationWhenInUseUsageDescription` Schlüssels in der Datei "Info.plist"der App und das Vorhandensein dieses Schlüssels ist beim Aufruf dieser Methode erforderlich. Weitere Informationen finden Sie in der [Apple-Dokumentation zu requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Verwenden Sie dieses Enum, um Standortdienste anzufordern, auch wenn sich die App im Hintergrund befindet. Sie müssen die Schlüssel `NSLocationAlwaysUsageDescription` und `NSLocationWhenInUseUsageDescription` Schlüssel in der Info.plist Ihrer App haben. Diese Schlüssel definieren den Text, der während der Benutzeraufforderung angezeigt wird. Weitere Informationen finden Sie in der [Apple-Dokumentation zur Autorisierung](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` ist der Standardwert für die Autorisierung einer Anforderung.

>[!IMPORTANT]
>
>Die Anwendung, die die Verwendung der `ACPPlacesRequestAuthorizationLevelWhenInUse` Berechtigung autorisiert hat, kann keine Ein-/Ausstiegsereignisse für Regionen auslösen, die im Hintergrund stattfinden.

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel
```

#### Beispiel

So fordern Sie die `ACPPlacesRequestAuthorizationLevelWhenInUse` Berechtigung an:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Aktualisierung auf `ACPPlacesRequestAuthorizationLevelAlways` Autorisierung:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways]
```

## Überwachungsmodus (nur iOS)

Die Überwachung kann auf einen der folgenden Werte eingestellt werden:

* `ACPPlacesMonitorModeContinuous`

   Die Überwachungserweiterung empfängt und verarbeitet Standorte häufiger. Diese Überwachungsstrategie verbraucht viel Energie, bietet aber eine höhere Genauigkeit. Weitere Informationen finden Sie in der [Apple-Dokumentation zur kontinuierlichen Überwachung](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation).

* `ACPPlacesMonitorModeSignificantChanges`

   Die Überwachungs-Erweiterung empfängt und verarbeitet nur Standortaktualisierungen, nachdem das Gerät eine erhebliche Entfernung vom zuvor verarbeiteten Speicherort entfernt hat. Diese Überwachungsstrategie verbraucht weniger Energie als die kontinuierliche Überwachungsstrategie. Weitere Informationen zur Überwachung finden Sie in der Dokumentation zu [Apple](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Die folgende Syntax und der Beispielcode für diese API:

#### Syntax

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Beispiel

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
