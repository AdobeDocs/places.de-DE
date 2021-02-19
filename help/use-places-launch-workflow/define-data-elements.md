---
title: Definieren von Datenelementen
description: Dieser Abschnitt enthält Informationen zum Erstellen, Verwenden und Veröffentlichen von Datenelementen in Experience Platform Launch für Orte.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---


# Definieren eines Datenelements {#define-data-elements}

Die folgenden Informationen helfen Ihnen, Datenelemente zu verstehen und zu erstellen und zu veröffentlichen.

## Datenelemente

Datenelemente sind die Bausteine für das Datenwörterbuch der Anwendung und werden verwendet, um Daten über Marketing- und Anzeigentechnologie hinweg zu erfassen, zu organisieren und bereitzustellen.

Ein Datenelement ist eine Variable, bei der der Wert einer Besucher-ID, einem Betreibernamen, einer Anzeigen-ID, einer Push-ID usw. zugeordnet werden kann. In Experience Platform Launch können Sie auf diesen Wert anhand des Variablennamens verweisen. Diese Sammlung von Datenelementen wird zum Wörterbuch definierter Daten, die Sie zum Erstellen Ihrer Regeln (Ereignisse, Bedingungen und Aktionen) verwenden können. Dieses Wörterbuch wird über den Experience Platform Launch hinweg freigegeben und kann mit jeder beliebigen Erweiterung in Ihrer Eigenschaft verwendet werden.

Mit der Erweiterung &quot;Orte&quot;können Sie auf Werte aus den folgenden Zielgruppen verweisen:

* Aktueller POI, der auf den POI verweist, in dem sich Ihr Kunde derzeit befindet.

   Befindet sich der Benutzer in mehreren POIs, wird der Benutzer zur Bibliothek mit höherem Rang ausgewählt. Wenn mehrere POIs zur Bibliothek mit dem höchsten Rang gehören, wird die mit dem kleinsten Radius ausgewählt.
* Letzter ausgesetzter POI, der auf den letzten POI verweist, den der Benutzer verlassen hat.
* Letzter eingegebener POI, der auf den letzten POI verweist, den der Benutzer eingegeben hat.

Jeder POI enthält die folgenden Datenreferenzen:

* **[!UICONTROL Kategorie]**: Kategorie des POI
* **[!UICONTROL Ort]**: Ort des POI
* **[!UICONTROL Land]**: Land des POI
* **[!UICONTROL Breitengrad]**: Breitengrad des POI
* **[!UICONTROL Längengrad]**: Längengrad des POI
* **[!UICONTROL Metadaten]**: benutzerdefinierte Metadaten des POI
* **[!UICONTROL Name]**: Name des POI
* **[!UICONTROL Radius]**: Radius der POI
* **[!UICONTROL Regions-ID]**: ID des POI
* **[!UICONTROL Region/Bundesland]**: Region, Provinz oder Bundesstaat des POI

### ein Datenelement erstellen

1. Klicken Sie auf der Seite &quot;Eigenschaft&quot;für Ihre App auf die Registerkarte **[!UICONTROL Datenelemente]**.

1. Klicken Sie auf **[!UICONTROL Neues Datenelement erstellen]**.

1. Suchen Sie in der Liste der installierten Erweiterungen nach **[!UICONTROL Orte]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Datenelementtyp]** einen Datenverweis für dieses Datenelement aus.

1. Wählen Sie eine POI-Zielgruppe.

1. Wenn dieses Datenelement ein benutzerdefinierter Metadatenverweis ist, wählen Sie einen Metadatenschlüssel aus.

1. Geben Sie einen Namen für das Datenelement ein und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Datenelement erstellen](/help/assets/create-de-7-v3.png)


## Datenelement verwenden

Nachdem ein Datenelement erstellt wurde, können Sie das Datenelement aus einer beliebigen Regelkomponente verwenden, wenn eine Datenelementauswahl vorhanden ist.

![Datenelement verwenden](/help/assets/use-de-v2.png)

Wenn in der Regelkomponente keine Datenelementauswahl vorhanden ist, können Sie das Datenelement verwenden, indem Sie den Datenelementnamen mit den Token **[!UICONTROL %]** umschließen.
Wenn der Name des Datenelements beispielsweise **[!UICONTROL Letzter POI-Ort]** lautet, können Sie **[!UICONTROL LAST POI-Stadt]** zu einer Texteingabe hinzufügen.


## Datenelemente veröffentlichen

Wenn Datenelemente in einer der Regelkomponenten verwendet werden, müssen diese Datenelemente ebenfalls in die Bibliothek aufgenommen und veröffentlicht werden.
