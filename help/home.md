---
title: Adobe Experience Platform Location Service
seo-title: Adobe Experience Platform Location Service
description: 'Der Location Service ist ein wichtiger Kontext, um die Interaktion der mobilen Benutzer zu verstehen. In diesem Kontext können Entwickler mobiler Apps den App-Entwurf verbessern und ihn zu einem personalisierteren und ansprechenderen Erlebnis machen. '
seo-description: 'Der Location Service ist ein wichtiger Kontext, um die Interaktion der mobilen Benutzer zu verstehen. In diesem Kontext können Entwickler mobiler Apps den App-Entwurf verbessern und ihn zu einem personalisierteren und ansprechenderen Erlebnis machen. '
translation-type: tm+mt
source-git-commit: a5eee2378475885a2aef9867ff2c38a8881c9bbe

---


# Übersicht {#home}

Der Adobe Experience Platform Location Service (Location Service) ist ein wichtiger Kontext für das Verständnis der Interaktion von Mobilbenutzern. In diesem Kontext können Entwickler mobiler Apps den App-Entwurf verbessern und ihn zu einem personalisierteren und ansprechenderen Erlebnis machen. Places ist ein Geolocation-Dienst, der Entwicklern mobiler Apps ermöglicht, den Standortkontext zu verstehen, indem Rich-und einfach zu verwendende SDK-Schnittstellen verwendet werden, die von einer flexiblen Datenbank mit Interessensgebieten (POIs) begleitet werden.

Mit dem Location Service können Sie Folgendes erreichen:

* Erstellen und verwalten Sie eine Datenbank mit POIs, die mit anderen Adobe Experience Cloud-Lösungen verwendet werden können.
* Fügen Sie den POIs benutzerspezifische Metadaten hinzu, um sie durch Angabe zusätzlicher Attribute reicher und aussagekräftiger zu gestalten.
* Visualisieren Sie die POIs auf einer Karte, um den räumlichen Kontext zu verstehen und Metadatenattribute hinzuzufügen/zu bearbeiten.
* Konfigurieren Sie das SDK in Adobe Experience Platform Launch, um die standortgesteuerten Regeln und metadatenbasierten Bedingungen zu definieren.
* Verringern Sie den Code, den Sie an den Speicherort des Monitorgeräts schreiben müssen, und verwenden Sie die Platzierungserweiterung, um die standortspezifischen Regeln automatisch auszulösen.

Auf diese Weise können Sie in Echtzeit Aktionen aus Standortsignalen ausführen, wann und wo sie wichtig sind. Der richtige Kontext bietet eine umfassendere Interaktion mit Mobilgeräten.

Die folgenden Möglichkeiten stehen Ihnen zur Verwendung von Orten zur Verfügung:

* Senden Sie eine Echtzeit-Benachrichtigung, wenn jemand einen POI eingibt, *"Hey...Willkommen im Stadion."*
* Analysieren Sie den Fußverkehr Ihrer eigenen Läden im Vergleich zu Ihren Konkurrenzgeschäften.
* Segmentieren Sie eine Zielgruppe basierend auf dem Offline-Verhalten, indem Sie Zielgruppenprofile mit dem Standortkontext verwenden.
* Targeting eines Benutzers mit einem Erlebnis im Geschäft, wenn relevant.

## Anwendungsfälle für den Location Service

Verbessern Sie diesen Abschnitt mit

## Komponenten des Location Service

Der Location Service umfasst die folgenden Komponenten:

* **Platzierung des Webdiensts**

   Sie können POIs mithilfe der REST-APIs für Orte erstellen und verwalten. Weitere Informationen zu REST-APIs finden Sie unter [Verwalten von Bibliotheken](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) und [Verwalten von POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Benutzeroberfläche des Location Service**

   Visualisieren Sie POIs auf einer Karte, um den räumlichen Kontext zu verstehen und POIs und ihre benutzerspezifischen Metadaten hinzuzufügen/zu bearbeiten.

* **Platzierungs-SDK**

   Die API-Schnittstelle für mehrere Plattformen, um den Standortkontext in Ihre mobilen Apps zu integrieren. Weitere Informationen zu den SDKs finden Sie unter [Plates Extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Platzierungsregeln**

   Die geointelligenten Startregeln, mit denen Sie Aktionen mit Ein- und Ausstiegsereignissen auslösen können. Die Regeln ermöglichen es Ihnen auch, Geo-Attribute unter Bedingungen zu verwenden, um das Erlebnis zu personalisieren.

* **Orts-Monitor**

   Das mobile Multi-Plattform-SDK, das in Ihre mobile App eingebettet werden kann, um Standortänderungen des Benutzers automatisch zu überwachen und Orte-Regeln auszulösen. Weitere Informationen finden Sie unter [Platzierungs-Monitorerweiterung](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## Terminologie

In dieser Dokumentation werden einige allgemeine Begriffe verwendet:

* Ein **interessanter Punkt (POI)** ist ein Geo-Ort, der für Ihr Unternehmen von Interesse ist.

   Sie können POIs mit Attributen wie Namen, Radius, Adresse, Kategorie und Metadaten-Tags definieren.

* Ein **Geofence** ist eine Art von POI.

   Dieser POI-Typ ist eine virtuelle geografische Grenze, die durch Breiten- und Längengradkoordinaten definiert wird.

* Ein **Beacon** ist eine Art von POI.

   Dieser POI-Typ ist ein physisches Gerät, das einen Standort durch die Ausgabe eines Bluetooth-Signals mit niedriger Leistung darstellt. Beacons-Unterstützung wird in einer zukünftigen Version angeboten.

* Eine **Bibliothek** ist eine Sammlung von POIs, die gruppiert sind, um Regeln einfach an einen Satz anstatt an einen POI anzuhängen.

* Die **Erweiterung** des Places SDK ist die Experience Platform Launch-Erweiterung, die zur Integration des Places SDK in Ihre mobilen Apps erforderlich ist.

   Die mit den anderen mobilen SDKs verwendete Erweiterung, um Ihren Erlebnissen Ortskontext hinzuzufügen.

* Eine **Organisation** ist die Adobe-Entität, die Ihr Unternehmen in der Adobe Experience Cloud identifiziert.

   Normalerweise ist ein Unternehmen Ihr Firmenname. Ein Unternehmen kann jedoch über mehr als eine Organisation verfügen. Der Organisationsadministrator kann Gruppen und Benutzer konfigurieren und die Single Sign-On-Funktion konfigurieren.

* Die **orgID** ist die ID für Ihr Unternehmen in der gesamten Adobe Experience Platform.

   Weitere Informationen finden Sie unter [Suchen der Organisations-ID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).