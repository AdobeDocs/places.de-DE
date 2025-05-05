---
title: Bericht zu Standortdaten in Analytics Workspace
description: Dieser Abschnitt enthält Informationen zum Erstellen von Berichten zu Standortdaten in Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Berichte zu Standortdaten in der Analytics-Workspace {#places-in-workspace}

Dieses Dokument zeigt ein Beispiel für die Berichterstellung zu Ihren Standortdaten in der Analytics-Workspace. Jeder Schritt enthält eine allgemeine Zusammenfassung mit Details, die durch Verweise auf andere Dokumentationsseiten bereitgestellt werden.

## Voraussetzungen

Dieses Dokument setzt Folgendes voraus:

1. Die Places-Erweiterung ist in Ihrer Anwendung implementiert.

   Weitere Informationen zur Implementierung der Places-Erweiterung finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Der Adobe Analytics-Benutzer ist Administrator und hat Zugriff auf Verarbeitungsregeln.

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter Übersicht über [Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=de).

1. In der Launch-Eigenschaft wurden Datenelemente für die gewünschten Places Service-Variablen erstellt.

   Weitere Informationen zu Datenelementen in Launch finden Sie unter [Definieren eines Datenelements](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Erstellen einer Launch-Regel

Erstellen Sie eine Regel, die bewirkt, dass der SDK Daten an Analytics sendet, wenn das Gerät einen POI betritt. Das Erstellen dieser Art von Regel wird auf der Seite [POI-Ein- und -Ausgangsdaten an Analytics senden](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) beschrieben.

In diesem Beispiel sind für die Aktion der Regel die folgenden Werte für die Analytics-Anfrage definiert:

* **[!UICONTROL Action]** wird der Wert **[!UICONTROL Places Entry]** angegeben.

* Der Kontextdatenschlüssel **[!UICONTROL poi.name]** wird auf den Wert des Datenelements **[!UICONTROL {%%POI Name%}]** festgelegt.

![„Aktion festlegen“](/help/assets/pt-setAction.png)

## 2. Erstellen von Analytics-Variablen

Um die Kontextdaten (die in Schritt 1 gesendet werden) zuzuordnen, müssen zunächst Variablen für die Analytics Report Suite erstellt werden. Weitere Informationen zum Erstellen von Variablen in Analytics finden Sie unter [Konversionsvariablen (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=de).

In diesem Beispiel wurde eine Konversionsvariable mit dem Namen **[!UICONTROL eVar2]** erstellt und **[!UICONTROL Places POI Name]** benannt. Für jede Standortvariable, die Sie in Berichten bereitstellen möchten, müssen zusätzliche Variablen erstellt werden.

![Erstellen einer Analytics-Variablen“](/help/assets/aa-evar.png)

## 3. Erstellen von Verarbeitungsregeln

Dieser Schritt ist erforderlich, um Kontextdaten (Schritt 1) Analytics-Variablen zuzuordnen (Schritt 2). Weitere Informationen zum Erstellen von Verarbeitungsregeln finden Sie unter [Übersicht über Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=de).

In diesem Beispiel wurde eine Verarbeitungsregel erstellt, um den Kontextdatenwert **[!UICONTROL poi.name)]** Places POI Name (eVar2 **[!UICONTROL zuzuordnen]**. Für jede erstellte Standortvariable müssen zusätzliche Verarbeitungsregeln erstellt werden.

![Erstellen einer Verarbeitungsregel“](/help/assets/aa-processing-rule.png)

## 4. Erstellen eines Berichts in Workspace

In diesem Schritt wird ein Basisbericht in Analytics Workspace angezeigt, um die in den Schritten 1 bis 3 erfassten Daten anzuzeigen. Weitere Informationen zur Verwendung von Analytics Workspace finden Sie unter [Analytics Workspace - Übersicht](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=de).

In diesem Beispiel hat der Bericht die folgenden Einstellungen:

* Metrik - **[!UICONTROL Vorfälle]**

* Dimension - **[!UICONTROL Aktionsname]**

   * Aufschlüsselung nach Dimension - **[!UICONTROL Orte POI-Name]**

![„Erstellen eines Berichts in Workspace“](/help/assets/aa-workspace.png)
