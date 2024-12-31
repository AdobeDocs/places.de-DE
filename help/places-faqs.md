---
title: Häufig gestellte Fragen
description: Dieses Thema enthält zusätzliche Informationen zu einigen häufig gestellten Fragen.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 1%

---

# Häufig gestellte Fragen

Im Folgenden finden Sie einige Informationen und häufig gestellte Fragen zum Places Service.

## Migration von trackLocation in der v4-SDK

Wenn Sie von SDK v4 migrieren und nach einem Ersatz für die `trackLocation`-API suchen, lesen Sie bitte den Abschnitt [Verwenden von Orten ohne Active Region Monitoring](use-places-without-active-monitoring.md).

## Größe und Zuverlässigkeit

Beachten Sie Folgendes für alle Geofences, die bei der Regionsüberwachung von einer Mobile App aus verwendet werden, unabhängig von der Verwendung von Adobe oder einem anderen Service. Die Betriebssysteme empfehlen einige Parameter, die beim Erstellen von Geofences zu beachten sind. Für maximale Zuverlässigkeit sollten Geofences einen Radius von mindestens 100 Metern haben. Es ist in Ordnung, kleinere Geofences zu erstellen, aber Ein- und Ausstiegsereignisse werden möglicherweise nicht oder erst generiert, nachdem der Benutzer für einen bestimmten Zeitraum aufgehört hat, sich zu bewegen.

Darüber hinaus kann die Genauigkeit und Zuverlässigkeit aufgrund von Hardware-Bedingungen wie ausgeschaltetem oder nicht verfügbarem Wi-Fi sowie aufgrund der Position des Geräts in Bezug auf die Behinderung von GPS-Signalen verringert werden. Beispielsweise können Berggebiete, städtische Umgebungen und Innenbereiche die Standortgenauigkeit der iOS- und Android-Betriebssysteme verringern.

## Wie funktioniert ein Exit-Ereignis-Trigger?

Der implementierte Regionsmonitor sollte eine Liste der nahegelegenen POIs anfordern. Nach Erhalt sollte für jeden POI eine Region beim Betriebssystem registriert werden. Das Betriebssystem ist nun für die Benachrichtigung der SDK verantwortlich, wenn das Gerät eine Grenze (Ein- oder Ausstieg) für eine der überwachten Regionen überschreitet. Die SDK Trigger nur dann ein Beendigungsereignis, wenn das Betriebssystem die SDK darüber informiert, dass das Ereignis aufgetreten ist. Der Hauptgrund für diese Benachrichtigung ist die zeitliche Sensitivität der Standortdaten.

Wenn das Betriebssystem kein Exit-Ereignis bereitstellen kann, wenn das Gerät eine Region verlässt, ist es sicherer, wenn der SDK das Exit-Ereignis einfach auslässt. Wenn der SDK ein Exitereignis erstellt, ohne dass das Ereignis vom Betriebssystem ausgelöst wird, besteht das Risiko, dass das Exitereignis deutlich außerhalb des Zeitraums verarbeitet wird, in dem sich das Gerät in der Nähe des POI befand.

## Anzahl der POIs

In der Verwaltungsoberfläche des Places Service-POI können Kunden bis zu 150.000 Punkte von Interesse zu einer bestimmten Bibliothek hinzufügen. Kunden können bei Bedarf mehrere Bibliotheken definieren, um Gruppierungen von POIs zu segmentieren.

## Einige Hinweise zu Standortänderungen und zur Überwachung aktiver Regionen

Die Überwachung einer geografischen Region beginnt unmittelbar nach der Registrierung für autorisierte Apps. Erwarten Sie jedoch nicht, sofort ein Ereignis zu erhalten, da nur Grenzüberschreitungen ein Ereignis erzeugen. Insbesondere wenn sich der Standort des Benutzers zur Registrierungszeit bereits innerhalb der Region befindet, generiert der Standort-Manager nicht automatisch ein Ereignis. Stattdessen muss die App warten, bis der Benutzer die Regionsgrenze überschreitet, bevor ein Ereignis generiert und an den Delegaten gesendet wird.

Seien Sie beim Festlegen der zu überwachenden Regionen vorsichtig. Regionen sind eine gemeinsam genutzte Systemressource, und die Gesamtzahl der systemweit verfügbaren Regionen ist begrenzt. Aus diesem Grund beschränkt Core Location die Anzahl der Regionen, die von einer einzigen App gleichzeitig überwacht werden können, auf 20. Um diese Grenze zu umgehen, sollten Sie nur die Regionen in der unmittelbaren Umgebung des Benutzers registrieren.

[Weitere Informationen finden Sie auf der Apple Developer Site] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
