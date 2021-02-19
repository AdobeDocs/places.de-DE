---
title: Massen-Upload-POIs
description: In diesem Abschnitt erfahren Sie, wie Sie POIs als Massenupload hochladen.
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Massenupload von POIs {#bulk-upload-pois}

Mit der Schaltfläche **POIs importieren** im Orte-Dienst können neue POIs mit einer CSV-Datei als Massen-Upload hochgeladen werden. Es wird eine Beispielvorlage für Tabellen bereitgestellt, die zeigt, welche Datenspalten erforderlich sind und wie optionale benutzerdefinierte Metadaten hinzugefügt werden.

![Massenimportbildschirm](/help/assets/Bulk-import.png)

In diesem Video wird der Vorgang für den Massenimport und die Massenbearbeitung dargestellt:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[POIs für den Massenimport und die Bearbeitung von Diensten](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python API-Skripten

Eine Reihe von Python-Skripten wurden erstellt, um den Stapelimport von POIs aus einer CSV-Datei in eine POI-Datenbank mithilfe der Web Service APIs zu vereinfachen. Diese Skripten können von dieser Open Source [git repo](https://github.com/adobe/places-scripts) heruntergeladen werden.

Bevor Sie diese Skripten ausführen, lesen Sie *Voraussetzungen für den Benutzerzugriff* in [Integrationsübersicht und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md), um auf die Webdienst-APIs zuzugreifen.

Im Folgenden finden Sie einige Informationen zu den Skripten:

>[!TIP]
>
>Diese Informationen sind auch in einer Readme-Datei im [git repo](https://github.com/adobe/places-scripts) enthalten.

## CSV-Datei nicht funktionierte, wurde behoben

Eine .csv-Beispieldatei, `places_sample.csv`, ist Teil dieses Pakets und enthält die erforderlichen Kopfzeilen und eine Reihe von Musterdaten. Diese Header sind alle Kleinbuchstaben und entsprechen den reservierten Metadatenschlüsseln, die in der Datenbank &quot;Orte&quot;verwendet werden. Spalten, die Sie der .csv-Datei hinzufügen, werden der POI-Datenbank in einem separaten Metadatenabschnitt für jeden POI als Schlüssel/Wert-Paare hinzugefügt und der Header-Wert wird als Schlüssel verwendet.

Im Folgenden finden Sie eine Liste der Spalten und der erforderlichen Werte:

* `lib_id`

   Eine gültige Bibliotheks-ID, die aus der POI-Datenbank abgerufen wird.

* `type`

   Point ist zurzeit der einzige gültige Wert.

* `longitude`

   Ein Wert zwischen -180 und 180.

* `latitude`

   Ein Wert zwischen -85 und 85.

* `radius`

   Ein Wert zwischen 10 und 20.000.

### Spaltenwerte

Die Werte der folgenden Spalten werden in der Benutzeroberfläche des Places-Dienstes verwendet:

* Farbe, die als Farbe des Pins verwendet wird, der die Position des POI in der Benutzeroberfläche des Orts-Dienstes darstellt.
   * Die gültigen Werte sind &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B und #3DC8DE und &quot;&quot;.
   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche des Places-Dienstes Blau als Standardfarbe.

      Die Werte entsprechen blau (#3E76D0), violett (#AA99E8), fuschia (#DC2ABA), orange (#FC685B), hellorange (#FC962E), gelb (#F6C436), hellgrün (#BECE5D), grün (#6 1B56B) bzw. hellblau (#3DC8DE).

* -Symbol, das als Symbol auf dem Pin verwendet wird, das die Position des POI auf der Benutzeroberfläche des Places-Dienstes darstellt.

   * Die gültigen Werte sind &quot;&quot;, Shop, Hotelbett, Auto, Flugzeug, Zug, Schiff, Stadion, amusementpark, Anker, Beaker, Bell, Bid, Buch, Box, Brieftasche, Broschüre, Bürste, Gebäude, Rechner, Kamera, Uhr, Bildung, Taschenlampe, folgen, Spiel, weiblich, männlich, Geschenk, Hammer, Herz, Schlüssel, Start, Glühbirne, Briefkasten, Geld, Posting, Geld, Geld, Posting, Pin Warenkorb, Warenkorb, Stern, Zielgruppe, Teekanne, Daumendown, Daumen, Trap, Trophäe, Schraubenschlüssel.

      Die Symbolwerte werden in der Reihenfolge aufgeführt, in der sie in der folgenden Abbildung angezeigt werden:

      ![Symbole in der Benutzeroberfläche](/help/assets/UI_icons.png)

   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche den Stern als Standardsymbol.

* Spalten, die nicht erwähnt werden, können leer gelassen werden.

## Ausführen des Skripts

1. Laden Sie Dateien von [git repo](https://github.com/adobe/places-scripts) in Ihren lokalen Ordner herunter.
1. Öffnen Sie in einem Texteditor die Datei `config.py` und führen Sie die folgenden Aufgaben aus:

   a. Bearbeiten Sie die folgenden Variablenwerte als Zeichenfolgen:

   * `csv_file_path`

      Dies ist der Pfad zu Ihrer `.csv`-Datei.

   * `access_code`

      Dies ist Ihr Zugriffscode, der durch den Aufruf von Adobe IMS erhalten wurde. Informationen zum Abrufen dieses Zugriffscodes finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

      Die Experience Cloud-orgID, in die die POIs importiert werden sollen. Informationen zum Abrufen der Organisations-ID finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      Dies ist der REST-API-Schlüssel, den Sie von der Adobe I/O Places Integration erhalten haben. Informationen zum Abrufen des API-Schlüssels finden Sie unter *Voraussetzungen für den Benutzerzugriff* in [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).
   b. Speichern Sie Ihre Änderungen.

1. Navigieren Sie in einem Terminalfenster zum Ordner `…/places-scripts/import/`.
1. Geben Sie `python ./places_import.py` ein und drücken Sie die Eingabetaste **[!UICONTROL enter]** (**[!UICONTROL return]**).


## CSV-Prüfungen vor dem Import

Das Skript führt zunächst die folgenden Prüfungen in der .csv-Datei durch:

* Ob eine `.csv`-Datei angegeben wurde.
* Gibt an, ob der Dateipfad gültig ist.
* Gibt an, ob die reservierten Metadaten-Header enthalten sind.

   Die reservierten Metadaten-Header sind lib_id, name, description, type, length, latitude, radius, country, state, city, street, Kategorie, icon und color.

   >[!TIP]
   >
   >Die Kopfzeilen sind alle in Kleinbuchstaben und können in beliebiger Reihenfolge aufgeführt werden.

* Prüft die Werte der im Abschnitt &quot;CSV-Datei&quot;angegebenen Spalten.

Wenn Fehler gefunden werden, gibt das Skript die Fehler aus und wird abgebrochen. Wenn keine Fehler gefunden werden, versucht das Skript, die POIs in Stapeln von 1000 zu importieren. Wenn der Stapel erfolgreich importiert wurde, gibt das Skript einen Statuscode von 200 aus. Wenn der Stapel nicht erfolgreich importiert wurde, werden Fehler gemeldet.

## Unit-Tests

Komponententests befinden sich in der Datei `tests.py`, sollten vor jeder Pull-Anforderung ausgeführt werden und alle bestehen. Zusätzliche Tests sollten mit neuem Code hinzugefügt werden. Um die Tests auszuführen, navigieren Sie zum Ordner `…/places-scripts/import/` und geben Sie `python ./places_import.py` in Terminal ein.
