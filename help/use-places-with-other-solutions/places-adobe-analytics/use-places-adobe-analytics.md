---
title: POI-Einstiegs- und -Ausstiegsdaten an Analytics senden
description: Dieser Abschnitt enthält Informationen zum Senden von POI-Einstiegs- und -Ausstiegsdaten an Analytics.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 4%

---


# POI-Einstiegs- und -Ausstiegsdaten an Analytics {#places-data-analytics} senden


>[!IMPORTANT]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie über den Places-Dienst in Ihrer Anwendung verfügen. Weitere Informationen zur Implementierung des Orte-Dienstes finden Sie unter [Platzierungen-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Orte-Dienst die Ein- und Ausstiegsregeln gesendet hat, können Sie in Experience Platform Launch Regeln erstellen, um die Daten des Orte-Dienstes an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Start und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche **[!UICONTROL Neue Regel erstellen]** in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche **[!UICONTROL Neue Regel erstellen]** oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie einen aussagekräftigen Namen für Ihre Regel ein.

   Auf diese Weise wird die Regel in Ihrer Liste der Regeln leicht erkennbar. In diesem Beispiel heißt die Regel **[!UICONTROL Daten an Analytics senden]**.

1. Klicken Sie im Bereich **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Places Service]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** **[!UICONTROL POI]** eingeben.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![&quot;Ereignis auswählen&quot;](/help/assets/pt-selectEvent.png)


## 3. hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, um Ihrer Regel Bedingungen hinzuzufügen. Fahren Sie andernfalls mit *Definieren Sie die Aktion* weiter unten.

In diesem Beispiel wird eine Bedingung erstellt, die bewirkt, dass die Regel nur dann Trigger wird, wenn der Name des aktuellen POI **[!UICONTROL Meine POI]** lautet.

1. Klicken Sie im Abschnitt **[!UICONTROL Bedingungen]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Places Service]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Bedingungstyp]** **[!UICONTROL Name]**.

1. Geben Sie im rechten Bereich im Textfeld **[!UICONTROL Meine POI]** ein.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![&quot;Bedingung festlegen&quot;](/help/assets/pt-setCondition.png)


## 4. Definieren der Aktion

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Adobe Analytics]** aus.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Aktionstyp]** **[!UICONTROL Track]**.

1. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die bzw. den Sie an Analytics senden möchten.

   Sie können auch zusätzliche Kontextdaten zu dieser Anforderung hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch aus dem SDK abzurufen.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   Im folgenden Beispiel wird ein `TrackAction`-Aufruf an Analytics gesendet, wobei zusätzliche Kontextdaten von `poi.name` dem Namen des POI entsprechen, der dieses Ereignis ausgelöst hat:

   ![&quot;Aktion festlegen&quot;](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob die Regel wie folgt aussieht:

![&quot;rule is created&quot;](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie auf die richtige Umgebung bereit.
