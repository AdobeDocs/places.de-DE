---
title: Ortsdaten an Adobe Analytics senden
seo-title: Ortsdaten an Adobe Analytics senden
description: Dieser Abschnitt enthält Informationen zum Senden von Ortsdaten an Analytics.
seo-description: 'Dieser Abschnitt enthält Informationen zum Senden von Ortsdaten an Analytics. '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# Ortsdaten an Adobe Analytics senden {#places-data-analytics}


>[!IMPORTANT]
>
>In diesem Dokument wird davon ausgegangen, dass Sie Places in Ihrer Anwendung implementiert haben. Weitere Informationen zur Implementierung von Orten finden Sie unter [Platzierungserweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem Orte die Ein- und Ausstiegsereignisse gesendet haben, können Sie in Experience Platform Launch Regeln erstellen, um Ortsdaten an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der **[!UICONTROL Rules]** Registerkarte auf **[!UICONTROL Create New Rule]**.

   Beachten Sie die folgenden Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche oben rechts auf dem Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie Ihrer Regel einen aussagekräftigen Namen, damit sie in Ihrer Regelliste leicht erkennbar ist. In diesem Beispiel heißt die Regel Daten an Analytics **senden**.

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Places]**.

4. Wählen Sie aus der **[!UICONTROL Event Type]** Dropdownliste **[!UICONTROL Enter POI]**.

5. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   !["Ereignis auswählen"](/help/assets/pt-selectEvent.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, wenn Sie Bedingungen zu Ihrer Regel hinzufügen möchten. Fahren Sie andernfalls mit *Definieren der unten stehenden Aktion* fort.


In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur ausgelöst wird, wenn der Name des aktuellen POI gleich **[!UICONTROL My POI]** ist.

1. Klicken Sie unter dem **[!UICONTROL Conditions]** Abschnitt auf **[!UICONTROL Add]**.

2. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Places]**.

3. Wählen Sie aus der **[!UICONTROL Condition Type]** Dropdownliste **[!UICONTROL Name]**.

4. Geben Sie im Fenster auf der rechten Seite im Textfeld **[!UICONTROL My POI]** ein.

5. Klicken Sie auf **[!UICONTROL Keep Changes]**.

   !["Bedingung festlegen"](/help/assets/ad-setCondition.png)


## 4. Definieren der Aktion

1. Klicken Sie unter dem **[!UICONTROL Actions]** Abschnitt auf **[!UICONTROL Add]**.

2. Wählen Sie aus der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Adobe Analytics]**.

3. Wählen Sie aus der **[!UICONTROL Action Type]** Dropdownliste **[!UICONTROL Track]**.

4. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die bzw. den Sie an Analytics senden möchten. Sie können auch zusätzliche Kontextdaten zu dieser Anforderung hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch aus dem SDK abzurufen.

5. Klicken Sie auf **[!UICONTROL Keep Changes]**.

Im folgenden Beispiel wird ein `TrackAction` Aufruf an Analytics mit zusätzlichen Kontextdaten von **poi.name** gesendet, die dem Namen des POI entsprechen, der dieses Eingabeereignis ausgelöst hat:

!["Aktion festlegen"](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

!["rule is created"](/help/assets/pt-ruleComplete.png)


1. Klicken Sie auf **[!UICONTROL Save]**

2. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.

