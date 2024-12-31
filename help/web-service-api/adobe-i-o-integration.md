---
title: Übersicht über Adobe Developer-Projekte
description: Informationen zum Erstellen eines Adobe Developer-API-Projekts.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Übersicht über den Places API-Zugriff und Voraussetzungen {#developer-prereqs}

Diese Informationen zeigen Ihnen, wie Sie ein Projekt in der Adobe Developer Console erstellen und ein Zugriffstoken generieren, das in Places-API-Anfragen verwendet werden kann.

## Voraussetzungen für den Benutzerzugriff

Überprüfen Sie beim Systemadministrator Ihrer Organisation, ob die folgenden Aufgaben abgeschlossen wurden:

* Sie wurden der Organisation hinzugefügt.
* Die Benutzerin bzw. der Benutzer wurde in der Adobe Experience Platform zu einem Profil hinzugefügt.

  Weitere Informationen finden Sie unter *Hinzufügen eines Benutzers oder Entwicklers zu Ihren Places Service- und Experience Platform Launch-Profilen* in [Zugriff auf Places Service erhalten](/help/places-gain-access.md).

### REST-API-Anfragen

Jede Anfrage an die Places Service-REST-API erfordert die folgenden Elemente:

* Eine Organisations-ID
* Ein API-Schlüssel (auch als Client-ID bezeichnet)
* Client-Geheimnis
* Ein Bearer-Token

Ein Projekt mit der [Adobe Developer-Konsole](https://developer.adobe.com/console) stellt diese Elemente bereit.

* Wie Sie ein Projekt für die Places Service-API erstellen, erfahren Sie *Abschnitt „Erstellen eines Places Service* Projekts“ weiter unten.

>[!IMPORTANT]
>
>Wenn Sie sich nicht bei der [Adobe Developer-](https://developer.adobe.com/console) anmelden können oder wenn Places Service auf der Seite „Integrationen erstellen *keine Option ist* finden Sie weitere Informationen unter *Organisationsanforderungen* in [Übersicht über die Webservices-API](/help/web-service-api/places-web-services.md).

## Erstellen eines Places Service-API-Projekts

Um ein Projekt für die Places Service-API zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich mit Ihrer Adobe ID bei ](https://developer.adobe.com) Adobe Developer-Website an.[
2. Klicken **[!UICONTROL oben]** der Seite auf „Konsole“.
3. Wenn Sie mehreren Adobe-Organisationen zugewiesen sind, wählen Sie die richtige Organisation aus der Dropdown-Liste oben rechts auf der Seite aus.
4. Klicken Sie auf die **[!UICONTROL Neues Projekt erstellen]**.
5. Klicken Sie **[!UICONTROL Abschnitt Erste Schritte mit]** neuen Projekt auf die Schaltfläche „API hinzufügen“.
6. Um die Places-API auszuwählen, blättern Sie auf der Seite nach unten zur Karte Places und klicken Sie auf das Kontrollkästchen in der oberen rechten Ecke der Karte.
7. Klicken Sie auf die Schaltfläche **[!UICONTROL Weiter]**.
8. Wählen Sie die OAuth-Server-zu-Server-Option aus (falls eine Option vorhanden ist).
9. Benennen Sie die Berechtigung und klicken Sie auf **[!UICONTROL Weiter]**.
10. Wählen Sie ein Profil aus (jedes sollte funktionieren, wenn mehrere vorhanden sind).
11. Klicken Sie auf **[!UICONTROL API speichern und konfigurieren]**.
12. Klicken Sie im linken Bedienfeld unter **[!UICONTROL auf den Link OAuth Server-]**-Server .
13. Diese Seite bietet Folgendes:
   * Eine Methode zum Generieren eines Zugriffstokens, das in den Places Service-REST-API-Anfragen verwendet wird.
   * Sehen Sie sich einen curl-Befehl an, um ein Beispiel dafür zu sehen, wie Sie ein Zugriffstoken aus Ihrem eigenen Code generieren können.
   * Anzeigen der Client-ID (auch als API-Schlüssel bezeichnet)
   * Anzeigen des Client-Geheimnisses
   * Organisations-ID anzeigen
   * Diese sind alle in den Anfragen an die Places Service-REST-API erforderlich.
14. Sie können das Projekt umbenennen, indem Sie auf den Projektnamen im Pfad oben links im Fenster klicken
15. Klicken Sie dann oben **[!UICONTROL auf]** Seite auf „Projekt bearbeiten“.

>[!IMPORTANT]
>
>Adobe-Zugriffs-Token sind **nur** 24 Stunden lang gültig. Speichern Sie daher den CURL-Beispielbefehl (Schritt 5). Wenn das Zugriffs-Token nicht mehr gültig ist, müssen Sie das Token neu generieren.
