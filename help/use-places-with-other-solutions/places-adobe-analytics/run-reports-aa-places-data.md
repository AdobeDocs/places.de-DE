---
title: Hinzufügen von Standortkontext zu Analytics-Anforderungen
description: Dieser Abschnitt enthält Informationen zum Hinzufügen von Standortkontext zu Analytics-Anfragen.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# Hinzufügen von Standortkontext zu Analytics-Anforderungen {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In diesem Dokument wird davon ausgegangen, dass Sie Places Service in Ihrer Anwendung implementiert haben. Weitere Informationen zur Implementierung des Places-Dienstes finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Places-Dienst die Ein- und Ausstiegsereignisse sendet, können Sie Regeln in Experience Platform Launch erstellen und Ihre Places-Dienst-Daten an alle Adobe Analytics-Ereignisse anhängen. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Launch aus und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:
   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche **[!UICONTROL Neue Regel erstellen]** in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche **[!UICONTROL Neue Regel erstellen]** oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Places-Dienstdaten an Analytics-Verfolgungsaktionsereignisse anhängen]**.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Mobile Core]** aus.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL Aktion verfolgen]** aus.

Jetzt können Sie die Trigger bestimmen, die Sie für diese Regel einbeziehen möchten. In diesem Beispiel basiert der Trigger auf allen `TrackAction` -Aufrufen. Klicken Sie nach der Konfiguration des Ereignisses auf **[!UICONTROL Änderungen beibehalten]**.

![&quot;Ereignis erstellen&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie dieses Verfahren aus, um Ihrer Regel Bedingungen hinzuzufügen. Andernfalls können Sie zum Abschnitt *Aktion definieren* unten springen.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für AT&amp;T-Kunden Trigger wird.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Bedingungen]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Mobile Core]** aus.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Betreibername]** aus.

1. Aktivieren Sie im Fenster auf der rechten Seite das Kontrollkästchen **[!UICONTROL AT&amp;T]** .

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![&quot;create a condition&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definieren Sie die Aktion

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Mobile Core]** aus.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Aktionstyp]** die Option **[!UICONTROL Daten anhängen]** aus.

1. Geben Sie im rechten Bereich im Feld **[!UICONTROL JSON-Payload]** die Daten ein, die diesem Ereignis hinzugefügt werden sollen.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

Im rechten Bereich können Sie eine Freiform-JSON-Payload hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor eine Erweiterung, die auf dieses Ereignis überwacht, das Ereignis hören kann. In diesem Beispiel werden diesem Ereignis einige Kontextdaten hinzugefügt, bevor die Analytics-Erweiterung es verarbeitet. Die hinzugefügten Kontextdaten beziehen sich nun auf den ausgehenden Analytics-Treffer.

Im folgenden Beispiel werden die Werte `poi.city` und `poi.name` zu den Kontextdaten des Analytics-Ereignisses hinzugefügt. Die Werte für die neuen Schlüssel werden vom SDK bei der Verarbeitung dieses Ereignisses dynamisch bestimmt.

![&quot;Erstellen einer Aktion&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Speichern Sie die Regel und erstellen Sie die Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob Ihre Regel wie folgt aussieht:

![&quot;Die Regel ist abgeschlossen.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
