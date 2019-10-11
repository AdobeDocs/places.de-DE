---
title: Platzierungserweiterung
seo-title: Platzierungserweiterung
description: Mit der Erweiterung "Orte"können Sie je nach Standort Ihrer Benutzer handeln.
seo-description: Mit der Erweiterung "Orte"können Sie je nach Standort Ihrer Benutzer handeln.
translation-type: tm+mt
source-git-commit: 1fb87285d2ccd581ee59ab1b1efbec4af04a0fab

---


# Platzierungserweiterung {#places-extension}

Mit der Erweiterung "Orte"können Sie je nach Standort Ihrer Benutzer handeln. Diese Erweiterung ist die Schnittstelle zu den APIs für die Abfrage von Orten. Durch Listening auf Ereignisse, die GPS-Koordinaten und Ereignisse für Geofenregionen enthalten, löst diese Erweiterung neue Ereignisse aus, die von der Rules Engine verarbeitet werden. Die Plates-Erweiterung ruft außerdem eine Liste des nächstgelegenen POI für die App-Daten ab, die von den APIs abgerufen werden. Die von den APIs zurückgegebenen Regionen werden im Cache und in der Persistenz gespeichert, was eine begrenzte Offlineverarbeitung ermöglicht.

## Installieren der Platzierungserweiterung in Adobe Experience Platform Launch

1. Klicken Sie in Experience Platform Launch auf die **[!UICONTROL Extensions]** Registerkarte.
2. Suchen Sie auf der **[!UICONTROL Catalog]** Registerkarte die **[!UICONTROL Adobe Places]** Erweiterung und klicken Sie auf **[!UICONTROL Install]**.
3. Wählen Sie die Orte-Bibliotheken aus, die Sie in dieser Eigenschaft verwenden möchten. Dies sind die Bibliotheken, auf die in Ihrer App zugegriffen werden kann.
4. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie auf klicken **[!UICONTROL Save]**, durchsucht das Experience Platform SDK die Places Services nach POIs in den ausgewählten Bibliotheken. Die POI-Daten werden beim Erstellen der App nicht in den Download der Bibliothek einbezogen, aber eine ortsbasierte Untergruppe von POIs wird zur Laufzeit auf das Gerät des Endbenutzers heruntergeladen und basiert auf den GPS-Koordinaten des Benutzers.

5. Schließen Sie den Veröffentlichungsprozess ab, um die SDK-Konfiguration zu aktualisieren.

   Weitere Informationen zur Veröffentlichung in Experience Platform Launch finden Sie unter [Veröffentlichen](https://docs.adobelaunch.com/launch-reference/publishing).

### Konfigurieren der Platzierungserweiterung {#configure-places-extension}

![](//help/assets/places-extension.png)

## Hinzufügen der Platzierungserweiterung zu Ihrer App {#add-places-to-app}

Sie können Ihre Android- und iOS-Apps mit der Erweiterung "Orte"versehen.

### Android

So fügen Sie Ihrer App die Platzierungserweiterung mit Java hinzu:

1. Fügen Sie dem Projekt mithilfe der Adle-Datei Ihrer App die Ortserweiterung hinzu.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

2. Importieren Sie die Erweiterung "Orte"in die Hauptaktivität Ihrer Anwendung.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

So fügen Sie Ihrer App die Platzierungserweiterung mit Objective-C oder Swift hinzu:

1. Fügen Sie Ihrem Projekt die Bibliotheken "Orte"und " [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) "hinzu. Sie müssen die folgenden Pods hinzufügen `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Wenn Sie keine Cocoapods verwenden, können Sie die Bibliotheken für den Mobile Core und Orte auch manuell auf unserer Seite [für](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) Veröffentlichungen auf Github einbinden.

2. Aktualisieren Sie Ihre Cocoapods:

   ```objective-c
   pod update
   ```

3. Öffnen Sie Xcode und importieren Sie in der AppDelegate-Klasse die Header Core und Places:

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

### Registrieren von Orten mit Mobile Core {#register-places-mobile-core}

Sie müssen Orte mit Mobile Core in Android und iOS registrieren.

#### Android

Registrieren Sie in der `OnCreate` Methode Ihrer App die Location Services-Erweiterungen:

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

## Konfigurationsschlüssel

Um die SDK-Konfiguration zur Laufzeit programmgesteuert zu aktualisieren, ändern Sie die Speicherplatzkonfigurationswerte mit den folgenden Informationen. Weitere Informationen finden Sie unter [Configuration API Reference](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Schlüssel | Erforderlich | Beschreibung |
| :--- | :--- | :--- |
| `places.libraries` | Ja | Die Platzierung von Bibliotheken für die mobile App. Er gibt die Bibliotheks-ID und den Namen der Bibliothek an, die von der mobilen App unterstützt werden. |
| `places.endpoint` | Ja | Der standardmäßige Experience Platform Location Query Service-Endpunkt, mit dem Informationen zu Bibliotheken und POIs abgerufen werden. |

