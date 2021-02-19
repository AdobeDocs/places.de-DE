---
title: Verwenden der Erweiterung "Orts Monitor"
description: Informationen zum Installieren, Konfigurieren und Verwenden der Erweiterung "Orts Monitor".
translation-type: tm+mt
source-git-commit: 7fdaace59886225b7fd9b0eba8cc6c2a139fa2d7
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 8%

---


# Verwenden der Erweiterung &quot;Orts Monitor&quot; {#using-places-monitor-extension}

Führen Sie die folgenden Aufgaben aus, um die Erweiterung &quot;Orts-Monitor&quot;zu verwenden:

## Installieren Sie die Erweiterung Places Monitor in Experience Platform Launch

1. Klicken Sie in Experience Platform Launch auf die Registerkarte **[!UICONTROL Erweiterungen]**.
1. Suchen Sie auf der Registerkarte **[!UICONTROL Katalog]** die Erweiterung **[!UICONTROL Orte Monitor]** und klicken Sie auf **Installieren**.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Führen Sie den Veröffentlichungsprozess aus, um die SDK-Konfiguration zu aktualisieren.

### Die Erweiterung &quot;Platzierungsmonitor&quot;konfigurieren {#configure-places-monitor-extension}

Es gibt keine Aufgaben zur Konfiguration der Plates Monitor-Erweiterung.

![Konfigurieren der ‌ &quot;Orte-Monitor](/help/assets/configure_places_monitor.png)&quot;

## hinzufügen der Erweiterung &quot;Platzierungsmonitor&quot;auf Ihre App {#add-monitor-extension-to-app}

Die Anweisungen zum Hinzufügen der Platzierungsmonitor-Erweiterung zu Ihrer Android- oder iOS-Anwendung finden Sie unten.

Weitere Plattformunterstützung für die Platzierungsmonitor-Erweiterung:
**[Cordova Places Monitor](https://github.com/adobe/cordova-acpplaces-monitor/blob/master/README.md)**

**[Bildschirm &quot;Ansprechende native Orte&quot;](https://github.com/adobe/react-native-acpplaces-monitor/blob/master/README.md)**

**[Flachbildschirm](https://github.com/adobe/flutter_acpplaces_monitor/blob/master/README.md)**


### Android

Führen Sie in Android die folgenden Schritte aus:

#### Java

1. hinzufügen Sie die Erweiterungen &quot;Orte-Monitor&quot;und &quot;Orte&quot;mithilfe der Dockingdatei Ihrer App an Ihr Projekt an.

1. Schließen Sie auch die neuesten Google-Standorte in der Datei &quot;gradle&quot;ein.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importieren Sie die Erweiterung &quot;Orts-Monitor&quot;in die Haupt-Aktivität Ihrer Anwendung.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

Führen Sie unter iOS die folgenden Schritte aus:

1. hinzufügen Sie die Bibliothek über Ihre Cocoapods `Podfile`, indem Sie `pod 'ACPPlacesMonitor'` hinzufügen.
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


## Registrieren und Beginn des Orts-Monitors {#register-start-places-monitor}

Sie müssen sich registrieren und den Orte-Monitor in Android oder iOS Beginn.

## Android

Führen Sie in Android die folgenden Schritte aus:

### Java

Registrieren Sie in der `OnCreate`-Methode Ihrer App die Plates Monitor Extensions:

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

Registrieren Sie im Ordner`application:didFinishLaunchingWithOptions` Ihrer iOS-App `PlacesMonitor` und Orte mit Mobile Core:

### Ziel-C

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
>Die Orteüberwachung hängt von der Platzierungserweiterung ab. Wenn Sie die Erweiterung &quot;Orts-Monitor&quot;manuell installieren, stellen Sie sicher, dass Sie auch die Bibliothek `libACPPlaces_iOS.a` zu Ihrem Projekt hinzufügen.


## hinzufügen Berechtigungen für das Manifest

### Android

**Java**

Um für alle Versionen von Android anzugeben, dass für Ihre App eine Ortsberechtigung erforderlich ist, fügen Sie ein `<uses-permission>`-Element in Ihrem App-Manifest als untergeordnetes Element des Elements der obersten Ebene `<manifest>` hinzu. Für Android-Anwendungen mit Zielgruppe API Level 29 und höher, die der App den Zugriff auf den Speicherort im Hintergrund ermöglichen, schließen Sie die ACCESS_HINTERGRUND_LOCATION-Berechtigung ein.

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

iOS unterstützt den Versand von Positionierungs-Ereignissen in Apps, die ausgesetzt oder nicht mehr ausgeführt werden. Um Ortsaktualisierungen im Hintergrund für die Platzierungsmonitor-Erweiterung zu erhalten, konfigurieren Sie die Funktion für Standortaktualisierungen für Ihre App in `Xcode.background-location-updates`.

![mit dem Orte-Monitor](/help/assets/using-the-places-monitor_1.png)

## Konfigurieren der plist-Schlüssel

Die folgenden Schlüssel müssen in der Datei `Info.plist` Ihrer App enthalten sein:

* `NSLocationWhenInUseUsageDescription` - Der Text sollte beschreiben, warum die App während der Ausführung im Vordergrund Zugriff auf die Standortinformationen des Benutzers anfordert.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - Der Text sollte beschreiben, warum die App jederzeit den Zugriff auf die Standortinformationen des Benutzers anfordert.

>[!TIP]
>
>Wenn Ihre App iOS 10 und früher unterstützt, ist auch der Schlüssel `NSLocationAlwaysUsageDescription` erforderlich.

![](/help/assets/using-the-places-monitor_2.png)
