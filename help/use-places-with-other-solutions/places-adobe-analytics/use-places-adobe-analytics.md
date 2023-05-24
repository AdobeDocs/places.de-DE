---
title: POI-Einstiegs- und -Ausstiegsdaten an Analytics senden
description: Dieser Abschnitt enthält Informationen zum Senden von POI-Einstiegs- und -Ausstiegsdaten an Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 4%

---

# POI-Einstiegs- und -Ausstiegsdaten an Analytics senden {#places-data-analytics}


>[!IMPORTANT]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie Places Service in Ihrer Anwendung implementiert haben. Weitere Informationen zur Implementierung des Places-Dienstes finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nachdem der Places-Dienst die Ein- und Ausstiegsereignisse sendet, können Sie in Experience Platform Launch Regeln erstellen, um Places-Dienst-Daten an Adobe Analytics zu senden. Um diesen Regeltyp zu erstellen, wählen Sie Ihre Eigenschaft in Launch aus und führen Sie die folgenden Schritte aus:

## 1. Regel erstellen

1. Im **[!UICONTROL Regeln]** Registerkarte, klicken Sie auf **[!UICONTROL Neue Regel erstellen]**.

   Berücksichtigen Sie folgende Informationen:

   * Wenn Sie keine Regeln für diese Eigenschaft haben, wird die **[!UICONTROL Neue Regel erstellen]** -Schaltfläche in der Mitte des Bildschirms angezeigt.
   * Wenn Ihre Eigenschaft über Regeln verfügt, wird die **[!UICONTROL Neue Regel erstellen]** oben rechts im Bildschirm.

## 2. Ereignis auswählen

1. Geben Sie einen aussagekräftigen Namen für Ihre Regel ein.

   Auf diese Weise kann die Regel in Ihrer Regelliste leicht erkennbar sein. In diesem Beispiel erhält die Regel den Namen **[!UICONTROL Daten an Analytics senden]**.

1. Klicken Sie im Bereich **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Aus dem **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Places Service]**.

1. Aus dem **[!UICONTROL Ereignistyp]** Dropdown-Liste auswählen **[!UICONTROL POI eingeben]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![&quot;Ereignis auswählen&quot;](/help/assets/pt-selectEvent.png)


## 3. Bedingungen hinzufügen

>[!IMPORTANT]
>
>Führen Sie diesen Schritt aus, um Ihrer Regel Bedingungen hinzuzufügen. Überspringen Sie andernfalls zu *Definieren der Aktion* unten.

In diesem Beispiel wird eine Bedingung erstellt, durch die die Regel nur dann Trigger wird, wenn der Name des aktuellen POI gleich **[!UICONTROL Mein POI]**.

1. Unter dem **[!UICONTROL Bedingungen]** Abschnitt, klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Aus dem **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Places Service]**.

1. Aus dem **[!UICONTROL Bedingungstyp]** Dropdown-Liste auswählen **[!UICONTROL Name]**.

1. Geben Sie im rechten Bereich im Textfeld ein. **[!UICONTROL Mein POI]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   ![&quot;set a condition&quot;](/help/assets/pt-setCondition.png)


## 4. Definieren Sie die Aktion

1. Unter dem **[!UICONTROL Aktionen]** Abschnitt, klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Aus dem **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Adobe Analytics]**.

1. Aus dem **[!UICONTROL Aktionstyp]** Dropdown-Liste auswählen **[!UICONTROL Verfolgen]**.

1. Fügen Sie im rechten Bereich die Aktion oder den Status hinzu, die/den Sie an Analytics senden möchten.

   Sie können dieser Anforderung auch zusätzliche Kontextdaten hinzufügen. Denken Sie daran, dass Sie Datenelemente verwenden können, um diese Daten dynamisch vom SDK abzurufen.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

   Im folgenden Beispiel wird eine `TrackAction` wird mit zusätzlichen Kontextdaten von `poi.name` entspricht dem Namen des POI, der dieses Eintrittsereignis ausgelöst hat:

   ![&quot;Aktion festlegen&quot;](/help/assets/pt-setAction.png)

## 5. Speichern Sie die Regel und erstellen Sie die Eigenschaft neu

Überprüfen Sie nach Abschluss der Konfiguration, ob Ihre Regel wie folgt aussieht:

![&quot;Regel wird erstellt&quot;](/help/assets/pt-ruleComplete.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Erstellen Sie Ihre Launch-Eigenschaft neu und stellen Sie sie in der richtigen Umgebung bereit.
