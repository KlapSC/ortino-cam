# Eigene Vorlagen und der Dialog »Formen« (seit 0.15.0)

Im **Muster-Studio** und im **Relief-Studio** kannst du einen eingestellten Stand als **eigene Vorlage** speichern und später wieder verwenden. Dazu gibt es einen neuen Dialog **»Formen«** mit zehn Grundformen. Eigene Vorlagen stehen in der Sparte **»Eigene«**, dem ersten Reiter der Galerie. Dieselbe Datei liest und schreibt auch der [Formen- und Muster-Generator](Formen-und-Muster-Generator) im Browser, du kannst dort gespeicherte Vorlagen also im Programm importieren.

> **Ehrlich zum Stand:** Alles ist mit Tests (Vitest) und im Browser (Chromium) mit dem echten Rechenkern geprüft, auch mit Dateien, die der Code des Web-Generators erzeugt hat. **Nichts davon wurde gefräst.** **Nie unter Windows (WebView2) geprüft:** ob gespeicherte Vorlagen dort einen Neustart, ein Update oder eine Windows-Bereinigung überstehen, ob der Dateidownload dort einen Speichern-Dialog zeigt und ob das Ablegen von Dateien dort geht. **Wer sichergehen will, sichert mit »Alle sichern« eine Datei und hebt sie auf.**

## Eine Vorlage speichern

1. Öffne das **Muster-Studio** oder das **Relief-Studio** (Werkzeugpalette oder Befehlspalette `Strg+K`: »Muster & Reliefs …«) oder den Dialog **»Formen«** (unten) und stelle ein, was du behalten willst.
2. Wähle rechts oben **»Als eigene Vorlage speichern«** und gib einen Namen ein (höchstens 80 Zeichen; vorgeschlagen werden Art und Datum).
3. Die Vorlage steht danach in der Sparte **»Eigene«**, die neueste zuerst. Dieselbe Vorlage wird nicht doppelt gespeichert.

Was gespeichert wird:

* **Muster:** die Musterart, der Zufallswert (Seed), **alle** Einstellungen als Zahlen und die Fläche (auch Drehung, Text und Schrift, soweit eingestellt).
* **Relief:** Größe, Tiefe, Zufallswert, Regler, Nachbearbeitung, Rand und die Ebenen mit ihren Quellen und Einstellungen.
* **Form:** die Form mit ihren Maßen (Millimeter) und Einstellungen.

## Die Sparte »Eigene«

* **Karten** mit Vorschau (Muster und Relief werden live vom Rechenkern gerechnet wie die übrigen Karten, Formen als Zeichnung mit Bögen), Name, Datum und Maßen. Ein Klick **verwendet** die Vorlage.
* **Umbenennen**, **Als Datei sichern** (eine Vorlage), **Löschen** (mit Rückfrage; wer sie nicht als Datei gesichert hat, hat sie danach nicht mehr).
* **Importieren:** Dateien wählen (bis zu zehn auf einmal) oder auf die Sparte ziehen. Muster, Formen und Reliefs aus einer Datei landen jeweils in der Sparte ihrer eigenen Auswahl; die Meldung zählt nach Art. Dieselbe Vorlage nochmals zu importieren ändert nichts.
* **Alle sichern:** alle eigenen Vorlagen in eine Datei.
* **Neu erstellen:** beginnt mit den Standardwerten (beim Muster die der gewählten Art, beim Relief eine Ebene, bei der Form die Grundform); bei Muster und Relief öffnet sich der Abschnitt »Erweitert«.
* Die Zeile »x von 200 Vorlagen gespeichert« zeigt, wie viel Platz noch ist.

**Verwenden:** Eine eigene Vorlage setzt sich wie eine mitgelieferte ein. Ein Muster kommt in der Größe der Vorlage (höchstens die gewählte Fläche) in die Mitte der Fläche; danach lässt es sich ändern, und »Fräsen einrichten« geht wie sonst. Ein Relief wird höchstens 90 % der Platte groß, mittig, mit höchstens 60 % der Plattendicke als Tiefe. Werte außerhalb der Bereiche dieser Programmversion werden begrenzt, Unbekanntes entfällt; das Programm sagt es mit »Nicht übernommen: …«. Kennt diese Programmversion die Musterart oder die Quelle einer Vorlage nicht, zeigt die Karte »nicht verfügbar« mit dem Grund.

## Der Dialog »Formen«

Der Dialog **»Formen«** gibt es seit 0.15.0. Du öffnest ihn im Schritt »Design« über die Befehlspalette (`Strg+K`: »Formen: Grundformen und eigene …«) oder über das Formen-Symbol im Kopf der Galerie des Muster-Studios. Er bietet zehn Grundformen: **Rechteck, abgerundetes Rechteck, Kreis, Ellipse, Vieleck, Stern, Herz, Zahnrad, Rosette und Langloch**. Du stellst die Maße in Millimetern ein, siehst die Vorschau und fügst die Form mit **»Auf Platte einfügen«** mittig auf die aktive Platte ein. Auch Formen lassen sich als eigene Vorlage speichern.

