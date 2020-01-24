---
title: Erstellen einer Regel für die Eigenschaft "Orte-Dienst"
description: 'Das Places SDK verfolgt den aktuellen Standort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs. '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# Einstiegs- und Ausstiegsregeln erstellen {#create-entry-exit-rules}

Mit der Platzierungserweiterung und den Platzierungsmonitor-Erweiterungen, die in Ihrer mobilen Anwendung installiert sind, können Sie Regeln im Adobe Experience Platform Launch erstellen, die ausgelöste oder konditionierte Standortdaten, einschließlich Ortseinstiegs- und Ausstiegsereignissen, ausgelöst werden.

## Regeln

Sie können eine Regel konfigurieren, die aus einem Ereignis, einer Bedingung und einer Aktion besteht. Jede Regel setzt sich wie folgt zusammen:

* Ein oder mehrere Ereignisse
* (Optional) Bedingungen
* Eine oder mehrere Aktionen

### Orts-Dienstereignisse

Der Places Service bietet die folgenden Ereignisse, für die Sie eine Regel ausführen können:

* **Geben Sie POI** ein, das vom Places SDK ausgelöst wird, wenn der Kunde den von Ihnen konfigurierten POI eingibt.
* **Ausstiegspunkt**, der vom Places SDK ausgelöst wird, wenn der Kunde den von Ihnen konfigurierten POI verlässt.

### Bedingungen für die Platzierung von Diensten

Bedingungen definieren die Kriterien, die die mit dem Ereignis oder dem Freigabestatus einer Erweiterung in diesem Fall verknüpften Daten erfüllen müssen, damit die Aktion durchgeführt werden kann. Sie können beispielsweise eine Bedingung festlegen, die eine Aktion auslöst, wenn Sie nur in San Francisco in einem Café einsteigen.

Das Plates SDK behält die folgenden Status bei:

* Aktueller POI, der den POI bezeichnet, in dem sich Ihr Kunde derzeit befindet.
* Letzter ausgesetzter POI, der auf den letzten POI verweist, den Ihr Kunde verlassen hat.
* Zuletzt eingegebene POI, die auf die letzte POI verweist, die Ihr Kunde eingegeben hat.

Jeder POI enthält die folgenden Datenelemente:

* ID
* Name
* Breiten-/Längengrad
* Radius
* Metadaten wie Stadt, Land, Bundesland, Kategorie

### Aktionen

Aktionen definieren, was die App tun wird, wenn die Bedingung für die Regel für das ausgelöste Ereignis erfüllt ist. Wenn Ihr Kunde z. B. Ihren POI eingibt, können Sie eine Begrüßungsnachricht so konfigurieren, dass sie auf seinem Mobilgerät angezeigt wird.

## Regel erstellen: ein Beispiel

>[!CAUTION]
>
>In diesem Beispiel wird davon ausgegangen, dass Sie eine POI-Bibliothek aller Cafés in den USA erstellt haben. For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

Das folgende Verfahren ist ein Beispiel dafür, wie eine Regel erstellt wird, die einen Beitrag zurück an Slack sendet, wenn Sie in einem Café in San Francisco einsteigen.

Das Ereignis, die Bedingung und die Aktion werden wie folgt definiert:

* **Ereignis**: Platziert das Eintragsereignis.
* **Bedingung**: Die Stadt für den **aktuellen POI** ist San Francisco.
* **Aktion**: Senden Sie einen Postback an Slack den Namen des Kaffeehauses, das Ihr Kunde eingegeben hat.

### Voraussetzung

Bevor Sie eine Regel erstellen, müssen Sie ein Datenelement in Adobe Experience Platform Launch erstellen. Datenelemente füllen automatisch die erforderlichen Informationen zu Ihrem POI in der Postback-Nachricht aus.

So erstellen Sie ein Datenelement beim Start der Experience Platform:

1. Klicken Sie auf die Registerkarte **Datenelemente** .
1. Click **Add Data Element**.
1. Geben Sie einen Namen ein, z. B. &quot; **Aktueller Coffee Shop-Name**&quot;.
1. Wählen Sie in der Dropdownliste **Erweiterung** die Option **Orte - Beta**.
1. Wählen Sie unter **Datenelement** die Option **Stadt** aus.
1. Wählen Sie im rechten Bereich die Option **Aktueller POI**.
1. Klicken Sie auf **Speichern**.

