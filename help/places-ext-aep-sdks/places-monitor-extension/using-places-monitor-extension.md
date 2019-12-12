---
title: Verwenden der Erweiterung "Orts Monitor"
description: Informationen zum Installieren, Konfigurieren und Verwenden der Erweiterung "Orts Monitor".
translation-type: tm+mt
source-git-commit: ac1d410a676557064d5390f8392f402541754478

---


# Verwenden der Erweiterung "Orts Monitor" {#using-places-monitor-extension}

Führen Sie die folgenden Aufgaben aus, um die Erweiterung "Orts-Monitor"zu verwenden:

## Installieren der Erweiterung "Platzierungsmonitor"im Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. Suchen Sie auf der **[!UICONTROL Catalog]** Registerkarte die **[!UICONTROL Places Monitor]** Erweiterung und klicken Sie auf **Installieren**.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. Folgen Sie dem Veröffentlichungsprozess, um die SDK-Konfiguration zu aktualisieren.

### Konfigurieren der Platzierungsmonitor-Erweiterung {#configure-places-monitor-extension}

Es gibt keine Konfigurationsaufgaben für die Plates Monitor-Erweiterung.

![Konfigurieren der ‌ "Orte-Monitor](/help/assets/configure_places_monitor.png)"

## Hinzufügen der Erweiterung "Orts-Monitor"zu Ihrer App {#add-monitor-extension-to-app}

Sie müssen der Android- oder iOS-App die Erweiterung "Orts Monitor"hinzufügen.

### Android

Führen Sie in Android die folgenden Schritte aus:

#### Java

1. Fügen Sie die Erweiterungen "Orte-Monitor"und "Orte"mithilfe der Dockingdatei Ihrer App zum Projekt hinzu.

1. Schließen Sie auch die neuesten Google-Standorte in der Datei "gradle"ein.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importieren Sie die Erweiterung "Orts-Monitor"in die Hauptaktivität Ihrer Anwendung.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

Führen Sie unter iOS die folgenden Schritte aus:

1. Fügen Sie die Bibliothek über Ihre Cocoapods zu Ihrem Projekt hinzu, `Podfile` indem Sie sie hinzufügen `pod 'ACPPlacesMonitor'`.
1. Importieren Sie die Bibliotheken für die Orts- und Orteüberwachung:

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## Registrieren und Starten des Orts-Monitors {#register-start-places-monitor}

Sie müssen sich registrieren und den Orte-Monitor in Android oder iOS starten.

## Android

Führen Sie in Android die folgenden Schritte aus:

### Java

Registrieren Sie in der `OnCreate` Methode Ihrer App die Plates Monitor-Erweiterungen:

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
            PlacesMonitor.start();//Start monitoring the geo-fences
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>Die Orteüberwachung hängt von der Platzierungserweiterung ab. Wenn Sie die Erweiterung „Places Monitor“ manuell installieren, stellen Sie sicher, dass Sie auch die `places.aar`-Bibliothek zu Ihrem Projekt hinzufügen.

## iOS

Registrieren Sie sich in der`application:didFinishLaunchingWithOptions`iOS-App `PlacesMonitor` und stellen Sie sie mit Mobile Core zusammen:

### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>Die Orteüberwachung hängt von der Platzierungserweiterung ab. When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## Berechtigungen zum Manifest hinzufügen

### Android

**Java**

Um für alle Versionen von Android anzugeben, dass für Ihre App eine Standortberechtigung erforderlich ist, fügen Sie ein `<uses-permission>` Element im App-Manifest als untergeordnetes Element des obersten `<manifest>` Elements hinzu. Wenn Android-Anwendungen, die auf API-Ebene ab 29 abzielen, der App den Zugriff auf den Speicherort im Hintergrund ermöglichen sollen, schließen Sie die ACCESS_HINTERGRUND_LOCATION-Berechtigung ein.

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## Aktivieren von Standortaktualisierungen im Hintergrund {#enable-location-updates-background}

iOS unterstützt die Bereitstellung von Standortereignissen für Apps, die ausgesetzt oder nicht mehr ausgeführt werden. Um Standortaktualisierungen im Hintergrund für die Places Monitor-Erweiterung zu erhalten, konfigurieren Sie die Funktion für Standortaktualisierungen für Ihre App in `Xcode.background-location-updates`.

![mit dem Orte-Monitor](/help/assets/using-the-places-monitor_1.png)

## Konfigurieren der plist-Schlüssel

Die folgenden Schlüssel müssen in der `Info.plist` Datei Ihrer App enthalten sein:

* `NSLocationWhenInUseUsageDescription` - Der Text sollte beschreiben, warum die App während der Ausführung im Vordergrund Zugriff auf die Standortinformationen des Benutzers anfordert.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - Der Text sollte beschreiben, warum die App jederzeit den Zugriff auf die Standortinformationen des Benutzers anfordert.

>[!TIP]
>
>Wenn Ihre App iOS 10 und früher unterstützt, ist auch der `NSLocationAlwaysUsageDescription` Schlüssel erforderlich.

![](/help/assets/using-the-places-monitor_2.png)
