---
title: Places Service
description: Places Service ist ein wichtiger Kontext, um die Interaktion von Mobile-Benutzern zu verstehen. Mithilfe dieses Kontexts können Entwickler von Mobile Apps das Design der App verbessern und sie zu einem personalisierteren und ansprechenderen Erlebnis machen.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

Der Standort ist ein wichtiger Kontext, um mobile Benutzer zu verstehen und mit ihnen zu interagieren. Mithilfe dieses Kontexts können Entwickler von Mobile Apps das Design der App verbessern und sie zu einem personalisierteren und ansprechenderen Erlebnis machen.

Places Service, früher als Adobe Experience Platform Location Service bezeichnet, ist ein Standortdienst, der es mobilen Apps mit Standorterkennung ermöglicht, den Standortkontext zu verstehen, indem umfangreiche und benutzerfreundliche SDK-Benutzeroberflächen sowie eine flexible Datenbank mit Zielpunkten (Points of Interest, POIs) verwendet werden.

Mit dem Places Service können Sie Folgendes erreichen:

* Erstellen und verwalten Sie eine Datenbank mit POIs, die mit anderen Adobe Experience Cloud-Lösungen genutzt werden können.
* Fügen Sie den POIs benutzerdefinierte Metadaten hinzu, um sie durch Angabe zusätzlicher Attribute anreicherender und aussagekräftiger zu machen.
* Visualisieren Sie die POIs auf einer Karte, um den räumlichen Kontext leicht zu verstehen und Metadatenattribute hinzuzufügen/zu bearbeiten.
* Konfigurieren Sie die SDK in Adobe Experience Platform Launch, um Ihre standortausgelösten Regeln und metadatenbasierten Bedingungen zu definieren.
* Reduzieren Sie den Code, den Sie schreiben müssen, um den Standort eines Geräts zu überwachen, und verwenden Sie die Places-Erweiterung, um die standortspezifischen Regeln automatisch mit Trigger zu versehen.

So können Sie Aktionen aus Standortsignalen in Echtzeit durchführen, wenn und wo es von Bedeutung ist. Der richtige Kontext bietet ein bereichernderes mobiles Interaktionserlebnis.

Im Folgenden finden Sie einige Möglichkeiten, wie Sie Places verwenden können:

* Eine Echtzeitbenachrichtigung senden, wenn jemand einen POI eingibt, *„Hey…Willkommen im Stadion.*
* Analysieren Sie den Fußgängerverkehr Ihrer eigenen Geschäfte im Vergleich zu Ihren Konkurrenzgeschäften.
* Segmentieren Sie eine Zielgruppe basierend auf dem Offline-Verhalten, indem Sie Zielgruppenprofile mit dem Standortkontext verwenden.
* Targeting von Benutzenden mit einem In-Store-Erlebnis, sofern relevant.

## Platziert Dienstkomponenten

Places Service umfasst die folgenden Komponenten:

* **Webservice**

  Sie können POIs mithilfe der Places REST-APIs erstellen und verwalten. Weitere Informationen zu den REST-APIs finden Sie unter [Bibliotheken verwalten](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) und [POI verwalten](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI-Verwaltungsschnittstelle**

  Visualisieren Sie POIs auf einer Karte, um den räumlichen Kontext zu verstehen und POIs und ihre benutzerdefinierten Metadaten hinzuzufügen/zu bearbeiten.

* **Places-Erweiterung**

  Die plattformübergreifende Mobile-API-Schnittstelle zur Integration des Standortkontexts in Ihre Mobile Apps. Weitere Informationen zu den SDKs finden Sie unter [Places-Erweiterung](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Launch-Regeln**

  Die geo-intelligenten Launch-Regeln, mit denen Sie Trigger-Aktionen mit Eintritts- und Austrittsereignissen durchführen können. Die Regeln ermöglichen es Ihnen auch, Geoattribute in Bedingungen zur Personalisierung des Erlebnisses zu verwenden.

## Terminologie

Im Folgenden finden Sie einige allgemeine Begriffe, die in dieser Dokumentation verwendet werden:

* Ein **Point of Interest (POI)** ist ein geografischer Standort, der für Ihr Unternehmen von Interesse ist.

  Sie können POIs mit Attributen wie Namen, Radius, Adresse, Kategorie und Metadaten-Tags definieren.

* Ein **Geofence** ist eine Art von POI.

  Dieser POI-Typ ist eine virtuelle geografische Grenze, die durch Längen- und Breitenkoordinaten definiert wird.

* Ein **Beacon** ist ein POI-Typ.

  Dieser POI-Typ ist ein physisches Gerät, das einen Standort durch Aussenden eines Bluetooth-Signals mit geringer Leistung darstellt. Die Beacons-Unterstützung wird in einer zukünftigen Version bereitgestellt.

* Eine **Bibliothek** ist eine Sammlung von POIs, die gruppiert sind, um Regeln einfach an mehrere statt nur an einen POI anzuhängen.

* Eine **Erweiterung** ist die Experience Platform Launch-Erweiterung, die zur Integration der Places SDK in Ihre Mobile Apps erforderlich ist.

  Die Erweiterung, die mit den anderen Mobile SDKs verwendet wird, um Ihren Erlebnissen Standortkontext hinzuzufügen.

* Eine **Organisation** ist die Adobe-Einheit, die Ihr Unternehmen in der Adobe Experience Cloud identifiziert.

  Normalerweise ist eine Organisation der Name Ihres Unternehmens. Ein Unternehmen kann jedoch über mehr als eine Organisation verfügen. Der Organisationsadministrator kann Gruppen und Benutzer konfigurieren und die Single-Sign-on-Funktion konfigurieren.

* Die **orgID** ist die ID für Ihr Unternehmen auf der gesamten Adobe Experience Platform.

  Weitere Informationen finden Sie unter [Ermitteln der Organisations-ID](https://forums.adobe.com/thread/2339895).

* Der Service **Experience Cloud-ID** bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Lösungen hinweg in der Experience Cloud hinweg.

  Weitere Informationen finden Sie unter [Übersicht](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=de).

