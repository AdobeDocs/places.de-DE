---
title: hinzufügen Standortkontext für Analytics-Anforderungen
description: Dieser Abschnitt enthält Informationen zum Hinzufügen von Standortkontext zu Analytics-Anforderungen.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---


# hinzufügen Standortkontext für Analytics-Anforderungen {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Bei diesem Dokument wird davon ausgegangen, dass Sie über den Places-Dienst verfügen, der in Ihrer Anwendung implementiert ist. Weitere Informationen zum Implementieren des Places-Dienstes finden Sie unter [Platzierungen von Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Orte-Dienst die Ein- und Ausstiegsregeln gesendet hat, können Sie Ereignis in Experience Platform Launch erstellen und Ihre Ortsdaten an alle Adobe Analytics-Ereignis anhängen. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Berücksichtigen Sie folgende Informationen:
   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche oben rechts auf dem Bildschirm.

## 2. Wählen Sie ein Ereignis

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Liste der Regeln leicht erkennbar ist.

   In diesem Beispiel wird die Regel benannt **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Klicken Sie unter dem **[!UICONTROL Events]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdown-Liste **[!UICONTROL Track Action]**.

Jetzt können Sie die Auslöser festlegen, die Sie für diese Regel einbeziehen möchten. In diesem Beispiel basiert der Auslöser auf allen `TrackAction` Aufrufen. Klicken Sie nach der Konfiguration des Ereignisses auf **[!UICONTROL Keep Changes]**.

![&quot;Ereignis erstellen&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. hinzufügen

>[!IMPORTANT]
>
>Führen Sie dieses Verfahren aus, um Ihrer Regel Bedingungen hinzuzufügen. Fahren Sie andernfalls mit dem Abschnitt Aktion *definieren* weiter unten fort.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für AT&amp;T-Kunden ausgelöst wird.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdown-Liste **[!UICONTROL Carrier Name]**.

1. Wählen Sie im Fenster auf der rechten Seite das **[!UICONTROL AT&T]** Kontrollkästchen aus.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

![&quot;Bedingung erstellen&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Mobile Core]**.

1. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdown-Liste **[!UICONTROL Attach Data]**.

1. Geben Sie im rechten Bereich im **[!UICONTROL JSON Payload]** Feld die Daten ein, die diesem Ereignis hinzugefügt werden sollen.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

Im rechten Bereich können Sie eine Freiform-JSON-Nutzlast hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor eine Erweiterung, die auf dieses Ereignis wartet, das Ereignis hören kann. In diesem Beispiel werden diesem Ereignis einige Kontextdaten hinzugefügt, bevor die Analytics-Erweiterung es verarbeitet. Die hinzugefügten Kontextdaten befinden sich nun beim ausgehenden Analytics-Treffer.

Im folgenden Beispiel werden den Kontextdaten des Analytics-Ereignisses Werte `poi.city` und `poi.name` Werte hinzugefügt. Die Werte für die neuen Schlüssel werden vom SDK bei der Verarbeitung dieses Ereignisses dynamisch festgelegt.

![&quot;Aktion erstellen&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![&quot;Die Regel ist abgeschlossen.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Klicken Sie auf **[!UICONTROL Save]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie auf die richtige Umgebung bereit.
