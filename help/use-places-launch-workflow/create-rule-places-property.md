---
title: Erstellen einer Regel für die Eigenschaft "Places Service"
description: Das Places SDK verfolgt den aktuellen Speicherort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---

# Einstiegs- und Ausstiegsregeln erstellen {#create-entry-exit-rules}

Mit der Places-Erweiterung und einer Region-Monitoring-Lösung, die in Ihrer Mobile App installiert ist, können Sie in Adobe Experience Platform Launch Regeln erstellen, die durch Standortdaten ausgelöst oder mit Bedingungen versehen werden, einschließlich Standorteinstiegs- und -ausstiegsereignissen.

## Regeln

Sie können eine Regel konfigurieren, die aus einem Ereignis, einer Bedingung und einer Aktion besteht. Jede Regel besteht aus Folgendem:

* Ein oder mehrere Ereignisse
* (Optional) Bedingungen
* Eine oder mehrere Aktionen

### Places-Dienstereignisse

Places Service bietet die folgenden Ereignisse, für die Sie eine Regel ausführen können:

* **POI eingeben**, der vom Places-SDK ausgelöst wird, wenn Ihr Kunde den von Ihnen konfigurierten POI aufruft.
* **Ausstiegspunkt**, der vom Places-SDK ausgelöst wird, wenn Ihr Kunde den von Ihnen konfigurierten POI beendet.

### Places-Dienstbedingungen

Bedingungen definieren die Kriterien, die die mit dem Ereignis oder dem freigegebenen Status einer Erweiterung in dieser Instanz verknüpften Daten erfüllen müssen, damit die Aktion ausgeführt wird. Beispielsweise können Sie eine Bedingung festlegen, um eine Aktion für einen Eintrag in einen Café nur in San Francisco Trigger.

Das Places SDK behält die folgenden Status bei:

* Aktueller POI, der den POI angibt, an dem sich Ihr Kunde derzeit befindet.
* Letzter ausgenommener POI, der auf den letzten POI verweist, den Ihr Kunde verlassen hat.
* Letzter eingegebener POI, der auf den letzten POI verweist, den Ihr Kunde eingegeben hat.

Jeder POI enthält die folgenden Datenelemente:

* ID
* Name
* Breiten-/Längengrad
* Radius
* Metadaten wie Stadt, Land, Bundesland, Kategorie

### Aktionen

Mit Aktionen wird definiert, was die App als Reaktion auf die Bedingung für die Regel tut, die für das ausgelöste Ereignis erfüllt ist. Wenn Ihr Kunde beispielsweise Ihren POI erreicht, können Sie eine Willkommensnachricht so konfigurieren, dass sie auf seinem Mobilgerät angezeigt wird.

## Erstellen Sie eine Regel: ein Beispiel

>[!CAUTION]
>
>In diesem Beispiel wird davon ausgegangen, dass Sie eine POI-Bibliothek aller Cafés in den USA erstellt haben. Weitere Informationen zum Erstellen von POIs und Bibliotheken finden Sie unter [POI erstellen](/help/poi-mgmt-ui/create-a-poi-ui.md) und *Erstellen einer Bibliothek* in [Verwalten mehrerer Bibliotheken](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

Das folgende Verfahren zeigt, wie Sie eine Regel erstellen, die einen Beitrag an den Slack zurücksendet, wenn Sie in San Francisco einen Café betreten.

Das Ereignis, die Bedingung und die Aktion werden wie folgt definiert:

* **Ereignis**: Places entry event.
* **Bedingung**: Die Stadt für den **aktuellen POI** ist San Francisco.
* **Aktion**: Senden Sie einen Postback an den Slack mit dem Namen des Cafés, den Ihr Kunde eingegeben hat.

### Voraussetzung

Bevor Sie eine Regel erstellen, müssen Sie in Adobe Experience Platform Launch ein Datenelement erstellen. Datenelemente füllen automatisch die erforderlichen Informationen zu Ihrem POI in der Postback-Nachricht aus.

So erstellen Sie ein Datenelement in Experience Platform Launch:

1. Klicken Sie auf **Datenelemente** Registerkarte.
1. Klicken **Datenelement hinzufügen**.
1. Geben Sie einen Namen ein, z. B. **Name des aktuellen Cafés**.
1. Im **Erweiterung** Dropdown-Liste auswählen **Places - Beta**.
1. Wählen Sie unter **Datenelement** die Option **Stadt** aus.
1. Wählen Sie im rechten Bereich **Aktueller POI**.
1. Klicken Sie auf **Speichern**.

### Erstellen einer Regel in Experience Platform Launch für den Places-Dienst

![Erstellen einer Regel](/help/assets/placesrule.png)

1. Klicken Sie in Experience Platform Launch auf den Tab **[!UICONTROL Regeln]**.
1. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.
1. Geben Sie einen Namen für die Regel ein, z. B. **[!UICONTROL Einstieg in den Coffeeshop in SF verfolgen]**.

### Erstellen Sie ein Ereignis

1. Klicken Sie im Abschnitt Ereignisse auf **[!UICONTROL + Hinzufügen]**. Ereignisse bestimmen, wann die Regel ausgelöst werden soll.
1. Im **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Places - Beta]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL POI eingeben]** aus.
1. Geben Sie unter **[!UICONTROL Name]** einen Namen für das Ereignis ein, z. B. **[!UICONTROL Betreten eines Cafés]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Bedingung

