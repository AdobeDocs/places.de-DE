---
title: Adobe Target
seo-title: Adobe Target
description: Dieser Abschnitt enthält Informationen zur Verwendung des Location Service mit Adobe Target.
seo-description: Dieser Abschnitt enthält Informationen zur Verwendung des Location Service mit Adobe Target.
translation-type: tm+mt
source-git-commit: 4ee8adb73f6dec15030a160c27edbeca71d3507b

---


# Standortdienst mit Adobe Target verwenden {#places-target}

Bei diesem Dokument wird davon ausgegangen, dass die Plates-Erweiterung in Ihrer Anwendung implementiert ist. Weitere Informationen zum Implementieren der Platzierungserweiterung finden Sie unter [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Platzierungserweiterung Ereignisse für Einstiege und Ausstiege gesendet hat, können Sie die Regeln beim Start nutzen, um Ihre Ortsdaten an Ihre Adobe Target SDK-Ereignisse anzuhängen. Wenn Sie die gewünschte Eigenschaft in Launch ausgewählt haben, können Sie diesen Regeltyp erstellen, indem Sie die folgenden Aufgaben ausführen:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Beachten Sie die folgenden Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts auf dem Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel wird die Regel benannt **[!UICONTROL Attach Places Data to Target Content Requested]**.

1. Klicken Sie unter dem **[!UICONTROL Events]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Adobe Target]**.

1. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdownliste **[!UICONTROL Content Requested]**.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

![Ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Fahren Sie andernfalls mit der Option Aktion *definieren* weiter unten fort.

Im folgenden Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für Benutzer ausgelöst wird, die die App fünf oder mehr Mal gestartet haben.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdownliste **[!UICONTROL Launches]**.

1. Ändern Sie im rechten Bereich die Dropdown-Liste und die Nummernsteuerelemente so, dass die Bedingung gelesen wird **[!UICONTROL User has launched the app greater than or equal to 5 times]**.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

![Bedingung hinzufügen](/help/assets/ad-setCondition_target.png)

## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdownliste **[!UICONTROL Attach Data]**.

1. Geben Sie im rechten Bereich im **[!UICONTROL JSON Payload]** Feld die Daten ein, die diesem Ereignis hinzugefügt werden sollen.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

Im rechten Bereich können Sie eine Freiform-JSON-Nutzlast hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor die Extensions, die auf dieses Ereignis warten, es hören.

Im folgenden Beispiel werden der Anforderung, die im Target-Ereignis verarbeitet wird, `poiCity` Werte hinzugefügt `poiName`**[!UICONTROL mboxparameters]** . Die Werte für die neuen Schlüssel werden vom SDK zum Zeitpunkt der Verarbeitung dieses Ereignisses dynamisch bestimmt.

>[!TIP]
>
>Diese JSON-Nutzlast verwendet eine spezielle Notation für das `request` Objekt. Im ursprünglichen Ereignis `request` ist ein Array anonymer Objekte. Wenn Daten mit "Daten anhängen"an alle Objekte in einem Array angehängt werden, bewirkt die `[*]` Notation auf einem Schlüssel, der bekanntermaßen ein Array enthält, dass die Nutzlast auf alle Objekte in diesem Array angewendet wird.
>
>Die Notation von `request[*]` kann laut wie _für jedes Objekt im`request`Array_ gelesen werden.

![die Aktion definieren](/help/assets/ad-setAction-target.png)

## 5. Speichern der Regel und Erstellen der Eigenschaft

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![Abgeschlossene Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Save]**

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
