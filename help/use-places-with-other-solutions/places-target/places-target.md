---
title: Adobe Target
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Places Service mit Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 3%

---

# Verwenden des Places Service mit Adobe Target {#places-target}

In diesem Dokument wird davon ausgegangen, dass die Places-Erweiterung in Ihrem Programm implementiert ist. Wenn Sie Hilfe bei der Implementierung der Places-Erweiterung benötigen, lesen Sie [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Places-Erweiterung Ereignisse für Ein- und Ausstiege gesendet hat, können Sie in Launch Regeln nutzen, um Ihre Places Service-Daten an Ihre Adobe Target SDK-Ereignisse anzuhängen. Wenn Ihre gewünschte Eigenschaft in Launch ausgewählt ist, können Sie diesen Regeltyp erstellen, indem Sie die folgenden Aufgaben ausführen:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn für diese Eigenschaft keine Regeln vorhanden sind, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Klicken Sie **[!UICONTROL Abschnitt]** Ereignisse“ auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Adobe Target]**.
1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Ereignistyp“ die Option **[!UICONTROL Inhalt angefordert]** aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Andernfalls fahren Sie unten mit *Definieren der Aktion* fort.

Im folgenden Beispiel wird eine Bedingung erstellt, die dazu führt, dass die Regel nur für Benutzende in den Trigger gerät, die die App mindestens fünf Mal gestartet haben.

1. Klicken **[!UICONTROL im Abschnitt]** auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Mobile Core]** aus.
1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Bedingungstyp“ **[!UICONTROL Launches]** aus.
1. Ändern Sie im rechten Bereich die Steuerelemente für Dropdown-Liste und Anzahl so, dass die Bedingung lautet **[!UICONTROL Der Benutzer hat die App mehr als oder gleich fünfmal gestartet]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Bedingung hinzufügen](/help/assets/ad-setCondition_target.png)

## 4. Definieren der Aktion

1. Klicken Sie **[!UICONTROL Abschnitt]** Aktionen“ auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Mobile Core]** aus.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste „Aktionstyp“ die Option **[!UICONTROL Daten anhängen]**.
1. Geben Sie im rechten Bereich in das Feld **[!UICONTROL JSON-]**&quot; die Daten ein, die zu diesem Ereignis hinzugefügt werden sollen.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

Im rechten Bereich können Sie eine Freiform-JSON-Payload hinzufügen, die Daten zu einem SDK-Ereignis hinzufügt, bevor die Erweiterungen, die auf dieses Ereignis warten, es hören.

Im folgenden Beispiel werden `poiCity`- und `poiName`-Werte zu den **[!UICONTROL mboxParameters]** für jede Anfrage hinzugefügt, die im Target-Ereignis verarbeitet wird. Die Werte für die neuen Schlüssel werden von der SDK zum Zeitpunkt der Verarbeitung dieses Ereignisses dynamisch bestimmt.

>[!TIP]
>
>Diese JSON-Payload verwendet eine spezielle Notation für das `request`. Im ursprünglichen Ereignis ist `request` ein Array anonymer Objekte. Beim Anhängen von Daten an alle Objekte in einem Array mithilfe von „Daten anhängen“ bewirkt die `[*]` Notation für einen Schlüssel, von dem bekannt ist, dass er ein Array enthält, dass die Payload auf alle Objekte in diesem Array angewendet wird.
>
>Die Notation von `request[*]` kann laut ausgelesen werden als _für jedes Objekt im `request`-Array_.

![Definieren Sie die Aktion](/help/assets/ad-setAction-target.png)

## 5. Speichern Sie die Regel und erstellen Sie die Eigenschaft neu

Stellen Sie nach Abschluss der Konfiguration sicher, dass die Regel wie folgt aussieht:

![Abgeschlossene Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
