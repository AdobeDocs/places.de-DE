---
title: Adobe Developer-Projektübersicht
description: Informationen zum Erstellen eines Adobe Developer-API-Projekts.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Übersicht über den API-Zugriff für Places und Voraussetzungen {#developer-prereqs}

Diese Informationen zeigen Ihnen, wie Sie ein Projekt in der Adobe Developer-Konsole erstellen und ein Zugriffstoken generieren, das in Places-API-Anfragen verwendet werden kann.

## Voraussetzungen für den Benutzerzugriff

Vergewissern Sie sich beim Systemadministrator Ihres Unternehmens, dass die folgenden Aufgaben abgeschlossen sind:

* Sie wurden zur Organisation hinzugefügt.
* Sie wurden zu einem Profil in der Adobe Experience Platform hinzugefügt.

  Weitere Informationen finden Sie unter *Benutzer oder Entwickler zu Ihren Places Service- und Experience Platform Launch-Profilen hinzufügen* in [Zugriff auf Places Service erhalten](/help/places-gain-access.md).

### REST-API-Anfragen

Für jede Anfrage an die Places Service-REST-API sind die folgenden Elemente erforderlich:

* Eine Organisations-ID
* API-Schlüssel (auch als Client-ID bezeichnet)
* Client-Geheimnis
* Trägertoken

Ein Projekt mit dem [Adobe Developer-Konsole](https://developer.adobe.com/console) stellt diese Elemente bereit.

* Informationen zum Erstellen eines Projekts für die Places Service-API finden Sie in der *Erstellen eines Places Service-Projekts* unten.

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei [Adobe Developer-Konsole](https://developer.adobe.com/console), oder wenn der Places-Dienst keine Option für die *Seite &quot;Integrationen erstellen&quot;*, siehe *Organisationsanforderungen* in [Übersicht über die Web-Services-API](/help/web-service-api/places-web-services.md).

## Erstellen eines Places Service-API-Projekts

Führen Sie die folgenden Schritte aus, um ein Projekt für die Places Service-API zu erstellen:

1. Anmelden bei [Adobe Developer-Website](https://developer.adobe.com) mit Ihrer Adobe ID.
2. Klicks **[!UICONTROL Konsole]** in der oberen rechten Ecke der Seite.
3. Wenn Sie mehr als einer Seitenorganisation zugewiesen sind, wählen Sie die richtige Adobe aus der Dropdownliste oben rechts auf der Seite aus.
4. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]** Schaltfläche.
5. Klicks **[!UICONTROL API hinzufügen]** im Abschnitt Erste Schritte mit Ihrem neuen Projekt .
6. Um die Places-API auszuwählen, scrollen Sie die Seite nach unten zur Karte Places und klicken Sie auf das Kontrollkästchen in der oberen rechten Ecke der Karte.
7. Klicken Sie auf die Schaltfläche **[!UICONTROL Next]**.
8. Wählen Sie die Option &quot;OAuth Server-to-Server&quot;(sofern eine Auswahl besteht).
9. Benennen Sie die Berechtigung und klicken Sie auf **[!UICONTROL Nächste]**.
10. Wählen Sie ein Profil aus (jedes Profil sollte funktionieren, wenn mehr als ein Profil vorhanden ist).
11. Klicks **[!UICONTROL API speichern und konfigurieren]**.
12. Klicken Sie im linken Bereich auf die **[!UICONTROL OAuth Server-zu-Server]** Link unter &quot;CREDENTIALS&quot;
13. Diese Seite bietet Folgendes:
   * Eine Möglichkeit, ein Zugriffstoken zu generieren, das in den REST-API-Anfragen des Places-Dienstes verwendet werden soll.
   * Sehen Sie sich einen curl-Befehl an, um ein Beispiel dafür anzuzeigen, wie Sie ein Zugriffstoken aus Ihrem eigenen Code generieren können.
   * Anzeigen der Client-ID (auch als API-Schlüssel bezeichnet)
   * Client-Geheimnis anzeigen
   * Organisations-ID anzeigen
   * All dies ist in den Anfragen an die Places Service REST API erforderlich.
14. Sie können das Projekt in eine aussagekräftigere Bezeichnung umbenennen, indem Sie im Pfad oben links im Fenster auf den Projektnamen klicken
15. Klicken Sie dann auf die **[!UICONTROL Projekt bearbeiten]** rechts oben auf der Seite.

>[!IMPORTANT]
>
>Adobe-Zugriffstoken sind gültig **only** 24 Stunden lang, speichern Sie also den CURL-Beispielbefehl (Schritt 5). Wenn das Zugriffstoken nicht mehr gültig ist, müssen Sie das Token neu generieren.
