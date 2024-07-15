---
title: Adobe Target
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Places-Dienstes mit Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 3%

---

# Verwenden des Places-Dienstes mit Adobe Target {#places-target}

In diesem Dokument wird davon ausgegangen, dass Sie die Places-Erweiterung in Ihrer Anwendung implementiert haben. Wenn Sie Hilfe bei der Implementierung der Places-Erweiterung benötigen, finden Sie weitere Informationen unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Places-Erweiterung Ereignisse für Einstiege und Ausstiege sendet, können Sie mithilfe von Regeln in Launch Ihre Places Service-Daten an Ihre Adobe Target SDK-Ereignisse anhängen. Wenn Sie Ihre gewünschte Eigenschaft in Launch ausgewählt haben, können Sie diesen Regeltyp erstellen, indem Sie die folgenden Aufgaben ausführen:

## 1. Erstellen einer Regel

1. Klicken Sie auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Places-Dienstdaten an angeforderte Target-Inhalte anhängen]**.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Adobe Target]** aus.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL Inhalt angefordert]** aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Andernfalls gehen Sie zu &quot;*Define the Action*&quot;weiter unten.

Im folgenden Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für Benutzer Trigger wird, die die App fünf oder mehr Mal gestartet haben.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Bedingungen]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Mobile Core]** aus.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Starts]** aus.
1. Ändern Sie im rechten Bereich die Dropdown-Liste und die Zahlensteuerelemente so, dass die Bedingung &quot;**[!UICONTROL Benutzer hat die App gestartet hat&quot;, die größer oder gleich fünf Mal ist]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![fügen Sie eine Bedingung hinzu](/help/assets/ad-setCondition_target.png)

## 4. Definieren Sie die Aktion

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Mobile Core]** aus.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Aktionstyp]** die Option **[!UICONTROL Daten anhängen]** aus.
1. Geben Sie im rechten Bereich im Feld **[!UICONTROL JSON-Payload]** die Daten ein, die diesem Ereignis hinzugefügt werden sollen.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

Im rechten Bereich können Sie eine Freiform-JSON-Payload hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor die für dieses Ereignis überwachenden Erweiterungen es hören.

Im folgenden Beispiel werden die Werte `poiCity` und `poiName` den **[!UICONTROL mboxParameters]** für jede Anforderung hinzugefügt, die im Target-Ereignis verarbeitet wird. Die Werte für die neuen Schlüssel werden vom SDK zum Zeitpunkt der Verarbeitung dieses Ereignisses dynamisch bestimmt.

>[!TIP]
>
>Diese JSON-Payload verwendet eine spezielle Notation für das `request` -Objekt. Im ursprünglichen Ereignis ist `request` ein Array anonymer Objekte. Beim Anhängen von Daten an alle Objekte in einem Array mit &quot;Daten anhängen&quot;bewirkt die `[*]`-Notation eines Schlüssels, der bekanntermaßen ein Array enthält, dass die Payload auf alle Objekte in diesem Array angewendet wird.
>
>Die Notation von `request[*]` kann für jedes Objekt im Array `request` _laut als_ gelesen werden.

![ Aktion definieren](/help/assets/ad-setAction-target.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob Ihre Regel wie folgt aussieht:

![fertige Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
