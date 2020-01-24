---
title: Hinzufügen von Ortskontext zu Analytics-Anforderungen
description: Dieser Abschnitt enthält Informationen zum Hinzufügen von Standortkontext zu Analytics-Anforderungen.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Hinzufügen von Ortskontext zu Analytics-Anforderungen {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In diesem Dokument wird davon ausgegangen, dass Sie über den Places-Dienst in Ihrer Anwendung verfügen. Weitere Informationen zum Implementieren des Places-Dienstes finden Sie unter [Platzierungen von Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Orte-Dienst die Ein- und Ausstiegsereignisse gesendet hat, können Sie Regeln im Experience Platform-Start erstellen und Ihre Ortsdaten an alle Adobe Analytics-Ereignisse anhängen. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]**Registerkarte auf**[!UICONTROL Create New Rule]**.

   Beachten Sie die folgenden Informationen:
   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die **[!UICONTROL Create New Rule]**Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die **[!UICONTROL Create New Rule]**Schaltfläche oben rechts auf dem Bildschirm.

## 2. Wählen Sie ein Ereignis

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel wird die Regel benannt **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Klicken Sie unter dem **[!UICONTROL Events]**Abschnitt auf**[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Event Type]**Dropdownliste**[!UICONTROL Track Action]**.

Jetzt können Sie die Auslöser festlegen, die Sie für diese Regel einbeziehen möchten. In diesem Beispiel basiert der Auslöser auf allen `TrackAction` Aufrufen. Klicken Sie nach der Konfiguration des Ereignisses auf **[!UICONTROL Keep Changes]**.

![&quot;Ereignis erstellen&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie dieses Verfahren aus, um Ihrer Regel Bedingungen hinzuzufügen. Fahren Sie andernfalls mit dem Abschnitt Aktion *definieren* weiter unten fort.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für AT&amp;T-Kunden ausgelöst wird.

1. Klicken Sie unter dem **[!UICONTROL Conditions]**Abschnitt auf**[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Condition Type]**Dropdownliste**[!UICONTROL Carrier Name]**.

1. Wählen Sie im Fenster auf der rechten Seite das **[!UICONTROL AT&T]**Kontrollkästchen aus.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

![&quot;Bedingung erstellen&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]**Abschnitt auf**[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Action Type]**Dropdownliste**[!UICONTROL Attach Data]**.

1. Geben Sie im rechten Bereich im **[!UICONTROL JSON Payload]**Feld die Daten ein, die diesem Ereignis hinzugefügt werden sollen.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

Im rechten Bereich können Sie eine Freiform-JSON-Nutzlast hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor eine Erweiterung, die auf dieses Ereignis überwacht, das Ereignis hören kann. In diesem Beispiel werden einige Kontextdaten zu diesem Ereignis hinzugefügt, bevor es von der Analytics-Erweiterung verarbeitet wird. Die hinzugefügten Kontextdaten befinden sich nun beim ausgehenden Analytics-Treffer.

Im folgenden Beispiel werden den Kontextdaten des Analytics-Ereignisses Werte `poi.city` und `poi.name` Werte hinzugefügt. Die Werte für die neuen Schlüssel werden vom SDK bei der Verarbeitung dieses Ereignisses dynamisch bestimmt.

![&quot;Aktion erstellen&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![&quot;Die Regel ist abgeschlossen.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Klicken Sie auf **[!UICONTROL Save]**

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
