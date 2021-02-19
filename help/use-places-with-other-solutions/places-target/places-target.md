---
title: Adobe Target
description: Dieser Abschnitt enthält Informationen zur Verwendung des Places-Dienstes mit Adobe Target.
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---


# Orte-Dienst mit Adobe Target {#places-target} verwenden

In diesem Dokument wird davon ausgegangen, dass die Plates-Erweiterung in Ihrer Anwendung implementiert ist. Wenn Sie Hilfe bei der Implementierung der Places-Erweiterung benötigen, finden Sie weitere Informationen unter [Platzierungen-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Plates-Erweiterung Ereignis für Einstiege und Ausstiege gesendet hat, können Sie die Regeln in Launch nutzen, um Ihre Ortsdienstdaten an Ihre Adobe Target SDK-Ereignis anzuhängen. Wenn Sie die gewünschte Eigenschaft in Start ausgewählt haben, können Sie diese Art von Regel erstellen, indem Sie die folgenden Aufgaben ausführen:

## 1. Regel erstellen

1. Klicken Sie auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts auf dem Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Liste der Regeln leicht erkennbar ist.

   In diesem Beispiel erhält die Regel den Namen **[!UICONTROL Ortsdienstdaten an angeforderte Zielgruppen-Content anhängen]**.

1. Klicken Sie unter **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Adobe Target]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** **[!UICONTROL Inhaltsanforderungen]** aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## 3. hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Fahren Sie andernfalls mit *Definieren Sie die Aktion* weiter unten.

Im folgenden Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für Benutzer Trigger wird, die die App fünf oder mehr Mal gestartet haben.

1. Klicken Sie im Abschnitt **[!UICONTROL Bedingungen]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Mobile Core]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Bedingungstyp]** **[!UICONTROL Starts]**.
1. Ändern Sie im rechten Bereich die Dropdown-Listen- und Nummernsteuerelemente so, dass die Bedingung **[!UICONTROL Benutzer die App gestartet hat, die größer oder gleich 5 Mal]** ist.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Bedingung hinzufügen](/help/assets/ad-setCondition_target.png)

## 4. Definieren der Aktion

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Mobile Core]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Aktionstyp]** **[!UICONTROL Daten anhängen]** aus.
1. Geben Sie im rechten Bereich im Feld **[!UICONTROL JSON Payload]** die Daten ein, die diesem Ereignis hinzugefügt werden sollen.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

Im rechten Bereich können Sie eine Freiform-JSON-Nutzlast hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor die für dieses Ereignis Listening-Erweiterungen es hören.

Im folgenden Beispiel werden den Werten `poiCity` und `poiName` für jede Anforderung, die im Ereignis Zielgruppe verarbeitet wird, **[!UICONTROL mboxParameters]** hinzugefügt. Die Werte für die neuen Schlüssel werden zum Zeitpunkt der Verarbeitung durch das SDK dynamisch bestimmt.

>[!TIP]
>
>Diese JSON-Nutzlast verwendet eine spezielle Notation für das `request`-Objekt. Im ursprünglichen Ereignis ist `request` ein Array anonymer Objekte. Wenn Daten mit &quot;Daten anhängen&quot;an alle Objekte in einem Array angehängt werden, bewirkt die `[*]`-Notation bei einem Schlüssel, der bekanntermaßen ein Array enthält, dass die Nutzlast auf alle Objekte in diesem Array angewendet wird.
>
>Die Notation von `request[*]` kann laut als _für jedes Objekt im `request`-Array_ gelesen werden.

![die Aktion definieren](/help/assets/ad-setAction-target.png)

## 5. Speichern der Regel und Erstellen der Eigenschaft

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![Abgeschlossene Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie auf die richtige Umgebung bereit.
