---
title: Massen-Upload-POIs
description: Dieser Abschnitt enthält Informationen zum Massen-Upload Ihrer POIs.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Massen-Upload von POIs {#bulk-upload-pois}

Die Schaltfläche **POIs importieren** im Places-Service kann verwendet werden, um neue POIs mithilfe einer CSV-Datei stapelweise hochzuladen. Eine Beispiel-Tabellenvorlage wird bereitgestellt, um zu zeigen, welche Datenspalten erforderlich sind und wie optionale benutzerdefinierte Metadaten hinzugefügt werden.

![Massenimportbildschirm](/help/assets/Bulk-import.png)

In diesem Video wird der Prozess für den Massenimport und die Massenbearbeitung gezeigt:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places Service - Massenimport und -bearbeitung von POIs](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python-API-Skripte

Es wurde ein Satz von Python-Skripten erstellt, um den Batch-Import von POIs aus einer CSV-Datei in eine POI-Datenbank mithilfe der Webservice-APIs zu vereinfachen. Diese Skripte können aus diesem Open-Source-Repository [Git-Repository) &#x200B;](https://github.com/adobe/places-scripts) werden.

Informationen zum Zugriff auf die Webservice-APIs vor der Ausführung dieser Skripte finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

Im Folgenden finden Sie einige Informationen zu den Skripten:

>[!TIP]
>
>Diese Informationen sind auch in einer Readme-Datei im [Git-Repository](https://github.com/adobe/places-scripts) enthalten.

## CSV-Datei

Eine CSV-Beispieldatei, `places_sample.csv`, ist Teil dieses Pakets und enthält die erforderlichen Kopfzeilen und eine Zeile mit Beispieldaten. Diese Kopfzeilen sind alle in Kleinbuchstaben geschrieben und entsprechen den reservierten Metadatenschlüsseln, die in der Places-Datenbank verwendet werden. Spalten, die Sie der CSV-Datei hinzufügen, werden der POI-Datenbank in einem separaten Metadatenabschnitt für jeden POI als Schlüssel/Wert-Paare hinzugefügt, und der Header-Wert wird als Schlüssel verwendet.

Im Folgenden finden Sie eine Liste der Spalten und Werte, die Sie verwenden müssen:

* `lib_id`

  Eine gültige Bibliotheks-ID, die aus der POI-Datenbank abgerufen wird.

* `type`

  Punkt ist derzeit der einzige gültige Wert.

* `longitude`

  Ein Wert zwischen -180 und 180.

* `latitude`

  Ein Wert zwischen -85 und 85.

* `radius`

  Ein Wert zwischen 10 und 20.000.

### Spaltenwerte

Die Werte der folgenden Spalten werden in der Places Service-Benutzeroberfläche verwendet:

* Farbe, die als Farbe des Pins verwendet wird, der den Standort des POI in der Karte der Places Service-Benutzeroberfläche darstellt.
   * Die gültigen Werte sind &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B und #3DC8DE sowie &quot;&quot;.
   * Wenn der Wert leer gelassen wird, verwendet die Places Service-Benutzeroberfläche Blau als Standardfarbe.

     Die Werte entsprechen Blau (#3E76D0), Lila (#AA99E8), Fuschia (#DC2ABA), Orange (#FC685B), Hellorange (#FC962E), Gelb (#F6C436), Hellgrün (#BECE5D), Grün (#61B56B) und Hellblau (#3DC8DE).

* icon, das als Symbol auf dem Pin verwendet wird, der die Position des POI auf der Karte der Places-Service-Benutzeroberfläche darstellt.

   * Die gültigen Werte sind &quot;&quot;, Shop, Hotelbett, Auto, Flugzeug, Zug, Schiff, Stadion, Freizeitpark, Anker, Becher, Glocke, Bid, Buch, Box, Aktenkoffer, Durchsuchen, Pinsel, Gebäude, Rechner, Kamera, Uhr, Erziehung, Taschenlampe, Folgen, Spiel, weiblich, männlich, Geschenk, Hammer, Herz, Heimat, Schlüssel, Start, Glühbirne, Postfach, Pin, Werbung, Band, ShoppingCart, Stern, Ziel, Teekanne, ThumbDown, ThumbUp, Falle, Trophäe, Schraubenschlüssel.

     Die Symbolwerte werden in der Reihenfolge aufgelistet, in der sie in der folgenden Abbildung angezeigt werden:

     ![Symbole in der Benutzeroberfläche](/help/assets/UI_icons.png)

   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche einen Stern als Standardsymbol.

* Nicht erwähnte Spalten können leer gelassen werden.

## Ausführen des Skripts

1. Laden Sie Dateien aus dem [Git-Repository](https://github.com/adobe/places-scripts) in Ihr lokales Verzeichnis herunter.
1. Öffnen Sie die `config.py`-Datei in einem Texteditor und führen Sie die folgenden Aufgaben aus:

   a. Bearbeiten Sie die folgenden Variablenwerte als Zeichenfolgen:

   * `csv_file_path`

     Dies ist der Pfad zur `.csv`.

   * `access_code`

     Dies ist Ihr Zugriffscode, der aus dem Aufruf an Adobe IMS abgerufen wurde. Informationen zum Abrufen dieses Zugriffscodes finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     Die Experience Cloud-Organisations-ID, in die die POIs importiert werden sollen. Informationen zum Abrufen der Organisations-ID finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Dies ist Ihr Places REST API-Schlüssel, der von Ihrer Adobe I/O Places-Integration bezogen wurde. Informationen zum Abrufen des API-Schlüssels finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   b. Speichern Sie Ihre Änderungen.

1. Navigieren Sie in einem Terminal-Fenster zum `…/places-scripts/import/`.
1. Geben Sie `python ./places_import.py` ein, und drücken Sie **[!UICONTROL Taste]** Eingabetaste **[!UICONTROL (]**).


## CSV-Prüfungen vor dem Import

Das Skript führt zunächst die folgenden Prüfungen für die CSV-Datei durch:

* Ob eine `.csv` angegeben wurde.
* Ob der Dateipfad gültig ist.
* Ob die reservierten Metadaten-Header enthalten sind.

  Die reservierten Metadaten-Kopfzeilen sind lib_id, Name, Beschreibung, Typ, Längengrad, Breitengrad, Radius, Land, Bundesland, Stadt, Straße, Kategorie, Symbol und Farbe.

  >[!TIP]
  >
  >Die Kopfzeilen sind alle in Kleinbuchstaben geschrieben und können in beliebiger Reihenfolge aufgelistet werden.

* Überprüft die Werte der im Abschnitt CSV-Datei angegebenen Spalten.

Wenn Fehler gefunden werden, druckt das Skript die Fehler aus und wird abgebrochen. Wenn keine Fehler gefunden werden, versucht das Skript, die POIs in Batches mit 1.000 zu importieren. Wenn der Batch erfolgreich importiert wurde, meldet das Script den Status-Code 200. Wenn der Stapel nicht erfolgreich importiert wurde, werden Fehler gemeldet.

## Komponententests

Modultests befinden sich in der `tests.py`-Datei, sollten vor jeder Pull-Anfrage ausgeführt werden und sollten alle erfolgreich sein. Zusätzliche Tests sollten mit neuem Code hinzugefügt werden. Um die Tests auszuführen, navigieren Sie zum `…/places-scripts/import/` Verzeichnis und geben Sie `python ./places_import.py` in Terminal ein.
