---
title: Erstellen einer Regel für die Eigenschaft "Orte-Dienst"
description: 'Das Places SDK verfolgt den aktuellen Speicherort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsdaten für diese POIs. '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---


# Einstiegs- und Ausstiegsregeln erstellen {#create-entry-exit-rules}

Mit der Platzierungserweiterung und den Platzierungsmonitor-Erweiterungen, die in Ihrer Mobilanwendung installiert sind, können Sie in Adobe Experience Platform Launch Regeln erstellen, die ausgelöst oder konditioniert werden, einschließlich Ortseinstiegs- und Ausstiegsregeln.

## Regeln

Sie können eine Regel konfigurieren, die aus einem Ereignis, einer Bedingung und einer Aktion besteht. Jede Regel setzt sich wie folgt zusammen:

* Ein oder mehrere Ereignis
* (Optional) Bedingungen
* Eine oder mehrere Aktionen

### Ereignis des Orts-Dienstes

Platziert Service-Angebot auf den folgenden Ereignissen, auf denen Sie eine Regel ausführen können:

* **Geben Sie POI** ein, das vom Places SDK ausgelöst wird, wenn der Kunde den von Ihnen konfigurierten POI eingibt.
* **Ausstiegspunkt**, der vom Places SDK ausgelöst wird, wenn der Kunde den von Ihnen konfigurierten POI verlässt.

### Bedingungen für die Platzierung von Diensten

Bedingungen definieren die Kriterien, denen die mit dem Ereignis oder dem Freigabestatus einer Erweiterung in diesem Fall verknüpften Daten entsprechen müssen, damit die Aktion durchgeführt werden kann. Sie können beispielsweise festlegen, dass eine Aktion bei einem Eintrag in einen Café nur in San Francisco Trigger wird.

Das Plates SDK behält die folgenden Status bei:

* Aktueller POI, der auf den POI verweist, in dem sich Ihr Kunde derzeit befindet.
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
>In diesem Beispiel wird davon ausgegangen, dass Sie eine POI-Bibliothek aller Cafés in den USA erstellt haben. Weitere Informationen zum Erstellen von POIs und Bibliotheken finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md) und *Erstellen einer Bibliothek* in [Verwalten mehrerer Bibliotheken](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

Das folgende Verfahren ist ein Beispiel dafür, wie eine Regel erstellt wird, die einen Beitrag an den Slack zurücksendet, wenn Sie in einem Café in San Francisco einsteigen.

Ereignis, Bedingung und Aktion werden wie folgt definiert:

* **Ereignis**: Platziert das Ereignis für die Eingabe.
* **Bedingung**: Die Stadt für den **aktuellen POI** ist San Francisco.
* **Aktion**: Senden Sie einen Postback an den Slack den Namen des Coffee Shops, den Ihr Kunde eingegeben hat.

### Voraussetzung

Bevor Sie eine Regel erstellen, müssen Sie ein Datenelement in Adobe Experience Platform Launch erstellen. Datenelemente füllen automatisch die erforderlichen Informationen zu Ihrem POI in der Postback-Nachricht aus.

So erstellen Sie ein Datenelement in Experience Platform Launch:

1. Klicken Sie auf die Registerkarte **Datenelemente**.
1. Klicken Sie auf **Hinzufügen Datenelement**.
1. Geben Sie einen Namen ein, z. B. **Aktueller Coffee Shop-Name**.
1. Wählen Sie in der Dropdown-Liste **Extension** **Places - Beta**.
1. Wählen Sie unter **Datenelement** die Option **Stadt** aus.
1. Wählen Sie im rechten Bereich **Aktuelle POI**.
1. Klicken Sie auf **Speichern**.

### Erstellen einer Regel in Experience Platform Launch für den Ortsvermittlungsdienst

![Erstellen einer Regel](/help/assets/placesrule.png)

1. Klicken Sie in Experience Platform Launch auf den Tab **[!UICONTROL Regeln]**.
1. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.
1. Geben Sie einen Namen für die Regel ein, z. B. **[!UICONTROL Eintrag für Coffee Shop in SF]** verfolgen.

### Erstellen Sie ein Ereignis

1. Klicken Sie im Abschnitt Ereignis auf **[!UICONTROL + Hinzufügen]**. Ereignis bestimmen, wann die Regel ausgelöst werden soll.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Places - Beta]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL POI eingeben]** aus.
1. Geben Sie unter **[!UICONTROL Name]** einen Namen für das Ereignis ein, z. B. **[!UICONTROL Betreten eines Cafés]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Bedingung

