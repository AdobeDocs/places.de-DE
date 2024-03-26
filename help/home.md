---
title: Places Service
description: Places Service ist ein wichtiger Kontext für das Verständnis der Interaktion mobiler Benutzer. In diesem Kontext können Entwickler mobiler Apps das App-Design verbessern und es zu einem personalisierteren und ansprechenderen Erlebnis machen.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

Standort ist ein wichtiger Kontext, um mobile Benutzer zu verstehen und mit ihnen zu interagieren. In diesem Kontext können Entwickler mobiler Apps das App-Design verbessern und es zu einem personalisierteren und ansprechenderen Erlebnis machen.

Places Service, früher als Adobe Experience Platform Location Service bezeichnet, ist ein Standortdienst, mit dem mobile Apps mit Standorterkennung den Standortkontext verstehen können. Dazu werden umfangreiche und benutzerfreundliche SDK-Schnittstellen sowie eine flexible Datenbank mit Zielpunkten (POIs) verwendet.

Mit dem Places-Dienst können Sie Folgendes erreichen:

* Erstellen und verwalten Sie eine Datenbank mit POIs, die mit anderen Adobe Experience Cloud-Lösungen genutzt werden können.
* Fügen Sie den Zielpunkten benutzerdefinierte Metadaten hinzu, um sie durch Angabe zusätzlicher Attribute reicher und aussagekräftiger zu machen.
* Visualisieren Sie die POIs auf einer Karte, um den räumlichen Kontext zu verstehen und Metadatenattribute hinzuzufügen/zu bearbeiten.
* Konfigurieren Sie das SDK in Adobe Experience Platform Launch, um Ihre standortbasierten Regeln und metadatenbasierten Bedingungen zu definieren.
* Reduzieren Sie den Code, den Sie schreiben müssen, um den Standort eines Geräts zu überwachen, und verwenden Sie die Places-Erweiterung, um die standortspezifischen Regeln automatisch Trigger.

Dadurch können Sie Aktionen aus Standortsignalen in Echtzeit ausführen, wann und wo es wichtig ist. Der richtige Kontext bietet eine umfassendere Interaktion mit Mobilgeräten.

Im Folgenden finden Sie einige Möglichkeiten zur Verwendung von Places:

* Senden Sie eine Echtzeitbenachrichtigung, wenn ein Benutzer einen POI aufruft. *&quot;Hey.Willkommen im Stadion.&quot;*
* Analysieren Sie den Fußverkehr Ihrer eigenen Stores im Vergleich zu Ihren Konkurrenzgeschäften.
* Segmentieren Sie eine Zielgruppe basierend auf dem Offline-Verhalten, indem Sie Zielgruppenprofile mit dem Standortkontext verwenden.
* Targeting eines Benutzers mit einem In-Store-Erlebnis, falls relevant.

## Places Service-Komponenten

Places Service umfasst die folgenden Komponenten:

* **Webdienst**

  Sie können POIs mithilfe der Places REST APIs erstellen und verwalten. Weitere Informationen zu den REST-APIs finden Sie unter [Bibliotheken verwalten](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) und [POIs verwalten](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI-Verwaltungsoberfläche**

  Visualisieren Sie POIs auf einer Karte, um den räumlichen Kontext zu verstehen und POIs und ihre benutzerdefinierten Metadaten hinzuzufügen/zu bearbeiten.

* **Places-Erweiterung**

  Die mobile API-Schnittstelle für mehrere Plattformen zur Integration des Standortkontexts in Ihre mobilen Apps. Weitere Informationen zu den SDKs finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Launch-Regeln**

  Die geo-intelligenten Launch-Regeln, mit denen Sie Aktionen mit Ein- und Ausstiegsereignissen Trigger haben. Die Regeln ermöglichen Ihnen auch die Verwendung von Geo-Attributen in Bedingungen zur Personalisierung des Erlebnisses.

## Terminologie

Im Folgenden finden Sie einige häufig verwendete Begriffe, die in dieser Dokumentation verwendet werden:

* A **Point of Interest (POI)** ist ein Geostandort, der für Ihre Organisation von Interesse ist.

  Sie können POIs mit Attributen wie Namen, Radius, Adresse, Kategorie und Metadaten-Tags definieren.

* A **Geofence** ist eine Art POI.

  Dieser POI-Typ ist eine virtuelle geografische Grenze, die durch Längen- und Breitenkoordinaten definiert wird.

* A **Beacon** ist eine Art POI.

  Dieser POI-Typ ist ein physisches Gerät, das einen Standort darstellt, indem ein Bluetooth-Signal mit geringer Leistung ausgegeben wird. Unterstützung für Beacons wird in einer zukünftigen Version verfügbar sein.

* Eine **Bibliothek** ist eine Sammlung von POIs, die gruppiert sind, um Regeln einfach an mehrere statt nur an einen POI anzuhängen.

* Ein **Erweiterung** ist die Experience Platform Launch-Erweiterung, die zur Integration des Places SDK in Ihre mobilen Apps erforderlich ist.

  Die Erweiterung, die mit den anderen mobilen SDKs verwendet wird, um Ihren Erlebnissen Ortskontext hinzuzufügen.

* Eine **Organisation** ist die Adobe-Einheit, die Ihr Unternehmen in der Adobe Experience Cloud identifiziert.

  Normalerweise ist eine Organisation Ihr Unternehmensname. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen. Der Organisationsadministrator kann Gruppen und Benutzer konfigurieren und die Single Sign-on-Funktion konfigurieren.

* Die **orgID** ist die ID für Ihr Unternehmen auf der gesamten Adobe Experience Platform.

  Weitere Informationen finden Sie unter [Suchen Ihrer Organisations-ID](https://forums.adobe.com/thread/2339895).

* Die **Experience Cloud-ID** -Dienst bietet eine universelle, beständige ID, mit der Ihre Besucher lösungsübergreifend in der Experience Cloud identifiziert werden können.

  Weitere Informationen finden Sie unter [Übersicht](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=de).

