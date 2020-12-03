---
title: Adobe Target
description: Dieser Abschnitt enthält Informationen zur Verwendung des Places-Dienstes mit Adobe Target.
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 2%

---


# Orte-Dienst mit Adobe Target verwenden {#places-target}

In diesem Dokument wird davon ausgegangen, dass die Plates-Erweiterung in Ihrer Anwendung implementiert ist. Weitere Informationen zum Implementieren der Platzierungserweiterung finden Sie unter [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Plates-Erweiterung Ereignis für Einstiege und Ausstiege gesendet hat, können Sie die Regeln in Launch nutzen, um Ihre Ortsdienstdaten an Ihre Adobe Target SDK-Ereignis anzuhängen. Wenn Sie die gewünschte Eigenschaft in Start ausgewählt haben, können Sie diese Art von Regel erstellen, indem Sie die folgenden Aufgaben ausführen:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts auf dem Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Liste der Regeln leicht erkennbar ist.

   In diesem Beispiel wird die Regel benannt **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Klicken Sie unter dem **[!UICONTROL Events]** Abschnitt auf **[!UICONTROL Add]**.
1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Adobe Target]**.
1. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdown-Liste **[!UICONTROL Content Requested]**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

![ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## 3. hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Fahren Sie andernfalls mit der Option Aktion *definieren* weiter unten fort.

Im folgenden Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für Benutzer ausgelöst wird, die die App fünf oder mehr Mal gestartet haben.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.
1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Mobile Core]**.
1. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdown-Liste **[!UICONTROL Launches]**.
1. Ändern Sie im rechten Bereich die Dropdown-Listen- und Nummernsteuerelemente so, dass die Bedingung gelesen wird **[!UICONTROL User has launched the app greater than or equal to 5 times]**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

![Bedingung hinzufügen](/help/assets/ad-setCondition_target.png)

## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.
1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Mobile Core]**.
1. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdown-Liste **[!UICONTROL Attach Data]**.
1. Geben Sie im rechten Bereich im **[!UICONTROL JSON Payload]** Feld die Daten ein, die diesem Ereignis hinzugefügt werden sollen.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

Im rechten Bereich können Sie eine Freiform-JSON-Nutzlast hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor die für dieses Ereignis Listening-Erweiterungen es hören.

Im folgenden Beispiel werden der Anforderung, die im Zielgruppe-Ereignis verarbeitet wird, `poiCity` Werte `poiName` **[!UICONTROL mboxparameters]** hinzugefügt. Die Werte für die neuen Schlüssel werden zum Zeitpunkt der Verarbeitung durch das SDK dynamisch bestimmt.

>[!TIP]
>
>Diese JSON-Nutzlast verwendet eine spezielle Notation für das `request` Objekt. Im ursprünglichen Ereignis `request` ist ein Array anonymer Objekte. Wenn Daten mit &quot;Daten anhängen&quot;an alle Objekte in einem Array angehängt werden, bewirkt die `[*]` Notation eines Schlüssels, der bekanntermaßen ein Array enthält, dass die Nutzlast auf alle Objekte in diesem Array angewendet wird.
>
>Die Notation von `request[*]` kann laut wie _für jedes Objekt im `request` Array_ gelesen werden.

![die Aktion definieren](/help/assets/ad-setAction-target.png)

## 5. Speichern der Regel und Erstellen der Eigenschaft

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![Abgeschlossene Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Save]**.
1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie auf die richtige Umgebung bereit.
