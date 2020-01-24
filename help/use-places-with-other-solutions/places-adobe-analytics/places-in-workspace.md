---
title: Bericht zu Standortdaten in Analytics Workspace
description: Dieser Abschnitt enthält Informationen zum Erstellen von Berichten zu Standortdaten in Analytics Workspace.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Bericht zu Standortdaten im Analytics Workspace {#places-in-workspace}

Dieses Dokument zeigt ein Beispiel für die Berichterstellung zu Ihren Standortdaten im Arbeitsbereich für Analytics. Jeder Schritt enthält eine Zusammenfassung auf hoher Ebene mit Details, die durch Verweis auf andere Dokumentationsseiten bereitgestellt werden.

## Voraussetzungen 

Dieses Dokument setzt Folgendes voraus:

1. Die Ortserweiterung ist in Ihrer Anwendung implementiert.

   Weitere Informationen zur Implementierung der Plates-Erweiterung finden Sie unter [Platzierungen-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Der Adobe Analytics-Benutzer ist ein Administrator und hat Zugriff auf Verarbeitungsregeln.

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter Übersicht über [Verarbeitungsregeln](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. In der Eigenschaft &quot;Start&quot;wurden Datenelemente für die Variablen des Orts-Dienstes erstellt, die Sie möchten.

   Weitere Informationen zu Datenelementen in Launch finden Sie unter Datenelement [definieren](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Regel zum Starten erstellen

Erstellen Sie eine Regel, die bewirkt, dass das SDK Daten an Analytics sendet, wenn das Gerät einen POI eingibt. Das Erstellen einer solchen Regel wird auf der Seite &quot;POI-Einstiegs- und [Ausstiegsdaten an Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) senden&quot;beschrieben.

In diesem Beispiel sind für die Aktion der Regel die folgenden Werte für die Analytics-Anforderung definiert:

* **[!UICONTROL Action]**wird der Wert**[!UICONTROL Places Entry]**.

* Der Kontextdatenschlüssel **[!UICONTROL poi.name]**wird auf den Wert des Datenelements festgelegt**[!UICONTROL {%%POI Name%%}]**.

![&quot;Aktion festlegen&quot;](/help/assets/pt-setAction.png)

## 2. Erstellen von Analytics-Variablen

Um die Kontextdaten zuzuordnen (gesendet in Schritt 1), müssen zunächst Variablen für die Analytics Report Suite erstellt werden. Weitere Informationen zum Erstellen von Variablen in Analytics finden Sie unter [Konversionsvariablen (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

In diesem Beispiel wurde eine Konversionsvariable **[!UICONTROL Evar2]**erstellt und benannt**[!UICONTROL Places POI Name]**. Für jede Ortsvariable, die Sie in Berichten bereitstellen möchten, müssen zusätzliche Variablen erstellt werden.

![&quot;Analysevariable erstellen&quot;](/help/assets/aa-evar.png)

## 3. Verarbeitungsregeln erstellen

Dieser Schritt ist erforderlich, um Kontextdaten (Schritt 1) Analytics-Variablen zuzuordnen (Schritt 2). For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

In diesem Beispiel wurde eine Verarbeitungsregel erstellt, um den Kontextdatenwert **[!UICONTROL poi.name]**zuzuordnen**[!UICONTROL Places POI Name (eVar2)]**. Für jede erstellte Ortsvariable müssen zusätzliche Verarbeitungsregeln erstellt werden.

![&quot;Verarbeitungsregel erstellen&quot;](/help/assets/aa-processing-rule.png)

## 4. Bericht in Workspace erstellen

Dieser Schritt zeigt einen grundlegenden Bericht in Analytics Workspace, um die in den Schritten 1-3 erfassten Daten anzuzeigen. Weitere Informationen zur Verwendung von Analytics Workspace finden Sie unter Übersicht über [den Arbeitsbereich für Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html).

In diesem Beispiel hat der Bericht die folgenden Einstellungen:

* Metrik - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Action Name]**

   * Unterteilt nach Dimension - **[!UICONTROL Places POI Name]**

![&quot;Bericht im Arbeitsbereich erstellen&quot;](/help/assets/aa-workspace.png)
