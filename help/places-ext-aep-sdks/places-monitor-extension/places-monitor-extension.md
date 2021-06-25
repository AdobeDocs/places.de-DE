---
title: Places Monitor-Erweiterung
description: Die Erweiterung Places Monitor verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind.
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Places Monitor-Erweiterung {#places-monitor-extension}

Die Erweiterung Places Monitor verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind. Diese Erweiterung ruft die POIs ab, die von der Places-Erweiterung registriert werden müssen, und übergibt die Ein- und Ausstiegsbenachrichtigungen an die Places-Erweiterung. Diese Benachrichtigungen sind in Experience Platform Launch-Regeln als Ereignisse verfügbar.

Die Erweiterung &quot;Monitor&quot;ist optional, da einige Kunden möglicherweise bereits Regionen mit dem Betriebssystem überwachen. Stellen Sie in diesem Fall sicher, dass Sie die Places-Erweiterungs-APIs hinzufügen, um die nächsten POIs aus der Places-Dienst-Datenbank zu empfangen und auch die Ein- und Ausstiegsereignisse zu übergeben, damit die entsprechenden Aktionen durchgeführt werden können.

## Places Monitor Deprecation

Am 31. August 2021 wird die Places Monitor-Erweiterung für die Adobe Experience Platform Mobile SDKs nicht mehr unterstützt. Die Places Monitor-Erweiterung erhält nach dem 31. August keine weiteren Updates oder Support.

Kunden, die derzeit die Erweiterung Places Monitor verwenden, können diese Erweiterung weiterhin verwenden, sofern keine weiteren Updates oder Support über Adobe verfügbar sind.

Die Einstellung der Places Monitor-Erweiterung hat keine Auswirkungen oder negativen Auswirkungen auf die Places Service-Erweiterung, die weiterhin mit Verbesserungen und Aktualisierungen unterstützt wird.

Kunden, die von der Places Monitor-Erweiterung zu ihrer eigenen Überwachungslösung übergehen möchten, sollten die Dokumentation auf Folgendes überprüfen: [Verwenden Sie den Places-Dienst mit Ihrer eigenen Überwachungslösung](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en). In diesem Dokument wird beschrieben, wie Sie mit dem Places-Dienst interagieren, indem Sie [Core Location Services](https://developer.apple.com/documentation/corelocation) unter iOS oder [Location Services](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary) aus Google Play implementieren.
