---
title: Places-Erweiterung
description: Mit der Erweiterung "Orte"können Sie je nach dem Standort Ihrer Benutzer handeln.
translation-type: tm+mt
source-git-commit: a7dddb78e1e00a0bde01ea668334932759a9dae8
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 5%

---


# Places-Erweiterung {#places-extension}

Mit der Erweiterung &quot;Orte&quot;können Sie je nach dem Standort Ihrer Benutzer handeln. Diese Erweiterung ist die Schnittstelle zu den Ores Abfrage Service APIs. Durch Listening auf Ereignis, die GPS-Koordinaten und Geofenregion-Ereignis enthalten, löst diese Erweiterung neue Ereignis aus, die von der Rules Engine verarbeitet werden. Die Plates-Erweiterung ruft außerdem eine Liste des nächstgelegenen POI für die App-Daten ab, die von den APIs abgerufen werden. Die von den APIs zurückgegebenen Regionen werden im Cache und in der Persistenz gespeichert, was eine begrenzte Offlineverarbeitung ermöglicht.

## Installieren der Platzierungserweiterung in Adobe Experience Platform Launch

1. Klicken Sie in Experience Platform Launch auf die Registerkarte **[!UICONTROL Erweiterungen]**.
1. Suchen Sie auf der Registerkarte **[!UICONTROL Katalog]** die Erweiterung **[!UICONTROL Orte]** und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wählen Sie die Orte-Bibliotheken aus, die Sie in dieser Eigenschaft verwenden möchten. Dies sind die Bibliotheken, auf die in Ihrer App zugegriffen werden kann.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Wenn Sie auf **[!UICONTROL Speichern]** klicken, sucht das Experience Platform SDK in den ausgewählten Bibliotheken nach POIs in den Places Services. Die POI-Daten werden beim Erstellen der App nicht in den Download der Bibliothek einbezogen, aber eine ortsbasierte Untergruppe von POIs wird zur Laufzeit auf das Gerät des Endbenutzers heruntergeladen und basiert auf den GPS-Koordinaten des Benutzers.

1. Schließen Sie den Veröffentlichungsprozess ab, um die SDK-Konfiguration zu aktualisieren.

   Weitere Informationen zum Veröffentlichen in Experience Platform Launch finden Sie unter [Veröffentlichen](https://docs.adobe.com/content/help/de-DE/launch/using/reference/publish/overview.html).

### Die Platzierungserweiterung {#configure-places-extension} konfigurieren

![](//help/assets/places-extension.png)

## hinzufügen der Platzierungserweiterung für Ihre App {#add-places-to-app}

Sie können Ihre Android- und iOS-Apps mit der Erweiterung &quot;Orte&quot;versehen. Die Schritte zum Hinzufügen von Orten zu Ihrer iOS- oder Android-Anwendung finden Sie unten. Die Platzierungserweiterungen stehen auch für die folgenden Plattformen zur Verfügung. Informationen zum Hinzufügen von Orten zu Ihrer Anwendung beim Entwickeln mit einer dieser Plattformen finden Sie unter den folgenden Links:

**[Cordova Places Plugin](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places Plugin](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flatter Places Plugin](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places Plugin](https://github.com/adobe/xamarin-acpcore)**


### Android

So fügen Sie Ihrer App die Platzierungserweiterung mit Java hinzu:

1. hinzufügen Sie die Platzierungs-Erweiterung mit der GPÜGELdatei Ihrer App auf Ihr Projekt.

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

1. hinzufügen Sie die Bibliotheken &quot;Orte&quot;und &quot;[Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core)&quot;in Ihr Projekt ein. Sie müssen die folgenden Pods zu Ihrem `Podfile` hinzufügen:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Wenn Sie keine Cocoapods verwenden, können Sie auch die Bibliotheken für den Mobile Core und die Orte manuell auf unserer [Seite für Veröffentlichungen](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) auf Github einbinden.

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

### Registrieren Sie die Platzierungserweiterung mit Mobile Core {#register-places-mobile-core}

Sie müssen die Platzierungserweiterung mit Mobile Core unter Android und iOS registrieren.

#### Android

Registrieren Sie in der `OnCreate`-Methode Ihrer App die Platzierungserweiterungen:

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

Registrieren Sie in der `application:didFinishLaunchingWithOptions:`-Methode Ihrer App die Plates-Erweiterung mit Ihren anderen SDK-Registrierungsaufrufen:

**Ziel-C**

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

### Modifizieren der Ortsmitgliedschaft zu live {#places-ttl}

Standortdaten können schnell statisch werden, insbesondere wenn das Gerät nicht über eine Aktualisierung des Hintergrundorts verfügt.

Steuern Sie die Time-to-Live-Verbindung für Plates-Mitgliedschaftsdaten auf dem Gerät, indem Sie die Konfigurationseinstellung `places.membershipttl` festlegen. Der übergebene Wert gibt an, wie viele Sekunden der Status &quot;Orte&quot;für das Gerät gültig bleibt.

#### Android

Aktualisieren Sie im Rückruf von `MobileCore.start()` die Konfiguration mit den erforderlichen Änderungen, bevor Sie `lifecycleStart` aufrufen:

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

Rufen Sie in der ersten Zeile im Rückruf der `ACPCore`&#39;s `start:`-Methode `updateConfiguration:` auf

**Ziel-C**

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