### Regel im Experience Platform Launch for Places-Dienst erstellen

![eine Regel erstellen](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]**tab.
1. Klicken Sie auf **[!UICONTROL Add Rule]**.
1. Geben Sie beispielsweise einen Namen für die Regel ein **[!UICONTROL Track entry for coffee shop in SF]**.

### Erstellen Sie ein Ereignis

1. Klicken Sie im Abschnitt Ereignisse auf **[!UICONTROL + Add]**. Ereignisse bestimmen, wann die Regel ausgelöst werden soll.
1. Wählen Sie in der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Places – Beta]**.
1. Wählen Sie in der **[!UICONTROL Event Type]**Dropdownliste**[!UICONTROL Enter POI]**.
1. Geben Sie **[!UICONTROL Name]**in einen Namen für das Ereignis ein, z. B.**[!UICONTROL Entering a coffee shop]**.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

### Erstellen einer Bedingung

1. Klicken Sie im Abschnitt Bedingungen auf **[!UICONTROL +Add]**. Die Bedingungen bestimmen, welche Kriterien erfüllt sein müssen, damit die Maßnahme durchgeführt werden kann.
1. In **[!UICONTROL Logic Type]**, select Regular, which allows actions to execute if the condition is met.
1. Wählen Sie in der **[!UICONTROL Extension]**Dropdownliste**[!UICONTROL Places – Beta]**.
1. Wählen Sie **[!UICONTROL Condition Type]**in**[!UICONTROL City]**.
1. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select**[!UICONTROL San Francisco]** as one of your cities.
1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

### Erstellen einer Aktion

1. In the **[!UICONTROL Actions]**section, click**[!UICONTROL + Add]**.
1. Lassen Sie in der **[!UICONTROL Extension]**Dropdownliste die Standardoption**[!UICONTROL Mobile Core]** ausgewählt.
1. Wählen Sie beispielsweise einen Aktionstyp **[!UICONTROL Send Postback]**.

   a. Geben Sie in **[!UICONTROL URL]**die Postback-URL für &quot;Slack&quot;ein, z. B.`https://hooks.slack.com/services/`.

   b. Aktivieren Sie das **[!UICONTROL Add Post Body]**Kontrollkästchen, um einen Beitragstext zu senden.

   c. Fügen Sie in **[!UICONTROL Post Body]**der Liste den Text des Beitrags hinzu, z. B.:`{ "text": "A customer has entered" }`

   c. Geben Sie beispielsweise einen Inhaltstyp ein **[!UICONTROL application/json]**.

   d. Wählen Sie beispielsweise einen Timeout-Wert **[!UICONTROL 5]**.

1. Klicken Sie auf **[!UICONTROL Keep Changes]**.

### Regel veröffentlichen

1. Um die Regel zu aktivieren, müssen Sie sie veröffentlichen. Weitere Informationen zum Veröffentlichen der Regel beim Start der Experience Platform finden Sie unter [Veröffentlichen](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Denken über Einstiege und Ausstiege hinaus

Die Verwendung von Orts-Dienst-Geo-Zaun-Einträgen und -Ausstiegen zum Auslösen von Regeln in Experience Platform Launch ist unglaublich leistungsstark, aber Sie können auch Standortdaten als Bedingung für das Auslösen anderer Ereignisse verwenden. Beispielsweise könnte ein Ereignis für die Verfolgung der Mobilgeräte-Core-Aktion ausgelöst werden, das basierend auf einem bestimmten trackAction-Aufrufereignis in Ihrer App ausgelöst werden kann. Auf der Grundlage dieses Ereignisses können Sie dem Ereignis vor Durchführung einer Aktion zusätzliche Positionsbedingungen hinzufügen. Öffnen Sie beispielsweise eine In-App-Umfrage, wenn ein Kaufereignis `trackAction` eintritt, jedoch **nur** , wenn der aktuelle Speicherort des Benutzers bestimmte Metadaten zum Orte-Dienst enthält.

![Bedingung erstellen](/help/assets/places-condition.png)