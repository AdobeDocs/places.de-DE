---
title: Platzierungsmonitor-Erweiterung
description: Die Erweiterung "Orts Monitor"verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Platziert die Monitorerweiterung {#places-monitor-extension}

Die Erweiterung &quot;Orts Monitor&quot;verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind. Diese Erweiterung ruft die POIs ab, die bei der Ortserweiterung registriert werden müssen, und leitet die Ein- und Ausstiegsbenachrichtigungen an die Ortserweiterung weiter. Diese Benachrichtigungen stehen als Ereignisse in Experience Platform Launch-Regeln zur Verfügung.

Die Erweiterung &quot;Monitor&quot;ist optional, da einige Kunden möglicherweise bereits Regionen mit dem Betriebssystem überwachen. Wenn dies der Fall ist, stellen Sie sicher, dass Sie die APIs für die Platzierungserweiterung hinzufügen, um die nächstgelegenen POIs aus der Datenbank für den Places-Dienst zu empfangen und auch die Ereignis für Ein- und Ausstieg zu übermitteln, damit die entsprechenden Aktionen durchgeführt werden können.
