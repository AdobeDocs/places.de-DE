---
title: POI-Einstiegs- und -Ausstiegsdaten an Analytics senden
description: Dieser Abschnitt enthält Informationen zum Senden von POI-Einstiegs- und -Ausstiegsdaten an Analytics.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# POI-Einstiegs- und -Ausstiegsdaten an Analytics senden {#places-data-analytics}


>[!IMPORTANT]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie Places in Ihrer Anwendung implementiert haben. Weitere Informationen zur Implementierung von Places finden Sie unter [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem Orte die Ein- und Ausstiegsereignisse gesendet haben, können Sie in Experience Platform Launch Regeln erstellen, um Ortsdaten an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Beachten Sie die folgenden Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche oben rechts auf dem Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie einen aussagekräftigen Namen für Ihre Regel ein.

   Auf diese Weise ist die Regel in Ihrer Regelliste leicht erkennbar. In diesem Beispiel wird die Regel benannt **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Places]**.

1. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdownliste **[!UICONTROL Enter POI]**.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   !["Ereignis auswählen"](/help/assets/pt-selectEvent.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, um Ihrer Regel Bedingungen hinzuzufügen. Fahren Sie andernfalls mit *Definieren der unten stehenden Aktion* fort.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur ausgelöst wird, wenn der Name des aktuellen POI gleich **[!UICONTROL My POI]** ist.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Places]**.

1. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdownliste **[!UICONTROL Name]**.

1. Geben Sie im rechten Bereich im Textfeld **[!UICONTROL My POI]** ein.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   !["Bedingung festlegen"](/help/assets/pt-setCondition.png)


## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Adobe Analytics]**.

1. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdownliste **[!UICONTROL Track]**.

1. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die bzw. den Sie an Analytics senden möchten.

   Sie können auch zusätzliche Kontextdaten zu dieser Anforderung hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch aus dem SDK abzurufen.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   Im folgenden Beispiel wird ein `TrackAction` Aufruf an Analytics mit zusätzlichen Kontextdaten gesendet, die dem Namen des POI `poi.name` entsprechen, der dieses Eingabeereignis ausgelöst hat:

   !["Aktion festlegen"](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

!["rule is created"](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Save]**

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
