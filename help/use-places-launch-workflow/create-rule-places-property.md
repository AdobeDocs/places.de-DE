---
title: Erstellen einer Regel für Ihre Places Service-Eigenschaft
description: Die Places SDK verfolgt den aktuellen Speicherort, überwacht die konfigurierten POIs um den aktuellen Speicherort und verfolgt die Ein- und Ausstiegsereignisse für diese POIs.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 14%

---

# Erstellen von Ein- und Ausstiegsregeln {#create-entry-exit-rules}

Wenn die Places-Erweiterung und eine Lösung zur Regionsüberwachung in Ihrer Mobile App installiert sind, können Sie in Adobe Experience Platform Launch Regeln erstellen, die ausgelöst oder durch Standortdaten bedingt werden, einschließlich Standorteintritts- und -austrittsereignissen.

## Regeln

Sie können eine Regel konfigurieren, die aus einem Ereignis, einer Bedingung und einer Aktion besteht. Jede Regel setzt sich wie folgt zusammen:

* Ein oder mehrere Ereignisse
* (Optional) Bedingungen
* Eine oder mehrere Aktionen

### Places Service-Ereignisse

Places Service bietet die folgenden Ereignisse, für die Sie eine Regel ausführen können:

* **POI eingeben** wird durch die Places SDK ausgelöst, wenn Ihr Kunde den von Ihnen konfigurierten POI aufruft.
* **POI „Beenden**, der von der Places SDK ausgelöst wird, wenn Ihr Kunde den konfigurierten POI verlässt.

### Places Service-Bedingungen

Bedingungen definieren die Kriterien, die die mit dem Ereignis verknüpften Daten oder der freigegebene Status einer Erweiterung in dieser Instanz erfüllen müssen, damit die Aktion durchgeführt wird. Sie können beispielsweise eine Bedingung festlegen, um eine Aktion bei einem Eintritt in ein Café nur in der Stadt San Francisco Trigger.

Die Places SDK behält die folgenden Status bei:

* Aktueller POI, der sich auf den POI bezieht, in dem sich Ihr Kunde derzeit befindet.
* POI „Zuletzt beendet“, der sich auf den letzten POI bezieht, den Ihr Kunde verlassen hat.
* POI des letzten Eintritts, der sich auf den letzten POI bezieht, den Ihr Kunde eingegeben hat.

Jeder POI enthält die folgenden Datenelemente:

* ID
* Name
* Breitengrad/Längengrad
* Radius
* Metadaten wie Stadt, Land, Bundesland, Kategorie

### Aktionen

Aktionen definieren, was die App als Reaktion auf die Bedingung tun wird, dass die Regel für das ausgelöste Ereignis erfüllt ist. Wenn Ihre Kundin oder Ihr Kunde beispielsweise Ihren POI eingibt, können Sie eine Begrüßungsnachricht konfigurieren, die auf dem Mobilgerät der Kundin bzw. des Kunden angezeigt werden soll.

## Erstellen einer Regel: Beispiel

>[!CAUTION]
>
>In diesem Beispiel wird davon ausgegangen, dass Sie eine POI-Bibliothek aller Cafés in den USA erstellt haben. Weitere Informationen zum Erstellen von POIs und Bibliotheken finden Sie unter [Erstellen eines POI](/help/poi-mgmt-ui/create-a-poi-ui.md) und *Erstellen einer Bibliothek* in [Verwalten mehrerer Bibliotheken](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html?lang=de).

Das folgende Verfahren ist ein Beispiel für die Erstellung einer Regel, die einen Beitrag zurück an Slack sendet, wenn Sie ein Café in San Francisco betreten.

Ereignis, Bedingung und Aktion werden wie folgt definiert:

* **Event**: Platziert Eintrittsereignis.
* **Bedingung**: Die Stadt für den **aktuellen POI** ist San Francisco.
* **Action**: Senden Sie ein Postback an Slack, um den Namen des Coffee Shops zu erhalten, den Ihr Kunde betreten hat.

### Voraussetzung

Bevor Sie eine Regel erstellen, müssen Sie ein Datenelement in Adobe Experience Platform Launch erstellen. Datenelemente füllen automatisch die erforderlichen Informationen zu Ihrem POI in der Postback-Nachricht aus.

So erstellen Sie ein Datenelement im Experience Platform Launch:

1. Klicken Sie auf **Registerkarte** Datenelemente“.
1. Klicken Sie **Datenelement hinzufügen**.
1. Geben Sie einen Namen ein, z. B **„Aktueller Coffee Shop-Name**.
1. Wählen **in der Dropdown** Liste „Erweiterung“ die Option **Places - Beta**.
1. Wählen Sie unter **Datenelement** die Option **Stadt** aus.
1. Wählen Sie im rechten Bereich die Option **Aktueller POI**.
1. Klicken Sie auf **Speichern**.

