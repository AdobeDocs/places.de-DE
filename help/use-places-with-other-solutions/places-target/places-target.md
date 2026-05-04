---
title: Adobe Target
description: In diesem Abschnitt finden Sie Informationen zur Verwendung des Places Service mit Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
TQID: https://experienceleague.adobe.com/WsfkEJD0mN5aYKETjcnqiC13dVe5NPYeKfOCTOK82uE
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 4%

---

# Verwenden des Places Service mit Adobe Target {#places-target}

In diesem Dokument wird davon ausgegangen, dass die Places-Erweiterung in Ihrem Programm implementiert ist. Wenn Sie Hilfe bei der Implementierung der Places-Erweiterung benötigen, lesen Sie [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem die Places-Erweiterung Ereignisse für Ein- und Ausstiege gesendet hat, können Sie in Launch Regeln nutzen, um Ihre Places Service-Daten an Ihre Adobe Target SDK-Ereignisse anzuhängen. Wenn Ihre gewünschte Eigenschaft in Launch ausgewählt ist, können Sie diesen Regeltyp erstellen, indem Sie die folgenden Aufgaben ausführen:

## &#x200B;1. Erstellen einer Regel

1. Klicken Sie auf der **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn für diese Eigenschaft keine Regeln vorhanden sind, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts im Bildschirm.

## &#x200B;2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist.

   In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Klicken Sie **[!UICONTROL Abschnitt]** Ereignisse“ auf **[!UICONTROL Hinzufügen]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Adobe Target]**.
1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Ereignistyp“ die Option **[!UICONTROL Inhalt angefordert]** aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![Ereignis hinzufügen](/help/assets/ad-setEvent_target.png)

## &#x200B;3. Hinzufügen von Bedingungen

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

## &#x200B;4. Definieren der Aktion

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

## &#x200B;5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Stellen Sie nach Abschluss der Konfiguration sicher, dass die Regel wie folgt aussieht:

![Abgeschlossene Regel](/help/assets/ad-ruleComplete-target.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
