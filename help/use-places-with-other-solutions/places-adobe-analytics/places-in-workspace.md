---
title: Bericht zu Standortdaten in Analytics Workspace
description: Dieser Abschnitt enthält Informationen zum Reporting von Standortdaten in Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---

# Bericht zu Standortdaten in Analytics Workspace {#places-in-workspace}

Dieses Dokument zeigt ein Beispiel für die Berichterstellung zu Ihren Standortdaten in Analytics Workspace. Jeder Schritt enthält eine allgemeine Zusammenfassung mit Details, die durch Verweise auf andere Dokumentationsseiten bereitgestellt werden.

## Voraussetzungen

In diesem Dokument wird von Folgendem ausgegangen:

1. Die Places-Erweiterung ist in Ihrer Anwendung implementiert.

   Weitere Informationen zur Implementierung der Places-Erweiterung finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Der Adobe Analytics-Benutzer ist ein Administrator und hat Zugriff auf Verarbeitungsregeln.

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter Übersicht über [Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. In der Launch-Eigenschaft wurden Datenelemente für die gewünschten Places-Dienst-Variablen erstellt.

   Weitere Informationen zu Datenelementen in Launch finden Sie unter [Datenelement definieren](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Erstellen einer Launch-Regel

Erstellen Sie eine Regel, die dazu führt, dass das SDK Daten an Analytics sendet, wenn das Gerät einen POI aufruft. Das Erstellen dieser Art von Regel wird im Abschnitt [POI-Einstiegs- und -Ausstiegsdaten an Analytics senden](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) Seite.

In diesem Beispiel hat die Aktion der Regel die folgenden Werte, die für die Analytics-Anforderung definiert sind:

* **[!UICONTROL Aktion]** wird ein Wert von **[!UICONTROL Places Entry]**.

* Der Kontextdatenschlüssel **[!UICONTROL poi.name]** auf den Wert des Datenelements eingestellt ist **[!UICONTROL {%%POI Name%%}]**.

![&quot;Aktion festlegen&quot;](/help/assets/pt-setAction.png)

## 2. Erstellen von Analytics-Variablen

Um die Kontextdaten zuzuordnen (gesendet in Schritt 1), müssen zunächst Variablen für die Analytics Report Suite erstellt werden. Weitere Informationen zum Erstellen von Variablen in Analytics finden Sie unter [Konversionsvariablen (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

In diesem Beispiel wird eine Konversionsvariable **[!UICONTROL eVar2]**, erstellt und benannt wurde **[!UICONTROL Places POI Name]**. Für jede Standortvariable, die Sie in Berichten verfügbar machen möchten, müssen zusätzliche Variablen erstellt werden.

![&quot;create an analytics variable&quot;](/help/assets/aa-evar.png)

## 3. Erstellen von Verarbeitungsregeln

Dieser Schritt ist erforderlich, um Kontextdaten (Schritt 1) Analytics-Variablen (Schritt 2) zuzuordnen. Weitere Informationen zum Erstellen von Verarbeitungsregeln finden Sie unter [Übersicht über Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

In diesem Beispiel wurde eine Verarbeitungsregel erstellt, um den Kontextdatenwert zuzuordnen **[!UICONTROL poi.name]** in **[!UICONTROL Places POI Name (eVar 2)]**. Für jede erstellte Ortsvariable müssen zusätzliche Verarbeitungsregeln erstellt werden.

![&quot;eine Verarbeitungsregel erstellen&quot;](/help/assets/aa-processing-rule.png)

## 4. Erstellen eines Berichts in Workspace

Dieser Schritt zeigt einen einfachen Bericht in Analytics Workspace, um die in den Schritten 1 bis 3 erfassten Daten anzuzeigen. Weitere Informationen zur Verwendung von Analytics Workspace finden Sie unter [Analysis Workspace - Übersicht](https://docs.adobe.com/content/help/de-DE/analytics/analyze/analysis-workspace/home.html).

In diesem Beispiel hat der Bericht die folgenden Einstellungen:

* Metrik - **[!UICONTROL Vorfälle]**

* Dimension - **[!UICONTROL Aktionsname]**

   * Aufschlüsselung nach Dimension - **[!UICONTROL Places POI Name]**

![&quot;Erstellen eines Berichts im Arbeitsbereich&quot;](/help/assets/aa-workspace.png)
