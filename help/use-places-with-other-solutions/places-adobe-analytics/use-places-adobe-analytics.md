---
title: POI-Ein- und Ausstiegsdaten an Analytics senden
description: In diesem Abschnitt finden Sie Informationen zum Senden von POI-Eintritts- und -Austrittsdaten an Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 4%

---

# POI-Ein- und Ausstiegsdaten an Analytics senden {#places-data-analytics}


>[!IMPORTANT]
>
>In diesem Abschnitt wird davon ausgegangen, dass Places Service in Ihrem Programm implementiert wurde. Weitere Informationen zur Implementierung des Places-Service finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Places Service die Ein- und Ausstiegsereignisse gesendet hat, können Sie in Experience Platform Launch Regeln erstellen, um Daten des Places Service an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Launch aus und führen Sie die folgenden Schritte aus:

## 1. Erstellen einer Regel

1. Klicken Sie auf der **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn für diese Eigenschaft keine Regeln vorhanden sind **[!UICONTROL wird die Schaltfläche]** Neue Regel erstellen“ in der Mitte des Bildschirms angezeigt.
   * Wenn Ihre Eigenschaft über Regeln **[!UICONTROL , befindet]** Schaltfläche „Neue Regel erstellen“ oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie einen aussagekräftigen Namen für Ihre Regel ein.

   Auf diese Weise ist die Regel in Ihrer Regelliste leicht erkennbar. In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Daten an Analytics senden]**.

1. Klicken Sie im Bereich **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Places Service]** aus.

1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Ereignistyp“ die Option **[!UICONTROL POI eingeben]** aus.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![„Ereignis auswählen“](/help/assets/pt-selectEvent.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, um Bedingungen zu Ihrer Regel hinzuzufügen. Andernfalls fahren Sie mit *Definieren der Aktion* unten fort.

In diesem Beispiel wird eine Bedingung erstellt, die dazu führt, dass die Regel nur dann in Trigger gerät, wenn der Name des aktuellen POI gleich **[!UICONTROL Mein POI]** ist.

1. Klicken **[!UICONTROL im Abschnitt]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Places Service]** aus.

1. Wählen Sie in **[!UICONTROL Dropdown-Liste]** Bedingungstyp“ **[!UICONTROL Name]** aus.

1. Geben Sie im rechten Bereich im Textfeld &quot;**[!UICONTROL POI“]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![„Bedingung festlegen“](/help/assets/pt-setCondition.png)


## 4. Definieren der Aktion

1. Klicken Sie **[!UICONTROL Abschnitt]** Aktionen“ auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Erweiterung die Option **[!UICONTROL Adobe Analytics]**.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste „Aktionstyp“ die Option **[!UICONTROL Verfolgen]**.

1. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die bzw. den Sie an Analytics senden möchten.

   Sie können dieser Anfrage auch beliebige zusätzliche Kontextdaten hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch aus der SDK abzurufen.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   Im folgenden Beispiel wird ein `TrackAction`-Aufruf an Analytics mit zusätzlichen Kontextdaten von `poi.name` gesendet, die dem Namen des POI entsprechen, der dieses Eintrittsereignis ausgelöst hat:

   ![„Aktion festlegen“](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie Ihre Eigenschaft neu

Stellen Sie nach Abschluss der Konfiguration sicher, dass die Regel wie folgt aussieht:

![„Regel wird erstellt“](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
