---
title: Bericht zu Standortdaten in Analytics Workspace
description: Dieser Abschnitt enthält Informationen zum Erstellen von Berichten zu Standortdaten in Analytics Workspace.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---


# Bericht zu Standortdaten im Analytics Workspace {#places-in-workspace}

Dieses Dokument zeigt ein Beispiel dafür, wie Sie Berichte zu Ihren Standortdaten im Analytics Workspace erstellen. Jeder Schritt enthält eine Zusammenfassung auf hoher Ebene mit Details, die durch Verweisen auf andere Dokumentationsseiten bereitgestellt werden.

## Voraussetzungen

Dieses Dokument setzt Folgendes voraus:

1. Die Ortserweiterung ist in Ihrer Anwendung implementiert.

   Weitere Informationen zur Implementierung der Plates-Erweiterung finden Sie unter [Platzierungen-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Der Adobe Analytics-Benutzer ist Administrator und hat Zugriff auf Verarbeitungsregeln.

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter Übersicht über [Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. In der Eigenschaft &quot;Start&quot;wurden Datenelemente für die Variablen des Orts-Dienstes erstellt, die Sie verwenden möchten.

   Weitere Informationen zu Datenelementen in Launch finden Sie unter [Datenelement](/help/use-places-launch-workflow/define-data-elements.md) definieren.


## 1. Regel zum Starten erstellen

Erstellen Sie eine Regel, die bewirkt, dass das SDK Daten an Analytics sendet, wenn das Gerät einen POI eingibt. Das Erstellen dieser Regel wird auf der Seite [POI-Einstiegs- und -Ausstiegsdaten an Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) beschrieben.

In diesem Beispiel sind für die Aktion der Regel die folgenden Werte für die Analytics-Anforderung definiert:

* **[!UICONTROL Die]** Aktion enthält den Wert  **[!UICONTROL Ortseinstieg]**.

* Der Kontextdatenschlüssel **[!UICONTROL poi.name]** ist auf den Wert des Datenelements **[!UICONTROL {%%POI Name%}]** eingestellt.

![&quot;Aktion festlegen&quot;](/help/assets/pt-setAction.png)

## 2. Erstellen von Analytics-Variablen

Um die Kontextdaten zuzuordnen (gesendet in Schritt 1), müssen zunächst Variablen für die Analytics Report Suite erstellt werden. Weitere Informationen zum Erstellen von Variablen in Analytics finden Sie unter [Konversionsvariablen (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

In diesem Beispiel wurde eine Konversionsvariable mit dem Namen **[!UICONTROL eVar2]** erstellt und mit dem Namen **[!UICONTROL Orte POI-Name]** benannt. Für jede Ortsvariable, die Sie in Berichte bereitstellen möchten, müssen zusätzliche Variablen erstellt werden.

![&quot;Eine Analytics-Variable erstellen&quot;](/help/assets/aa-evar.png)

## 3. Verarbeitungsregeln erstellen

Dieser Schritt ist erforderlich, um Kontextdaten (Schritt 1) Analytics-Variablen zuzuordnen (Schritt 2). Weitere Informationen zum Erstellen von Verarbeitungsregeln finden Sie unter [Übersicht über Verarbeitungsregeln](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

In diesem Beispiel wurde eine Verarbeitungsregel erstellt, um den Kontextdatenwert **[!UICONTROL poi.name]** dem **[!UICONTROL Orte POI-Namen (eVar2)]** zuzuordnen. Für jede erstellte Ortsvariable müssen zusätzliche Verarbeitungsregeln erstellt werden.

![&quot;Verarbeitungsregel erstellen&quot;](/help/assets/aa-processing-rule.png)

## 4. Erstellen eines Berichts in Workspace

Dieser Schritt zeigt einen Basisbericht in Analytics Workspace zur Ansicht der in den Schritten 1-3 erfassten Daten. Weitere Informationen zur Verwendung von Analytics Workspace finden Sie unter [Übersicht über Analytics Workspace](https://docs.adobe.com/content/help/de-DE/analytics/analyze/analysis-workspace/home.html).

In diesem Beispiel hat der Bericht die folgenden Einstellungen:

* Metrik - **[!UICONTROL Vorfälle]**

* Dimension - **[!UICONTROL Aktionsname]**

   * Unterteilt nach Dimension - **[!UICONTROL Orte POI-Name]**

![&quot;Bericht im Arbeitsbereich erstellen&quot;](/help/assets/aa-workspace.png)
