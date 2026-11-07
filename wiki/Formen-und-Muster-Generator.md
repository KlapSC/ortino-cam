# Formen- und Muster-Generator im Browser (seit 0.15.0)

Der **Formen- und Muster-Generator** ist ein kostenloses Werkzeug im Community-Portal: [ortino-cam.com/tools/generator](https://ortino-cam.com/tools/generator). Du brauchst **kein Konto und keine Installation**. Du stellst ein Muster oder eine Form für CNC-Fräse oder Laser ein, siehst sofort die Vorschau und ob sie sich mit deinem Fräser ausführen lässt, und lädst sie als **SVG** oder **DXF** herunter. Fräsen kannst du die Datei in ortino.CAM oder in jeder anderen Software, die SVG oder DXF liest.

> **Ehrlich zum Stand:** Die Ampel misst die Geometrie **am Rechner**. **Kein Muster und keine Form wurde bisher gefräst oder gelasert.** Die Seite ist mit Tests und in Chromium gegen eine Nachbildung des Servers geprüft; die SVG- und DXF-Dateien liest der Importer von ortino.CAM wieder ein (Maße, Fläche und Bögen stimmen). **Nicht geprüft:** das echte Portal im Internet, die Last auf dem Dienst (die Grenzen unten sind nur auf einem Entwicklungsrechner gemessen), die Dateien in fremder CAM-Software und an einer Maschine, andere Browser als Chromium. **Der Generator erzeugt keinen G-Code.**

## Was er kann

* **Reiter »Muster«:** 37 der 39 Musterarten des Muster-Studios, 74 der 76 Vorlagen mit Vorschaubild (Waben, Sterne, Voronoi, Chevron, Fischschuppen, Kagome, Spiralen und viele mehr; mit Suche und Kategorien). Du stellst Breite und Höhe ein (10 bis 1200 mm je Seite, zusammen höchstens 360 000 mm², zum Beispiel 600 × 600 oder 1200 × 300 mm), den Zufallswert (gleicher Wert, gleiches Muster) und die Einstellungen der Art. Es fehlen **Text aus Löchern** und **Bild als Lochraster**: Sie brauchen eine Schrift oder ein Bild, das der Dienst nicht annimmt; dafür gibt es das [Muster-Studio](Zeichnen-und-Importieren) im Programm.
* **Fräsbarkeits-Ampel:** Du gibst den **Durchmesser deines Fräsers** und den **Mindeststeg** ein. Die Seite meldet »Gut fräsbar«, »Fräsbar mit Hinweisen« oder »So nicht fräsbar«, nennt Messwerte (dünnster Steg, schmalste Öffnung, Inseln, Schnittlänge) und bietet Korrekturen mit einem Klick an (zu kleine Öffnungen weglassen, dünne Stege verbreitern oder verschmelzen, Innenecken auf Fräserradius runden, Brücken). Die Fräszeit ist eine **Schätzung**. Die Voreinstellung der Seite (Fräser Ø 3,175 mm, Mindeststeg 2 mm) ist eine Annahme der Seite, nicht des Musters: Stell deinen Fräser ein.
* **Reiter »Formen«:** zehn Grundformen (Rechteck, abgerundetes Rechteck, Kreis, Ellipse, Vieleck, Stern, Herz, Zahnrad, Rosette, Langloch) mit Maßen in Millimetern. Die Formen entstehen **im Browser** und gehen auch ohne Server. Hinweise zum Fräser zeigen, was der runde Fräser an einer Form nicht ausfräsen kann (spitze Innenecken, zu schmale Zahnlücken, zu kleine Bohrungen). Das Zahnrad ist eine Zierform, kein Getriebezahnrad.
* **Herunterladen:** **SVG** (Maßstab 1:1 in Millimetern, Ebenen für Öffnungen und Umriss), **DXF** (Einheit Millimeter; Standard sind Polylinien mit Bögen, für ältere Programme gibt es »Einzelne Linien und Bögen«) und **PNG** (zum Ansehen). **Bögen bleiben Bögen**, nicht viele kleine Strecken. Die Öffnungen innen kommen zuerst, der Umriss zuletzt; den Umriss kannst du weglassen.
* **Eigene Vorlagen:** Die Sparte **»Eigene«** speichert deine Einstellungen im Browser und tauscht sie als Datei `.ortino-vorlage.json` aus, im selben Format wie das Programm (siehe [Eigene Vorlagen](Eigene-Vorlagen)). Die Seite sagt es selbst: Die Vorlagen sind nur in diesem Browser gespeichert. Sichere sie als Datei.

## Was er nicht kann

* **Kein G-Code.** G-Code entsteht erst in ortino.CAM: SVG oder DXF importieren (siehe [Zeichnen und Importieren](Zeichnen-und-Importieren)), den Fräser und die Bearbeitung wählen (zum Beispiel Tasche oder Profil), prüfen, simulieren, dann erst fräsen.
* Keine Text- und Bildmuster, keine Drehung, kein Reiter für Reliefs. Einen Knopf »In ortino.CAM öffnen« gibt es für Muster noch nicht; du speicherst die Datei und importierst sie, oder du importierst die Vorlage unter »Eigene«.
* Keine Aussage darüber, ob ein Muster in deinem Material hält. Das hängt von Holz, Fräser, Maschine und Spannung ab. **Probiere es an einem Reststück.**

## Grenzen des Dienstes

Die Muster rechnet der Server des Portals. Damit er für alle da bleibt, gelten Grenzen (Voreinstellung des Portals): höchstens **60 Berechnungen je Minute** und Adresse, höchstens vier Rechnungen gleichzeitig im ganzen Server, nach **10 Sekunden** bricht eine Rechnung ab. Dann zeigt die Seite eine Meldung mit Lösung (kleinere Fläche, größere Zellen, weniger Korrekturen oder das Muster im Programm rechnen) und die letzte Vorschau bleibt gedimmt stehen.

## Datenschutz

* Die Seite braucht **kein Konto**, setzt **keine Cookies** und lädt **nichts von Dritten**.
* **Formen** werden im Browser gerechnet; dabei geht nichts an den Server.
* **Muster** rechnet der Server aus den eingestellten Werten (Musterart, Größe, Zufallswert, Einstellungen als Zahlen, Materialdicke für die Zeitschätzung). Er schreibt sie **weder in eine Datenbank noch in eine Datei noch ins Betriebsprotokoll**. Im Betriebsprotokoll steht je Aufruf nur Methode, Pfad, Statuscode, Dauer und eine Anfragenummer, **nicht die IP-Adresse und nicht der Inhalt**. Im Arbeitsspeicher hält der Server nur die Zähler der Ratenbegrenzung je Adresse (nach einem Neustart weg) und einige zuletzt berechnete Muster. Ein vorgeschalteter Webserver kann Zugriffe wie bei jeder Seite des Portals mit IP-Adresse protokollieren; Einzelheiten stehen in der [Datenschutzerklärung des Portals](https://ortino-cam.com/privacy).
* **Eigene Vorlagen** schreibt die Seite **nur nach deinem Klick** auf »Als eigene Vorlage speichern« in den Speicher deines Browsers. Der Server erfährt davon nichts.

## Weiter

* [Eigene Vorlagen](Eigene-Vorlagen) (im Programm, gleiches Dateiformat)
* [Zeichnen und Importieren](Zeichnen-und-Importieren) (Muster-Studio, SVG und DXF importieren)
* [Community-Portal](Community-Portal)
