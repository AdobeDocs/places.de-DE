---
title: Hinzufügen von Standortkontext zu Analytics-Anfragen
description: In diesem Abschnitt finden Sie Informationen zum Hinzufügen von Standortkontext zu Analytics-Anfragen.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# Hinzufügen von Standortkontext zu Analytics-Anfragen {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In diesem Dokument wird davon ausgegangen, dass Sie Places Service in Ihrem Programm implementiert haben. Weitere Informationen zur Implementierung des Places-Service finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Places Service die Ein- und Ausstiegsereignisse gesendet hat, können Sie Regeln auf Experience Platform Launch erstellen und Ihre Places Service-Daten an alle Adobe Analytics-Ereignisse anhängen. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Launch aus und führen Sie die folgenden Schritte aus:

## 1. Erstellen einer Regel

1. Klicken Sie auf der **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:
   * Wenn für diese Eigenschaft keine Regeln vorhanden sind **[!UICONTROL wird die Schaltfläche]** Neue Regel erstellen“ in der Mitte des Bildschirms angezeigt.
   * Wenn Ihre Eigenschaft über Regeln **[!UICONTROL , befindet]** Schaltfläche „Neue Regel erstellen“ oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Klicken Sie **[!UICONTROL Abschnitt]** Ereignisse“ auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Mobile Core]** aus.

1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Ereignistyp“ die Option **[!UICONTROL Aktion]**.

Jetzt können Sie die Trigger bestimmen, die Sie für diese Regel einbeziehen möchten. In diesem Beispiel basiert der Trigger auf allen `TrackAction`. Klicken Sie nach der Konfiguration des Ereignisses auf **[!UICONTROL Änderungen beibehalten]**.

![„Ereignis erstellen“](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie dieses Verfahren aus, um Bedingungen zu Ihrer Regel hinzuzufügen. Andernfalls fahren Sie mit dem Abschnitt *Definieren der Aktion* weiter unten fort.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für AT&amp;T-Kunden in Trigger gerät.

1. Klicken **[!UICONTROL im Abschnitt]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Mobile Core]** aus.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste „Bedingungstyp“ die Option **[!UICONTROL Provider-Name]** aus.

1. Aktivieren Sie im Fenster rechts das Kontrollkästchen **[!UICONTROL AT&amp;T]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![„Bedingung erstellen“](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definieren der Aktion

1. Klicken Sie **[!UICONTROL Abschnitt]** Aktionen“ auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Mobile Core]** aus.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste „Aktionstyp“ die Option **[!UICONTROL Daten anhängen]**.

1. Geben Sie im rechten Bereich in das Feld **[!UICONTROL JSON-]**&quot; die Daten ein, die zu diesem Ereignis hinzugefügt werden sollen.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

Im rechten Bereich können Sie eine Freiform-JSON-Payload hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor eine Erweiterung, die auf dieses Ereignis wartet, das Ereignis hören kann. In diesem Beispiel werden diesem Ereignis Kontextdaten hinzugefügt, bevor es von der Analytics-Erweiterung verarbeitet wird. Die hinzugefügten Kontextdaten befinden sich jetzt im ausgehenden Analytics-Treffer.

Im folgenden Beispiel werden den Kontextdaten des Analytics-Ereignisses `poi.city`- und `poi.name`-Werte hinzugefügt. Die Werte für die neuen Schlüssel werden von der SDK dynamisch bestimmt, wenn dieses Ereignis verarbeitet wird.

![„Erstellen einer Aktion“](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Stellen Sie nach Abschluss der Konfiguration sicher, dass die Regel wie folgt aussieht:

![„Die Regel ist abgeschlossen.“](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
