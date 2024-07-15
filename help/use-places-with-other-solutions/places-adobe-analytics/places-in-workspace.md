---
title: Bericht zu Standortdaten in Analytics Workspace
description: Dieser Abschnitt enthält Informationen zum Reporting von Standortdaten in Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Bericht zu Standortdaten in Analytics Workspace {#places-in-workspace}

Dieses Dokument zeigt ein Beispiel für die Berichterstellung zu Ihren Standortdaten in der Analytics Workspace. Jeder Schritt enthält eine allgemeine Zusammenfassung mit Details, die durch Verweise auf andere Dokumentationsseiten bereitgestellt werden.

## Voraussetzungen

In diesem Dokument wird von Folgendem ausgegangen:

1. Die Places-Erweiterung ist in Ihrer Anwendung implementiert.

   Weitere Informationen zur Implementierung der Places-Erweiterung finden Sie unter [Places-Erweiterungen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Der Adobe Analytics-Benutzer ist ein Administrator und hat Zugriff auf Verarbeitungsregeln.

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter Übersicht über [Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

1. In der Launch-Eigenschaft wurden Datenelemente für die gewünschten Places-Dienst-Variablen erstellt.

   Weitere Informationen zu Datenelementen in Launch finden Sie unter [Definieren eines Datenelements](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Erstellen einer Launch-Regel

Erstellen Sie eine Regel, die dazu führt, dass das SDK Daten an Analytics sendet, wenn das Gerät einen POI aufruft. Das Erstellen dieser Art von Regel wird auf der Seite [POI-Einstiegs- und Ausstiegsdaten an Analytics senden](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) beschrieben.

In diesem Beispiel hat die Aktion der Regel die folgenden Werte, die für die Analytics-Anforderung definiert sind:

* **[!UICONTROL Aktion]** erhält den Wert **[!UICONTROL Places Entry]**.

* Der Kontextdatenschlüssel **[!UICONTROL poi.name]** wird auf den Wert des Datenelements **[!UICONTROL {%%POI Name%}]** gesetzt.

![&quot;set an action&quot;](/help/assets/pt-setAction.png)

## 2. Erstellen von Analytics-Variablen

Um die Kontextdaten zuzuordnen (gesendet in Schritt 1), müssen zunächst Variablen für die Analytics Report Suite erstellt werden. Weitere Informationen zum Erstellen von Variablen in Analytics finden Sie unter [Konversionsvariablen (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=de).

In diesem Beispiel wurde eine Konversionsvariable mit dem Namen **[!UICONTROL eVar2]** erstellt, die den Namen **[!UICONTROL Places POI Name]** trägt. Für jede Standortvariable, die Sie in Berichten verfügbar machen möchten, müssen zusätzliche Variablen erstellt werden.

![&quot;create an analytics variable&quot;](/help/assets/aa-evar.png)

## 3. Erstellen von Verarbeitungsregeln

Dieser Schritt ist erforderlich, um Kontextdaten (Schritt 1) Analytics-Variablen (Schritt 2) zuzuordnen. Weitere Informationen zum Erstellen von Verarbeitungsregeln finden Sie unter [Übersicht über Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

In diesem Beispiel wurde eine Verarbeitungsregel erstellt, um den Kontextdatenwert **[!UICONTROL poi.name]** dem Wert **[!UICONTROL Places POI Name (eVar 2)]** zuzuordnen. Für jede erstellte Ortsvariable müssen zusätzliche Verarbeitungsregeln erstellt werden.

![&quot;Erstellen einer Verarbeitungsregel&quot;](/help/assets/aa-processing-rule.png)

## 4. Erstellen eines Berichts in Workspace

Dieser Schritt zeigt einen Basisbericht in Analytics Workspace, um die in den Schritten 1 bis 3 erfassten Daten anzuzeigen. Weitere Informationen zur Verwendung von Analytics Workspace finden Sie unter [Übersicht über Analytics Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=de).

In diesem Beispiel hat der Bericht die folgenden Einstellungen:

* Metrik - **[!UICONTROL Vorfälle]**

* Dimension - **[!UICONTROL Aktionsname]**

   * Aufschlüsselung nach Dimension - **[!UICONTROL Orte-POI-Name]**

![&quot;Erstellen eines Berichts im Arbeitsbereich&quot;](/help/assets/aa-workspace.png)