### Erstellen einer Regel auf Experience Platform Launch für Places Service

![Erstellen einer Regel](/help/assets/placesrule.png)

1. Klicken Sie in Experience Platform Launch auf den Tab **[!UICONTROL Regeln]**.
1. Klicken Sie **[!UICONTROL Regel hinzufügen]**.
1. Geben Sie einen Namen für die Regel ein, z. B **[!UICONTROL „Eintrag für Coffee Shop in SF verfolgen]**.

### Erstellen eines Ereignisses

1. Klicken Sie im Abschnitt Ereignisse auf **[!UICONTROL + Hinzufügen]**. Ereignisse bestimmen, wann die Regel ausgelöst werden soll.
1. Wählen **[!UICONTROL in der Dropdown]** Liste „Erweiterung“ die Option **[!UICONTROL Places - Beta]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL POI eingeben]** aus.
1. Geben Sie unter **[!UICONTROL Name]** einen Namen für das Ereignis ein, z. B. **[!UICONTROL Betreten eines Cafés]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Bedingung

1. Klicken Sie im Abschnitt Bedingungen auf **[!UICONTROL +Hinzufügen]**. Bedingungen bestimmen, welche Kriterien erfüllt sein müssen, damit eine Maßnahme ergriffen wird.
1. Wählen Sie unter **[!UICONTROL Logiktyp]** die Option „Standard“ aus, wodurch Aktionen ausgeführt werden können, wenn die Bedingung erfüllt ist.
1. Wählen **[!UICONTROL in der Dropdown]** Liste „Erweiterung“ die Option **[!UICONTROL Places - Beta]**.
1. Wählen Sie unter **[!UICONTROL Bedingungstyp]** die Option **[!UICONTROL Stadt]** aus.
1. Geben Sie einen Bedingungsnamen ein, z. B **[!UICONTROL „Café in SF]**.
1. Klicken Sie im rechten Bereich auf **[!UICONTROL Aktueller POI]** und wählen Sie in der Dropdown-Liste **[!UICONTROL San Francisco]** als eine Ihrer Städte aus.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Erstellen einer Aktion

1. Klicken Sie **[!UICONTROL Abschnitt]** Aktionen“ auf **[!UICONTROL + Hinzufügen]**.
1. Lassen Sie in **[!UICONTROL Dropdown-Liste]** Erweiterung“ die Standardoption **[!UICONTROL Mobile Core]** ausgewählt.
1. Wählen Sie einen Aktionstyp aus, z. B **[!UICONTROL „Postback senden]**.

   a. **[!UICONTROL Sie unter „URL]** die Postback-URL für das Slack ein, z. B. `https://hooks.slack.com/services/`.

   b. Um einen Beitragstext zu senden, aktivieren Sie das **[!UICONTROL Beitragstext hinzufügen]**.

   c. Fügen Sie **[!UICONTROL POST-]**) den POST-Textkörper hinzu, z. B.: `{ "text": "A customer has entered" }`

   c. Geben Sie einen Inhaltstyp ein, z. B **[!UICONTROL „application/json]**.

   d. Wählen Sie einen Zeitüberschreitungswert, z. B. **[!UICONTROL 5]**.

1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

### Publish - die Regel

1. Um die Regel zu aktivieren, müssen Sie sie veröffentlichen. Weitere Informationen zum Veröffentlichen der Regel auf Experience Platform Launch finden Sie unter [Veröffentlichen](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=de).

### Über Ein- und Austritte hinaus denken

Die Verwendung von Places Service-Geofencing-Einträgen und -Ausgängen für Ereignisregeln in Experience Platform Launch ist unglaublich leistungsstark, aber Sie können auch Standortdaten als Bedingung verwenden, damit andere Trigger ausgelöst werden. Sie könnten beispielsweise einen Mobile Core Track Action-Ereignisereignis-Trigger bereit haben, der basierend auf einem bestimmten trackAction-Aufrufereignis in Ihrer App ausgelöst wird. Basierend auf diesem Ereignis können Sie zusätzliche Standortbedingungen für das Ereignis platzieren, bevor eine Aktion ausgeführt wird. Öffnen Sie beispielsweise eine In-App-Umfrage, wenn ein Kaufereignis `trackAction`, aber **nur** wenn der aktuelle Standort des Benutzers bestimmte Places Service-Metadaten enthält.

![Bedingung erstellen](/help/assets/places-condition.png)
