---
title: Adobe Target
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Places-Dienstes mit Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# Verwenden des Places-Dienstes mit Adobe Target {#places-target}

In diesem Dokument wird davon ausgegangen, dass Sie die Places-Erweiterung in Ihrer Anwendung implementiert haben. Wenn Sie Hilfe bei der Implementierung der Places-Erweiterung benötigen, lesen Sie [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Places-Erweiterung Ereignisse für Einstiege und Ausstiege sendet, können Sie mithilfe von Regeln in Launch Ihre Places Service-Daten an Ihre Adobe Target SDK-Ereignisse anhängen. Wenn Sie Ihre gewünschte Eigenschaft in Launch ausgewählt haben, können Sie diesen Regeltyp erstellen, indem Sie die folgenden Aufgaben ausführen:

## 1. Erstellen einer Regel

1. Im **[!UICONTROL Regeln]** Registerkarte, klicken Sie auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts im Bildschirm.

## 2. Auswählen eines Ereignisses

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel erhält die Regel den Namen **[!UICONTROL Anfügen von Places-Dienstdaten an angeforderte Target-Inhalte]**.

1. Unter dem **[!UICONTROL Veranstaltungen]** Abschnitt, klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Aus dem **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Adobe Target]**.
1. Aus dem **[!UICONTROL Ereignistyp]** Dropdown-Liste auswählen **[!UICONTROL Inhalt angefordert]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Andernfalls können Sie zum *Definieren der Aktion* unten.

Im folgenden Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur für Benutzer Trigger wird, die die App fünf oder mehr Mal gestartet haben.

1. Unter dem **[!UICONTROL Bedingungen]** Abschnitt, klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Aus dem **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Mobile Core]**.
1. Aus dem **[!UICONTROL Bedingungstyp]** Dropdown-Liste auswählen **[!UICONTROL Starts]**.
1. Ändern Sie im rechten Bereich die Dropdown-Listen- und Zahlensteuerelemente so, dass die Bedingung **[!UICONTROL Der Benutzer hat die App gestartet, die größer oder gleich fünfmal ist.]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Bedingung hinzufügen](/help/assets/ad-setCondition_target.png)

## 4. Definieren Sie die Aktion

1. Unter dem **[!UICONTROL Aktionen]** Abschnitt, klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Aus dem **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Mobile Core]**.
1. Aus dem **[!UICONTROL Aktionstyp]** Dropdown-Liste auswählen **[!UICONTROL Daten anhängen]**.
1. Im rechten Bereich im **[!UICONTROL JSON-Payload]** Geben Sie die Daten ein, die diesem Ereignis hinzugefügt werden sollen.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

Im rechten Bereich können Sie eine Freiform-JSON-Payload hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor die für dieses Ereignis überwachenden Erweiterungen es hören.

Im folgenden Beispiel: `poiCity` und `poiName` -Werte hinzugefügt werden **[!UICONTROL mboxParameters]** für jede Anfrage, die im Target-Ereignis verarbeitet wird. Die Werte für die neuen Schlüssel werden vom SDK zum Zeitpunkt der Verarbeitung dieses Ereignisses dynamisch bestimmt.

>[!TIP]
>
>Diese JSON-Payload verwendet eine spezielle Notation für die `request` -Objekt. Im ursprünglichen Ereignis: `request` ist ein Array anonymer Objekte. Wenn Sie Daten mithilfe von &quot;Daten anhängen&quot;an alle Objekte in einem Array anhängen, wird die `[*]` -Notation auf einem Schlüssel, der bekanntermaßen ein Array enthält, bewirkt, dass die Payload auf alle Objekte in diesem Array angewendet wird.
>
>Die Notation von `request[*]` kann laut gelesen werden als _für jedes Objekt im `request` array_.

![Aktion definieren](/help/assets/ad-setAction-target.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob Ihre Regel wie folgt aussieht:

![abgeschlossene Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
