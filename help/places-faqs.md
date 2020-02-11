---
title: Häufig gestellte Fragen
description: Dieses Thema enthält weitere Informationen zu einigen häufig gestellten Fragen.
translation-type: tm+mt
source-git-commit: 8691dbf061ac020a60d3880fe16951dcc79040cb

---


# Häufig gestellte Fragen

Hier finden Sie einige Informationen und häufig gestellte Fragen zum Places Service.

## Größe und Zuverlässigkeit

Beachten Sie, dass bei der regionalen Überwachung von einer mobilen App aus alle Geofencing-Funktionen verwendet werden, unabhängig davon, ob Adobe oder ein anderer Dienst verwendet wird. Die Betriebssysteme empfehlen einige Parameter, die beim Erstellen von Geofencing zu beachten sind. Für eine maximale Zuverlässigkeit sollten Geofencing einen Radius von mindestens 100 Metern haben. Es ist in Ordnung, kleinere Geofencing zu erstellen, aber Einstiegs- und Ausstiegsereignisse werden möglicherweise nicht generiert oder können generiert werden, nachdem der Benutzer die Bewegung für einen bestimmten Zeitraum beendet hat.

Darüber hinaus können Genauigkeit und Zuverlässigkeit aufgrund von Hardwarebedingungen wie z. B. ausgeschalteter oder nicht verfügbarer Wi-Fi sowie aufgrund der Position des Geräts im Zusammenhang mit der Behinderung von GPS-Signalen verringert werden. Beispielsweise können Bergregionen, städtische Einstellungen und Innenbereiche die Standortgenauigkeit von iOS- und Android-Betriebssystemen reduzieren.

## Wie wird ein exit-Ereignis ausgelöst?

Wenn das Orts Monitor (SDK) eine neue Liste der nahe gelegenen POIs erhält, registriert es eine Region mit dem Betriebssystem für jeden POI. Das Betriebssystem ist nun dafür verantwortlich, das SDK zu benachrichtigen, wenn das Gerät eine Grenze (ein- oder ausstieg) für einen der überwachten Regionen überschreitet. Das SDK löst nur dann ein exit-Ereignis aus, wenn das Betriebssystem dem SDK mitteilt, dass das Ereignis aufgetreten ist. Der Hauptgrund für diese Benachrichtigung ist die Zeitempfindlichkeit der Standortdaten.

Wenn das Betriebssystem kein exit-Ereignis bereitstellen kann, wenn das Gerät eine Region verlässt, ist es sicherer, dass das SDK das exit-Ereignis einfach weglässt. Wenn das SDK ein Ausstiegsereignis produziert, ohne dass das Ereignis vom Betriebssystem ausgelöst wird, besteht die Gefahr, dass das Ausstiegsereignis weit über den Zeitraum hinaus verarbeitet wird, in dem sich das Gerät in der Nähe des POI befand.

## Anzahl der POI

In der Verwaltungsoberfläche des Orts-Service-POI können Kunden bis zu 150.000 Interessenspunkte in einer bestimmten Bibliothek hinzufügen. Kunden können mehrere Bibliotheken definieren, um POI-Gruppen zu segmentieren.

## Einige Hinweise zur Standortänderung und zur aktiven Regionsüberwachung

Die Überwachung einer geografischen Region beginnt unmittelbar nach der Registrierung für zugelassene Apps. Erwarten Sie jedoch nicht, dass Sie sofort ein Ereignis erhalten, da nur Grenzübergänge ein Ereignis generieren. Insbesondere wenn sich der Standort des Benutzers zum Zeitpunkt der Registrierung bereits in der Region befindet, generiert der Location Manager nicht automatisch ein Ereignis. Stattdessen muss die App warten, bis der Benutzer die Regionsgrenze überschreitet, bevor ein Ereignis generiert und an den Delegaten gesendet wird.

Achten Sie bei der Angabe der zu überwachenden Regionen besonders darauf. Regionen sind eine gemeinsame Systemressource, und die Gesamtzahl der systemweit verfügbaren Regionen ist begrenzt. Aus diesem Grund wird die Anzahl der Regionen, die gleichzeitig von einer einzelnen App überwacht werden können, auf 20 begrenzt. Um diese Grenze zu umgehen, sollten Sie nur die Regionen in der unmittelbaren Umgebung des Benutzers registrieren.

[Weitere Informationen finden Sie auf der Apple Developer-Website] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11).

