---
title: POI-Einstiegs- und -Ausstiegsdaten an Analytics senden
description: Dieser Abschnitt enthält Informationen zum Senden von POI-Einstiegs- und -Ausstiegsdaten an Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 4%

---

# POI-Einstiegs- und -Ausstiegsdaten an Analytics senden {#places-data-analytics}


>[!IMPORTANT]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie Places Service in Ihrer Anwendung implementiert haben. Weitere Informationen zur Implementierung des Places-Dienstes finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Places-Dienst die Ein- und Ausstiegsereignisse sendet, können Sie in Experience Platform Launch Regeln erstellen, um Places-Dienst-Daten an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Launch aus und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Klicken Sie auf der Registerkarte **[!UICONTROL Regeln]** auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, befindet sich die Schaltfläche **[!UICONTROL Neue Regel erstellen]** in der Mitte des Bildschirms.
   * Wenn Ihre Eigenschaft über Regeln verfügt, befindet sich die Schaltfläche **[!UICONTROL Neue Regel erstellen]** oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie einen aussagekräftigen Namen für Ihre Regel ein.

   Auf diese Weise kann die Regel in Ihrer Regelliste leicht erkennbar sein. In diesem Beispiel trägt die Regel den Namen **[!UICONTROL Daten an Analytics senden]**.

1. Klicken Sie im Bereich **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Places Service]** aus.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL POI eingeben]** aus.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![&quot;Ereignis auswählen&quot;](/help/assets/pt-selectEvent.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, um Ihrer Regel Bedingungen hinzuzufügen. Überspringen Sie andernfalls &quot;*Aktion definieren*&quot;unten.

In diesem Beispiel wird eine Bedingung erstellt, durch die die Regel nur dann Trigger wird, wenn der Name des aktuellen POI gleich **[!UICONTROL Mein POI]** ist.

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Bedingungen]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Places Service]** aus.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Name]** aus.

1. Geben Sie im rechten Bereich im Textfeld **[!UICONTROL Mein POI]** ein.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![&quot;set a condition&quot;](/help/assets/pt-setCondition.png)


## 4. Definieren Sie die Aktion

1. Klicken Sie unter dem Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL Hinzufügen]**.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Adobe Analytics]** aus.

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Aktionstyp]** die Option **[!UICONTROL Track]** aus.

1. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die/den Sie an Analytics senden möchten.

   Sie können dieser Anforderung auch zusätzliche Kontextdaten hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch vom SDK abzurufen.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   Im folgenden Beispiel wird ein `TrackAction` -Aufruf an Analytics mit zusätzlichen Kontextdaten von `poi.name` gesendet, die dem Namen des POI entsprechen, der dieses Eintrittsereignis ausgelöst hat:

   ![&quot;set an action&quot;](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie die Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob Ihre Regel wie folgt aussieht:

![&quot;rule is created&quot;](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
