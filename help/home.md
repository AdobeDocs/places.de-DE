---
title: Places Service
description: 'Der Ortsdienst ist ein wichtiger Kontext für das Verständnis der Interaktion von Mobilbenutzern. In diesem Kontext können Entwickler mobiler Apps den App-Entwurf verbessern und ihn zu einem personalisierteren und ansprechenderen Erlebnis machen. '
translation-type: tm+mt
source-git-commit: 05b4d29aa7925f7a43e70c644e3cb88045cbe446
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 10%

---


# Places Service {#home}

![&quot;Places Service&quot;](/help/assets/places-service-header.png)

Der Standort ist ein wichtiger Kontext, um Benutzer von Mobilgeräten zu verstehen und mit ihnen zu interagieren. In diesem Kontext können Entwickler mobiler Apps den App-Entwurf verbessern und ihn zu einem personalisierteren und ansprechenderen Erlebnis machen.

Places Service, früher als Adobe Experience Platform Location Service bekannt, ist ein Geolokationsdienst, mit dem mobile Apps mit Standortbewusstsein den Standortkontext verstehen können. Dazu werden umfangreiche und benutzerfreundliche SDK-Schnittstellen sowie eine flexible Datenbank mit POIs (Points of Interest) verwendet.

Mit dem Orts-Dienst können Sie Folgendes erreichen:

* Erstellen und verwalten Sie eine Datenbank mit POIs, die mit anderen Adobe Experience Cloud-Lösungen verwendet werden können.
* Fügen Sie den POIs benutzerspezifische Metadaten hinzu, um sie durch Angabe zusätzlicher Attribute reicher und aussagekräftiger zu gestalten.
* Visualisieren Sie die POIs auf einer Karte, um den räumlichen Kontext zu verstehen und Metadatenattribute hinzuzufügen/zu bearbeiten.
* Konfigurieren Sie das SDK in Adobe Experience Platform Launch, um die durch Ihren Standort ausgelösten Regeln und metadatenbasierten Bedingungen zu definieren.
* Verringern Sie den zu schreibenden Code, um den Standort des Geräts zu überwachen, und verwenden Sie die Platzierungserweiterung, um die standortspezifischen Regeln automatisch Trigger.

Auf diese Weise können Sie in Echtzeit Aktionen aus Standortsignalen ausführen, wann und wo sie wichtig sind. Der richtige Kontext bietet eine umfassendere Interaktion mit Mobilgeräten.

Die folgenden Möglichkeiten stehen Ihnen zur Verwendung von Orten zur Verfügung:

* Senden Sie eine Benachrichtigung in Echtzeit, wenn jemand einen POI eingibt, *&quot;Hey...Willkommen im Stadion.&quot;*
* Analysieren Sie den Fußverkehr Ihrer eigenen Läden im Vergleich zu Ihren Konkurrent-Läden.
* Segmentieren Sie eine Audience nach dem Offlineverhalten, indem Sie Audiencen-Profil mit Standortkontext verwenden.
* Zielgruppe eines Benutzers mit einem Erlebnis im Geschäft, falls relevant.

## Platziert Dienstkomponenten

Der Orte-Dienst umfasst die folgenden Komponenten:

* **Webdienst**

   Sie können POIs mithilfe der REST-APIs für Orte erstellen und verwalten. Weitere Informationen zu den REST-APIs finden Sie unter [Bibliotheken verwalten](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) und [POIs verwalten](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI-Verwaltungsoberfläche**

   Visualisieren Sie POIs auf einer Karte, um den räumlichen Kontext zu verstehen und POIs und ihre benutzerspezifischen Metadaten hinzuzufügen/zu bearbeiten.

* **Places-Erweiterung**

   Die API-Schnittstelle für mehrere Plattformen, um den Standortkontext in Ihre mobilen Apps zu integrieren. Weitere Informationen zu den SDKs finden Sie unter [Plates extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Regeln starten**

   Die geo-intelligenten Startregeln, mit denen Sie Aktionen mit Ein- und Ausstiegs-Ereignissen Trigger haben. Die Regeln ermöglichen es Ihnen auch, Geo-Attribute unter Bedingungen zu verwenden, um das Erlebnis zu personalisieren.

* **Platzierungsmonitor-Erweiterung**

   Das mobile Multi-Plattform-SDK, das in Ihre mobile App eingebettet werden kann, um automatisch die Standortänderungen und Trigger Places-Regeln Ihres Benutzers zu überwachen. Weitere Informationen finden Sie unter [Plates Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## Terminologie

Im Folgenden finden Sie einige allgemeine Begriffe, die in dieser Dokumentation verwendet werden:

* Ein **POI (Point of Interest)** ist ein Geo-Ort, der für Ihr Unternehmen von Interesse ist.

   Sie können POIs mit Attributen wie Namen, Radius, Adresse, Kategorie und Metadaten-Tags definieren.

* Ein **geofence** ist ein Typ von POI.

   Dieser POI-Typ ist eine virtuelle geografische Grenze, die durch Breiten- und Längengradkoordinaten definiert wird.

* Ein **Beacon** ist ein Typ von POI.

   Dieser POI-Typ ist ein physisches Gerät, das einen Standort durch die Ausgabe eines Bluetooth-Signals mit niedriger Leistung darstellt. Beacons-Unterstützung wird in einer zukünftigen Version angeboten.

* Eine **Bibliothek** ist eine Sammlung von POIs, die gruppiert sind, um Regeln einfach an mehrere statt nur an einen POI anzuhängen.

* Eine **extension** ist die Experience Platform Launch-Erweiterung, die zum Integrieren des Places SDK in Ihre mobilen Apps erforderlich ist.

   Die mit den anderen mobilen SDKs verwendete Erweiterung, um Ihren Erlebnissen Ortskontext hinzuzufügen.

* Eine **Organisation** ist die Adobe-Einheit, die Ihr Unternehmen in der Adobe Experience Cloud identifiziert.

   Normalerweise ist ein Unternehmen Ihr Name für die Firma. Eine Firma kann jedoch über mehr als eine Organisation verfügen. Der Organisationsadministrator kann Gruppen und Benutzer konfigurieren und die Single Sign-On-Funktion konfigurieren.

* Die **orgID** ist die ID für Ihr Unternehmen auf der gesamten Adobe Experience Platform.

   Weitere Informationen finden Sie unter [Suchen Ihrer orgID](https://forums.adobe.com/thread/2339895).

* Der Dienst **Experience Cloud-ID** stellt eine universelle, beständige ID bereit, die Ihre Besucher in allen Lösungen des Experience Cloud identifiziert.

   Weitere Informationen finden Sie unter [Übersicht](https://docs.adobe.com/content/help/de-DE/id-service/using/intro/overview.html).
