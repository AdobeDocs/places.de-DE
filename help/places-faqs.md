---
title: Häufig gestellte Fragen
seo-title: Häufig gestellte Fragen
description: Dieses Thema enthält weitere Informationen zu einigen häufig gestellten Fragen.
seo-description: Dieses Thema enthält weitere Informationen zu einigen häufig gestellten Fragen.
translation-type: tm+mt
source-git-commit: f4b8bccc154df346e67ef17295d7c6b42c68b26d

---


# Häufig gestellte Fragen

Hier finden Sie einige Informationen und häufig gestellte Fragen zum Location Service.

## Größe und Zuverlässigkeit

Beachten Sie, dass bei der regionalen Überwachung von einer mobilen App aus alle Geofencing-Funktionen verwendet werden, unabhängig davon, ob Adobe oder ein anderer Dienst verwendet wird. Die Betriebssysteme empfehlen einige Parameter, die beim Erstellen von Geofencing zu beachten sind. Für eine maximale Zuverlässigkeit sollten Geofencing einen Radius von mindestens 100 Metern haben. Es ist in Ordnung, kleinere Geofencing zu erstellen, aber Einstiegs- und Ausstiegsereignisse werden möglicherweise nicht generiert oder können generiert werden, nachdem der Benutzer die Bewegung für einen bestimmten Zeitraum beendet hat.

Darüber hinaus können Genauigkeit und Zuverlässigkeit aufgrund von Hardwarebedingungen wie z. B. ausgeschalteter oder nicht verfügbarer Wi-Fi sowie aufgrund der Position des Geräts im Zusammenhang mit der Behinderung von GPS-Signalen verringert werden. Beispielsweise können Bergregionen, städtische Einstellungen und Innenbereiche die Standortgenauigkeit von iOS- und Android-Betriebssystemen reduzieren.

## Wie wird ein exit-Ereignis ausgelöst?

Wenn das Orts Monitor (SDK) eine neue Liste der nahe gelegenen POIs erhält, registriert es eine Region mit dem Betriebssystem für jeden POI. Das Betriebssystem ist nun dafür verantwortlich, das SDK zu benachrichtigen, wenn das Gerät eine Grenze (ein- oder ausstieg) für einen der überwachten Regionen überschreitet. Das SDK löst nur dann ein exit-Ereignis aus, wenn das Betriebssystem dem SDK mitteilt, dass das Ereignis aufgetreten ist. Der Hauptgrund für diese Benachrichtigung ist die Zeitempfindlichkeit der Standortdaten.

Wenn das Betriebssystem kein exit-Ereignis bereitstellen kann, wenn das Gerät eine Region verlässt, ist es sicherer, dass das SDK das exit-Ereignis einfach weglässt. Wenn das SDK ein Ausstiegsereignis produziert, ohne dass das Ereignis vom Betriebssystem ausgelöst wird, besteht die Gefahr, dass das Ausstiegsereignis weit über den Zeitraum hinaus verarbeitet wird, in dem sich das Gerät in der Nähe des POI befand.
