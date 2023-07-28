---
title: Places-Erweiterung
description: Mit der Places-Erweiterung können Sie basierend auf dem Standort Ihrer Benutzer handeln.
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 5%

---

# Places-Erweiterung {#places-extension}

Mit der Places-Erweiterung können Sie basierend auf dem Standort Ihrer Benutzer handeln. Diese Erweiterung ist die Schnittstelle zu den Places Query Service-APIs. Durch das Überwachen auf Ereignisse, die GPS-Koordinaten und Geofence-Region-Ereignisse enthalten, sendet diese Erweiterung neue Ereignisse, die von der Regel-Engine verarbeitet werden. Die Places-Erweiterung ruft außerdem eine Liste des nächstgelegenen Zielpunkts für die App-Daten ab, die aus den APIs abgerufen werden. Die von den APIs zurückgegebenen Regionen werden im Cache und in der Persistenz gespeichert, was eine eingeschränkte Offline-Verarbeitung ermöglicht.

## Installieren der Places-Erweiterung in Adobe Experience Platform Launch

1. Klicken Sie in Experience Platform Launch auf die **[!UICONTROL Erweiterungen]** Registerkarte.
1. Im **[!UICONTROL Katalog]** Registerkarte, suchen Sie die **[!UICONTROL Orte]** und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wählen Sie die Places-Bibliotheken aus, die Sie in dieser Eigenschaft verwenden möchten. Dies sind die Bibliotheken, auf die in Ihrer App zugegriffen werden kann.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Wenn Sie auf **[!UICONTROL Speichern]**, durchsucht das Experience Platform SDK die Places Services in den von Ihnen ausgewählten Bibliotheken nach POIs. Die POI-Daten sind beim Erstellen der App nicht im Download der Bibliothek enthalten, aber eine standortbasierte Untergruppe von POIs wird zur Laufzeit auf das Gerät des Endbenutzers heruntergeladen und basiert auf den GPS-Koordinaten des Benutzers.

1. Schließen Sie den Veröffentlichungsprozess ab, um die SDK-Konfiguration zu aktualisieren.

   Weitere Informationen zur Veröffentlichung in Experience Platform Launch finden Sie unter [Publishing](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=de).

### Konfigurieren der Places-Erweiterung {#configure-places-extension}

![](/help/assets/places-extension.png)

## Hinzufügen der Places-Erweiterung zu Ihrer App {#add-places-to-app}

Sie können die Places-Erweiterung zu Ihren Android- und iOS-Apps hinzufügen. Die Schritte zum Hinzufügen von Places zu Ihrer iOS- oder Android-Anwendung finden Sie unten. Places-Erweiterungen sind auch für die folgenden Plattformen verfügbar: Informationen zum Hinzufügen von Places zu Ihrer Anwendung bei der Entwicklung mit einer dieser Plattformen finden Sie unter den zugehörigen Links:

**[Cordova Places-Plug-in](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places Plugin](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flutter Places-Plug-in](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places-Plugin](https://github.com/adobe/xamarin-acpcore)**


### Android

So fügen Sie die Places-Erweiterung mithilfe von Java zu Ihrer App hinzu:

1. Fügen Sie Ihrem Projekt mithilfe der Gradle-Datei Ihrer App die Places-Erweiterung hinzu.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importieren Sie die Erweiterung Places in die Hauptaktivität Ihrer Anwendung.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

So fügen Sie Ihrer App eine Places-Erweiterung mithilfe von Objective-C oder Swift hinzu:

1. Fügen Sie die Orte hinzu und [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) Bibliotheken in Ihrem Projekt. Sie müssen die folgenden Pods zu Ihrem `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Wenn Sie Cocoapods nicht verwenden, können Sie die Mobile Core- und Places-Bibliotheken auch manuell aus unserer [Veröffentlichungsseite](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) auf Github.

1. Aktualisieren Sie Ihre Cocoapods:

   ```objective-c
   pod update
   ```

1. Öffnen Sie Xcode und importieren Sie in Ihrer AppDelegate-Klasse die Header Core und Places :

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

### Registrieren der Places-Erweiterung mit Mobile Core {#register-places-mobile-core}

Sie müssen die Places-Erweiterung bei Mobile Core in Android und iOS registrieren.

#### Android

In der `OnCreate` -Methode die Places-Erweiterungen registrieren:

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

In der `application:didFinishLaunchingWithOptions:` -Methode, registrieren Sie die Places-Erweiterung mit Ihren anderen SDK-Registrierungs-Aufrufen:

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

### Ändern der Gültigkeitsdauer der Places-Mitgliedschaft {#places-ttl}

Standortdaten können schnell veraltet sein, insbesondere wenn das Gerät keine Hintergrundstandortaktualisierungen erhält.

Steuern Sie die Live-Zeit für Places-Mitgliedschaftsdaten auf dem Gerät, indem Sie die `places.membershipttl` Konfigurationseinstellung. Der übergebene Wert stellt die Anzahl der Sekunden dar, in denen der Status Places für das Gerät gültig bleibt.

#### Android

Innerhalb des Rückrufs von `MobileCore.start()` Aktualisieren Sie die Konfiguration mit den erforderlichen Änderungen, bevor Sie `lifecycleStart`:

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

In der ersten Zeile im Callback von `ACPCore`s `start:` Methode, Aufruf `updateConfiguration:`

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

Um die SDK-Konfiguration zur Laufzeit programmgesteuert zu aktualisieren, verwenden Sie die folgenden Informationen, um die Konfigurationswerte der Places-Erweiterung zu ändern. Weitere Informationen finden Sie unter [Referenz zur Konfigurations-API](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Schlüssel | Erforderlich | Beschreibung |
| :--- | :--- | :--- |
| `places.libraries` | Ja | Die Places-Erweiterungsbibliotheken für die mobile App. Sie gibt die Bibliotheks-ID und den Namen der Bibliothek an, die von der Mobile App unterstützt werden. |
| `places.endpoint` | Ja | Der standardmäßige Places Query Service-Endpunkt, der zum Abrufen von Informationen zu Bibliotheken und POIs verwendet wird. |
| `places.membershipttl` | Nein | Standardwert ist 3600 (Sekunden in einer Stunde). Gibt an, wie lange die Places-Mitgliedschaftsinformationen für das Gerät in Sekunden gültig bleiben. |
