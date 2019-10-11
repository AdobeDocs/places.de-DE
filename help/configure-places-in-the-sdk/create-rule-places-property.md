---
title: Erstellen einer Regel für Ihre Places-Eigenschaft
seo-title: Erstellen einer Regel für Ihre Places-Eigenschaft
description: 'Das Places SDK verfolgt den aktuellen Standort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs. '
seo-description: 'Das Places SDK verfolgt den aktuellen Standort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs. '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Regel für die Eigenschaft "Orte"erstellen {#creating-rule-places-property}

Das Location Service SDK verfolgt den aktuellen Standort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs.

## Regeln

Sie können eine Regel konfigurieren, die aus einem Ereignis, einer Bedingung und einer Aktion besteht. Jede Regel setzt sich wie folgt zusammen:

* Ein oder mehrere Ereignisse
* (Optional) Bedingungen
* Eine oder mehrere Aktionen

### Ereignisse

Orte bieten die folgenden Ereignisse, für die Sie eine Regel ausführen können:

* **[!UICONTROL Enter POI]**, der vom Places SDK ausgelöst wird, wenn der Kunde den von Ihnen konfigurierten POI eingibt.
* **[!UICONTROL Exit POI]**, der vom Places SDK ausgelöst wird, wenn der von Ihnen konfigurierte POI von Ihrem Kunden verlassen wird.

### Bedingungen

Bedingungen definieren die Kriterien, die die mit dem Ereignis oder dem Freigabestatus einer Erweiterung in diesem Fall verknüpften Daten erfüllen müssen, damit die Aktion durchgeführt werden kann. Sie können beispielsweise eine Bedingung festlegen, die eine Aktion auslöst, wenn Sie nur in San Francisco in einem Café einsteigen.

Das Location Service SDK behält die folgenden Status bei:

* Aktueller POI, der den POI bezeichnet, in dem sich Ihr Kunde derzeit befindet.
* Letzter ausgesetzter POI, der auf den letzten POI verweist, den Ihr Kunde verlassen hat.
* Zuletzt eingegebene POI, die auf die letzte POI verweist, die Ihr Kunde eingegeben hat.

Jeder POI enthält die folgenden Datenelemente:

* ID
* Name:
* Breiten-/Längengrad
* Radius
* Metadaten wie Stadt, Land, Bundesland, Kategorie

### Aktionen

Aktionen definieren, was die App tun wird, wenn die Bedingung für die Regel für das ausgelöste Ereignis erfüllt ist. Wenn Ihr Kunde z. B. Ihren POI eingibt, können Sie eine Begrüßungsnachricht so konfigurieren, dass sie auf seinem Mobilgerät angezeigt wird.

## Regel erstellen: ein Beispiel

>[!CAUTION]
>
>In diesem Beispiel wird davon ausgegangen, dass Sie eine POI-Bibliothek aller Kaffeehäuser in den USA erstellt haben. Weitere Informationen zum Erstellen von POIs und Bibliotheken finden Sie unter [Erstellen eines POI](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/managing-pois-in-the-places-ui#create-a-poi) und [Erstellen einer Bibliothek](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/manage-libraries#create-a-library).

Das folgende Verfahren ist ein Beispiel dafür, wie eine Regel erstellt wird, die einen Beitrag zurück an Slack sendet, wenn Sie in einem Café in San Francisco einsteigen.

Das Ereignis, die Bedingung und die Aktion werden wie folgt definiert:

* **Ereignis**: Einstiegsereignis für den Location Service.
* **Bedingung**: Ort für den **aktuellen POI** ist San Francisco
* **Aktion**: Senden Sie einen Postback an Slack den Namen des Kaffeehauses, das Ihr Kunde eingegeben hat.

### Voraussetzung

Bevor Sie eine Regel erstellen, müssen Sie ein Datenelement in Experience Platform Launch erstellen. Datenelemente füllen automatisch die erforderlichen Informationen zu Ihrem POI in der Postback-Nachricht aus.

So erstellen Sie ein Datenelement beim Start der Experience Platform:

1. Click the **[!UICONTROL Data Elements]** tab.
2. Klicken Sie auf **[!UICONTROL Add Data Element]**.
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. Wählen Sie in der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Places – Beta]**.
5. Wählen Sie **[!UICONTROL Data Element]** in **[!UICONTROL City]**.
6. Wählen Sie im rechten Bereich die Option **Aktueller POI**.
7. Klicken Sie auf **[!UICONTROL Save]**.

### Regel im Experience Platform Launch für Location Service erstellen

![](//help/assets/create-a-rule.png)

1. Klicken Sie in Experience Platform Launch auf die **[!UICONTROL Rules]** Registerkarte.
2. Klicken Sie auf **Regel hinzufügen**.
3. Geben Sie einen Namen für die Regel ein, z. B. **Track Eintrag für Café in SF**.

### Erstellen Sie ein Ereignis

1. Klicken Sie im Abschnitt Ereignisse auf **[!UICONTROL + Add]**. Ereignisse bestimmen, wann die Regel ausgelöst werden soll.
2. Wählen Sie in der **[!UICONTROL Extension]** Dropdownliste **[!UICONTROL Places – Beta]**.
3. Wählen Sie in der **[!UICONTROL Event Type]** Dropdownliste **[!UICONTROL Enter POI]**.
4. Geben Sie **[!UICONTROL Name]** in einen Namen für das Ereignis ein, z. B. **[!UICONTROL Entering a coffee shop]**.
5. Klicken Sie auf **[!UICONTROL Keep Changes]**.

### Erstellen einer Bedingung

1. Klicken Sie im Abschnitt Bedingungen auf **[!UICONTROL +Add]**. Die Bedingungen bestimmen, welche Kriterien erfüllt sein müssen, damit die Maßnahme durchgeführt werden kann.
2. Wählen Sie **[!UICONTROL Logic Type]** Regular, was die Ausführung von Aktionen erlaubt, wenn die Bedingung erfüllt ist.
3. Wählen Sie in der Dropdownliste **Erweiterung** die Option **[!UICONTROL Places – Beta]**.
4. Wählen Sie **[!UICONTROL Condition Type]** in **[!UICONTROL City]**.
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. Klicken Sie im rechten Bereich auf **[!UICONTROL Current POI]** und wählen Sie in der Dropdownliste **[!UICONTROL San Francisco]** eine Ihrer Städte aus.
7. Klicken Sie auf **[!UICONTROL Keep Changes]**.

### Erstellen einer Aktion

1. Klicken Sie im **[!UICONTROL Actions]** Abschnitt auf **[!UICONTRO+ Hinzufügen]**.
2. Lassen Sie in der Dropdownliste **[!UICONTRO Erweiterung]** die standardmäßige Option **[!UICONTRO Mobile Core]** ausgewählt.
3. Wählen Sie einen Aktionstyp, z. B. "Postback **[!UICONTRO senden"]**.

   a. Geben Sie in **[!UICONTROL URL]** die Postback-URL für "Slack"ein, z. B. `https://hooks.slack.com/services/`.

   b. Aktivieren Sie das Kontrollkästchen " **[!UICONTRO Beitragstext]** hinzufügen", um einen Beitragstext zu senden.

   c. Fügen Sie im **[!UICONTRO Beitragstext]** beispielsweise den Beitragstext hinzu: `{ "text": "A customer has entered" }`

   c. Geben Sie einen Inhaltstyp ein, z. B. **[!UICONTRO application/json]**.

   d. Wählen Sie einen Timeout-Wert, z. B. **5**.

4. Click **[!UICONTRO Keep Changes]**.

### Regel veröffentlichen

1. Um die Regel zu aktivieren, müssen Sie sie veröffentlichen. Weitere Informationen zum Veröffentlichen der Regel beim Start der Experience Platform finden Sie unter [Veröffentlichen](https://docs.adobelaunch.com/launch-reference/publishing).