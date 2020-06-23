---
title: Places-Erweiterung
description: Mit der Erweiterung "Orte"können Sie je nach dem Standort Ihrer Benutzer handeln.
translation-type: tm+mt
source-git-commit: 0ac139fce666540b36a8c82fe4c05974e12e987f
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 5%

---


# Places-Erweiterung {#places-extension}

Mit der Erweiterung &quot;Orte&quot;können Sie je nach dem Standort Ihrer Benutzer handeln. Diese Erweiterung ist die Schnittstelle zu den Ores Abfrage Service APIs. Durch Listening auf Ereignis, die GPS-Koordinaten und Geofenregion-Ereignis enthalten, löst diese Erweiterung neue Ereignis aus, die von der Rules Engine verarbeitet werden. Die Plates-Erweiterung ruft außerdem eine Liste des nächstgelegenen POI für die App-Daten ab, die von den APIs abgerufen werden. Die von den APIs zurückgegebenen Regionen werden im Cache und in der Persistenz gespeichert, was eine begrenzte Offlineverarbeitung ermöglicht.

## Installieren der Platzierungserweiterung beim Starten der Adobe Experience Platform

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. Suchen Sie auf der **[!UICONTROL Catalog]** Registerkarte die **[!UICONTROL Places]** Erweiterung und klicken Sie auf **[!UICONTROL Install]**.
1. Wählen Sie die Orte-Bibliotheken aus, die Sie in dieser Eigenschaft verwenden möchten. Dies sind die Bibliotheken, auf die in Ihrer App zugegriffen werden kann.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie auf klicken **[!UICONTROL Save]**, durchsucht das Experience Platform-SDK die Orte-Dienste nach POIs in den von Ihnen ausgewählten Bibliotheken. Die POI-Daten werden beim Erstellen der App nicht in den Download der Bibliothek einbezogen, aber eine ortsbasierte Untergruppe von POIs wird zur Laufzeit auf das Gerät des Endbenutzers heruntergeladen und basiert auf den GPS-Koordinaten des Benutzers.

1. Schließen Sie den Veröffentlichungsprozess ab, um die SDK-Konfiguration zu aktualisieren.

   Weitere Informationen zum Veröffentlichen in Experience Platform Launch finden Sie unter [Veröffentlichen](https://docs.adobe.com/content/help/de-DE/launch/using/reference/publish/overview.html).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Hinzufügen der Platzierungserweiterung für Ihre App {#add-places-to-app}

Sie können Ihre Android- und iOS-Apps mit der Erweiterung &quot;Orte&quot;versehen. Die Schritte zum Hinzufügen von Orten zu Ihrer iOS- oder Android-Anwendung finden Sie unten. Für Cordova und React Native stehen ebenfalls Plätze zur Verfügung. Informationen zum Hinzufügen von Orten zu Ihrer Anwendung beim Entwickeln mit einer dieser Plattformen finden Sie unter den folgenden Links:

**[Cordova Places Plugin](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places Plugin](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

### Android

So fügen Sie Ihrer App die Platzierungserweiterung mit Java hinzu:

1. Hinzufügen Sie die Platzierungs-Erweiterung mit der GPÜGELdatei Ihrer App auf Ihr Projekt.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importieren Sie die Platzierungserweiterung in die Haupt-Aktivität Ihrer Anwendung.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

So fügen Sie Ihrer App die Platzierungserweiterung mit Objective-C oder Swift hinzu:

1. Hinzufügen Sie die Bibliotheken &quot;Orte&quot;und &quot; [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) &quot;in Ihr Projekt ein. Sie müssen die folgenden Pods hinzufügen `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Wenn Sie keine Cocoapods verwenden, können Sie auch die Bibliotheken für den Mobile Core und die Orte manuell auf unserer Seite [für](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) Veröffentlichungen auf Github einbinden.

1. Aktualisieren Sie Ihre Cocoapods:

   ```objective-c
   pod update
   ```

1. Öffnen Sie Xcode und importieren Sie in der AppDelegate-Klasse die Header Core und Places:

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### Registrieren der Platzierungserweiterung mit Mobile Core {#register-places-mobile-core}

Sie müssen die Platzierungserweiterung mit Mobile Core unter Android und iOS registrieren.

#### Android

Registrieren Sie in der `OnCreate` Methode Ihrer App die Plates-Erweiterungen:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Registrieren Sie in der `application:didFinishLaunchingWithOptions:` Methode Ihrer App die Plates-Erweiterung bei Ihren anderen SDK-Registrierungsaufrufen:

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### Ändern der Mitgliederzeit für Orte {#places-ttl}

Standortdaten können schnell statisch werden, insbesondere wenn das Gerät nicht über eine Aktualisierung des Hintergrundorts verfügt.

Legen Sie die `places.membershipttl` Konfigurationseinstellung fest, um die Live-Übertragung der Mitgliedschaftsdaten auf dem Gerät zu steuern. Der übergebene Wert gibt an, wie viele Sekunden der Status &quot;Orte&quot;für das Gerät gültig bleibt.

#### Android

Im Rückruf der `MobileCore.start()` Aktualisierung der Konfiguration mit den erforderlichen Änderungen vor dem Aufruf `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Rufen Sie in der ersten Zeile in der Rückruffunktion der `ACPCore``start:` Methode `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## Konfigurationsschlüssel

Um die SDK-Konfiguration zur Laufzeit programmgesteuert zu aktualisieren, ändern Sie die Konfigurationswerte der Plates-Erweiterung mithilfe der folgenden Informationen. Weitere Informationen finden Sie unter [Configuration API Reference](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Schlüssel | Erforderlich | Beschreibung |
| :--- | :--- | :--- |
| `places.libraries` | Ja | Die Speichererweiterungsbibliotheken für die mobile App. Er gibt die Bibliotheks-ID und den Namen der Bibliothek an, die von der mobilen App unterstützt werden. |
| `places.endpoint` | Ja | Der Standardendpunkt &quot;Orts Abfrage Service&quot;, mit dem Informationen zu Bibliotheken und POIs abgerufen werden. |
| `places.membershipttl` | Nein | Standardwert von 3600 (Sekunden in einer Stunde). Gibt an, wie lange (in Sekunden) die Platzierungsmitgliedschaftsinformationen für das Gerät gültig bleiben. |