* Rechteck (auch abgerundet und als Langloch), Kreis, Ellipse, Vieleck und Stern kommen als die entsprechenden **Formen des Programms** auf die Platte, Herz, Zahnrad, Rosette sowie Vieleck und Stern mit Eckenradius als Pfad. Rundungen bleiben **echte Kreisbögen**, nicht viele kleine Strecken.
* Das **Zahnrad** ist eine Zierform mit Trapezzähnen, **kein Getriebezahnrad**. Das **Herz** hat ein festes Seitenverhältnis (Höhe etwa 0,91 · Breite).
* Passt eine Eingabe nicht (zum Beispiel ein Innendurchmesser größer als der Durchmesser), sagt der Dialog es mit der Lösung; ein zu großer Radius wird begrenzt, mit Hinweis.
* Ist die Form größer als die Platte, warnt der Dialog.

## Dateien und Austausch

Eine Vorlage ist eine **JSON-Datei** (UTF-8) mit der Endung `.ortino-vorlage.json`. Sie nennt das Format (`ortino-vorlage`, Version 1), die Art (`muster`, `form` oder `relief`), den Namen, den Zeitpunkt und die Einstellungen (nur Zahlen, Texte und Wahrheitswerte, nie Bilder und nie etwas, das ausgeführt wird). **Alle sichern** schreibt eine Datei `ortino-vorlagen-<Datum>.ortino-vorlage.json` mit der Liste. Das Programm prüft jede Datei streng: höchstens 1 MB, höchstens 200 Vorlagen je Datei, gültige Zeichen im Namen, bekannte Felder. Eine kaputte Datei oder ein kaputter Eintrag ergibt eine Meldung mit Ursache und Lösung, nie einen Absturz; hat eine Datei eine neuere Version, als das Programm kennt, sagt es das und bittet um ein Update. Weil das Format dasselbe ist, kannst du Dateien aus dem [Online-Generator](Formen-und-Muster-Generator) hier importieren (Formen bleiben dabei echte Formen) und Dateien des Programms weitergeben.

## Wo die Vorlagen liegen

Eigene Vorlagen liegen im **Speicher der Oberfläche** des Programms (`localStorage`, wie bei einer Webseite im Browser), bis zu 200 Vorlagen und etwa 2 MB. Sie liegen **nicht** im Datenordner, **nicht** im Projekt und **nicht** in der [Sicherung im Portal](Sicherung-im-Portal) und wandern nicht von selbst auf einen anderen Rechner. Ist der Speicher nicht benutzbar, arbeitet das Programm mit den Vorlagen weiter, solange es geöffnet ist, und sagt es. Ist die gespeicherte Liste nicht lesbar, überspringt das Programm sie, überschreibt sie nicht blind und hebt eine Kopie auf.

**Windows (WebView2):** Der Speicher gehört zum Profil des Programmfensters. Ob die Vorlagen dort einen Neustart, ein Update oder eine Bereinigung der WebView2-Daten überstehen, ist **nicht geprüft**. Deshalb: **»Alle sichern« und die Datei aufheben**, besonders vor einem Update.

## Grenzen

* **Muster aus einem Bild** (»Bild als Lochraster«) lassen sich nicht speichern: Bilddaten gehören nicht in eine Vorlage. Der Knopf sagt es.
* **Reliefs:** Von den 62 mitgelieferten Vorlagen lassen sich 60 speichern, nicht **»Bild«** und **»Formen wölben«**. Reliefs aus einem **Foto**, **Höhenbild**, **3D-Modell**, einer **Maske**, aus **Komponenten** oder mit **Pinselstrichen** werden abgelehnt: Der Knopf ist dann gesperrt und nennt die Ursache.
* Eine Vorlage hält **Einstellungen**, keine Platte und keine Lage auf der Platte.
* Höchstens **200 Vorlagen** und etwa **2 MB** im Speicher, eine Datei höchstens **1 MB**.
* Nicht im Web-Designer des Portals.
* Alles nur gerechnet, **nichts gefräst**; die Ampel des Muster-Studios und die Kennzahlen des Relief-Studios sind Messungen am Bildschirm.

## Weiter

* [Zeichnen und Importieren](Zeichnen-und-Importieren) (Muster-Studio)
* [Bearbeitungen](Bearbeitungen) (Relief-Studio)
* [Formen- und Muster-Generator](Formen-und-Muster-Generator) (im Browser)
* [Sicherung im Portal](Sicherung-im-Portal)
