---
title: Massen-Upload-POIs
seo-title: Massen-Upload-POIs
description: Dieser Abschnitt enthält Informationen zum Hochladen von POIs als Massendatei.
seo-description: Dieser Abschnitt enthält Informationen zum Hochladen von POIs als Massendatei.
translation-type: tm+mt
source-git-commit: 3a9653dcc7f5d18b717c4bb59424b8cad7104dd7

---


# Massenupload von POIs {#bulk-upload-pois}

Eine Reihe von Python-Skripten wurden erstellt, um den Stapelimport von POIs aus einer CSV-Datei in eine POI-Datenbank mithilfe der Web Service APIs zu vereinfachen. Diese Skripten können von diesem Open-Source- [Git-Repo](https://github.com/adobe/places-scripts)heruntergeladen werden.

Bevor Sie diese Skripten ausführen, stellen Sie sicher, dass Sie Zugriff auf die Webdienst-APIs haben, siehe *Voraussetzungen für den Benutzerzugriff* in der Übersicht über die [Adobe-E/A-Integration](/help/web-service-api/adobe-i-o-integration.md).

Im Folgenden finden Sie einige Informationen zu den Skripten:

>[!TIP]
>
>Diese Informationen sind auch in einer Readme-Datei im [Git-Repo](https://github.com/adobe/places-scripts)enthalten.

## CSV-Datei nicht funktionierte, wurde behoben

Eine .csv-Beispieldatei `places_sample.csv`ist Teil dieses Pakets und enthält die erforderlichen Kopfzeilen und eine Reihe von Musterdaten. Diese Header sind alle Kleinbuchstaben und entsprechen den reservierten Metadatenschlüsseln, die in der Datenbank "Orte"verwendet werden. Wenn Sie Kopfzeilen hinzufügen, werden die zusätzlichen Spalten der POI-Datenbank in einem separaten Metadatenabschnitt für jeden POI als Schlüssel/Wert-Paare hinzugefügt.

Im Folgenden finden Sie eine Liste der Spalten und Werte, die Sie verwenden müssen:

* `lib_id`

   Eine gültige Bibliotheks-ID, die aus der POI-Datenbank abgerufen wird.

* `type`

   Point ist zurzeit der einzige gültige Wert.

* `longitude`

   Ein Wert zwischen -180 und 180.

* `latitude`

   Ein Wert zwischen -85 und 85.

* `radius`

   Ein Wert zwischen 10 und 2000.

### Spaltenwerte

Die Werte der folgenden Spalten werden in der Benutzeroberfläche des Location Service verwendet:

* Farbe, die als Farbe des Pins verwendet wird, der die Position des POI in der Benutzeroberfläche des Location Service darstellt.
   * Die gültigen Werte sind "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B und #3DC8DE.
   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche des Location Service Blau als Standardfarbe.

      Die Werte entsprechen blau, violett, fuschia, orange, hellorange, gelb, hellgrün, grün und hellblau.

* Symbol, das als Symbol auf dem Pin verwendet wird, das die Position des POI auf der Benutzeroberfläche des Location Service darstellt.
   * Die gültigen Werte sind "", Anker, Beaker, Glocke, Durchsuchen, Buch, Bürste, Gebäude, Rechner, Kamera, Einkaufswagen, Uhr, Box, Taschenlampe, Folgen, Gebot, Band, Bildung, Hammer, Herz, Home, Schlüssel, Mailbox, männlich, Förderung, Geld, Trap, Spiel, Start, Stern, Glühbirne, Pin, Ziel, Tebapot, DaumenDown, DaumenUp. Aktentasche, Trophäe, Weibchen und Schraubenschlüssel.
   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche den Stern als Standardsymbol.

* Spalten, die nicht erwähnt werden, können leer gelassen werden.

## Ausführen des Skripts

1. Laden Sie Dateien in das entsprechende Verzeichnis herunter.
1. Öffnen Sie die `config.py` Datei in einem Texteditor und führen Sie die folgenden Aufgaben aus:

   a. Bearbeiten Sie die folgenden Variablenwerte als Zeichenfolgen:

   * `csv_file_path`

      Der Pfad zu Ihrer `.csv` Datei.

   * `access_code`

      Dies ist Ihr Zugriffscode, den Sie beim Aufruf von Adobe IMS erhalten haben.

   * `org_id`

      Die Experience Cloud-Organisations-ID, in die die POIs importiert werden sollen.

   * `api_key`

      Dies ist der REST-API-Schlüssel für Platzierungen, den Sie von der Adobe-E/A-Platzierungsintegration erhalten haben.
   b. Speichern Sie Ihre Änderungen.

1. Navigieren Sie in einem Terminalfenster zum `…/places-scripts/import/` Ordner.
1. Geben Sie `python ./places_import.py` die **[!UICONTROL enter]** (**[!UICONTROL return]**) Taste ein.


## CSV-Prüfungen vor dem Import

Das Skript führt zunächst die folgenden Prüfungen in der .csv-Datei durch:

* Ob eine `.csv` Datei angegeben wurde.
* Ob der Dateipfad gültig ist.
* Ob die reservierten Metadaten-Header enthalten sind.

   Die reservierten Metadaten-Header sind lib_id, name, description, type, length, latitude, radius, country, state, city, street, category, icon und color.

   >[!TIP]
   >
   >Die Kopfzeilen sind alle in Kleinbuchstaben und können in beliebiger Reihenfolge aufgeführt werden.

* Prüft die Werte der im Abschnitt "CSV-Datei"angegebenen Spalten.

Wenn Fehler gefunden werden, gibt das Skript die Fehler aus und wird abgebrochen. Wenn keine Fehler gefunden werden, versucht das Skript, die POIs in Stapeln von 1000 zu importieren. Wenn der Stapel erfolgreich importiert wurde, gibt das Skript einen Statuscode von 200 aus. Wenn der Stapel nicht erfolgreich importiert wurde, werden Fehler gemeldet.

## Komponententests

Komponententests befinden sich in der `tests.py` Datei, sollten vor jeder Pull-Anforderung ausgeführt werden und alle bestehen. Zusätzliche Tests sollten mit neuem Code hinzugefügt werden. Um die Tests auszuführen, navigieren Sie zum `…/places-scripts/import/` Ordner und geben Sie `python ./places_import.py` in Terminal ein.



