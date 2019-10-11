---
title: Objekte für benutzerdefinierte Orte
seo-title: Benutzerdefinierte native Klassen, die mit den Places APIs verwendet werden.
seo-description: Benutzerdefinierte native Klassen, die mit den Places APIs verwendet werden.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Objekte für benutzerdefinierte Orte {#places-objects}

Hier sind die benutzerdefinierten nativen Klassen, die mit den Places APIs verwendet werden:

## iOS

### ACPPlacesPoi

Die Definition lautet:

```text
/**
 *  @class ACPPlacesPoi
 *
 *  This class contains data that is directly correlated to the properties maintained by the Places database.
 */
@interface ACPPlacesPoi : NSObject

@property (nonatomic, strong, nullable) NSString* identifier;  ///< The identifier for the POI
@property (nonatomic, strong, nullable) NSString* name;  ///< The name of the POI
@property (nonatomic) double latitude;  ///< The latitude of the POI's center
@property (nonatomic) double longitude;  ///< The longitude of the POI's center
@property (nonatomic) NSUInteger radius;  ///< The radius of the POI
@property (nonatomic, strong, nullable) NSDictionary<NSString*, NSString*>* metaData;  ///< Dictionary containing meta data for the POI
@property (nonatomic) Boolean userIsWithin;  ///< Indicates if the device is currently inside of this POI

@end
```

