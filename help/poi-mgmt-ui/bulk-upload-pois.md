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

Die Schaltfläche **POIs importieren** im Places-Dienst kann verwendet werden, um neue POIs mit einer CSV-Datei stapelweise hochzuladen. Eine Beispiel-Tabellenvorlage wird bereitgestellt, um anzuzeigen, welche Datenspalten erforderlich sind und wie optionale benutzerdefinierte Metadaten hinzugefügt werden.

![Bildschirm für den Massenimport](/help/assets/Bulk-import.png)

In diesem Video wird der Prozess für den Massenimport und die Massenbearbeitung gezeigt:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places-Dienst - Massen-Import und -Bearbeiten von POIs](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python-API-Skripte

Es wurde eine Reihe von Python-Skripten erstellt, um den Batch-Import von POIs aus einer CSV-Datei in eine POI-Datenbank mithilfe der Web Service-APIs zu vereinfachen. Diese Skripte können von diesem Open-Source-Skript [git repo](https://github.com/adobe/places-scripts) heruntergeladen werden.

Bevor Sie diese Skripte ausführen, lesen Sie *Voraussetzungen für den Benutzerzugriff* in der [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md) , um auf die Webdienst-APIs zuzugreifen.

Im Folgenden finden Sie einige Informationen zu den Skripten:

>[!TIP]
>
>Diese Informationen sind auch in einer Readme-Datei im [git repo](https://github.com/adobe/places-scripts) enthalten.

## CSV-Datei

Eine .csv-Beispieldatei, `places_sample.csv`, ist Teil dieses Pakets und enthält die erforderlichen Kopfzeilen und eine Reihe von Beispieldaten. Diese Kopfzeilen sind alle in Kleinbuchstaben und entsprechen den reservierten Metadatenschlüsseln, die in der Places-Datenbank verwendet werden. Spalten, die Sie zur .csv-Datei hinzufügen, werden der POI-Datenbank in einem separaten Metadatenabschnitt für jeden POI als Schlüssel-Wert-Paare hinzugefügt und der Header-Wert wird als Schlüssel verwendet.

Im Folgenden finden Sie eine Liste der Spalten und der Werte, die Sie verwenden müssen:

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

Die Werte der folgenden Spalten werden in der Benutzeroberfläche von Places Service verwendet:

* Farbe, die als Farbe des Pins verwendet wird, der den Standort des POI in der UI-Zuordnung des Places-Dienstes darstellt.
   * Die gültigen Werte sind &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B und #3DC8DE und &quot;&quot;.
   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche des Places Service Blau als Standardfarbe.

     Die Werte entsprechen blau (#3E76D0), violett (#AA99E8), fuschia (#DC2ABA), orange (#FC685B), hellorange (#FC962E), gelb (#F6C436), hellgrün (#BECE5D), grün (#66 1B56B) bzw. hellblau (#3DC8DE).

* -Symbol, das als Symbol auf dem Pin verwendet wird, das den Standort des POI auf der UI-Karte des Places-Dienstes darstellt.

   * Die gültigen Werte sind &quot;&quot;, shop, hotelbed, car, flieger, train, ship, ship, stadium, amusementpark, anchor, beaker, bell, bid, book, box, briefcase, browse, bürste, building, rechner, kamera, uhr, flashlight, folgen, spiel, wild, männlich, geschenk, hammer, herz, home, launch, lightbulb, geld, pin, pin, pin, pin, pin, pin, pin, pin, pin, pin, pin, pin, pin, pin, pin, posten, posten, Band, ShoppingCart, Stern, Ziel, Teekopf, DaumenDown, DaumenUp, Falle, Trophäe, Schraubenschlüssel.

     Die Symbolwerte werden in der Reihenfolge aufgelistet, in der sie in der folgenden Abbildung dargestellt werden:

     ![ Symbole in der Benutzeroberfläche](/help/assets/UI_icons.png)

   * Wenn der Wert leer gelassen wird, verwendet die Benutzeroberfläche den Stern als Standardsymbol.

* Spalten, die nicht erwähnt werden, können leer gelassen werden.

## Ausführen des Skripts

1. Laden Sie Dateien aus dem [git repo](https://github.com/adobe/places-scripts) in Ihr lokales Verzeichnis herunter.
1. Öffnen Sie in einem Texteditor die Datei `config.py` und führen Sie die folgenden Aufgaben aus:

   a. Bearbeiten Sie die folgenden Variablenwerte als Zeichenfolgen:

   * `csv_file_path`

     Dies ist der Pfad zu Ihrer `.csv` -Datei.

   * `access_code`

     Dies ist Ihr Zugriffscode, der über den Aufruf an Adobe IMS abgerufen wurde. Informationen zum Abrufen dieses Zugriffscodes finden Sie unter *Voraussetzungen für den Benutzerzugriff* in der [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     Die Experience Cloud orgID, in die die Zielpunkte importiert werden sollen. Informationen zum Abrufen der Organisations-ID finden Sie unter *Voraussetzungen für den Benutzerzugriff* in der [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Dies ist Ihr Places-REST-API-Schlüssel, den Sie von Ihrer Adobe I/O Places-Integration erhalten haben. Informationen zum Abrufen des API-Schlüssels finden Sie unter *Voraussetzungen für den Benutzerzugriff* in der [Übersicht über die Integration und Voraussetzungen](/help/web-service-api/adobe-i-o-integration.md).

   b. Speichern Sie Ihre Änderungen.

1. Navigieren Sie in einem Terminal-Fenster zum Ordner &quot;`…/places-scripts/import/`&quot;.
1. Geben Sie `python ./places_import.py` ein und drücken Sie die Taste **[!UICONTROL enter]** (**[!UICONTROL return]**).


## CSV-Prüfungen vor dem Import

Das Skript führt zunächst die folgenden Prüfungen der .csv -Datei durch:

* Gibt an, ob eine `.csv` -Datei angegeben wurde.
* Ob der Dateipfad gültig ist.
* Gibt an, ob die reservierten Metadaten-Header enthalten sind.

  Die reservierten Metadaten-Header sind lib_id, name, description, type, longitude, Breitengrad, Radius, Land, Bundesland, Stadt, Straße, Kategorie, Symbol und Farbe.

  >[!TIP]
  >
  >Die Kopfzeilen sind alle in Kleinbuchstaben und können in beliebiger Reihenfolge aufgelistet werden.

* Überprüft die Werte der im Abschnitt CSV-Datei angegebenen Spalten.

Wenn Fehler gefunden werden, werden die Fehler vom Skript ausgegeben und abgebrochen. Wenn keine Fehler gefunden werden, versucht das Skript, die POIs in Stapeln von 1000 zu importieren. Wenn der Batch erfolgreich importiert wurde, zeigt das Skript den Statuscode 200 an. Wenn der Batch nicht erfolgreich importiert wurde, werden Fehler gemeldet.

## Unit-Tests

Unit-Tests befinden sich in der Datei &quot;`tests.py`&quot;, sollten vor jeder Pull-Anforderung ausgeführt werden und sollten alle bestehen. Zusätzliche Tests sollten mit neuem Code hinzugefügt werden. Um die Tests auszuführen, navigieren Sie zum Ordner &quot;`…/places-scripts/import/`&quot;und geben Sie im Terminal &quot;`python ./places_import.py`&quot;ein.