1. Klicken Sie im Abschnitt &quot;Bedingungen&quot;auf **[!UICONTROL +Hinzufügen]**. Die Bedingungen bestimmen, welche Kriterien erfüllt sein müssen, damit die Maßnahme durchgeführt wird.
1. Wählen Sie unter **[!UICONTROL Logiktyp]** die Option „Standard“ aus, wodurch Aktionen ausgeführt werden können, wenn die Bedingung erfüllt ist.
1. Im **[!UICONTROL Erweiterung]** Dropdown-Liste auswählen **[!UICONTROL Places - Beta]**.
1. Wählen Sie unter **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Stadt]** aus.
1. Geben Sie einen Bedingungsnamen ein, z. B. **[!UICONTROL Kaffeehaus in SF]**.
1. Klicken Sie im rechten Bereich auf **[!UICONTROL Aktueller POI]** und wählen Sie in der Dropdown-Liste **[!UICONTROL San Francisco]** als eine Ihrer Städte aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Aktion

1. Im **[!UICONTROL Aktionen]** Abschnitt, klicken Sie auf **[!UICONTROL + Hinzufügen]**.
1. Im **[!UICONTROL Erweiterung]** in der Dropdown-Liste beibehalten **[!UICONTROL Mobile Core]** ausgewählt.
1. Wählen Sie einen Aktionstyp aus, z. B. **[!UICONTROL Postback senden]**.

   a. In **[!UICONTROL URL]** Geben Sie die Postback-URL für den Slack ein, z. B. `https://hooks.slack.com/services/`.

   b. Um einen POST-Hauptteil zu senden, wählen Sie die **[!UICONTROL Post-Körper hinzufügen]** aktivieren.

   c. in **[!UICONTROL Post-Körper]** Fügen Sie den Post-Hauptteil hinzu, z. B.: `{ "text": "A customer has entered" }`

   c. Geben Sie einen Inhaltstyp ein, z. B. **[!UICONTROL application/json]**.

   d. Wählen Sie einen Timeout-Wert aus, z. B. **[!UICONTROL 5]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Regel veröffentlichen

1. Um die Regel zu aktivieren, müssen Sie sie veröffentlichen. Weitere Informationen zum Veröffentlichen der Regel in Experience Platform Launch finden Sie unter [Veröffentlichung](https://docs.adobe.com/content/help/de-DE/launch/using/reference/publish/overview.html).

### Denken über Einstiege und Ausstiege hinaus

Die Verwendung von Places Service-Geo-Fence-Einträgen und -Ausstiegen zu Trigger-Regeln in Experience Platform Launch ist unglaublich leistungsstark, Sie können aber auch Standortdaten als Bedingung für andere Ereignisse verwenden. Sie könnten beispielsweise einen Mobile Core-Verfolgungsaktion-Trigger für die Auslösung auf Grundlage eines bestimmten trackAction -Aufruferereignisses in Ihrer App einrichten. Basierend auf diesem Ereignis können Sie dem Ereignis zusätzliche Standortbedingungen zuweisen, bevor eine Aktion ausgeführt wird. Öffnen Sie beispielsweise bei einem Kauf eine In-App-Umfrage `trackAction` -Ereignis eintritt, aber **only** wenn der aktuelle Standort des Benutzers bestimmte Places Service-Metadaten enthält.

![Erstellen einer Bedingung](/help/assets/places-condition.png)
