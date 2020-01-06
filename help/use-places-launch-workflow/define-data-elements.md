---
title: Definieren von Datenelementen
description: Dieser Abschnitt enthält Informationen zum Erstellen, Verwenden und Veröffentlichen von Datenelementen in Experience Platform Launch for Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Define a data element {#define-data-elements}

Die folgenden Informationen helfen Ihnen, Datenelemente zu verstehen und zu erstellen und zu veröffentlichen.

## Datenelemente

Datenelemente sind die Bausteine für das Datenwörterbuch der Anwendung und werden verwendet, um Daten über Marketing- und Anzeigentechnologie hinweg zu erfassen, zu organisieren und bereitzustellen.

Ein Datenelement ist eine Variable, bei der der Wert einer Besucher-ID, einem Betreibernamen, einer Anzeigen-ID, einer Push-ID usw. zugeordnet werden kann. In Experience Platform Launch können Sie auf diesen Wert anhand seines Variablennamen verweisen. Diese Sammlung von Datenelementen wird zum Wörterbuch definierter Daten, die Sie zum Erstellen Ihrer Regeln (Ereignisse, Bedingungen und Aktionen) verwenden können. Dieses Wörterbuch wird über Experience Platform Launch freigegeben, wo es mit jeder Erweiterung in Ihrer Eigenschaft verwendet werden kann.

Mit der Erweiterung &quot;Orte&quot;können Sie auf Werte aus den folgenden Zielen verweisen:

* Aktueller POI, der den POI bezeichnet, in dem sich Ihr Kunde derzeit befindet.

   Befindet sich der Benutzer in mehreren POIs, wird der Benutzer zur Bibliothek mit höherem Rang ausgewählt. Wenn mehrere POIs zur Bibliothek mit dem höchsten Rang gehören, wird die mit dem kleinsten Radius ausgewählt.
* Letzter ausgesetzter POI, der auf den letzten POI verweist, den der Benutzer verlassen hat.
* Letzter eingegebener POI, der auf den letzten POI verweist, den der Benutzer eingegeben hat.

Jeder POI enthält die folgenden Datenreferenzen:

* **[!UICONTROL Category]**: Kategorie des POI
* **[!UICONTROL City]**: Ort des POI
* **[!UICONTROL Country]**: Land des POI
* **[!UICONTROL Latitude]**: Breitengrad des POI
* **[!UICONTROL Longitude]**: Längengrad des POI
* **[!UICONTROL Metadata]**: benutzerdefinierte Metadaten des POI
* **[!UICONTROL Name]**: Region POI
* **[!UICONTROL Radius]**: Radius der POI
* **[!UICONTROL Region ID]**: ID des POI
* **[!UICONTROL Region/State]**: Region, Provinz oder Bundesstaat des POI

### Datenelement erstellen

1. Klicken Sie auf der Seite &quot;Eigenschaft&quot;für Ihre App auf die **[!UICONTROL Data Elements]**Registerkarte.

1. Klicken Sie auf **[!UICONTROL Create New Data Element]**.

1. Suchen Sie in der Liste der installierten Erweiterungen nach **[!UICONTROL Places]**.

1. Wählen Sie in der **[!UICONTROL Data Element Type]**Dropdownliste einen Datenverweis für dieses Datenelement aus.

1. Wählen Sie ein POI-Ziel.

1. Wenn dieses Datenelement ein benutzerdefinierter Metadatenverweis ist, wählen Sie einen Metadatenschlüssel aus.

1. Geben Sie einen Namen für das Datenelement ein und klicken Sie auf **[!UICONTROL Save]**.

   ![Datenelement erstellen](/help/assets/create-de-7-v3.png)


## Datenelemente zu verwenden

Nachdem ein Datenelement erstellt wurde, können Sie das Datenelement aus einer beliebigen Regelkomponente verwenden, wenn eine Datenelementauswahl vorhanden ist.

![Datenelement verwenden](/help/assets/use-de-v2.png)

Wenn die Regelkomponente keine Datenelementauswahl enthält, können Sie das Datenelement verwenden, indem Sie den Datenelementnamen mit den **[!UICONTROL %%]**Token einschließen.
Wenn der Name des Datenelements beispielsweise**[!UICONTROL Last POI City]** lautet, können Sie **[!UICONTROL LAST POI City]**der Texteingabe hinzufügen.


## Datenelemente veröffentlichen

Wenn Datenelemente in einer der Regelkomponenten verwendet werden, müssen diese Datenelemente ebenfalls in die Bibliothek aufgenommen und veröffentlicht werden.
