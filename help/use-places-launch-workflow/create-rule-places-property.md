---
title: Erstellen einer Regel für die Eigenschaft "Places Service"
description: Das Places SDK verfolgt den aktuellen Speicherort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 14%

---

# Einstiegs- und Ausstiegsregeln erstellen {#create-entry-exit-rules}

Mit der Places-Erweiterung und einer Region-Monitoring-Lösung, die in Ihrer Mobile App installiert ist, können Sie in Adobe Experience Platform Launch Regeln erstellen, die durch Standortdaten ausgelöst oder mit Bedingungen versehen werden, einschließlich Standorteinstiegs- und -ausstiegsereignissen.

## Regeln

Sie können eine Regel konfigurieren, die aus einem Ereignis, einer Bedingung und einer Aktion besteht. Jede Regel setzt sich aus Folgendem zusammen:

* Ein oder mehrere Ereignisse
* (Optional) Bedingungen
* Eine oder mehrere Aktionen

### Places-Dienstereignisse

Places Service bietet die folgenden Ereignisse, für die Sie eine Regel ausführen können:

* **Geben Sie POI** ein, der vom Places-SDK ausgelöst wird, wenn Ihr Kunde den von Ihnen konfigurierten POI betritt.
* **POI beenden**, der vom Places-SDK ausgelöst wird, wenn Ihr Kunde den von Ihnen konfigurierten POI beendet.

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

## Erstellen einer Regel: ein Beispiel

>[!CAUTION]
>
>In diesem Beispiel wird davon ausgegangen, dass Sie eine POI-Bibliothek aller Cafés in den USA erstellt haben. Weitere Informationen zum Erstellen von POIs und Bibliotheken finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md) und *Erstellen einer Bibliothek* in [Verwalten mehrerer Bibliotheken](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

Das folgende Verfahren ist ein Beispiel dafür, wie eine Regel erstellt wird, die einen Beitrag an die Slack sendet, wenn Sie in einem Café in San Francisco einsteigen.

Das Ereignis, die Bedingung und die Aktion werden wie folgt definiert:

* **Ereignis**: Places entry event.
* **Bedingung**: Die Stadt für den **aktuellen POI** ist San Francisco.
* **Aktion**: Senden Sie einen Postback an die Slack mit dem Namen des Cafés, den Ihr Kunde eingegeben hat.

### Voraussetzung

Bevor Sie eine Regel erstellen, müssen Sie in Adobe Experience Platform Launch ein Datenelement erstellen. Datenelemente füllen automatisch die erforderlichen Informationen zu Ihrem POI in der Postback-Nachricht aus.

So erstellen Sie ein Datenelement unter Experience Platform Launch:

1. Klicken Sie auf die Registerkarte **Datenelemente**.
1. Klicken Sie auf **Datenelement hinzufügen**.
1. Geben Sie einen Namen ein, z. B. **Name des aktuellen Cafés**.
1. Wählen Sie in der Dropdownliste **Erweiterung** die Option **Orte - Beta** aus.
1. Wählen Sie unter **Datenelement** die Option **Stadt** aus.
1. Wählen Sie im rechten Bereich **Aktueller POI** aus.
1. Klicken Sie auf **Speichern**.

### Erstellen einer Regel im Experience Platform Launch für den Places-Dienst

![ Erstellen einer Regel](/help/assets/placesrule.png)

1. Klicken Sie in Experience Platform Launch auf den Tab **[!UICONTROL Regeln]**.
1. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.
1. Geben Sie einen Namen für die Regel ein, z. B. **[!UICONTROL Eintrag für den Coffeeshop in SF]**.

### Erstellen eines Ereignisses

1. Klicken Sie im Abschnitt &quot;Ereignisse&quot;auf **[!UICONTROL + Hinzufügen]**. Ereignisse bestimmen, wann die Regel ausgelöst werden soll.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Orte - Beta]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL POI eingeben]** aus.
1. Geben Sie unter **[!UICONTROL Name]** einen Namen für das Ereignis ein, z. B. **[!UICONTROL Betreten eines Cafés]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Bedingung

1. Klicken Sie im Abschnitt &quot;Bedingungen&quot;auf **[!UICONTROL +Add]**. Die Bedingungen bestimmen, welche Kriterien erfüllt sein müssen, damit die Maßnahme durchgeführt wird.
1. Wählen Sie unter **[!UICONTROL Logiktyp]** die Option „Standard“ aus, wodurch Aktionen ausgeführt werden können, wenn die Bedingung erfüllt ist.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Erweiterung]** die Option **[!UICONTROL Orte - Beta]** aus.
1. Wählen Sie unter **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Stadt]** aus.
1. Geben Sie einen Bedingungsnamen ein, z. B. **[!UICONTROL Café in SF]**.
1. Klicken Sie im rechten Bereich auf **[!UICONTROL Aktueller POI]** und wählen Sie in der Dropdown-Liste **[!UICONTROL San Francisco]** als eine Ihrer Städte aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Aktion

1. Klicken Sie im Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL + Hinzufügen]**.
1. Behalten Sie in der Dropdownliste **[!UICONTROL Erweiterung]** die Standardoption **[!UICONTROL Mobile Core]** bei.
1. Wählen Sie einen Aktionstyp aus, z. B. **[!UICONTROL Postback senden]**.

   a. Geben Sie in **[!UICONTROL URL]** die Postback-URL für Slack ein, z. B. `https://hooks.slack.com/services/`.

   b. Um einen POST-Hauptteil zu senden, aktivieren Sie das Kontrollkästchen **[!UICONTROL Post-Hauptteil hinzufügen]** .

   c. Fügen Sie in **[!UICONTROL Post-Hauptteil]** den POST-Hauptteil hinzu, z. B.: `{ "text": "A customer has entered" }`

   c. Geben Sie einen Inhaltstyp ein, z. B. **[!UICONTROL application/json]**.

   d. Wählen Sie einen Timeout-Wert aus, z. B. **[!UICONTROL 5]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Publish the rule

1. Um die Regel zu aktivieren, müssen Sie sie veröffentlichen. Weitere Informationen zum Veröffentlichen der Regel auf Experience Platform Launch finden Sie unter [Veröffentlichen](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html).

### Denken über Einstiege und Ausstiege hinaus

Die Verwendung von Places Service Geo-Fence-Einträgen und -Ausstiegen zu Trigger-Regeln in Experience Platform Launch ist unglaublich leistungsstark, aber Sie können auch Standortdaten als Bedingung für andere Ereignisse verwenden. Sie könnten beispielsweise einen Mobile Core-Verfolgungsaktion-Trigger für die Auslösung auf Grundlage eines bestimmten trackAction -Aufruferereignisses in Ihrer App einrichten. Basierend auf diesem Ereignis können Sie dem Ereignis zusätzliche Standortbedingungen zuweisen, bevor eine Aktion ausgeführt wird. Öffnen Sie beispielsweise eine In-App-Umfrage, wenn ein Kauf- `trackAction` -Ereignis auftritt, aber **nur**, wenn der aktuelle Standort des Benutzers bestimmte Places Service-Metadaten enthält.

![Erstellen einer Bedingung](/help/assets/places-condition.png)