1. Klicken Sie im Abschnitt &quot;Bedingungen&quot;auf **[!UICONTROL +Hinzufügen]**. Die Bedingungen bestimmen, welche Kriterien erfüllt sein müssen, damit die Maßnahme durchgeführt werden kann.
1. Wählen Sie unter **[!UICONTROL Logiktyp]** die Option „Standard“ aus, wodurch Aktionen ausgeführt werden können, wenn die Bedingung erfüllt ist.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Extension]** **[!UICONTROL Places - Beta]**.
1. Wählen Sie unter **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Stadt]** aus.
1. Geben Sie einen Bedingungsnamen ein, z. B. **[!UICONTROL Coffee shop in SF]**.
1. Klicken Sie im rechten Bereich auf **[!UICONTROL Aktueller POI]** und wählen Sie in der Dropdown-Liste **[!UICONTROL San Francisco]** als eine Ihrer Städte aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Aktion

1. Klicken Sie im Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL + Hinzufügen]**.
1. Lassen Sie in der Dropdown-Liste **[!UICONTROL Extension]** die Standardoption **[!UICONTROL Mobile Core]** ausgewählt.
1. Wählen Sie einen Aktionstyp aus, z. B. **[!UICONTROL Postback senden]**.

   a. Geben Sie unter **[!UICONTROL URL]** die Postback-URL für den Slack ein, z. B. `https://hooks.slack.com/services/`.

   b. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Hinzufügen Post Body]**, um einen Beitragstext zu senden.

   c. Fügen Sie unter **[!UICONTROL Post Body]** den Post-Body hinzu, z. B.: `{ "text": "A customer has entered" }`

   c. Geben Sie einen Inhaltstyp ein, z. B. **[!UICONTROL application/json]**.

   d. Wählen Sie einen Timeout-Wert aus, z. B. **[!UICONTROL 5]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Regel veröffentlichen

1. Um die Regel zu aktivieren, müssen Sie sie veröffentlichen. Weitere Informationen zum Veröffentlichen der Regel in Experience Platform Launch finden Sie unter [Veröffentlichen](https://docs.adobe.com/content/help/de-DE/launch/using/reference/publish/overview.html).

### Denken über Einstiege und Ausstiege hinaus

Die Verwendung von Orte-Dienst-Geo-Zaun-Einstiegen und Ausstiegen in Trigger-Regeln in Experience Platform Launch ist unglaublich leistungsstark, aber Sie können auch Standortdaten als Bedingung für das Auslösen anderer Ereignis verwenden. Sie könnten beispielsweise einen Ereignis für die Verfolgung von Mobilgeräten mit einem bestimmten trackAction-Aufruf-Ereignis in Ihrer App auslösen. Auf der Grundlage dieses Ereignisses können Sie dem Ereignis vor der Durchführung einer Aktion zusätzliche Standortbedingungen hinzufügen. Öffnen Sie beispielsweise eine In-App-Umfrage, wenn ein Kauf-Ereignis `trackAction` stattfindet, aber **nur**, wenn der aktuelle Speicherort des Benutzers bestimmte Metadaten zum Orte-Dienst enthält.

![eine Bedingung erstellen](/help/assets/places-condition.png)