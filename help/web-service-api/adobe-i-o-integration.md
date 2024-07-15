---
title: Adobe Developer-Projektübersicht
description: Informationen zum Erstellen eines Adobe Developer-API-Projekts.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Übersicht über den API-Zugriff für Places und Voraussetzungen {#developer-prereqs}

Diese Informationen zeigen Ihnen, wie Sie ein Projekt in der Adobe Developer Console erstellen und ein Zugriffstoken generieren, das in Places-API-Anfragen verwendet werden kann.

## Voraussetzungen für den Benutzerzugriff

Vergewissern Sie sich beim Systemadministrator Ihres Unternehmens, dass die folgenden Aufgaben abgeschlossen sind:

* Sie wurden zur Organisation hinzugefügt.
* Sie wurden zu einem Profil in der Adobe Experience Platform hinzugefügt.

  Weitere Informationen finden Sie unter *Hinzufügen eines Benutzers oder Entwicklers zu Ihrem Places-Dienst und Experience Platform Launch-Profilen* in [Zugriff auf Places-Dienst erhalten](/help/places-gain-access.md).

### REST-API-Anfragen

Für jede Anfrage an die Places Service-REST-API sind die folgenden Elemente erforderlich:

* Eine Organisations-ID
* API-Schlüssel (auch als Client-ID bezeichnet)
* Client-Geheimnis
* Trägertoken

Ein Projekt mit der [Adobe Developer-Konsole](https://developer.adobe.com/console) stellt diese Elemente bereit.

* Informationen zum Erstellen eines Projekts für die Places Service-API finden Sie unten im Abschnitt *Erstellen eines Places Service-Projekts* .

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei [Adobe Developer-Konsole](https://developer.adobe.com/console) anmelden können oder der Places-Dienst keine Option auf der Seite *Integrationen erstellen* ist, finden Sie weitere Informationen unter *Organisationsanforderungen* in der Übersicht über die Web-Services-API](/help/web-service-api/places-web-services.md).[

## Erstellen eines Places Service-API-Projekts

Führen Sie die folgenden Schritte aus, um ein Projekt für die Places Service-API zu erstellen:

1. Melden Sie sich mit Ihrer Adobe ID bei der [Adobe Developer-Website](https://developer.adobe.com) an.
2. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Konsole]** .
3. Wenn Sie mehr als einer Adobe-Organisation zugewiesen sind, wählen Sie die richtige Organisation aus der Dropdownliste oben rechts auf der Seite aus.
4. Klicken Sie auf die Schaltfläche **[!UICONTROL Neues Projekt erstellen]** .
5. Klicken Sie im Abschnitt Erste Schritte mit Ihrem neuen Projekt auf die Schaltfläche **[!UICONTROL API hinzufügen]** .
6. Um die Places-API auszuwählen, scrollen Sie die Seite nach unten zur Karte Places und klicken Sie auf das Kontrollkästchen in der oberen rechten Ecke der Karte.
7. Klicken Sie auf die Schaltfläche **[!UICONTROL Weiter]**.
8. Wählen Sie die Option &quot;OAuth Server-to-Server&quot;(sofern eine Auswahl besteht).
9. Benennen Sie die Berechtigung und klicken Sie auf &quot;**[!UICONTROL Weiter]**&quot;.
10. Wählen Sie ein Profil aus (jedes Profil sollte funktionieren, wenn mehr als ein Profil vorhanden ist).
11. Klicken Sie auf **[!UICONTROL Speichern und konfigurieren Sie die API]**.
12. Klicken Sie im linken Bereich unter &quot;CREDENTIALS&quot;auf den Link **[!UICONTROL OAuth Server-to-Server]** .
13. Diese Seite bietet Folgendes:
   * Eine Möglichkeit, ein Zugriffstoken zu generieren, das in den REST-API-Anfragen des Places-Dienstes verwendet werden soll.
   * Sehen Sie sich einen curl-Befehl an, um ein Beispiel dafür anzuzeigen, wie Sie ein Zugriffstoken aus Ihrem eigenen Code generieren können.
   * Anzeigen der Client-ID (auch als API-Schlüssel bezeichnet)
   * Client-Geheimnis anzeigen
   * Organisations-ID anzeigen
   * All dies ist in den Anfragen an die Places Service REST API erforderlich.
14. Sie können das Projekt in eine aussagekräftigere Bezeichnung umbenennen, indem Sie im Pfad oben links im Fenster auf den Projektnamen klicken
15. Klicken Sie dann oben rechts auf der Seite auf die Schaltfläche **[!UICONTROL Projekt bearbeiten]** .

>[!IMPORTANT]
>
>Adobe-Zugriffstoken sind 24 Stunden lang gültig **nur**, daher speichern Sie den CURL-Beispielbefehl (Schritt 5). Wenn das Zugriffstoken nicht mehr gültig ist, müssen Sie das Token neu generieren.
