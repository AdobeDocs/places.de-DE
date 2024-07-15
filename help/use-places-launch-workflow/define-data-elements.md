---
title: Definieren von Datenelementen
description: Dieser Abschnitt enthält Informationen zum Erstellen, Verwenden und Veröffentlichen von Datenelementen in Experience Platform Launch für Orte.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# Datenelement definieren {#define-data-elements}

Die folgenden Informationen helfen Ihnen dabei, Datenelemente zu verstehen und zu erstellen und zu veröffentlichen.

## Über Datenelemente

Datenelemente sind die Bausteine für das Datenwörterbuch der Anwendung und werden verwendet, um Daten über Marketing- und Anzeigentechnologie hinweg zu erfassen, zu organisieren und bereitzustellen.

Ein Datenelement ist eine Variable, bei der der Wert einer Besucher-ID, einem Betreibernamen, einer Advertising ID, einer Push-ID usw. zugeordnet werden kann. Auf Experience Platform Launch können Sie diesen Wert anhand des Variablennamens referenzieren. Diese Sammlung von Datenelementen wird zum Wörterbuch definierter Daten, die Sie zum Erstellen Ihrer Regeln verwenden können (Ereignisse, Bedingungen und Aktionen). Dieses Wörterbuch wird über Experience Platform Launch hinweg freigegeben, wo es mit jeder beliebigen Erweiterung in Ihrer Eigenschaft verwendet werden kann.

Mit der Erweiterung Places können Sie Werte aus den folgenden Zielen referenzieren:

* Aktueller POI, der den POI angibt, an dem sich Ihr Kunde derzeit befindet.

  Wenn sich der Benutzer an mehreren POIs befindet, wird der Benutzer zur Bibliothek mit höherem Rang ausgewählt. Wenn mehrere Zielpunkte zur Bibliothek mit dem höchsten Rang gehören, wird die Bibliothek mit dem kleinsten Radius ausgewählt.
* Letzter ausgeschlossener POI, der auf den letzten POI verweist, den der Benutzer verlassen hat.
* Zuletzt eingegebener POI, der auf den letzten POI verweist, den der Benutzer eingegeben hat.

Jeder POI enthält die folgenden Datenreferenzen:

* **[!UICONTROL Kategorie]**: Kategorie des POI
* **[!UICONTROL Stadt]**: Stadt des POI
* **[!UICONTROL Land]**: Land des POI
* **[!UICONTROL Breitengrad]**: Breitengrad des POI
* **[!UICONTROL Längengrad]**: Längengrad des POI
* **[!UICONTROL Metadaten]**: benutzerdefinierte Metadaten des POI
* **[!UICONTROL Name]**: Name des POI
* **[!UICONTROL Radius]**: Radius des POI
* **[!UICONTROL Regions-ID]**: ID des POI
* **[!UICONTROL Region/Bundesstaat]**: Region, Provinz oder Bundesstaat des POI

### ein Datenelement erstellen

1. Klicken Sie auf der Eigenschaftsseite für Ihre App auf die Registerkarte **[!UICONTROL Datenelemente]** .

1. Klicken Sie auf **[!UICONTROL Neues Datenelement erstellen]**.

1. Suchen Sie in der Liste der installierten Erweiterungen nach **[!UICONTROL Places]**.

1. Wählen Sie in der Dropdownliste **[!UICONTROL Datenelementtyp]** einen Datenverweis für dieses Datenelement aus.

1. Wählen Sie ein POI-Ziel aus.

1. Wenn dieses Datenelement ein benutzerdefinierter Metadatenverweis ist, wählen Sie einen Metadatenschlüssel aus.

1. Geben Sie einen Namen für das Datenelement ein und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Datenelement erstellen](/help/assets/create-de-7-v3.png)


## Datenelement verwenden

Wenn nach der Erstellung eines Datenelements eine Datenelementauswahl vorhanden ist, können Sie das Datenelement aus einer beliebigen Regelkomponente verwenden.

![Verwenden Sie das Datenelement](/help/assets/use-de-v2.png)

Wenn in der Regelkomponente keine Datenelementauswahl vorhanden ist, können Sie das Datenelement verwenden, indem Sie den Datenelementnamen mit den Token **[!UICONTROL %%]** umschließen.
Wenn der Datenelementname beispielsweise **[!UICONTROL Letzter POI Ort]** ist, können Sie einer Texteingabe den Wert **[!UICONTROL LETZTE POI Stadt]** hinzufügen.


## Publish-Datenelemente

Wenn Datenelemente in einer der Regelkomponenten verwendet werden, müssen diese Datenelemente ebenfalls in die Bibliothek aufgenommen und veröffentlicht werden.
