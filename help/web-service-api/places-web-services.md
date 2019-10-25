---
title: 'Übersicht über die Web-Services-API '
seo-title: 'Übersicht über die Web-Services-API '
description: Places ist der Satz von Diensten, die es Adobe-Kunden erleichtern, die Adobe Experience Cloud- und Adobe Experience Platform-Lösungen mit Standortdaten und dem richtigen Erlebnis zur richtigen Zeit und am richtigen Ort zu kombinieren.
seo-description: Places ist der Satz von Diensten, die es Adobe-Kunden erleichtern, die Adobe Experience Cloud- und Adobe Experience Platform-Lösungen mit Standortdaten und dem richtigen Erlebnis zur richtigen Zeit und am richtigen Ort zu kombinieren.
translation-type: tm+mt
source-git-commit: e204958ac3acbf5fb45d2347987f35557be70e43

---


# Übersicht über die Web-Services-API {#places-web-services-api}

Places ist der Satz von Diensten, die es Adobe-Kunden erleichtern, die Adobe Cloud-Plattform- und Adobe Experience Platform-Lösungen mit Standortdaten und dem richtigen Erlebnis zur richtigen Zeit und am richtigen Ort auszurüsten.

Mit den Web-Services-APIs können Sie Folgendes tun:

* Geofencing verwalten
* Messen Sie die Position von Benutzern, selbst wenn sich die App im Hintergrund befindet.
* Daten in Echtzeit verwenden, wenn es wichtig ist

Dieser Abschnitt enthält Informationen zur Verwendung der REST-APIs und der POI-Datenbank, die die POI-Daten Ihrer Organisation enthält.

## REST-APIs

Mit der Places REST API können Sie programmatisch mit den POIs Ihres Unternehmens arbeiten. Mit diesen APIs können Sie Ihre Bibliotheken und POIs in diesen Bibliotheken erstellen, aktualisieren und löschen. Diese APIs verwenden die JSON-Standards (JavaScript Object Notation), um die gesendeten und empfangenen Daten zu formatieren. Ein Hauptvorteil von JSON besteht darin, dass API-Abfragen von Entwicklern und Computern leicht zu schreiben, zu lesen und zu analysieren sind.

Bevor Sie die Web-Services-API verwenden können, stellen Sie sicher, dass folgende Anforderungen erfüllt sind:

* Orte werden in Ihrer Organisation bereitgestellt und Sie haben als Benutzer entsprechenden Zugriff.

   Weitere Informationen finden Sie im Abschnitt *Organisationsanforderungen* unten.

* Nachdem Orte in Ihrem Unternehmen bereitgestellt wurden und Sie Zugriff haben, erstellen Sie eine Adobe-Integration für Orte.

   Weitere Informationen finden Sie unter *Erstellen der Ortsintegration* in der Übersicht über die [Adobe-E/A-Integration](/help/web-service-api/adobe-i-o-integration.md).

Weitere Informationen:

* Weitere Informationen zu den verfügbaren APIs und deren Verwendung finden Sie unter [Verwalten von Bibliotheken](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) und [Verwalten von POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Weitere Informationen zu den Kopfzeilen und Parametern in diesen APIs finden Sie unter [Kopfzeilen und Parameter](/help/web-service-api/api-usage/headers-and-parameters.md).

## Organisatorische Anforderungen {#org-requirements}

Vergewissern Sie sich beim Systemadministrator, dass die folgenden Aufgaben ausgeführt wurden, um auf die Web-Services-REST-APIs zuzugreifen:

* Orte wurden bereitgestellt und erscheinen in der Organisation.
* Sie wurden der Organisation hinzugefügt.
* Sie wurden zu "Orte in Ihrer Organisation"hinzugefügt.

   Weitere Informationen finden Sie unter *Hinzufügen eines Benutzers zu "Orte"und "Erlebnisplattformstart* "in den [häufig gestellten Fragen](/help/places-faqs.md).

* Sie wurden als Entwickler für Orte zu Ihrem Unternehmen hinzugefügt.

   Weitere Informationen zur Rolle "Entwickler"finden Sie unter Entwickler [verwalten](https://helpx.adobe.com/enterprise/using/manage-developers.html).