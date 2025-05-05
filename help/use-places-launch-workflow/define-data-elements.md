---
title: Definieren von Datenelementen
description: In diesem Abschnitt finden Sie Informationen zum Erstellen, Verwenden und Veröffentlichen von Datenelementen in Experience Platform Launch for Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# Definieren eines Datenelements {#define-data-elements}

Die folgenden Informationen helfen Ihnen, Datenelemente zu verstehen und sie zu erstellen und zu veröffentlichen.

## Über Datenelemente

Datenelemente sind die Bausteine für das Datenwörterbuch der Anwendung und werden zum Erfassen, Organisieren und Bereitstellen von Daten in Marketing- und Werbetechnologien verwendet.

Ein Datenelement ist eine Variable, bei der der Wert einer Besucher-ID, einem Provider-Namen, einer Advertising-ID, einer Push-ID usw. zugeordnet werden kann. In Experience Platform Launch können Sie diesen Wert anhand des Variablennamens referenzieren. Diese Sammlung von Datenelementen wird zum Wörterbuch definierter Daten, die Sie zum Erstellen Ihrer Regeln (Ereignisse, Bedingungen und Aktionen) verwenden können. Dieses Wörterbuch wird auf allen Experience Platform Launch-Instanzen gemeinsam genutzt, wo es mit jeder Erweiterung in Ihrer Eigenschaft verwendet werden kann.

Mit der Places -Erweiterung können Sie auf Werte aus den folgenden Zielen verweisen:

* Aktueller POI, der sich auf den POI bezieht, in dem sich Ihr Kunde derzeit befindet.

  Wenn sich der Benutzer in mehreren POIs befindet, wird derjenige ausgewählt, der zur Bibliothek mit dem höheren Rang gehört. Wenn mehrere POIs zur höchsten Rang-Bibliothek gehören, wird der mit dem kleinsten Radius ausgewählt.
* POI „Zuletzt beendet“, der sich auf den letzten POI bezieht, den der Benutzer verlassen hat.
* POI des letzten Eintritts, der sich auf den letzten POI bezieht, den der Benutzer eingegeben hat.

Jeder POI enthält die folgenden Datenverweise:

* **[!UICONTROL Category]**: Kategorie des POI
* **[!UICONTROL City]**: Stadt des POI
* **[!UICONTROL Country]**: Land des POI
* **[!UICONTROL Breitengrad]**: Breitengrad des POI
* **[!UICONTROL Längengrad]**: Längengrad des POI
* **[!UICONTROL Metadata]**: benutzerdefinierte Metadaten des POI
* **[!UICONTROL Name]**: Name des POI
* **[!UICONTROL Radius]**: Radius des POI
* **[!UICONTROL Regions-]**: ID des POI
* **[!UICONTROL Region/Bundesland]**: Region, Provinz oder Bundesland des POI

### ein Datenelement erstellen

1. Klicken Sie auf der Eigenschaftsseite für Ihre App auf die Registerkarte **[!UICONTROL Datenelemente]** .

1. Klicken Sie auf **[!UICONTROL Neues Datenelement erstellen]**.

1. Suchen Sie in der Liste der installierten Erweiterungen nach **[!UICONTROL Places]**.

1. Wählen **[!UICONTROL in der Dropdown]** Liste Datenelementtyp einen Datenverweis für dieses Datenelement aus.

1. POI-Ziel auswählen.

1. Wenn dieses Datenelement eine benutzerdefinierte Metadatenreferenz ist, wählen Sie einen Metadatenschlüssel aus.

1. Geben Sie einen Namen für das Datenelement ein und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Datenelement erstellen](/help/assets/create-de-7-v3.png)


## Verwenden eines Datenelements

Wenn nach dem Erstellen eines Datenelements eine Datenelementauswahl vorhanden ist, können Sie das Datenelement aus einer beliebigen Regelkomponente verwenden.

![Verwenden des Datenelements](/help/assets/use-de-v2.png)

Wenn in der Regelkomponente keine Datenelementauswahl vorhanden ist, können Sie das Datenelement verwenden, indem Sie den Datenelementnamen in die **[!UICONTROL %%]**-Token einschließen.
Wenn der Datenelementname beispielsweise „Letzte POI-Stadt&#x200B;**[!UICONTROL lautet]** können Sie **[!UICONTROL LETZTE POI-Stadt]** zu einer Texteingabe hinzufügen.


## Publish-Datenelemente

Wenn Datenelemente in einer der Regelkomponenten verwendet werden, müssen diese Datenelemente auch in die Bibliothek aufgenommen und veröffentlicht werden.
