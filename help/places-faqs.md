---
title: Häufig gestellte Fragen
description: Dieses Thema enthält zusätzliche Informationen zu einigen häufig gestellten Fragen.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Häufig gestellte Fragen

Im Folgenden finden Sie einige Informationen und häufig gestellte Fragen zu Places Service.

## Migration von trackLocation im v4-SDK

Wenn Sie vom v4-SDK migrieren und nach einem Ersatz für die Variable `trackLocation` API, siehe Thema [Verwenden des Places-Dienstes ohne aktive Regionsüberwachung](use-places-without-active-monitoring.md).

## Größe und Zuverlässigkeit

Wichtig: Beachten Sie, dass alle Geofences in der Regionsüberwachung von einer mobilen App aus verwendet werden, unabhängig von der Verwendung von Adobe oder einem anderen Dienst. Die Betriebssysteme empfehlen einige Parameter, die bei der Erstellung von Geofences zu beachten sind. Für maximale Zuverlässigkeit sollten Geofences einen Radius von mindestens 100 Metern haben. Es ist in Ordnung, kleinere Geofences zu erstellen, aber Einstiegs- und Ausstiegsereignisse können nicht generiert oder generiert werden, nachdem der Benutzer die Bewegung für einen bestimmten Zeitraum beendet hat.

Darüber hinaus können Genauigkeit und Zuverlässigkeit auf der Grundlage von Hardware-Bedingungen wie ausgeschaltetem oder nicht verfügbarem WLAN und auch auf der Grundlage des Standorts des Geräts in Bezug auf die Behinderung von GPS-Signalen reduziert werden. Beispielsweise können Bergregionen, städtische Einstellungen und Innenbereiche die Standortgenauigkeit von den iOS- und Android-Betriebssystemen verringern.

## Wie wird ein Exitereignis Trigger?

Der implementierte Regionsmonitor sollte eine Liste nahegelegener Zielpunkte anfordern. Nach dem Erhalt sollte eine Region für jeden POI beim Betriebssystem registriert werden. Das Betriebssystem ist jetzt für die Benachrichtigung des SDK verantwortlich, wenn das Gerät eine Grenze (Ein- oder Ausstieg) für eine der überwachten Regionen überschreitet. Das SDK Trigger nur dann ein exit -Ereignis, wenn das Betriebssystem das SDK darüber informiert, dass das Ereignis aufgetreten ist. Der Hauptgrund für diese Benachrichtigung ist die Zeitempfindlichkeit der Standortdaten.

Wenn das Betriebssystem kein exit -Ereignis bereitstellen kann, wenn das Gerät eine Region verlässt, ist es sicherer, dass das SDK das exit -Ereignis einfach weglässt. Wenn das SDK ein exit -Ereignis erstellt, ohne dass das Ereignis vom Betriebssystem ausgelöst wird, besteht das Risiko, dass das exit -Ereignis weit außerhalb des Zeitraums verarbeitet wird, in dem sich das Gerät in der Nähe des POI befunden hat.

## Anzahl der Zielpunkte

In der Verwaltungsoberfläche für POI des Places-Dienstes können Kunden bis zu 150.000 Zielpunkte in einer bestimmten Bibliothek zusammenfassen. Kunden können bei Bedarf mehrere Bibliotheken definieren, um POIs zu segmentieren.

## Einige Hinweise zu Standortänderung und aktiver Regionsüberwachung

Die Überwachung einer geografischen Region beginnt unmittelbar nach der Registrierung für zugelassene Apps. Erwarten Sie jedoch nicht, dass Sie sofort ein Ereignis erhalten, da nur Grenzübergänge ein Ereignis generieren. Insbesondere wenn sich der Standort des Benutzers zum Zeitpunkt der Registrierung bereits in der Region befindet, generiert der Standortmanager nicht automatisch ein Ereignis. Stattdessen muss Ihre App warten, bis der Benutzer die Regionsgrenze überschreitet, bevor ein Ereignis generiert und an den Delegaten gesendet wird.

Achten Sie bei der Angabe der zu überwachenden Regionen auf Bedacht. Regionen sind eine gemeinsame Systemressource, und die Gesamtzahl der systemweit verfügbaren Regionen ist begrenzt. Aus diesem Grund ist die Anzahl der Regionen, die gleichzeitig von einer einzelnen App überwacht werden können, vom Kernstandort auf 20 begrenzt. Um diese Grenze zu umgehen, sollten Sie nur die Regionen in der unmittelbaren Umgebung des Benutzers registrieren.

[Weitere Informationen finden Sie auf der Entwickler-Site von Apple .] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
