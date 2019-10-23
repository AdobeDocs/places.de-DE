---
title: Platzierungsmonitor-Erweiterung
seo-title: Platzierungsmonitor-Erweiterung
description: Die Erweiterung "Orts Monitor"verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind.
seo-description: 'Die Erweiterung "Orts Monitor"verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind. '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Platzierungsmonitor-Erweiterung {#places-monitor-extension}

Die Erweiterung "Orts Monitor"verarbeitet die Interaktionen mit dem Betriebssystem, um die POIs zu registrieren und zu überwachen, die dem Benutzer am nächsten sind. Diese Erweiterung ruft die POIs ab, die bei der Ortserweiterung registriert werden müssen, und leitet die Ein- und Ausstiegsbenachrichtigungen an die Ortserweiterung weiter. Diese Benachrichtigungen stehen in den Experience Platform Launch-Regeln als Ereignisse zur Verfügung.

Die Erweiterung "Monitor"ist optional, da einige Kunden möglicherweise bereits Regionen mit dem Betriebssystem überwachen. Wenn dies der Fall ist, stellen Sie sicher, dass Sie die APIs für die Platzierungserweiterung hinzufügen, um die nächstgelegenen POIs aus der Datenbank "Orte"zu empfangen und auch die Ein- und Ausstiegsereignisse zu übermitteln, damit die entsprechenden Aktionen durchgeführt werden können.
