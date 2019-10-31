---
title: Ausführen von Berichten in Adobe Analytics mit Ortsdaten
seo-title: Ausführen von Berichten in Adobe Analytics mit Ortsdaten
description: Dieser Abschnitt enthält Informationen zum Ausführen von Berichten in Analytics, die Ortsdaten enthalten.
seo-description: Dieser Abschnitt enthält Informationen zum Ausführen von Berichten in Analytics, die Ortsdaten enthalten.
translation-type: tm+mt
source-git-commit: 7ca51580a4cfa9c00431ad3972bd10e2a12dfbd1

---


# Ausführen von Berichten in Adobe Analytics mit Ortsdaten {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In diesem Dokument wird davon ausgegangen, dass Adobe Places in Ihrer Anwendung implementiert ist. Weitere Informationen zur Implementierung von Adobe Places finden Sie unter [Platzierungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem Orte die Einstiegs- und Ausstiegsereignisse gesendet haben, können Sie Regeln im Experience Platform Launch erstellen und Ihre Ortsdaten an alle Adobe Analytics-Ereignisse anhängen. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Beachten Sie die folgenden Informationen:
   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche oben rechts auf dem Bildschirm.

## 2. Wählen Sie ein Ereignis

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel wird die Regel benannt **[!UICONTROL Attach Places Data to Analytics Track Action Events]**.

2. Klicken Sie unter dem **[!UICONTROL Events]** Abschnitt auf **[!UICONTROL Add]**.

3. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Mobile Core]**.

4. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdownliste **[!UICONTROL Track Action]**.

Jetzt können Sie die Auslöser festlegen, die Sie für diese Regel einbeziehen möchten. In diesem Beispiel basiert der Auslöser auf allen `TrackAction` Aufrufen. Klicken Sie nach der Konfiguration des Ereignisses auf **[!UICONTROL Keep Changes]**.

!["Ereignis erstellen"](/help/assets/pt-selectEvent.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie dieses Verfahren aus, um Ihrer Regel Bedingungen hinzuzufügen. Fahren Sie andernfalls mit dem Abschnitt Aktion *definieren* weiter unten fort.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für AT&amp;T-Kunden ausgelöst wird.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.

2. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTORL Mobilcore]**.

3. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdownliste **[!UICONTROL Carrier Name]**.

4. Wählen Sie im Fenster auf der rechten Seite das **[!UICONTROL AT&T]** Kontrollkästchen aus.

5. Klicken Sie auf **[!UICONTROL Keep Changes]**.

!["Bedingung erstellen"](/help/assets/pt-setCondition.png)

## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.

2. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Mobile Core]**.

3. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdownliste **[!UICONTROL Attach Data]**.

4. Geben Sie im rechten Bereich im **[!UICONTROL JSON Payload]** Feld die Daten ein, die diesem Ereignis hinzugefügt werden sollen.

5. Klicken Sie auf **[!UICONTROL Keep Changes]**.

Im rechten Bereich können Sie eine Freiform-JSON-Nutzlast hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor eine Erweiterung, die auf dieses Ereignis überwacht, das Ereignis hören kann. In diesem Beispiel werden einige Kontextdaten zu diesem Ereignis hinzugefügt, bevor es von der Analytics-Erweiterung verarbeitet wird. Die hinzugefügten Kontextdaten befinden sich nun beim ausgehenden Analytics-Treffer.

Im folgenden Beispiel werden den Kontextdaten des Analytics-Ereignisses Werte `poi.city` und `poi.name` Werte hinzugefügt. Die Werte für die neuen Schlüssel werden vom SDK bei der Verarbeitung dieses Ereignisses dynamisch bestimmt.

!["Aktion erstellen"](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

!["Die Regel ist abgeschlossen."](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Save]**

2. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
