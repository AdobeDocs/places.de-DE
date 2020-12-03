---
title: 'Häufig gestellte Fragen '
description: Dieses Thema enthält weitere Informationen zu einigen häufig gestellten Fragen.
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---


# Häufig gestellte Fragen 

Im Folgenden finden Sie einige Informationen und häufig gestellte Fragen zum Places Service.

## Migrieren von trackLocation im v4 SDK

Wenn Sie vom v4-SDK migrieren und nach einem Ersatz für die `trackLocation` API suchen, lesen Sie bitte das Thema Orte [verwenden ohne Active Region Monitoring](use-places-without-active-monitoring.md).

## Größe und Zuverlässigkeit

Beachten Sie, dass bei der Regionsüberwachung unabhängig von der Adobe oder einem anderen Dienst alle Geofencing-Funktionen einer mobilen App verwendet werden. Die Betriebssysteme empfehlen einige Parameter, die beim Erstellen von Geofencing zu beachten sind. Für eine maximale Zuverlässigkeit sollten Geofencing einen Radius von mindestens 100 Metern haben. Es ist in Ordnung, kleinere Geofencing zu erstellen. Ein- und Ausstiegsdaten können jedoch nicht generiert werden oder generiert werden, nachdem der Benutzer die zeitliche Navigation beendet hat.

Darüber hinaus können Genauigkeit und Zuverlässigkeit aufgrund von Hardwarebedingungen wie z. B. ausgeschalteter oder nicht verfügbarer Wi-Fi sowie aufgrund der Position des Geräts im Zusammenhang mit der Behinderung von GPS-Signalen verringert werden. Beispielsweise können Bergregionen, städtische Einstellungen und Innenbereiche die Standortgenauigkeit von iOS- und Android-Betriebssystemen reduzieren.

## Wie löst ein Ausstiegs-Ereignis aus?

Wenn das Orts Monitor (SDK) eine neue Liste von nahe gelegenen POIs erhält, wird für jeden POI eine Region mit dem Betriebssystem registriert. Das Betriebssystem ist nun dafür verantwortlich, das SDK zu benachrichtigen, wenn das Gerät eine Grenze (ein- oder ausstieg) für einen der überwachten Regionen überschreitet. Das SDK löst nur dann ein exit-Ereignis aus, wenn das Betriebssystem dem SDK mitteilt, dass das Ereignis aufgetreten ist. Der Hauptgrund für diese Benachrichtigung ist die Zeitempfindlichkeit der Standortdaten.

Wenn das Betriebssystem beim Verlassen eines Bereichs kein Ausstiegsgerät bereitstellen kann, ist es sicherer, dass das SDK das Ereignis &quot;exit&quot;einfach weglässt. Wenn das SDK ein Ausstiegs-Ereignis ohne Auslösung des Ereignisses durch das Betriebssystem erstellt, besteht die Gefahr, dass das Ausstiegsgerät weit über den Zeitraum hinaus verarbeitet wird, in dem sich das Ereignis in der Nähe des POI befand.

## Anzahl der POI

In der Verwaltungsoberfläche des Orts-Service-POI können Kunden bis zu 150.000 Interessenspunkte in einer bestimmten Bibliothek hinzufügen. Kunden können mehrere Bibliotheken definieren, um POI-Gruppen zu segmentieren, falls gewünscht.

## Einige Hinweise zur Standortänderung und zur aktiven Regionsüberwachung

Die Überwachung einer geografischen Region beginnt unmittelbar nach der Registrierung für genehmigte Apps. Erwarten Sie jedoch nicht, dass Sie sofort ein Ereignis erhalten, da nur Grenzübergänge ein Ereignis erzeugen. Insbesondere wenn sich der Standort des Benutzers zur Registrierungszeit bereits in der Region befindet, generiert der Location Manager nicht automatisch ein Ereignis. Stattdessen muss die App warten, bis der Benutzer die Bereichsgrenze überschreitet, bevor ein Ereignis generiert und an den Delegaten gesendet wird.

Achten Sie bei der Angabe der zu überwachenden Regionen besonders darauf. Regionen sind eine gemeinsame Systemressource, und die Gesamtzahl der systemweit verfügbaren Regionen ist begrenzt. Aus diesem Grund wird die Anzahl der Regionen, die gleichzeitig von einer einzelnen App überwacht werden können, auf 20 begrenzt. Um diese Grenze zu umgehen, sollten Sie nur die Regionen in der unmittelbaren Umgebung des Benutzers registrieren.

[Weitere Informationen finden Sie auf der Apple Developer-Website] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11).
