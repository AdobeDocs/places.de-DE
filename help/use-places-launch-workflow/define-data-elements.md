---
title: Definieren von Datenelementen
description: In diesem Abschnitt finden Sie Informationen zum Erstellen, Verwenden und Veröffentlichen von Datenelementen in Experience Platform Launch for Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
TQID: https://experienceleague.adobe.com/NQ83uUZJtNglAcxD6HNl4Gw1Y8-0-uqfu-hH8H0EITg
product_v2:
  - id: a829a185-511f-4bf8-8dcf-9e684f8011cf
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 1%

---

# Definieren eines Datenelements {#define-data-elements}

Die folgenden Informationen helfen Ihnen, Datenelemente zu verstehen und sie zu erstellen und zu veröffentlichen.

## Über Datenelemente

Datenelemente sind die Bausteine für das Datenwörterbuch der Anwendung und werden zum Erfassen, Organisieren und Bereitstellen von Daten in Marketing- und Werbetechnologien verwendet.

Ein Datenelement ist eine Variable, bei der der Wert einer Besucher-ID, einem Provider-Namen, einer Advertising-ID, einer Push-ID usw. zugeordnet werden kann. In Experience Platform Launch können Sie diesen Wert anhand des Variablennamens referenzieren. Diese Sammlung von Datenelementen wird zum Wörterbuch definierter Daten, die Sie zum Erstellen Ihrer Regeln (Ereignisse, Bedingungen und Aktionen) verwenden können. Dieses Wörterbuch ist in Experience Platform Launch gemeinsam, wo es mit jeder Erweiterung in Ihrer Eigenschaft verwendet werden kann.

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


## Veröffentlichen von Datenelementen

Wenn Datenelemente in einer der Regelkomponenten verwendet werden, müssen diese Datenelemente auch in die Bibliothek aufgenommen und veröffentlicht werden.
