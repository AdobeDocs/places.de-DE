---
title: POI-Einstiegs- und -Ausstiegsdaten an Analytics senden
description: Dieser Abschnitt enthält Informationen zum Senden von POI-Einstiegs- und -Ausstiegsdaten an Analytics.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 2%

---


# POI-Einstiegs- und -Ausstiegsdaten an Analytics senden {#places-data-analytics}


>[!IMPORTANT]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie über den Places-Dienst in Ihrer Anwendung verfügen. Weitere Informationen zum Implementieren des Places-Dienstes finden Sie unter [Platzierungen von Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Orte-Dienst die Ein- und Ausstiegsregeln gesendet hat, können Sie in Experience Platform Launch Regeln erstellen, um die Daten des Orte-Dienstes an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die **[!UICONTROL Create New Rule]** Schaltfläche oben rechts auf dem Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie einen aussagekräftigen Namen für Ihre Regel ein.

   Auf diese Weise wird die Regel in Ihrer Liste der Regeln leicht erkennbar. In diesem Beispiel wird die Regel benannt **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Places Service]**.

1. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdown-Liste **[!UICONTROL Enter POI]**.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   ![&quot;Ereignis auswählen&quot;](/help/assets/pt-selectEvent.png)


## 3. hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, um Ihrer Regel Bedingungen hinzuzufügen. Fahren Sie andernfalls mit *Definieren der unten stehenden Aktion* fort.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur ausgelöst wird, wenn der Name des aktuellen POI gleich **[!UICONTROL My POI]** ist.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Places Service]**.

1. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdown-Liste **[!UICONTROL Name]**.

1. Geben Sie im rechten Bereich im Textfeld **[!UICONTROL My POI]** ein.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   ![&quot;Bedingung festlegen&quot;](/help/assets/pt-setCondition.png)


## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.

1. Wählen Sie aus der **[!UICONTROL Extension]** Dropdown-Liste **[!UICONTROL Adobe Analytics]**.

1. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdown-Liste **[!UICONTROL Track]**.

1. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die bzw. den Sie an Analytics senden möchten.

   Sie können auch zusätzliche Kontextdaten zu dieser Anforderung hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch aus dem SDK abzurufen.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   Im folgenden Beispiel wird ein `TrackAction` Aufruf an Analytics mit zusätzlichen Kontextdaten gesendet, die dem Namen des POI `poi.name` entsprechen, der dieses Ereignis ausgelöst hat:

   ![&quot;Aktion festlegen&quot;](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![&quot;rule is created&quot;](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Save]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie auf die richtige Umgebung bereit.
